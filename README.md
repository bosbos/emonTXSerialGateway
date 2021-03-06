# emonTXSerialGateway
ESP8266 emonTX Serial to EmonCMS gateway

## What is it
This is a small ESP8266 (Arduino IDE support) script that forwards the data it receives over Serial to EmonCMS.

Total cost should be something like $4, a lot less than a RaspberryPI gateway plus a RF module. On top of it all, I am programming my ESP8266 modules with the same IDE and language and programmer I am using for my emonTX, already had everything.

## What do you use it for
I use it to forward all my [emonTX v3](http://openenergymonitor.org/emon/modules/emonTxV3) readings to [EmonCMS](http://emoncms.org/) without needing to have a RaspberryPI gateway with a RMF12PI at all.
It is however not limited just to emonTX, any device that can output serial data could be made to work like this.

## Requirements
- ESP8266 module with separate power supply
  ESP-01 will do, schematic soon
- ground of ESP module must be connected to ground of sending device
- Serial baudrate to be the same on both sending device and ESP module
- Serial sending format to be
```
NODEID VALUE1 VALUE2 VALUE3 VALUE....
```
  This format is the format that most of the [emonTX sketches](https://github.com/openenergymonitor/emonTxFirmware/tree/master/emonTxV3) output. In some case you will need to enable debug, in others you will need just a small modification to the sketch to add NODEID or to remove extraneous text amongst values.

## Getting started
- download this sketch
- download all the libraries mentioned in the sketch and put them in your Arduino IDE's libraries folder
- get and add your emoncms.org write key to the sketch
- modify your emonTX sketch to print in the requiered format
- burn the sketch to your ESP module
- connect ground to ground and emonTX TX line to ESP RX line
  (on emonTX v3.4 the TX line is labeled RX as on the programmer, connect to RX)
- start them up
- if you included the WiFiManager library it will start an access point for you to easily configure which access point the ESP will connect to
- after it restarts you should start seeing data in your EmonCMS account


#### TODO
- add MQTT support
- more error checking
- ... ideas, pull requests, issue reports are all welcome :)
