# Construction Protocol

It may be helpful to have the [parts](parts.md) page open as well, so you can identify what you need for each step.

## Make Ribbon Cables

1. Measure ribbon cables and mark length (figure below A)
   1. 5" ribbon cable for pump board to min-eVOLVER PCB connection
   2. Two 4" ribbon cables for smart sleeve PCB to min-eVOLVER PCB connection
2. Cut ribbon cables to size using scissors or razor.
3. Open the connector and align to the end of the ribbon cable (figure below B)
   1. _The connectors should both have the knob on the same side_ (figure below A, red arrows)
   2. You can apply pressure to the connector so that it stays in place as you work with it
4. Crimp on ribbon cable connectors (one on each side of cable)
   1. _Be careful_ not to break the connectors, they're fragile!
   2. The easiest way crimp these connectors is to use a clamp or vice (figure below C), unless you have a specialized tool
      1. Place the connector in the _center_ of the clamp (making sure it remains in the right location)
      2. Tighten clamp until sides of connector are flush and it is full closed (figure below D)
   3. You can also use pliers, but this is more annoying / prone to breaking the connectors

<figure><img src="../../../.gitbook/assets/image (60).png" alt=""><figcaption><p>(A) Ribbon cable connector placed at 5" with both knobs on the same side (arrows). (B) Align the ribbon cable connector with the end of the cable. (C) Connector is placed in center of clamp. (D) Completed ribbon cable after connector is crimped on.</p></figcaption></figure>

## Prepare case

1. Unscrew the 3 screws on the top of the case (figure below, left)
2. Unscrew the 2 screws on the bottom (figure below, right) and unscrew the right middle rubber foot (yellow arrow)

<figure><img src="../../../.gitbook/assets/image (59).png" alt=""><figcaption><p>(Left) Remove 3 screws from the top of the case. (Right) Unscrew the 2 screws on the bottom and twist off the right middle rubber foot (yellow arrow).</p></figcaption></figure>

## Construct Pump Board

Solder 2x8 ribbon cable connector into pump PCB, screw pumps into front of case, and solder pumps into pump PCB.

Use the below video:

{% embed url="https://youtu.be/NriRKiqgiUg" %}

## Construct min-eVOLVER PCB

{% hint style="info" %}
Surface mount soldering of the min-eVOLVER PCB is outside of the scope of this guide. It is assumed that you have an already assembled min-eVOLVER PCB.
{% endhint %}

### Solder SAMD21 Arduino

1. Place the 2x12-pin header on a workbench with the flat (non conical) side of the pins up (figure below A). Place the SAMD21 board on top of it
   1. You can also carefully plug the SAMD21 into a breadboard if you want to avoid it moving
2. Carefully solder the SAMD21 board pins.
   1. Avoid adding too much solder so that it globs onto the small electronic components!
   2. Start with the four corners to lock it flat in place on the header
   3. Solder all pins
      1. If you want to be extra careful, only solder half the pins on a side before switching to the other side (to avoid overheating the board)
   4. Make sure that each pin is individual and no solder has reached the electronic components on the board surface
3. \[**Recommended**] Strengthen SAMD21 Board USB
   1. The micro-USB port on the SAMD21 easily pops off when you move the ribbon cable
   2. You will have a useless board and it will be necessary to get a new one
   3. Therefore, you should add [epoxy](https://www.mcmaster.com/7605A5/) to the perimeter of the connector in the (locations shown in the figure below C)&#x20;
   4. Follow directions on the epoxy label for use
   5. A weigh boat and pipette tip work for mixing and application
   6. _Important - Avoid putting epoxy into the holes in the micro-USB connector_
   7. Otherwise, be generous with the epoxy, it's ok to get it on the electronics

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption><p>(A) The SAMD21 board and the 2x12-pin header with flat side of the 24-pins up. (B) SAMD21 board partially soldered, starting from the pins in the corners. (C) Locations for epoxy (cyan) avoiding openings in the micro-USB connector. (D) Placing the jumpers on the right two selector pins for each vial. (E) The assembled min-eVOLVER PCB.</p></figcaption></figure>

### Assemble min-eVOLVER PCB

1. Press the SAMD21 board into the min-eVOLVER PCB until you feel a click and the SAMD21 sits mostly flush
   1. Micro-USB port should be on edge of board
   2. Carefully align the pins with the sockets
2. Slide the shorting jumpers onto the right two pins for each vial (see figure above D)

### OD 90 vs OD 135

1. OD90 = OD LED and photodiode at 90 degrees from eachother
2. OD135 = OD LED and photodiode at 135 degrees from eachother
3. _By default, we choose to use OD90 for our vials, which is typically better at measuring higher ODs > 0.4 and is what most people want_
4. You can also place the jumper across the left two pins for each vial, meaning you will register OD135.
5. You will need to make different OD calibrations for OD135 and OD90

## Assemble min-eVOLVER PCB and pumps with the case

1. Place min-eVOLVER PCB on standoffs. Screw 1/4" screws into the front left and back right corners (figure A below)
2. Plug the 5" ribbon cable in to the pumps and to the ribbon cable port to the left of the SAMD21 (figure B below)
3. Close the case and replace the 5 screws and rubber foot that you had removed previously (figure C below)

<figure><img src="../../../.gitbook/assets/image (11).png" alt=""><figcaption><p>(A) min-eVOLVER on standoffs inside case and screwed down with 1/4" screws. (B) Demonstrating how the ribbon cable connecting pumps and min-eVOLVER PCB should be plugged in. (C) Assembled min-eVOLVER PCB, pumps, and case.</p></figcaption></figure>

## Construct eVOLVER smart sleeves and screw in to case

1. If your smart sleeves came disassembled:
   1. See general smart sleeve construction guide [here](../../../guides/building-a-smart-sleeve.md)
   2. Firmly push the OD LED and photodiodes in to the smart sleeve
   3. Do not use the acrylic base plate (clear plastic below the computer fan)
2. If your smart sleeves came assembled:
   1. Unscrew them enough to remove the acrylic base plate. Keep the fan spacer on (figure A below)
   2. We will also not use the acrylic base plate and instead directly screw our smart sleeves to the case
3. Screw the smart sleeves into the min-eVOLVER (figure B below)
   1. It can be easier to tighten each screw a little at a time to avoid misalignment&#x20;
   2. Do not over tighten screws, go until smart sleeves are firmly in place
4. Plug 3.5" ribbon cables into back of smart sleeves and to the min-eVOLVER (figure C below)
5. Place vial cover over vials (figure D below)

<figure><img src="../../../.gitbook/assets/image (61).png" alt=""><figcaption><p>(A) Screws unscrewed enough to remove the base plate, which is sitting next to the vial. Fan spacer on the bottom is left on. (B) Smart sleeves are screwed in to the case. (C) Smart sleeves are connected to the case via 3.5" ribbon cables. (D) Vial cover is placed over vials.</p></figcaption></figure>

## Flash the min-eVOLVER with Arduino code&#x20;

1. Plug the min-eVOLVER into your computer via the micro-USB cable
   1. Do not plug in the 12V power supply
2. Download the min-eVOLVER Arduino [code](https://github.com/FYNCH-BIO/evolver-arduino/tree/master/SAMD21/MINEVOLVER)
3. Follow the Arduino Software Installation [guide](../../../guides/arduino-software-installation.md)
4. Upload the min-eVOLVER Arduino code onto the device
