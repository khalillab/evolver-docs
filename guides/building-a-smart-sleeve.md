---
description: A guide for building Smart Sleeves on eVOLVER
cover: ../.gitbook/assets/build_smartsleeve.jpeg
coverY: 0
---

# Building a Smart Sleeve

1. [Background](building-a-smart-sleeve.md#background)
2. [Guide](building-a-smart-sleeve.md#guide)

If you need additional aid or have questions about this process, feel free to ask on the [forum](https://www.evolver.bio/t/building-a-smart-sleeve-for-continuous-culture-40-ml/30)!

## Background

eVOLVER hardware is primarily divided between the Smart Sleeves and Motherboard. The Motherboard is where all the sensitive control hardware is, whereas the Smart Sleeve is nice modular way of integrating all the sensors to control your culture conditions.

#### Goal

The goal of this tutorial is to show how one can build an eVOLVER Smart Sleeve using commonly found tools and easily customizable parts.

#### Time/Cost

In this post, we are describing the Smart Sleeve built for continuous culture documented in our [**Nature Biotechnology paper**](https://www.nature.com/articles/nbt.4151). It typically takes 10 to 15 minutes for construction of this version of the Smart Sleeve with all the appropriate parts (e.g. soldered PCB, constructed aluminum tube). Raw materials cost roughly $40/ vial however cost for 3D printing, machining, and coloring (spray painting/ anodizing) parts vary due to accessibility to appropriate tools.

#### That all sounds great, **but I have never soldered or 3D printed before, how do I start?**

Here is a great introductory tutorial on soldering from our friends at [**Sparkfun**](https://learn.sparkfun.com/tutorials/how-to-solder-through-hole-soldering)**.** Also, you can easily outsource your 3D printed parts to be produced by folks at [**3DHubs**](https://www.3dhubs.com/) by uploading the appropriate [**STL file**](https://www.fynchbio.com/s/Tube-Holder.STL) (if you’re a student, don’t forget the student discount!). Generally, building a Smart Sleeve is simple because we only use through hole components and screw terminals, so it is much easier to make than surface mount designs.

**How can I modify or change the design?**

We built our PCB designs on [**KiCAD**](http://kicad-pcb.org/), an open-sourced software for circuit board design, and our 3D models on Solidworks. Here is a schematic of the PCB [**here**](https://www.fynchbio.com/s/Vial\_Board\_Schematic.pdf) and the Solidworks part [**here**](https://www.fynchbio.com/s/Tube-Holder.SLDPRT). There are many other programs for vial board design, including a bunch of tutorials on [Eagle from Sparkfun](https://learn.sparkfun.com/tutorials/using-eagle-schematic), another popular CAD tool for the open-source community.

#### **Does this tutorial include how to build the Motherboard?**

No. This tutorial only provides instructions on how to build a Smart Sleeve.

## Guide

**1. Order all of the necessary parts and tools.**

![](../.gitbook/assets/ss\_parts.jpeg)



List of supplies needed ( **displayed in photograph above** ):

1. Laser Cut 1/4" Acrylic Base
2. 2 pieces of laser cut 1/8" Acrylic Fan Spacers
3. 5/64" Hex Key
4. IR LED
5. IR Photodiode
6. Thermistor
7. 2x Socket head screw
8. 12 V DC Computer Fan with Magnets Glued
9. Vial Board
10. Lab Tape
11. 3D Printed Part
12. Aluminum Tube
13. Soldering Iron + Solder
14. 2x Stainless Steel Screws, 2.5" 4-40 threading **(Not Shown)**

**2. Familiarize yourself with how the Vial Board, 3D printed part, and aluminum tube should be assembled.**

![](../.gitbook/assets/ss\_step2.jpeg)

Take notice if all the components line up properly:

* Tapped 2-56 holes on the Aluminum Tube lines up with holes on heating resistors (2 black rectangular components soldered on vial board)
* The heating resistors should sit on two rectangular holes on the 3D printed part
* Green screw terminals line up with the LED holes on the 3D printed part

Take note of where the two holes labeled “thermistor” are on the PCB.

**3. Tape thermistor on the aluminum tube near where the two vias were located on the PCB.**

![](../.gitbook/assets/ss\_step3.jpeg)

When taping the thermistor, ensure the writing on the thermistor is facing away from the aluminum tube. Tape the thermistor parallel to the length of the tube about .5 cm away from the bottom of the tube. The leads should be exposed when slotted into the 3D printed part.

**4. Slot the aluminum tube into the 3D printed part. Verify that the holes for the LEDs on both the aluminum tube and 3D printed part are properly aligned.**

![](../.gitbook/assets/ss\_step4.jpeg)

Make sure 3D printed part is slotted tightly. Add additional pieces of tape if is loose. Avoid damaging the thermistor by twisting or rotating the parts.

**5. Align the PCB over the 3D printed part, with the two thermistor leads threading through the vias on the PCB.**

![](../.gitbook/assets/ss\_step5.jpeg)

Also verify that the two small 2-56 holes on the aluminum sleeve align with the holes on the heating resistor.

**6. Use the** **2x Socket head screws to fasten the heating resistors to the aluminum sleeve.**

![](../.gitbook/assets/ss\_step6.jpeg)

Aligning the hole with the heating resistor makes screwing the socket cap in much easier. Thermal paste can also be applied before this step to form better contact between the heaters and aluminum tube.

**7. Place the 1/8" laser cut acrylic pieces onto of the fan to act as spacers between the magnets and glass vessel.**

![](../.gitbook/assets/ss\_step7.jpeg)

**8. Use the two 4-40 stainless steel screws to fasten the assembled 3D printed part and the computer fan with spacers. Fasten both screws onto the 1/4" acrylic piece.**

![](../.gitbook/assets/ss\_step8a.jpeg)

![](../.gitbook/assets/ss\_step8b.jpeg)

**9. Coil the wires from the computer fan around the Smart Sleeve and connect to appropriate ports on the screw terminal labeled “fan”.**

The red wire should go into PWR and the black wire should go into the GND ports.

![](../.gitbook/assets/ss\_step9.jpeg)

**10. Attach the LED (clear packaging) and photodiode (dark packaging) for OD measurement to the appropriately labeled slots.**

![](../.gitbook/assets/ss\_step10.jpeg)

Both the photodiode and LED should have a short and a long lead. This corresponds to the polarity of components. Make sure for both components, the _**longer lead is connected to PWR**_ . If this is done improperly, you will not get a reliable signal.

**11. Bend the LED and diode into the corresponding slots.**

![](../.gitbook/assets/ss\_step11.jpeg)

**12. Finally, solder the thermistor onto the PCB.**

![](../.gitbook/assets/ss\_step12.jpeg)

**That’s it! You’re done.**

Following a similar framework for building the Smart Sleeves enables adding different parameters, adaptation to different vial sizes, and other creative eVOLVER applications! Have fun! Let me know if anything is unclear on the [forum](https://www.evolver.bio/t/building-a-smart-sleeve-for-continuous-culture-40-ml/30).
