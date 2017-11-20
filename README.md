# Pi-iC880a

Adapter board to interface between the Raspberry Pi and the [iC880a LoRaWAN](https://wireless-solutions.de/products/radiomodules/ic880a.html) concentrator.  It also supports an EEPROM for HAT identification, DS3231 RTC chip for maintaining time between powercycles, and a [DHT-22](http://www.hobbytronics.co.uk/rht03-humidity-temp-sensor?keyword=dht22) for temperature/humidity sensing.

This board supports using 3 different GPS modules for the timing/positioning
 1. [Adafruit Ultimate GPS module](https://www.adafruit.com/product/746) soldered onto the board.  
 1. The MT3339 GPS modules (as used on the adafruit break out board) soldered directly to the PCB.  
 1. Ublox LEA-6T soldered onto the iC880a Concentrator.
 
 ## GPS Options
 In order to support the different GPS options there are solder jumpers on the PCB to link the required lines.  There are 3 jumpers: TX, RX, PPS.  The jumpers for TX & RX need to be used whichever GPS module is in use.  The PPS link is needed if using either the Ultimate GPS, or the MT3339.
 
 ## Backup battery options
 There are also pads for 0 ohm resistors to enable a choice of which peripherals have the backup battery connected.  These can either be popuplated with 0ohm resistors, or just bridged using solder.
 
 ## Enabling the UBlox module
 All GPIOs from the iC880a board are connected to the Pi.  In order to enable the UBlox module on the iC880a a couple of these need to be configured as shown below.
 
 | Pi I/O | Function | Pin State |
 | ------ | -------- | --------- |
 |  23    |  GPS  EN | HIGH      |
 |  27    | !GPS RST | HIGH      | 
