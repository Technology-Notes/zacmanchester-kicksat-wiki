*** Note: This details how to use GCC with Eclipse to program the Sprite rather than Energia. Most people will want to use Energia as detailed [here](https://github.com/zacinaction/kicksat/wiki/Getting-started-with-the-Sprite-Development-Kit). ***

This guide will explain how to program chipsat boards using the usb programmer on TI MSP430 Launchpad boards.

## Hooking up a TI MSP430 Launchpad board to a chipsat board via SBW (spi-bi-wire)
The inexpensive TI MSP430 Launchpad board contains two halves: the lower half holds a breakout board for a microcontroller chip, the upper half holds a debugger which can be connected to a computer through USB. The upper half of this board is entirely separated from the bottom half the board, other than a common ground, via five jumper connections: VCC, TXD, RXD, RESET, and TEST. 

![TI MSP430 Launchpad](http://i.imgur.com/OuiAB.png)

If not already done so, remove the five jumpers on these five connections. To program chipsat boards, the following four connections are needed for a SBW interface: VCC, GROUND, TEST, and RESET. Connect these four connections to the corresponding pins on a chipsat board (note, there is a ground connection on the bottom half of the TI MSP430 Launchpad board which can be used). When plugged into a computer USB port, this board will automatically supply power to a chipsat board.

## Programming and debugging a chipsat board in Xubuntu
### Programming through Eclipse
Assuming a project was set up as explained in the Setting Up the Dev Environment wiki page, programming the chipsat board is simply a matter of clicking a button. You first build your project by clicking the "Build All" button, or by pressing CTRL-B. This button is the fifth from the left. To upload the code to the board, you can either click the circular purple button named "use mspdebug to upload code to msp430-target", or you can right click on your project and go to MSP430->Upload to Target, or you can click MSP430 in the top taskbar, and also use "Upload to Target.

Open the console in the bottom of Eclipse to verify the program is uploaded correctly. If the console displays a message saying that it is "Initializing FET..." for a long period of time, then the Eclipse plugin is likely using its prebuilt version of mspdebug which does not currently function. It instead needs to use the mspdebug binary located at /usr/local/bin. This can be changed in Window->Preferences, and under the MSP430 tab (refer to the How to Set Up a Dev Environment wiki page for more information).

![Programming through eclipse](http://i.imgur.com/bNC5o.png)

### Programming through the terminal
The simplest way to program a chipsat board is to open a terminal window in the same directory as the .elf of your program. The following command starts up mspdebug to interface with the TI MSP430 launchpad board: `mspdebug rf2500`

If an error message appears stating the kernal driver could not be detached, operation not permitted, then you likely did not create a UDEV rule as explained in the How to Set Up a Dev Environment wiki page.

With mspdebug started, you can program a chipsat board by using the command: `prog <filename>.elf`

![Programming through the terminal](http://i.imgur.com/TwnG8.png)

### Debugging with the terminal and Eclipse
Although the MSP430 eclipse plugin allows one click debugging, the debugging environment does not correctly display numerical variables you may want to observe. The instructions for using that debugger will still be provided since it can  still be used for simply stepping through your program.

To debug with the terminal and the Zylin plugin that was set up, you must first open a terminal anywhere and open the mspdebug interface with the command `mspdebug rf2500`. Next, enter the command `gdb`. The terminal should display "Bound to port 2000. Now waiting for connection...". If it says cant bind to the port because it is already is use, try closing all terminals, eclipse, and starting again. You must leave this terminal open, however you can still use the eclipse buttons to upload code to the chipsat board at the same time.

When you are ready to debug, press the down arrow next to the debug button (looks like a bug next to the green play buttons), and select your debug configuration you made. When you select this, you should see some commands execute in the eclipse console window, and additional commands start executing on the terminal window you left open. Eclipse will ask you to switch to its debug window mode which you may accept.

![Start debugging](http://i.imgur.com/7MSWd.png)

![Debugging](http://i.imgur.com/mUtmU.png)

You are now debugging. If you did not specify a break point initially, then the debugger will enter the program. If you can not get the debugger to work correctly, press the stop button and check the terminal window to see if that stopped the debugging/stream of commands. If it did not, press CTRL-C in the terminal window until debugging stops. Next, enter the command `reset` to start the program from the beginning, and then enter `gdb` again. The message about being bound should appear again. Attempt to debug in eclipse again by executing your debug configuration under the bug icon.

Debugging is not perfect, and may sometimes stop working for no apparent reason, but stepping through your program, using breakpoints, and viewing variables all work.

Once you have debugging working, you can simplify this way of debugging to a two click process without the need for an external terminal window. You can automate the process of starting mspdebug and entering gdb by running the external tools configuration we set up by clicking the arrow next to the green play button with a toolbox and running the configuration. At the console, you should see the terminal commands we entered manually, and the final line should read "Bound to port 2000. Now waiting for connection...". If it does, you can start debugging using the same process as above minus the terminal window.

![External Tools Configuration](http://i.imgur.com/ZguPW.png)

![Wating to debug](http://i.imgur.com/XappT.png)

### Using the Eclipse MSP430 Plugin one click debugger
To use this debugger, simply click the arrow next to the bug, and choose the debug configuration you set up with the MSP430 debuger plugin in eclipse. This automates the entire process to one click. The most common error you will likely receive is that the port can not be bound because it is already in use. If this is the case, try restarting eclipse and making sure all instances of mspdebug are closed. You can additionally start `mspdebug rf2500` in a terminal, run the `gdb` command, and then exit out of it with CTRL-C to make sure you have stopped it. This debugger has step through functionality and the ability to use breakpoints, but it displays variables incorrectly if you try to do so.