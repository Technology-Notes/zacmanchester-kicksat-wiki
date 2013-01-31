- Fresh install of Ubuntu 12.10 (Mint 14)
- Install gnuradio, gnuradio-dev, cmake, git, libboost-all-dev, libusb-1.0-0, libusb-1.0-0-dev, libfftw3-dev, swig

## Install RTL-SDR driver
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

## Install Sprite GNURadio Blocks
- git clone git://github.com/zacinaction/kicksat
- cd kicksat/GroundStation/GNURadio/gr-sprite
- mkdir build
- cd build
- cmake ..
- make
- sudo make install

