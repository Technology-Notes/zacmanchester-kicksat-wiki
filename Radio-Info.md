### KickSat:

**Frequency:** 437.505 MHz

**Power:** 1 Watt

**Modulation:** AFSK

**Bit Rate:** 1200 bps

**Packet Format:** AX.25

The KickSat beacon radio will transmit telemetry packets with information like battery charge state, temperature, and Sprite deployment status. Standard Ham radio equipment and software can be used to receive and decode the beacon packets.

### Sprites:

**Frequency:** 437.240 MHz

**Power:** 10 mW

**Modulation:** MSK

**Encoding:** Data bits are encoded as 511 bit PRN codes (Gold Codes)

**Chip Rate:** 64 khz (this is the rate at which PRN bits are transmitted)

**Bit Rate:** 125 bps (this is the rate at which data bits are transmitted and is equal to Chip Rate / PRN Length)

**Packet Format:** Custom

Due to the low power of the Sprite transmitter, some signal processing tricks are used to ensure data can be successfully decoded with low gain antennas. The Sprite receiver is written in C++ for the GNURadio framework and is [available on GitHub](https://github.com/zacinaction/kicksat-groundstation). An automated install script is available [here](https://github.com/zacinaction/kicksat/wiki/Installing-GNURadio-(Ubuntu)).
