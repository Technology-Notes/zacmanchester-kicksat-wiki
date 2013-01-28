### Using the Serail Port for Debugging

One of the most useful things when you're debugging your code is the ability to send data from the microcontroller back to your PC. To do this we'll use the Serial class. Here's a quick example (which you can download [here](https://github.com/zacinaction/kicksat/blob/master/DevelopmentKit/Energia/SerialDemo/SerialDemo.ino)):

``` /*
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
} ```

Basically, you'll need to call `Serial.begin(9600);` in your setup function, then anywhere you'd like to send data back, call `Serial.println("Put stuff here");`. To see the data on your PC, click the "Serial Monitor" button in the top right corner of the Energia window.

### Using the Magnetometer

### Using the Gyroscope

### Using the Radio