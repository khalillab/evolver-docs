---
description: Separating fluidic control from the motherboard
---

# Fluidics box

## What's in the box

The fluidics box can be opened by removing the 8 phillips head screws on the sides. Inside the box is the fluidics board (with a SAMD21 and three PWM boards) with RS485 and 5V connections for the SAMD21, and a 12V power supply beneath the board. Should the need arise to update the arduino code on the SAMD21, you'll need to open the box to get to it.

<figure><img src="../../.gitbook/assets/Screen Shot 2023-06-06 at 3.26.00 PM.png" alt=""><figcaption></figcaption></figure>

The connections to the pumps are numbered according to their address, i.e. cable 1 connects to pumps 1-8, cable 2 connects to pumps 9-16, etc.

## Troubleshooting and repair

Not many things can go wrong inside the box, but we have dealt with a situation where the 5V power connection was faulty and led to malfunction. This part can be replaced by opening the box and replacing the faulty connector.

## Modifications

### Adding another pump array

The existing pump pox can control up to 16 additional pumps (or any other 12V valve, actuator, etc) with no modifications. Typically this would mean using connections 5 and 6 on the back of the box, which correspond to indices 33-48.&#x20;

### Modifying fluidics code

Adding another pump array will of course require changes to custom\_script.py, because pump indices 33-48 are not being sent commands during normal eVOLVER operation. The MESSAGE variable holds all information on how long to run each pump, and this is where you should implement your commands in custom\_script. See the [turbidostat](../../software/dpu/custom\_script.py.md#turbidostat) section of the custom\_script page for more information.

### Daisy-chaining multiple boxes

Two RS485 ports (the telephone jack-looking ports) are available on the back of the fluidics box so that multiple boxes can be linked together on the same RS485 "line". All SAMD21 microcontrollers are receiving the same serial data from the Raspberry Pi, and only responding to commands when the appropriate address for that SAMD21 is in the command, like "temp" or "stir". Additional fluidics boxes can have the same "pump" address with higher pump indices (i.e. pumps 49-96 for a second box), so long as you change the number of expected pump values on the conf.yml file. You will also need to modify the SAMD21 arduino code accordingly. You can also have a different address for the other fluidics box, by adding another parameter in the conf.yml and modifying the arduino code accordingly.

