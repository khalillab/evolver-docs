---
hidden: true
---

# ATTiny1634 Writing

For upgrading an Arduino so that it can program another microcontroller

[https://www.arduino.cc/en/Tutorial/BuiltInExamples/ArduinoISP](https://www.arduino.cc/en/Tutorial/BuiltInExamples/ArduinoISP)

[https://github.com/FYNCH-BIO/evolver-arduino/blob/master/ATtiny1634/lightsense.c](https://github.com/FYNCH-BIO/evolver-arduino/blob/master/ATtiny1634/lightsense.c)

## AVRDUDE and AVR-gcc

### Follow instructions here:

[https://blog.zakkemble.net/avr-gcc-builds/](https://blog.zakkemble.net/avr-gcc-builds/)

Tried to upload blink to Arduino Uno and got this error

avrdude: stk500\_recv(): programmer is not responding

avrdude: stk500\_getsync() attempt 1 of 10: not in sync: resp=0x58

&#x20;

Had to remove all wires going to Arduino ports and unplug usb before it would upload

## Pin layout Arduino to ATtiny1634

Map of controller pins in on the microcontroller

![](<../../../.gitbook/assets/image (1) (1) (1) (1) (1) (2).png>)![](<../../../.gitbook/assets/Untitled picture.png>)

&#x20;<img src="../../../.gitbook/assets/Untitled picture.jpg" alt="" data-size="original">

## Burning ATtiny1634

[https://www.arduino.cc/en/Tutorial/BuiltInExamples/ArduinoISP](https://www.arduino.cc/en/Tutorial/BuiltInExamples/ArduinoISP)

&#x20;

Load up ArduinoISP (in the Arduino IDE examples) onto the programmer Arduino

Download C code for ATtiny from here:

[https://github.com/FYNCH-BIO/evolver-arduino/tree/master/ATtiny1634](https://github.com/FYNCH-BIO/evolver-arduino/tree/master/ATtiny1634)

&#x20;

### On the terminal

Navigate to the folder containing ATtiny code (lightsense.c)

#### Run commands:

avr-gcc -g -Os -mmcu=attiny1634 -c lightsense.c\
avr-gcc -g -mmcu=attiny1634 -o lightsense.elf lightsense.o\
avr-objcopy -j .text -j .data -O ihex lightsense.elf lightsense.hex\
avrdude -p t1634 -P \<Your Arduino Port> -c arduino -b 19200 -U flash:w:lightsense.hex -v -v -v -v

_From <_[_https://github.com/FYNCH-BIO/evolver-arduino/tree/master/ATtiny1634_](https://github.com/FYNCH-BIO/evolver-arduino/tree/master/ATtiny1634)_>_

Replace \<Your Arduino Port> with the port used by your Arduino (found in IDE under Tools>Port)

avrdude -p t1634 -P COM9 -c arduino -b 19200 -U flash:w:lightsense.hex -v -v -v -v

avr-gcc -g -Os -mmcu=attiny1634 -c LEDblink.c\
avr-gcc -g -mmcu=attiny1634 -o LEDblink.elf LEDblink.o\
avr-objcopy -j .text -j .data -O ihex LEDblink.elf LEDblink.hex\
avrdude -p t1634 -P COM9 -c arduino -b 19200 -U flash:w:LEDblink.hex -v -v -v -v

## Alternative guide? or ATTiny as an arduino?

[https://github.com/SpenceKonde/ATTinyCore](https://github.com/SpenceKonde/ATTinyCore)
