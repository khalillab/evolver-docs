# LUX Board Troubleshooting

1. Make sure that the board is receiving 6V
   1. 12V power supply needs to be on
   2. Measure voltage from two jumper cables plugged in to correct pins in ribbon cable using a multimeter
2. Plug in to LUX Arduino and check what inputs it is receiving
   1. Link Arduino troubleshooting guide
   2. Use `SerialUSB.println(input2String);` to check if there are serial events
   3. Open up serial monitor
   4. This should instruct you about what to check next based off of the output
3. If no output,
   1. The LUX board may be incorrectly flashed with code
      1. Plug an Arduino Uno directly into the board to see what outputs it receives
   2. If the boards were previously working or have been verified to be outputting the correct signal directly to an Arduino, the connection between the SAMD21 and the LUX board is broken
