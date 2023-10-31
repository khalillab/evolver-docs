# Construction Protocol

## Make Ribbon Cables

1. Measure ribbon cables and mark length
   1. 5" ribbon cable for pump board to min-eVOLVER PCB connection
   2. Two 3.5" ribbon cables for smart sleeves to min-eVOLVER PCB connection
2. Crimp on ribbon cable connectors
   1. _Be careful_ not to break the connectors, they're plastic!
   2. Open the connector and place on the ribbon in correct location (figure below A)
      1. _The connectors should both have the knob on the same side_
   3. The easiest way crimp these connectors is to use a clamp or vice, unless you have a specialized tool (figure below B)
      1. Place the connector in the clamp (making sure it remains in the right location)
      2. Tighten clamp until no space remains in sides of connector
   4. You can also use pliers or a hammer, but this is more annoying / prone to breaking the connectors
3. Cut excess ribbon cable - razor is easiest (figure below C)

<figure><img src="../../../.gitbook/assets/image (6).png" alt=""><figcaption><p>(A) Ribbon cable connector placed at 5" with both knobs on the same side (arrows). (B) Connector is placed in clamp. (C) Ribbon cable after connector is crimped on and excess cable is trimmed with a razor.</p></figcaption></figure>

## Prepare case

1. Unscrew the 3 screws on the top of the case
2. Unscrew the 2 screws on the bottom and the right middle rubber foot

<figure><img src="../../../.gitbook/assets/image (17).png" alt=""><figcaption><p>(Left) Remove 3 screws from the top of the case. (Right) Unscrew the 2 screws on the bottom and the right middle rubber foot</p></figcaption></figure>

## Construct Pump Board

Solder 2x8 ribbon cable connector into pump PCB, screw pumps into front of case, and solder pumps into pump PCB.

Use the below video:

{% embed url="https://youtu.be/QBEHd3Vmz8s" %}

## Construct min-eVOLVER PCB

1. Surface mount soldering of the min-eVOLVER PCB is outside of the scope of this guide. It is assumed that you have an already assembled min-eVOLVER PCB.
2. Place the 2x12-pin header on a workbench with the flat (non conical) side up. Place the SAMD21 board on top of it
3. Carefully solder the SAMD21 board pins.
   1. Avoid adding too much solder so that it globs onto the small electronic components!
   2. Start with the four corners to lock it flat in place on the header
   3. Solder all pins
      1. If you want to be extra careful, only solder half the pins on a side before switching to the other side (to avoid overheating)
   4. Make sure that each pin is individual and no solder has reached the electronic components on the board surface
4. Press the SAMD21 board into the min-eVOLVER PCB
   1. Careful to not bend pins
   2. Micro-USB port should be on edge of board
5. Slide the shorting jumpers onto the right two pins for each vial (see figure below C)

<figure><img src="../../../.gitbook/assets/image (10).png" alt=""><figcaption><p>(A) The SAMD21 board and the 2x12-pin header with flat side up. (B) SAMD21 board partially soldered, starting from the pins in the corners. (C) Placing the jumpers on the right two selector pins for each vial. (D) The assembled min-eVOLVER PCB.</p></figcaption></figure>

#### (Advanced Users Only) Selecting OD90 vs OD135 in the min-eVOLVER

1. OD90 = OD LED and photodiode at 90 degrees from eachother
2. OD135 = OD LED and photodiode at 135 degrees from eachother
3. By default, we choose to use OD90 for our vials, which is typically better at measuring higher ODs > 0.4 and is what most people want
4. You can also place the jumper across the left two pins for each vial, meaning you will register OD135. You will need to make different OD calibrations for OD135 and OD90

## Assemble min-eVOLVER PCB and pumps with the case

1. Place min-eVOLVER PCB on standoffs. Screw 1/4" screws into the front left and back right corners (figure A below)
2. Plug the 5" ribbon cable in to the pumps and to the ribbon cable port to the left of the SAMD21 (figure B below)
3. Close the case and replace the 5 screws and rubber foot that you had removed previously (figure C below)

<figure><img src="../../../.gitbook/assets/image (11).png" alt=""><figcaption><p>(A) min-eVOLVER on standoffs inside case and screwed down with 1/4" screws. (B) Demonstrating how the ribbon cable connecting pumps and min-eVOLVER PCB should be plugged in. (C) Assembled min-eVOLVER PCB, pumps, and case.</p></figcaption></figure>

## Construct eVOLVER smart sleeves and screw in to case

1. If your smart sleeves came disassembled:
   1. See general smart sleeve construction guide [here](../../../guides/building-a-smart-sleeve.md)
   2. Instead we will use 2-3/8" screws to hold our smart sleeves together
   3. Firmly push the OD LED and photodiodes in to the smart sleeve
2. If your smart sleeves came assembled:
   1. Unscrew them from the acrylic base plate (below the computer fan)
   2. We will also not use the acrylic base plate and instead directly screw our smart sleeves to the case (see below)
3. Screw the smart sleeves into the min-eVOLVER
   1. Do not over tighten screws, go until smart sleeves are firmly in place
4. Plug 3.5" ribbon cables into back of smart sleeves and to the min-eVOLVER
5. Place vial cover over vials

<figure><img src="../../../.gitbook/assets/image (56).png" alt=""><figcaption><p>(Left) Smart sleeves are screwed in to the case. (Center) Smart sleeves are connected to the case via 3.5" ribbon cables. (Right) Vial cover is placed over vials.</p></figcaption></figure>

## Flash the min-eVOLVER with Arduino code

Follow the Arduino Software Installation [guide](../../../guides/arduino-software-installation.md) and upload the min-eVOLVER Arduino [code](https://github.com/FYNCH-BIO/evolver-arduino/tree/master/SAMD21/MINEVOLVER) onto the device
