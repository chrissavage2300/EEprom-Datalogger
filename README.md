The purpose of this project is to take in readings from various sensors (Light and Temperature) and store them in a EEprom. I re-started this project because I wanted to log temperature and the amount of light in a particular area for a garden. I wanted it to be small and not be a full fledged datalogger with a transmitter.

Features:
* Capacitor Backup that will last at the very least 12 hours (During the night)
* Solar charging during the day
* Integrated ORing power circuit so it will charge the capacitor and run the supporting circuitry
* According to my calculations, for a whole year of 1 reading per hour every day I will need about 8kb of memory per sensor. ADC readings iwll be 8 bits each. In practice there's no need for a 10 bit ADC.
* 32kHz Clock run from Timer 1 for accurate timing
* Why Supercapacitor? Temperature range pretty much. Lithium's only go down to 0C and often times temperatures dip below that. Supercapacitors have a range of -40C to 60C which covers the range of outdoor temperatures. 

~~Apparently Li-SoCl2 batteries are a thing and have a huge temperature range. It only needs to provide roughly 50uA at all times. It roughly equates to a 1mAh battery, but I am being generous here. These are not rechargable. LiFePO4's would be good but I need to find them in a small size. ~~

Thoughts: Possibly adding a transmitter, or atleast the footprint for one for future use. The benefit of having a transmitter would be being able to see the temperature in real time. Then it just becomes a datalogger, which is what this project was spawned from. 

Transmitter choices. Only need to send a few bytes of data and not eery far either:
* RFM71, original datalogging board supports this. Original datalogging board does not have the proper super capacitor circuitry. Complex software routine.
* Cheap 433 Mhz transmitter and reciever. Possibly drift with temperature. But they are simple and I only need to send a few bytes at a time. They are also inexpensive. The ones I have now also have an integrated antenna. 
* 433Mhz Transmitter from Linx Technologies. A little bit more in price, no integrated antenna, but also use PLL's to lock frequency so they should not drift with time or temperature. Transmitter costs about $9 while the reciever costs #16. Antenna's are ~$2. Software wise the same technique that is needed on the cheaper ones would be needed here. The cheaper ones need a few bytes to turn on and get started. These may only need one or two. These modules also have a power down input pin and consume only a few nA when powered down.These also support a higher speed as well.

* HC-11 or HC-12. Uses simple UART as well. Advantage here is speed (9600 BPS). No power down circuitry. Even in sleep they still consume 22uA. These modules are roughly $6 each and come with an antenna. They are also bidirectional so both ends can talk to each other. 

* Bluetooth. Not a possiblity since the modules need to lock into each other. BT tends to search for devices. May not be low power either.

So its really a toss up betweeen the cheap 433Mhz and the Linx technology RF modules.
