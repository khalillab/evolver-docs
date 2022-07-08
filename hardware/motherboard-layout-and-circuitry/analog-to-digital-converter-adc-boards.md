# Analog-to-Digital Converter (ADC) Boards

## Description

Another customizable control board, the ADC board is designed to plug into the Motherboard and measure the signal from dozens of sensors in the system. The sensors currently integrated in each sleeve are simple and can be measured with basic voltage divider circuits. The sensor and resistor are placed in series, and the voltage across a resistor changes when the measurement from the sensor changes. The board reads this voltage and has two main roles: (1) remove noise from the signal through a low pass filter and (2) multiplex the signal from all 16 channels to one analog input pin on the Arduino. When the signal arrives at the input pin, the Arduino changes the analog signal to a digital signal via its own 12-bit ADC. Nature Biotechnology:
