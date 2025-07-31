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

We built our PCB designs on [**KiCAD**](http://kicad-pcb.org/), an open-sourced software for circuit board design, and our 3D models on Solidworks. Here is a schematic of the PCB [**here**](https://www.fynchbio.com/s/Vial_Board_Schematic.pdf) and the Solidworks part [**here**](https://www.fynchbio.com/s/Tube-Holder.SLDPRT). There are many other programs for vial board design, including a bunch of tutorials on [Eagle from Sparkfun](https://learn.sparkfun.com/tutorials/using-eagle-schematic), another popular CAD tool for the open-source community.

#### **Does this tutorial include how to build the Motherboard?**

No. This tutorial only provides instructions on how to build a Smart Sleeve.

## Guide

Use the below video to help if you are confused about any of the steps in this guide.

{% embed url="https://youtu.be/6M6KdABQahk" %}

### 1. Source parts

* To assemble each Smart Sleeve, you will need all 16 components listed in Figure 1.
* See [here](../getting-started/part-sourcing.md) for part sourcing or order the Smart Sleeve unassembled from Fynch Bio

<figure><img src="../.gitbook/assets/Fig 1 (1).png" alt="" width="563"><figcaption><p>Figure 1</p></figcaption></figure>

List of supplies needed (**Figure 1**):

1. Aluminum Vial Sleeve Tube
2. Thermistor
3. 2x IR Photodiode
4. IR LED
5. 2x Stainless Steel Screws, 2.5" 4-40 Thread
6. 2x Black pan head screws, 1/4" 2-56 Thread
7. 1.5mm Flathead screwdriver
8. Number 1 Phillips screwdriver
9. Laser cut 1/8" Acrylic Fan Spacer with circular cutout
10. Laser cut 1/8" Acrylic Fan Spacer
11. Laser Cut 1/4" Acrylic Base
12. 12V DC Computer Fan with 3D Printed Magnet Holder
13. Vial Board PCB
14. 3D Printed Tube Holder
15. Lab Tape **(Not Shown)**
16. Soldering Iron + Solder **(Not Shown)**

### 2. Assemble Aluminum Tube and Vial Board

1. Align the holes as shown in Figure 2
2. Secure the two pieces together using a 1/4" black head screw (Figure 3)
3. Repeat this process to align and secure the holes on the opposite side

<div align="center"><figure><img src="../.gitbook/assets/Fig 2 (1).png" alt="" width="375"><figcaption><p>Figure 2</p></figcaption></figure> <figure><img src="../.gitbook/assets/Fig 3.png" alt="" width="375"><figcaption><p>Figure 3</p></figcaption></figure></div>

### **3. Tape Thermistor Onto Aluminum Vial Sleeve**

1. The thermistor has one side covered in plastic (with writing) and one exposed side (Figure 4). Ensure the exposed side faces the aluminum tube
2. Thread the thermistor’s lead wires through the two holes on the PCB (Figure 5) and secure it in place using lab tape, as shown in Figures 6.1 and 6.2.
   1. The holes are labelled "Thermistor" on the top side of the PCB
   2. Tape the thermistor parallel to the length of the tube, about 0.5 cm away from the bottom of the tube. The leads should be exposed when slotted into the 3D printed part.
   3. Avoid allowing tape into the hole in the aluminum tube to the right of the thermistor
3. The aluminum tube may need to be cleaned with alcohol if tape is not sticking

<div><img src="../.gitbook/assets/Fig 4.png" alt="Figure 4" width="375"> <figure><img src="../.gitbook/assets/Fig 5.png" alt="" width="375"><figcaption><p>Figure 5</p></figcaption></figure></div>

<div><figure><img src="../.gitbook/assets/Fig 6.1.png" alt="" width="375"><figcaption><p>Figure 6.1</p></figcaption></figure> <figure><img src="../.gitbook/assets/Fig 6.2.png" alt="" width="375"><figcaption><p>Figure 6.2</p></figcaption></figure></div>

### 4. Insert the Aluminum Tube into the 3D Printed Tube Holder

1. Next, insert the black 3D-printed tube holder beneath the PCB (Figure 7), positioning the indented section over the thermistor
   1. All holes in the 3D-printed tube holder should align with the holes in the aluminum tube
   2. Avoid damaging the thermistor by twisting or rotating the parts.
2. Secure all components using two 4-40 stainless steel screws (Figure 8).
   1. If the screws are not sliding into the holes, loosen the black screws that are securing the heaters to the aluminum tube. Make sure to tighten these after you get the stainless steel screws through

<div><img src="../.gitbook/assets/Fig 7.png" alt="Figure 7" width="375"> <figure><img src="../.gitbook/assets/Fig 8.png" alt="" width="375"><figcaption><p>Figure 8</p></figcaption></figure></div>

### 5. Assemble Acrylic Parts and Fan

1. Slide the solid acrylic fan spacer onto the 4-40 stainless steel screws, followed by the spacer with the circular cutout (Figure 9.1).
2. Orient the fan according to the directional arrows shown in Figure 9.2 and slide it onto the screws
   1. The arrows are on the same side as the 16-pin ribbon cable connector that overhangs off of the vial PCB
3. Coil the fan wires _very_ tightly around the base of the Smart Sleeve and connect them to the right two ports of the screw terminal labeled “P2” (Figure 9.3)
   1. The red wire should be connected to the ‘+’ terminal and the black wire should be connected to the ‘-’ terminal
   2. It can help get the fan wires into the terminal to bend their tips
   3. This can be challenging, so it's okay if you have to rotate the fan 90 degrees to give more slack
4. Finally, attach the acrylic base to the bottom of the Smart Sleeve (Figure 9.4) and secure the assembly by tightening the two 4-40 stainless steel screws.

<div><figure><img src="../.gitbook/assets/Fig 9.2.png" alt="" width="375"><figcaption><p>Figure 9.1</p></figcaption></figure> <figure><img src="../.gitbook/assets/Fig 9.2 (1).png" alt="" width="375"><figcaption><p>Figure 9.2</p></figcaption></figure></div>

<div><figure><img src="../.gitbook/assets/Fig 9.3 (1).png" alt="" width="375"><figcaption><p>Figure 9.3</p></figcaption></figure> <figure><img src="../.gitbook/assets/Fig 9.4.png" alt="" width="375"><figcaption><p>Figure 9.4</p></figcaption></figure></div>

### 6. Connect the IR LED and IR Photodiodes

1. Both the IR LED (clear) and the IR photodiodes (black) feature one long and one short lead (Figure 10.1). The long lead should be connected to the ‘+’ vial on the PCB, and the short lead to the ‘–’ vial (Figure 11.1).

<div><img src="../.gitbook/assets/Fig 10.png" alt="Figure 10" width="375"> <figure><img src="../.gitbook/assets/Fig 11.1.png" alt="" width="375"><figcaption><p>Figure 11.1</p></figcaption></figure></div>

2. Connect the IR LED
   1. Connect the IR LED (clear) to the IR LED screw terminal ports on the PCB, using the following polarity:
      1. Long lead to the ‘+’ port and short lead to the ‘–’ port (Figure 11.2)
   2. Bend the sensor into the corresponding slot, which is an opening on the black 3D-printed part below the IR LED terminal (Figure 11.3)
   3. Using a screwdriver, firmly press the IR LED into the hole until it no longer moves
   4. Press the leads towards the 3D-printed part so that they are separate as shown in Figure 11.4.

![Figure 11.2](<../.gitbook/assets/Fig 11.2.png>)

<div><figure><img src="../.gitbook/assets/Fig 11.3.png" alt="" width="375"><figcaption><p>Figure 11.3</p></figcaption></figure> <figure><img src="../.gitbook/assets/Fig 11.4.png" alt="" width="375"><figcaption><p>Figure 11.4</p></figcaption></figure></div>

3. Repeat the same process for both IR photodiodes (black), connecting each to the appropriate screw terminal ports labeled with “Spare A” and “PD135” (Figures 12 and 13)
   1. _Again, make sure the long lead goes into the + terminal_

<div><img src="../.gitbook/assets/Fig 12.png" alt="Figure 12" width="375"> <figure><img src="../.gitbook/assets/Fig 13.png" alt="" width="375"><figcaption><p>Figure 13</p></figcaption></figure></div>

### 7. Solder the Thermistor

Finally, solder the thermistor onto the PCB (Figure 14).

![Figure 14](../.gitbook/assets/ss_step12.jpeg)

### **That’s it! You’re done.**

Following a similar framework for building the Smart Sleeves enables adding different parameters, adaptation to different vial sizes, and other creative eVOLVER applications! Have fun!

Let us know if anything is unclear on the [forum](https://www.evolver.bio/t/building-a-smart-sleeve-for-continuous-culture-40-ml/30).
