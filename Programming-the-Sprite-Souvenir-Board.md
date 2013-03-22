The Sprite souvenir boards are populated with fully functional CC430 microcontroller / radio transceiver chips. With a few modifications they can be programmed to blink LEDs and transmit signals. This how-to guide will show you how to get started.

**Note that this guide only covers basic programming of the CC430. Some extra components need to be populated on the board to get the radio working. A future how-to guide will detail those extra steps.**

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
First, you'll need to solder headers onto the four plated holes on the right side of the Sprite board. Depending on what kind of headers you have, you may need to snap off the appropriate number (that's why they're called "breakaway").

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

Connect three jumper wires to the right-most three pins in the top row of the large header on the Launchpad. These pins are marked VCC, TEST, and RST from right to left. Make sure to connect to the pins in the top row, not the bottom. Connect your fourth jumper wire to the ground (GND) pin on the lower right of the Launchpad.

![Launchpad Wires](https://dl.dropbox.com/u/19178351/GItHub%20Wiki%20Pictures/Souvenir_LPWires.jpg)

Now connect the opposite ends of the jumper wires to the Sprite. The connections are TEST, RST, VCC, and GND, going counterclockwise from the upper right.

![Wires](https://dl.dropbox.com/u/19178351/GItHub%20Wiki%20Pictures/Souvenir_Wires.jpg)

# Blinking LEDs

Now that everything is hooked up, you're ready to run your first Sprite program. Download and install the Sprite build of Energia as documented on the [the developer kit wiki page](https://github.com/zacinaction/kicksat/wiki/Getting-started-with-the-Sprite-Development-Kit#installing-software).

Here's the code we're going to run:
```
/*
  Blink
  Turns on an LEDs on the Sprite souvenir in sequence
 */

void setup() {                
  // initialize the digital pins as outputs.
  // Pins 1-6 have LEDs connected on the Sprite Replica boards:
  pinMode(1, OUTPUT);
  pinMode(2, OUTPUT);
  pinMode(3, OUTPUT);
  pinMode(4, OUTPUT);
  pinMode(5, OUTPUT);
  pinMode(6, OUTPUT);
  
  digitalWrite(1, HIGH);   // set the LED above the "i" on
}

void loop() {
  //Turn LEDs on in sequence
  digitalWrite(6, HIGH);   // set the LED on
  delay(300);
  digitalWrite(5, HIGH);   // set the LED on
  delay(300);
  digitalWrite(4, HIGH);   // set the LED on
  delay(300);
  digitalWrite(3, HIGH);   // set the LED on
  delay(300);
  digitalWrite(2, HIGH);   // set the LED on
  delay(600);
  digitalWrite(2, LOW);    // set the LED off
  digitalWrite(3, LOW);    // set the LED off
  digitalWrite(4, LOW);    // set the LED off
  digitalWrite(5, LOW);    // set the LED off
  digitalWrite(6, LOW);    // set the LED off
  delay(600);
}
```
Once you fire up Energia and plug the Launchpad into your computer with a USB cable, copy and paste the code into the Energia window and hit "Upload".

![Energia](https://dl.dropbox.com/u/19178351/GItHub%20Wiki%20Pictures/Souvenir_Energia.png)

If all goes well, after a few seconds you should start to see the LEDs on your souvenir board light up!

![Blink](https://dl.dropbox.com/u/19178351/GItHub%20Wiki%20Pictures/Souvenir_Blink.jpg)