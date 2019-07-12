## Analog vs Digital

|Analog|Digital|
|---|---|
|Sensed with using the analog pins on the Arduino|Sensed with digital or Analog IO pins|
|Requires Special hardware that is built in the Arduino|Requires High Voltage to be within Arduino Spec.(5V in most cases)|
|Is how all sensors actually function|Used only for Boolean values.(This can be used at high speeds for serial data)|

## Analog Sensors

### Description
Analog Sensors can be powered to send an analog signal to a microcontroller or even be used directly in a circuit.
Examples of analog changing sensors:
* Photoresistor - uses light to control the resistance in a circuit.
* Capacitive - Measure the capacitance on a surface that touches it. Very commonly used with cell phone screens and touch sensitive buttons. Some have the ability to output more or less voltage depending on the touch strength.
* Thermistor - uses a temperature difference to change the resistance within a circuit.
Examples of analog output sensors:
* Many Accelerometers - Creates an analog signal depending on their speed of movement.
* Many Gyroscopes - Creates an analog signal depending on rotation in a 2d field.  
* Microphone - Creates a voltage from the movement of a suspended membrane and magnetic fields. 

## Digital
### Description
Digital sensors only output boolean values (High and Low). As such digital sensors are technically only switches.
Examples of Digital Sensors:
* Tilt switch - Uses mercury to bridge two contacts and complete a eletrical circuit.
* A standard switch/ button - Allows electrons to flow through the circuit when activated.
### Why do we care
Digital IO can be used to send and receive serialized and Paralleled data. This will be used on a vast majority of our sensors.
Data IO can use many different standards. We'll be looking at I2C,  SPI, and Parallel.
### Parallel
* Simpler than Serial.
* Uses one line per bit of data that needs to be sent/received.
* No real limit on bits as long as the microcontroller can handle the data.
* Not used much any more.
* Can get around IO limit by using shift registers.
* Does not require a clock signal to keep the sender and receiver in sync. 
<figure>
	<img src="https://2.bp.blogspot.com/-Y0eLMqTuD18/VEjJeLi6kiI/AAAAAAAAAGE/zrzrIh9EcZA/s1600/12.jpg" width="45%"/>
	<figcaption>Shown: 8-Bit Parallel Data transfer</figcaption>
</figure>
Manually addressing and and storing bits into a Parallel EEPROM chip.

<iframe width="90%" height="85%"  src="https://www.youtube.com/embed/BA12Z7gQ4P0" frameborder="0" allow="accelerometer;  encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Addressing and storing bits with an arduino. (Can also be used to Read EEPROM chips for items like Gameboys and such.)

<iframe width="90%" height="85%" src="https://www.youtube.com/embed/K88pgWhEb1M" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

As an aside this guy does a lot of computer logic and showing how the low level logic works. It's a great watch.


#### Serial Data
* More complex than parallel.
* Amount of lines varies depending on standard. 
  * I2C requires one line for data. 
  * SPI requires 2 for data. One for transmission, one for receive. 
* Can daisy chain multiple components 
* Widely supported on most digital components.
* Requires a clock signal to keep components and microcontroller in sync.
<figure>
<img src="http://iwatchsystems.com/technical/wp-content/uploads/2010/12/Srl.gif" width="45%">
<figcaption>Shown: MSB means Most Significant Bit. LSB means Least Significant Bit. </figcaption>
</figure>

Data Transmission over 2 wires. One clock and one data.

<iframe width="90%" height="85%" src="https://www.youtube.com/embed/eq5YpKHXJDM" frameborder="0" allow="accelerometer;  encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### SPI
* Minimum of four wires.
* 2 Data IO. 
  * MOSI - Master Out Slave In 
  * MISO - Master In Slave Out
* SCLK - Signal Clock for sync between components
* SS - Slave Select for choosing which component to send and receive data to. Need one line for each component.
* Lower overhead and higher data transfer speed. 
* Supports rates up to 10MHz or 10million bits per second

### I2C
* Minimum of 2 wires(Not including power and ground)
* SDA - Signal Data handles send and receive on one line
* SCL - Signal Clock handles the syncing of data between devices
* Higher overhead and lower data transfer speed.
* Allows at most 1008 slave devices.
* Is also a multi master system allowing multiple masters to access the same components. They must take turn however.
* Sends an extra bit for every 8-bits sent
* Can operate at up to 5MHz


