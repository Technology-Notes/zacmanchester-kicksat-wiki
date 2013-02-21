Thankfully the latest version of Ubuntu has a recent enough version of GNURadio for our purposes (3.6.1 at the time of this writing). The following steps will detail how to get a working GNURadio setup for receiving Sprite signals. I started with a fresh install of [Linux Mint 14 XFCE](http://www.linuxmint.com/edition.php?id=127), but any Ubuntu-based distro should work just fine.

## Install Prerequisites
Using the package manager (either Synaptic from the GUI or apt-get from the terminal), install the following:
- gnuradio
- gnuradio-dev
- cmake
- git
- libboost-all-dev
- libusb-1.0-0
- libusb-1.0-0-dev
- libfftw3-dev, swig

## Install RTL-SDR Driver
This is the driver that allows us to use the USB radio dongle. Open a terminal, cd into your favorite directory (probably somewhere in your home folder), and run the following commands in order:
- git clone git://git.osmocom.org/rtl-sdr.git
- cd rtl-sdr
- mkdir build
- cd build
- cmake .. -DINSTALL_UDEV_RULES=ON
- make
- sudo make install

## Install RTL-SDR GNURadio Block
Once again, open a terminal, cd into a directory you like, and run the following commands in order:
- git clone git://git.osmocom.org/gr-osmosdr
- cd gr-osmosdr
- mkdir build
- cd build
- cmake ..
- make
- sudo make install

The last thing you'll need to do here is to create a text file ~/.gnuradio/config.conf with the following contents:
```
[grc]
local_blocks_path=/usr/local/share/gnuradio/grc/blocks
```

## Install Sprite GNURadio Blocks
Now were going to install the Sprite reciever blocks for GNURadio. Same drill as before...
- git clone git://github.com/zacinaction/kicksat
- cd kicksat/GroundStation/GNURadio/gr-sprite
- mkdir build
- cd build
- cmake ..
- make
- sudo make install
- sudo ldconfig

### That's it! You should now have a working GNURadio installation.
