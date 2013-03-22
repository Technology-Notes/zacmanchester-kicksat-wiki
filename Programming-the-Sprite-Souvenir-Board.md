The Sprite souvenir boards are populated with fully functional CC430 microcontroller / radio transceiver chips. With a few modifications they can be programmed to blink LEDs and transmit signals. This how-to guide will show you how to get started.

# Supplies
In addition to a Sprite souvenir board, you'll need:
* [1 TI MSP430 Launchpad Kit](https://www.sparkfun.com/products/10020)
* [4 Breakaway Headers](https://www.sparkfun.com/products/116)
* [4 Jumper Wires](https://www.sparkfun.com/products/9389)
* A soldering iron
* Solder

I provided links to SparkFun above, but you can get this stuff from any decent purveyor of electronic components.

![Supplies](https://dl.dropbox.com/u/19178351/GItHub%20Wiki%20Pictures/Souvenir_Supplies.jpg)

# Soldering On The Headers
First, you'll need to solder headers onto the four plated holes on the right side of the Sprite board.

![Holes](https://dl.dropbox.com/u/19178351/GItHub%20Wiki%20Pictures/Souvenir_Holes.jpg)

Place the headers in the board so that the short ends are sticking out the bottom and the long ends are sticking out the top. A vice or a friend with a pair of tweezers to hold the pins in place while you solder might be helpful for this part.

![Vice](https://dl.dropbox.com/u/19178351/GItHub%20Wiki%20Pictures/Souvenir_Vice.jpg)

Now solder the back side of each pin in place with a small bead of solder.

![Soldering](https://dl.dropbox.com/u/19178351/GItHub%20Wiki%20Pictures/Souvenir_Soldering.jpg)

Here's what the finished product should look like:

![Back](https://dl.dropbox.com/u/19178351/GItHub%20Wiki%20Pictures/Souvenir_Back.jpg)
![Front](https://dl.dropbox.com/u/19178351/GItHub%20Wiki%20Pictures/Souvenir_Front.jpg)

# Connecting The Programmer

Unbox the Launchpad and remove all of the jumpers on the top of the board. It should look like this:

![Launchpad](https://dl.dropbox.com/u/19178351/GItHub%20Wiki%20Pictures/Souvenir_Launchpad.jpg)

Connect three jumper wires to the right-most three pins in the top row of the large header on the Launchpad. These pins are marked VCC, TEST, and RST from right to left. Make sure to connect to the pins in the top row, not the bottom.Connect your fourth jumper wire to the ground (GND) pin on the lower right of the Launchpad.

![Launchpad Wires](https://dl.dropbox.com/u/19178351/GItHub%20Wiki%20Pictures/Souvenir_LPWires.jpg)

Now connect the opposite ends of the jumper wires to the Sprite. The connections are TEST, RST, VCC, GND, going counterclockwise from the upper right.

![Wires](https://dl.dropbox.com/u/19178351/GItHub%20Wiki%20Pictures/Souvenir_Wires.jpg)

# Blinking LEDs

Now that everything is hooked up, you're ready to run your first Sprite program. Download and install the Sprite build of Energia as documented on the developer kit page.

