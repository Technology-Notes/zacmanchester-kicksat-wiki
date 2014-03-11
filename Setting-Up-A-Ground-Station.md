## What You Need:

To set up a ground station to listen to KickSat and/or the Sprites, you need 3 things: An antenna, a low noise amplifier (LNA), and a software defined radio (SDR) interface. Below is a list of examples of hardware that should work with links to suppliers.

### Antennas:

* [Arrow Antenna 440-5](http://arrowantennas.com/arrowii/440-5ii.html). This is the one I have the most experience with and recommend, but any small hand-held Yagi antenna should work.

### LNAs:

* [Down East Microwave L432LNA](http://www.downeastmicrowave.com/PDF/l-lna.PDF)
* [Advanced Receiver P432VDG](http://www.advancedreceiver.com/page5.html)
* [RFBay LNA-440](http://rfbay.com/LNA/LNA-440.pdf)
* [dg0ve LNA70-1](http://www.dg0ve.de/en/lna70_en.htm)

### SDRs:

* [DVB-T USB Stick](http://www.nooelec.com/store/software-defined-radio/tv28tv2-sdr-dvb-t-usb-stick-set.html#.Uxu38uddVqs). The E4000 and R820T chipsets are best.
* [Funcube Dongle](http://funcubedongle.3dcartstores.com/FUNcube-Dongle-Pro-A20_p_27.html)

### Odds 'n Ends:

* [MCX to BNC Adapter](http://www.amazon.com/Generic-Female-Right-Angle-Adapter/dp/B00EQ1UZC2/ref=sr_1_16?ie=UTF8&qid=1394326600&sr=8-16&keywords=mcx+to+bnc) to connect a DVB-T stick to an Arrow antenna.
* [SMA to BNC Adapter](http://www.amazon.com/Female-Male-Plug-Coax-Adapter/dp/B002A6CWDA/ref=sr_1_2?ie=UTF8&qid=1394327837&sr=8-2&keywords=sma+to+bnc) to connect a Funcube dongle to an Arrow antenna.
* [BNC Cables](http://www.amazon.com/s/ref=nb_sb_noss_1?url=search-alias%3Delectronics&field-keywords=BNC%20RG58). You'll want a couple of these. Make sure they're 50 Ohms (RG58 cable will work).

## Putting it Together:

### Software:

You'll need to have GNURadio installed to run the Sprite receiver. I've tried recording .wav files with several other SDR programs (SDR#, HDSDR, etc.) and demodulating them later with GNURadio with limited success. It seems most Ham radio SDR programs are optimized for audio and do some unpredictable things when not used in their intended application. If you want to record .wav files, please use GNURadio as it is known to work reliably.

The best solution is to install GNURadio natively on your system. If you have the latest Ubuntu Linux (13.10 as of this writing), this is pretty painless - just follow the [instruction elsewhere on this wiki](https://github.com/zacinaction/kicksat/wiki/Installing-GNURadio-(Ubuntu)). If you are unable to install Ubuntu, then you can run the radio stuff in a virtual machine on Windows or MacOS X. You'll need to install the free [VMWare Player](https://my.vmware.com/web/vmware/free#desktop_end_user_computing/vmware_player/6_0) for Windows or [VMWare Fusion](https://my.vmware.com/web/vmware/free#desktop_end_user_computing/vmware_player/6_0) for Mac (not free but has a trial period).
