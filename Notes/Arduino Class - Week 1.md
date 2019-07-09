## Ohm's Law
* Current is equal to the voltage divided by the resistance.
* Ex:
<code>C=V/R
C=10V/10ohms
C=1A</code>
* This can also be changed to find other values with simple Algebra.
* Ex:
<code>2A=9V/R
R*2A=9V
R=9V/2A
R=4.5ohms</code>

## PWM (Pulse Width Modulation)
* A way of controlling how long something is active within a set 
frequency.
<img 
src="http://solarhomestead.com/wp-content/uploads/2015/09/pulse-width-modulation-PWM.jpg" 
width="50%">
* Can be used to control the brightness of an led and can also be used 
to control amplitude of a audio signal. (Class D Amplifiers work under 
this principle.)

## Blinking an led with an Arduino
* First we connect our Arduino as so.
* Squiggly line is a resistor while the triangle with line is the LED. 
<img 
src="https://www.arduino.cc/en/uploads/Tutorial/ExampleCircuit_sch.png" 
width="35%">
* Then we program the Arduino with the following code.
BlinkSketch.ino
```arduino
/* Most DevBoards will have an LED already 
   connected to pin 13 so you can either use the
   following or replace LED_BUILTIN with 13 */
// Only runs once. 
void setup() {
	pinMode(LED_BUILTIN, OUTPUT);    // Sets up the pin specified to 
use as an output.
}

// Runs until power is cut or placed in sleep mode.
void loop() {
	digitalWrite(LED_BUILTIN, HIGH); // Sets pin 13 to full voltage. 
In this case it's 5V.
	delay(1000);			 // Do nothing for one second.
	digitalWrite(LED_BUILTIN, LOW);  // Sets pin 13 to no voltage.
	delay(1000);			 // Do nothing for one second.
}
```
* If you connect the LED to pin 3, 5, 6, 9, 10, or 11 you can use the 
purpose built PWM feature on the board. 490Hz for all pins except 5 and 
6 which can run at 980Hz.
* Use the following code. (Grabbed from the Arduino documentation at 
https://www.arduino.cc/reference/en/language/functions/analog-io/analogwrite/ 
)
```arduino
int ledPin = 9;      // LED connected to digital pin 9
int analogPin = 3;   // potentiometer connected to analog pin 3
int val = 0;         // variable to store the read value

void setup() {
  pinMode(ledPin, OUTPUT);  // sets the pin as output
}

void loop() {
  val = analogRead(analogPin);  // read the input pin
  analogWrite(ledPin, val / 4); // analogRead values go from 0 to 1023, 
analogWrite values from 0 to 255
}
```


