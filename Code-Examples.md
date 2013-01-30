There are a bunch of the code examples for the Sprite development kit available [here](https://github.com/zacinaction/kicksat/tree/master/DevelopmentKit/Energia). Some of them are explained in detail below.

## Using the Serial Port for Debugging

One of the most useful things when you're debugging your code is the ability to send data from the microcontroller back to your PC. To do this we'll use the Serial class. Here's a quick example (which you can download [here](https://github.com/zacinaction/kicksat/blob/master/DevelopmentKit/Energia/SerialDemo/SerialDemo.ino)):

```
/*
  SerialDemo
  Demonstrates the use of the Serial port for sending information
  back to the host PC
*/

void setup() {
  Serial.begin(9600);
}

void loop() {
  Serial.println("Hello Earthlings\n");
  delay(1000);
}
```

Basically, you'll need to call `Serial.begin(9600);` in your setup function, then any time you'd like to send data back, call `Serial.println("Put stuff here");`.

After you compile and upload the code onto the Sprite, click the "Serial Monitor" button in the top right corner of the Energia window to read what's being sent over the serial connection. Make sure the correct serial port is selected for the serial monitor by checking under Tools->Serial Port. On a Mac you should select "/dev/cu.uart-...". On Windows you'll see a list of numbered COM ports. Just try them until you find the right one (you'll know it's right when you see text start appearing in the Serial Monitor window). 

![SerialDemo](https://dl.dropbox.com/u/19178351/GItHub%20Wiki%20Pictures/Example_SerialDemo.png)

![Hello](https://dl.dropbox.com/u/19178351/GItHub%20Wiki%20Pictures/Example_SerialHello.png)

## Using the Magnetometer

Now we'll try out one of the sensors on the Sprite. The magnetometer is a 3-axis chip from Honeywell called the HMC5883L. It's data sheet is [here](http://dlnmh9ip6v2uc.cloudfront.net/datasheets/Sensors/Magneto/HMC5883L-FDS.pdf).

We're going to read the x, y, and z values from the magnetometer and then write them to the serial port. Fire up Energia and copy and paste the following code (or [download the file here](https://github.com/zacinaction/kicksat/blob/master/DevelopmentKit/Energia/MagnetometerDemo/MagnetometerDemo.ino)).

```
#include <SpriteMag.h>

SpriteMag mag = SpriteMag();

void setup() {
  mag.init();
  Serial.begin(9600);
}

void loop() {
  
  MagneticField b = mag.read();
  
  Serial.print("x: ");
  Serial.print(b.x);
  Serial.print("    y:");
  Serial.print(b.y);
  Serial.print("    z: ");
  Serial.println(b.z);
  
  delay(250);
}
```

This code uses a few more C/C++ features than the last example. SpriteMag is a class, and we create an instance of the class (which we call "mag") at the beginning of the program. You can think of "mag" as an object or "bucket of code" representing the physical magnetometer. It collects all the code we need to interact with the magnetometer into a neat package.

In the setup function we call `mag.init()` to initialize the magnetometer. After that, you can call `mag.read()` whenever you want to read from the magnetometer. Note that `mag.read()` returns a struct called `MagneticField`. You can think of a struct as a container for data. In this case, `MagneticField` has three pieces of data - the x, y, and z components of the local magnetic field vector. We access the values by putting ".x", ".y", or ".z" after the struct name (`b.x`, `b.y`, and `b.z` in this case).

One more thing to point out in this example is the use of `Serial.print()` as well as `Serial.println()`. The difference is that `Serial.println()` prints on a new line, while `Serial.print()` continues on the same line.

Now you can hit the upload button and launch the serial monitor just like in the previous example. The values you'll see are the raw readings from the magnetometer and need to be scaled to whatever particular units you want (see the data sheet).

## Using the Gyroscope

The gyroscope on the Sprite is an ITG-3200 chip made by Invensense. Here's the [datasheet](http://www.sparkfun.com/datasheets/Sensors/Gyro/PS-ITG-3200-00-01.4.pdf).  

The ITG-3200 is a 3-axis MEMS gyro. It will tell you your instantaneous angular velocity vector (how fast you're spinning and in which direction). Like in the previous example, we're going to read the x, y, and z components of the angular velocity vector then write them to the serial port. Here's the code:

```
#include <SpriteGyro.h>

SpriteGyro gyro = SpriteGyro();

void setup() {
  gyro.init();
  Serial.begin(9600);
}

void loop() {
  
  AngularVelocity w = gyro.read();
  
  Serial.print("x: ");
  Serial.print(w.x);
  Serial.print("    y:");
  Serial.print(w.y);
  Serial.print("    z: ");
  Serial.println(w.z);
  
  delay(250);
}
```

Just like in the magnetometer example, we create an instance of the SpriteGyro class (called "gyro" in the code above), call `gyro.init()` in our `setup()` function, then call `gyro.read()` whenever we want to read from the sensor. Also like the magnetometer code, the `read()` function returns a struct containing the x, y, and z components of the vector we're measuring.

Upload the code, fire up the serial monitor, and you should be able to twist and turn your Sprite in different directions and watch the angular velocity components change. As with the magnetometer, the numbers are raw values from the sensor and must be scaled to appropriate units (see the datasheet).

You may notice that your gyro has a bias. That is, it will display a non-zero value even when the Sprite is perfectly still. This is normal. You can calibrate your gyro by noting the offset and subtracting it off the measured value.