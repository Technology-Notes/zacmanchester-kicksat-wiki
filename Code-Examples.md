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

## Using the Gyroscope

## Using the Radio