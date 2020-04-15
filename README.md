The purpose of this project is to take in readings from various sensors (Light and Temperature) and store them in a EEprom. I re-started this project because I wanted to log temperature and the amount of light in a particular area for a garden. I wanted it to be small and not be a full fledged datalogger with a transmitter.

Features:
* Capacitor Backup that will last at the very least 12 hours (During the night)
* Solar charging during the day
* Integrated ORing power circuit so it will charge the capacitor and run the supporting circuitry
* According to my calculations, for a whole year of 1 reading per hour every day I will need about 8kb of memory per sensor. ADC readings iwll be 8 bits each. In practice there's no need for a 10 bit ADC.
* 32kHz Clock run from Timer 1 for accurate timing
* Why Supercapacitor? Temperature range pretty much. Lithium's only go down to 0C and often times temperatures dip below that. Supercapacitors have a range of -40C to 60C which covers the range of outdoor temperatures. 
* Ive integrated a set of UART commands to feedback the status of the micro. It will always take data, there is no stop.
* Upgraded the caps from 3F to 2x6F for a total of 12F. This should last about 27 hours at 370uA consumption. I never could figure out where that is all going, but its not the micro. It only takes 2-3 minutes to charge in full sun though. So even if its cloudy or the sun panel isnt efficient enough, it only needs a few minutes to charge fully. 
* Note: When sending UART commands a "1" has to come before it, so "1a" to read the EEprom. This is by design to wake up the micro so it can recieve stuff properly.
* The Micro Keeps track of the current EEprom address. One issue is that if power ever does get low enough, it will lose the current EEprom address and therefore return to 0 and then all data will be lost. I could have dumped in the EEprom address into the micro's own EEprom and store it if power gets low, but I chose not to.


Commands are as follows:
* "1a" = Read EEprom
* "1E" = Erase EEprom
* "1q" = Status, spits out Seconds,Minutes,MaxAddress,Temp,Solar in that order
* "1t" = current time in MM:SS. Does not track hours passed. 
* "1m" = Used Memory Locations. Shows how much memory has been written to. Currently, two bytes get written into the EEprom



