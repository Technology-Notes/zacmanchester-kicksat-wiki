To program the Sprite we'll be using a piece of software called [Energia](http://energia.nu/). Energia is a port of the [Arduino](http://arduino.cc/) environment and libraries to the Texas Instruments MSP430 microcontroller which is used on the Sprite. If you've ever programmed an Arduino, it should be very familiar. If you've never programmed a microcontroller before, I'd recommend having a look through the [documentation](http://arduino.cc/en/Reference/HomePage) and [examples](http://arduino.cc/en/Tutorial/HomePage) provided by both the [Energia](https://github.com/energia/Energia/wiki/Getting-Started) and [Arduino](http://arduino.cc/en/Guide/Environment) projects (note that not all of the examples will run on the Sprite).

## Installing Software

I've compiled a modified version of Energia for the Sprite. There are binaries and installation instructions below for Windows and Mac. Installing on Linux is also possible, but you'll have to compile it from the [source code](https://github.com/zacinaction/Energia/tree/Branch_CC430_RF_support) yourself.

### Windows
1. Download the LaunchPad (programmer) drivers for Windows: [LaunchPad CDC drivers zip file for Windows 32 and 64 bit](https://github.com/energia/Energia/raw/gh-pages/files/EZ430-UART.zip)
2. Unzip and double click DPinst.exe for Windows 32bit or DPinst64.exe for Windows 64 bit.
3. Follow the installer instructions.
4. Download the [KickSat build of Energia for Windows](https://dl.dropbox.com/u/19178351/Energia-KickSat/Energia-KickSat-Windows.zip)
5. Unzip the folder somewhere convenient
6. Run Energia by double-clicking the "Energia" icon inside the folder.

### Mac
1. Download the LaunchPad (programmer) drivers for Mac OS X: [LaunchPad CDC drivers zip file for Mac OS X](https://github.com/energia/Energia/raw/gh-pages/files/MSP430LPCDC-1.0.3b.zip)
2. Unzip and double click MSP430LPCDC 1.0.3b.pkg
3. Follow the instructions.
4. Download the [KickSat build of Energia for Mac](https://dl.dropbox.com/u/19178351/Energia-KickSat/Energia-KickSat-Mac.zip)
5. Unzip the Energia app and place it in your Applications folder. **Note:** If you're running Mountain Lion, you may have to [change your security settings to allow unsigned apps](http://www.maclife.com/article/howtos/how_tweak_settings_gatekeeper_mountain_lion).
6. Run Energia by double-clicking the Energia application

### Linux
I won't give step by step instructions here since they will vary depending on your distribution. Most recent linux distributions ship with the LaunchPad drivers already installed. To get Energia running you'll need a JDK installed as well as Ant mspgcc, and mspdebug. These are likely available through your distribution's package manager. Once you have the prerequisites installed, download or git clone the [source code](https://github.com/zacinaction/Energia/tree/Branch_CC430_RF_support), open a terminal, cd into the build directory, and type "ant run".

There are several [tutorials](http://elabz.com/msp430-in-64-bit-ubuntu-12-04-linux-the-arduino-way/) [available](http://www2.sakoman.com/OMAP/how-to-develop-msp430-launchpad-code-on-linux.html) [online](http://forum.43oh.com/topic/2184-energia-linux-installation/) for getting Energia running on linux.

## Connecting the Hardware

## Your First Sprite Program