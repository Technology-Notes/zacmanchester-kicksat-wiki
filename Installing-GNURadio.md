Thankfully the latest version of Ubuntu has a recent enough version of GNURadio for our purposes (3.6.1 at the time of this writing). The following steps will detail how to get a working GNURadio setup for receiving Sprite signals. I started with a fresh install of [Ubuntu](http://www.ubuntu.com/download/desktop), but any Ubuntu-based distro (Kubunut, Xubuntu, Mint, etc.) should work just fine.

## Install Prerequisites
Open a terminal and run the following command:
```
sudo apt-get install gnuradio gnuradio-dev cmake git libboost-all-dev libusb-1.0-0 libusb-1.0-0-dev libfftw3-dev swig python-numpy
```
You'll be asked to enter your administrator password and told about some additional packages that will be installed to cover dependencies. Hit enter and wait a few minutes while the necessary packages are downloaded and installed.
## Install RTL-SDR Driver
Once you've installed the prerequisite packages, it's time to install the driver that allows us to use the USB radio dongle. The following command will download and install the latest RTL-SDR driver:
```
cd ~ && git clone --progress git://git.osmocom.org/rtl-sdr.git && cd rtl-sdr && mkdir build && cd build && cmake .. -DINSTALL_UDEV_RULES=ON && make && sudo make install
```

## Install RTL-SDR GNURadio Block
This will install a block in GNURadio companion, allowing you to use the RTL-SDR driver from GNURadio's GUI editor. Copy and past, then execute the following in your terminal:
```
cd ~ && git clone --progress git://git.osmocom.org/gr-osmosdr && cd gr-osmosdr && mkdir build && cd build && cmake .. && make && sudo make install
```

The last thing you'll need to do here is to create a text file ~/.gnuradio/config.conf with the following contents:
```
[grc]
local_blocks_path=/usr/local/share/gnuradio/grc/blocks
```

## Install Sprite GNURadio Blocks
Now were going to install the Sprite reciever blocks for GNURadio. Same drill as before...
```
cd ~ && git clone git://github.com/zacinaction/kicksat && cd kicksat/GroundStation/GNURadio/gr-sprite && mkdir build && cd build && cmake .. && make && sudo make install && sudo ldconfig
```
### That's it! You should now have a working GNURadio installation.