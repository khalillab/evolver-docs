# Arduino Code Structure

This page aims to explain the general code structure for the Arduinos ([SAMD21 mini-breakout boards](https://www.sparkfun.com/products/13664)) used in the eVOLVER. The repository can be found [here](https://github.com/FYNCH-BIO/evolver-arduino).

Arduino provides [guides](https://www.arduino.cc/en/Guide) about how to use their products - if you're new to Arduino programming we recommend starting there!

### General Information

Three main libraries are used throughout the Arduino files to simplify the code structure and usability.

* The `evolver_si` (eVOLVER serial input) library handles parsing the serial information that comes from the RPi.
* The `Tlc5940` library handles communication with the [IC](https://www.ti.com/lit/ds/symlink/tlc5940.pdf) that is used for [PWM](https://en.wikipedia.org/wiki/Pulse-width\_modulation).
* The `PID_v1` library contains all the logic and calculations for [PID control](https://en.wikipedia.org/wiki/PID\_controller).

{% hint style="info" %}
See the [server code structure](server-code-structure/#serial-message-structure) page for information on serial communications structure.
{% endhint %}

The Arduino code structure can be thought of in 3 sections: pre-setup, setup, and loop. The fluidics script is slightly different and will be explained separately, but it has the same basic structure.

## Pre-setup

This is everything before the `setup` function. This is where we import header files and setup any global variables/constants.&#x20;

#### Multiplexer variables

Variables indicating the pins for controlling the 4-bit multiplexer for selecting which Smart Sleeve to communicate with, `s0`, `s1`, `s2`, `s3`, and `SIG_PIN`. S0-3 are for selecting the channel, and `SIG_PIN` is output of the mux. We use the ADC on the SAMD21 on pin 0.

#### Serial Communications variables

`inputString` holds incoming serial data from the RPi.

`stringComplete` boolean stating if the string is "complete", meaning that a "!" character has been detected in the incoming serial data.

`end_mark` is what the SAMD21 uses to denote the end of it's messages going out to the RPi - it is not what the SAMD21 is looking for as the end of an incoming message.

Serial communication variables notating what strings are used as commas, and the `address` variable which is the identifier of the SAMD21 - ie, the SAMD21 will only act on data addressed to what is in this variable.&#x20;

We initialize an `evolver_si` object called `in` which handles all serial input.

#### PID variables

Three very important variables if PID is being used are `Setpoint`, `Output`, and `Input` - these three `double` arrays hold what value the PID should be trying to hit, what value is sent out to the actuation element (like a resistive heater), and what the current value being read from the ADC of that element is, respectively. These will be talked about more later.

After these variables are initialized, 16 PID objects are initialized (one for each Smart Sleeve) and put into an array.

## Setup

The setup code runs one time when the system is turned on.

In this block we generally initialize the various pins of the SAMD21 for INPUT or OUTPUT and set pins to be digital LOW or HIGH. We also initialize the PWM if applicable and turn on the `Serial` communications modules on the microcontroller. If PID is being used, we also set those for the proper range and modes.

## Loop

This is the section of the script that is run continuously (on loop) over and over. The general logic is to read from the serial line, see if there are any messages to act on, read data from the Smart Sleeves if applicable, then update any elements that are being controlled for each Smart Sleeve.

If a message on serial is found, the script will save those values, send a message back to the RPi, and continue looping until it receives an ACK from the RPi addressed to it to act on the previously sent values. See the [server code structure](server-code-structure/#serial-message-structure) for more information on serial messages between the RPi and SAMD21s.

## Arduino Functions

TODO: normalize the naming of functions.

### serialEvent

This function reads from `Serial1` and constructs a string in `inputString` containing the data. When it detects the end of the message ("!") it will return. This string is then checked by the `evolver_si` object `in` to determine if the message is formatted appropriately and if the SAMD21 should act on it (ie addressed to it.)

### dataResponse

This function sends out data via serial to the RPi.

It sets pin 12 to a digital HIGH first, which tells the RS-485 that it will be communicating out, then formats the output string containing all the data from the Smart Sleeves.

Then it will delay for 100 ms in order to allow enough time for pin 12 to actually flip and for the RS-485 chip to react before outputting serial data over `Serial1` (the default Tx pin). Lastly it will flip pin 12 back to LOW, indicating it is done using the Serial bus.

### update\_values

This function updates the `Setpoint` variable to the values from  commands sent from the Rpi.

### read\_MuxShield

This function reads data from the Smart Sleeves through the multiplexer. It also handles any averaging for that data and updates the PID based on the readings.

It first creates an array for holding data from the vials, then calls a helper function `readMux` passing the vial it wishes to get data from. Then it calculates the average for each vial, and sets the `Input` for each accordingly. It will then call the `Compute` function of the PIDs with the updated data and make a call to the `Tlc` PWM chip to set the new value as decided by the PID controller.

{% hint style="danger" %}
the `Tlc.update` function should only be called 1 time within a single `loop` of the Arduino!! More information can be found in the [Tlc datasheet](https://www.ti.com/lit/ds/symlink/tlc5940.pdf).
{% endhint %}

### readMux

Gets data from the multiplexer for a given channel and returns the value that is read off of the ADC.

First, it loops through each control pin (S0-3) and sets them appropriately to select the desired channel. Then, it reads off of the `SIG_PIN` and returns that value.

## Fluidics Special Cases

The fluidics script follows the same basic structure as above, but has some special code for handling peristaltic pumps and IPP millifluidics.

In the pre-setup, there is an `int` array called `speedset` which contains two values for PWM OFF and ON, which are 4095 and 0 respectively by default.

### Pump Class

The pump class is an object for keeping track of a single peristaltic pump. They get initialized with the address they are controlling, and have local variables keeping track of whether or not it is current running, how long it needs to pump, and chemostat periodicity information.

#### update

This function checks whether the pump needs to be turned on or off by checking the timing based on milliseconds since it began pumping. If it needs to turn off it sets the Tlc for it's given address and updates local variables.

If it is off and is in chemostat mode (`pumpInterval` > 0), it checks wheter it is time to turn on and sets the Tlc appropriately.

#### setPump

Turns on a pump based on a passed command.

Sets the `timeToPump` and `pumpInterval` variables, then sets the Tlc accordingly.

### IPP class

IPPs pump by sequentially activating pneumatic valves, where the flow rate of the pump is correlated to the frequency at which the valves are actuated. Each IPP object keeps track of the 3 solenoids it needs to actuate to pump, as well as whether or not the pump is currently running.

Example of commands to use these:

IPP Usage: `pumpi,<Hz>|<Pump number>|<IPP index>,...`

To run 2 IPPs on address (0, 1, 2) and (3, 4, 5) after the normal 32 influx/efflux pumps:

```
pumpi,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,10|1|1,10|1|2,10|1|3,5|2|1,5|2|2,5|2|3,--,--,--,--,--,--,--,--,--,--,_!
```

Then acknowledge like normal.

To turn off IPPs, a command with 0 as Hz to the desired pump number. It can be in any address slot. You do not need to have an entry for each individual solenoid channel - just specificy the high level IPP pump index (the second value in the set of three between the pipes).

```
pumpi,0|1|1,0|2|1,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,_!
```

The initialization simply sets addresses of the solenoids.

#### update

This function is [overloaded](https://en.wikibooks.org/wiki/Computer\_Programming/Function\_overloading) (ie two function stubs). If a `long` holdTime is passed, it will change the frequency of the IPP without having to turn it off completely and reset it, useful for very slow pumps. If the pump is off, it will also turn it on. Otherwise, it will check the timing and state of the solenoids and update them accordingly.

#### setAddress

For an IPP, sets up a given address to be solenoid 1, 2, or 3 of an IPP. The valves do not necessarily need to be sequential addresses, although it is normal to set things up this way (see example above).

### Setup

In the setup, the pump objects are initialized. There are two potential layouts on the PCB, one where each address is just sequential, and another where the pump PCB has the pumps layed out a little differently and as such the address for Vial2 is not address 2. The initialization code should be commented out or modified for the given physical setup of the pump arrays.

### Loop

In the loop, the way the serial commands are parsed is a little bit different from normal as chemostats and IPP commands use the pipe "|" character to denote more information for a given address.

As an example, in the command:

```
pumpi,2|4,10,--,--,--,--,--,--,--,--,--,--,--,--,--,--,3|4,15,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,--,_!
```

Addresses 0 and 16 are set as chemostats. The time to pump is the first number, and the pumping interval is the second. So address 0 will run for 2 seconds every 4 seconds, and address 16 will run for 3 seconds every 4 seconds.

Addresses 1 and 17 are set to run for 10 seconds and 15 seconds one time, respectively.

{% hint style="danger" %}
The `Tlc.update()` function is only called a single time at the end of the loop! Do not call this function multiple times, it will cause things to not work.
{% endhint %}
