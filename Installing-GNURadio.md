- Fresh install of latest version of Ubuntu, Linux Mint, etc.
- I used Linux Mint 14 XFCE
- Install gnuradio, gnuradio-dev, cmake, git, libboost-all-dev, libusb-1.0-0, libusb-1.0-0-dev, libfftw3-dev, swig

### Install RTL-SDR Driver
- git clone git://git.osmocom.org/rtl-sdr.git
- cd rtl-sdr
- mkdir build
- cd build
- cmake .. -DINSTALL_UDEV_RULES=ON
- make
- sudo make install

## Install RTL-SDR GNURadio Block
- git clone git://git.osmocom.org/gr-osmosdr
- cd gr-osmosdr
- mkdir build
- cd build
- cmake ..
- make
- sudo make install
- Create the file ~/.gnuradio/config.conf with the following contents:
```
[grc]
local_blocks_path=/usr/local/share/gnuradio/grc/blocks
```

## Install Sprite GNURadio Blocks
- git clone git://github.com/zacinaction/kicksat
- cd kicksat/GroundStation/GNURadio/gr-sprite
- mkdir build
- cd build
- cmake ..
- make
- sudo make install
- sudo ldconfig
