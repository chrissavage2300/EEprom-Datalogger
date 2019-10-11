The purpose of this project is two fold: To log data from various sensors record it over time, and also transmit it to a remote display. I re-started this project because I wanted to log temperature and the amount of light in a particular area for a garden. I wanted it to be small and not be a full fledged datalogger with a transmitter.

Features:
* Capacitor Backup that will last at the very least 12 hours (During the night)
* Integrated ORing power circuit so it will charge the capacitor and run the supporting circuitry
* According to my calculations, for a whole year of 1 reading per hour every day I will need about 8kb of memory per sensor. ADC readings iwll be 8 bits each. In practice there's no need for a 10 bit ADC.
