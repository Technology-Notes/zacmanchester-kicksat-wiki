***Caution: Please don't plug the Sprite in before reading the hardware section below - you could damage the solar cells.***

To program the Sprite we'll be using a piece of software called [Energia](http://energia.nu/). Energia is a port of the [Arduino](http://arduino.cc/) environment and libraries to the Texas Instruments MSP430 microcontroller which is used on the Sprite. If you've ever programmed an Arduino, it should be very familiar. If you've never programmed a microcontroller before, I'd recommend having a look through the [documentation](http://arduino.cc/en/Reference/HomePage) and [examples](http://arduino.cc/en/Tutorial/HomePage) provided by both the [Energia](https://github.com/energia/Energia/wiki/Getting-Started) and [Arduino](http://arduino.cc/en/Guide/Environment) projects (note that not all of the examples will run on the Sprite).

## Installing Software

We'll be using a version of Energia specially modified for the Sprite. There are binaries and installation instructions below for Windows and Mac. Installing on Linux is also possible, but you'll have to compile it from the [source code](https://github.com/zacinaction/Energia/tree/Branch_CC430_RF_support) yourself.

### Windows
1. Download the LaunchPad (programmer) drivers for Windows: [LaunchPad CDC drivers zip file for Windows 32 and 64 bit](https://github.com/energia/Energia/raw/gh-pages/files/EZ430-UART.zip)
2. Unzip and double click DPinst.exe for Windows 32bit or DPinst64.exe for Windows 64 bit.
3. Follow the installer instructions.
4. Download the [KickSat build of Energia for Windows](https://s3.amazonaws.com/KickSat/Energia-KickSat-Windows.zip)
5. Unzip the folder somewhere convenient
6. Run Energia by double-clicking the "Energia" icon inside the folder.

### Mac
1. Download the LaunchPad (programmer) drivers for Mac OS X: [LaunchPad CDC drivers zip file for Mac OS X](https://github.com/energia/Energia/raw/gh-pages/files/MSP430LPCDC-1.0.3b.zip)
2. Unzip and double click MSP430LPCDC 1.0.3b.pkg
3. Follow the installer instructions.
4. Download the [KickSat build of Energia for Mac](https://s3.amazonaws.com/KickSat/Energia-KickSat-Mac.zip)
5. Unzip the Energia app and place it in your Applications folder. **Note:** If you're running Mountain Lion, you may have to [change your security settings to allow unsigned apps](http://www.maclife.com/article/howtos/how_tweak_settings_gatekeeper_mountain_lion).
6. Run Energia by double-clicking the Energia application

### Linux
I won't give step by step instructions here since they will vary depending on your distribution. Most recent linux distributions ship with the LaunchPad drivers already installed. To get Energia running you'll need a JDK installed as well as Ant, mspgcc, and mspdebug. These are likely available through your distribution's package manager. Once you have the prerequisites installed, download or git clone --depth 1 the [source code](https://github.com/zacinaction/Energia/tree/Branch_CC430_RF_support), open a terminal, cd into the build directory, and type "ant run".

There are several [tutorials](http://elabz.com/msp430-in-64-bit-ubuntu-12-04-linux-the-arduino-way/) [available](http://www2.sakoman.com/OMAP/how-to-develop-msp430-launchpad-code-on-linux.html) [online](http://forum.43oh.com/topic/2184-energia-linux-installation/) for getting Energia running on linux.

## Connecting the Hardware
1. Unbox the development kit

    ![UnBox](https://dl.dropbox.com/u/19178351/GItHub%20Wiki%20Pictures/HowTo_UnBox.jpg)

2. Because the solar cells run at a different voltage than the programmer, they must be disconnected before plugging the Sprite into the programmer to avoid damage. To do this, remove the small jumper on the left edge of the Sprite. After the Sprite has been disconnected from the programmer, you can replace the jumper.

    ![Jumper](https://dl.dropbox.com/u/19178351/GItHub%20Wiki%20Pictures/HowTo_Jumper.jpg)

3. Plug the Sprite into the programmer.

    ![PluggedIn](https://dl.dropbox.com/u/19178351/GItHub%20Wiki%20Pictures/HowTo_PluggedIn.jpg)

4. Connect the programmer to your computer's USB port. You should see a green LED illuminate on the programmer.
5. Run Energia (see above).

## Your First Sprite Program
Once everything is connected and Energia is running it's time to write some code. We'll go through a basic example that will blink the LED on the Sprite.

1. Make sure the correct microcontroller is selected. Click Tools->Board and make sure "Launchpad w/ cc430f5137" is selected.

    ![MCU_Select](https://dl.dropbox.com/u/19178351/GItHub%20Wiki%20Pictures/HowTo_MCU_Select.jpg)

2. Click the "Open" button at the top of the Energia window, then under the "Basics" menu, select "Blink". ***Note that if you use the File->Open dialog box instead of the Open button, it will be located under examples->Basics->Blink->Blink.ino inside your Energia folder***. We'll need to modify this code slightly to work on the Sprite.

    ![Open](https://dl.dropbox.com/u/19178351/GItHub%20Wiki%20Pictures/HowTo_Open.jpg)

3. Looking at the source code, you'll notice two functions - "setup" and "loop". This is how all Arduino/Energia programs are structured. The setup code will run one time when the microcontroller first starts up. The loop code will then run repeatedly until the microcontroller is powered off. The code we've just opened is configured to blink an LED attached to pin 14, but on the Sprite the LED is attached to pin 5. Let's replace the three instances of "14" with "5".

    ![Blink](https://dl.dropbox.com/u/19178351/GItHub%20Wiki%20Pictures/HowTo_Blink.png)

4. To make sure our code compiles without any errors, click the "Verify" button (the round check mark button at the upper left of the Energia window).

    ![Verify](https://dl.dropbox.com/u/19178351/GItHub%20Wiki%20Pictures/HowTo_Verify.png)

5. Now we're ready to load our code onto the Sprite. Click the "Upload" button (located to the right of the "Verify" button).

    ![Upload](https://dl.dropbox.com/u/19178351/GItHub%20Wiki%20Pictures/HowTo_Upload.png)

6. After a few seconds, you should see the green LED on the Sprite illuminate, then turn on and off once per second.

    ![Blink](https://dl.dropbox.com/u/19178351/GItHub%20Wiki%20Pictures/HowTo_Blink.jpg)
