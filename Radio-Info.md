**If you have questions, please ask them on the [KickSat-gs Google Group](https://groups.google.com/forum/#!forum/kicksat-gs)**

### KickSat:

* **Frequency:** 437.505 MHz
* **Power:** 1 Watt
* **Modulation:** AFSK
* **Bit Rate:** 1200 bps
* **Packet Format:** AX.25

The KickSat beacon radio will transmit telemetry packets with information like battery charge state, temperature, and Sprite deployment status. Packets will be transmitted every 30 seconds when the satellite is powered on and every 250 seconds when it is in charging mode. Standard Ham radio equipment and software can be used to receive and decode the beacon packets (e.g. the fantastic [GQRX](http://gqrx.dk/)).

[CelesTrak](http://celestrak.com/NORAD/elements/cubesat.txt) now has KickSat listed in it's catalog, so you should be able to look it up by name in most satellite tracking applications. I will continue to update the TLE below once per day (last updated 4/27/14).
```
KICKSAT                 
1 39685U 14022F   14117.04766786  .00463410  94334-4  13190-2 0   215
2 39685  51.6539 350.9098 0022756 295.5675  64.2911 15.92270127  1300
```

### Sprites:

* **Frequency:** 437.240 MHz
* **Power:** 10 mW
* **Modulation:** MSK
* **Encoding:** Data bits are encoded as 511 bit PRN codes (Gold Codes)
* **Chip Rate:** 64 khz (this is the rate at which PRN bits are transmitted)
* **Bit Rate:** 125 bps (this is the rate at which data bits are transmitted and is equal to Chip Rate / PRN Length)
* **Packet Format:** Custom

All of the Sprites transmit on the same frequency. Each Sprite has a unique pair of PRN codes that it encodes its transmissions with, allowing a receiver to tell the Sprites apart (this is known as [CDMA](http://en.wikipedia.org/wiki/CDMA)). A [list of all Sprite PRN codes](https://docs.google.com/spreadsheet/ccc?key=0ArAGbHISj5okdEhBbkZiWGxBSjNmcEs4ZkgwMmNsUEE&usp=sharing) codes is available online.

Due to the low power of the Sprite transmitter, some signal processing tricks are used to ensure that data can be successfully decoded with low gain antennas. The Sprite receiver is written in C++ for the GNURadio framework and is [available on GitHub](https://github.com/zacinaction/kicksat-groundstation). An automated install script is available [here](https://github.com/zacinaction/kicksat/wiki/Installing-GNURadio-(Ubuntu)).

