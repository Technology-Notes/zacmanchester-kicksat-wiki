**If you have questions, please ask them on the [KickSat-gs Google Group](https://groups.google.com/forum/#!forum/kicksat-gs)**

### KickSat:

* **Frequency:** 437.505 MHz
* **Power:** 1 Watt
* **Modulation:** AFSK
* **Bit Rate:** 1200 bps
* **Packet Format:** AX.25

The KickSat beacon radio will transmit telemetry packets with information like battery charge state, temperature, and Sprite deployment status. Packets will be transmitted every 30 seconds when the satellite is powered on and every 250 seconds when it is in charging mode. Standard Ham radio equipment and software can be used to receive and decode the beacon packets (e.g. the fantastic [GQRX](http://gqrx.dk/)).

Here is the initial TLE for KickSat from the launch vehicle (Updated Apr. 18, 2014). I will continue to update this TLE as the mission progresses.
```
CRS3-OPM
1 99999U          14108.81636063  .00001338  00000-0  59407-5 0 00000
2 99999 051.6860 036.7175 0016056 261.5992 149.6458 15.83392889000018
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

