# Unboxing and Setting Up

If you have any questions about this process, feel free to reach out on the [forum](https://www.evolver.bio/t/unboxing-and-setting-up-your-evolver/123)!

Congrats on getting your eVOLVER and supporting our open-sourced community. We rely on support from you guys to help sustain this ecosystem so we can let everyone do the experiments that they want to! In this tutorial, we are going to teach you how to put this system together:

![](../.gitbook/assets/evolver.jpeg)

If you ordered the standard kit, this is the tutorial for you! The kit contains the following major components:

* Vial Platform
* 16 Smart Sleeves
* 2x Pump Arrays (total 32 pumps)
* Fluidic Box to for control of 32 Pumps (can expand to 48 w/ additional hardware)

## 1) First Unboxing the System

There are several components with protective foam. Insure all the components were delivered intact.

_16 Smart Sleeves and a Box of Accessories_

![](../.gitbook/assets/parts1.jpeg)

![](../.gitbook/assets/parts2.jpeg)

_Pump Array and Fluidics Box_

![](../.gitbook/assets/parts3.jpeg)

_Vial Platform_

![](../.gitbook/assets/parts4.jpeg)

## 2) Set up power and ethernet for the vial platform

The Vial Platform is the unit on which all the Smart Sleeves will be screwed onto. This system contains the eVOLVER Motherboard, Raspberry Pi, and Power Modules that control the Smart Sleeves. Parts used to setup the Vial Platform should be labeled with a black dot.

_Contents of the Vial Platform Components Bag:_

![](../.gitbook/assets/parts5.jpeg)

First, plug in Power and the Ethernet Connection to the system and ensure all the components turn ON properly (e.g. the touch screen turns ON). For more information on how to configure the router, please read the [tutorial on router setup](configuring-computer-and-networking/).

![](../.gitbook/assets/parts6.jpeg)

![](../.gitbook/assets/parts7.jpeg)

The Ethernet should plug into your router, more information about assigning a static IP [in this tutorial](https://www.evolver.bio/t/tutorial-configuring-local-router-and-computer-for-basic-evolver-use/71)_._

## 3) Plug in and screw on Smart Sleeves

If the system turns ON properly, turn off the eVOLVER and start fastening the Smart Sleeves. Use the 4-40 screws to fasten down each Smart Sleeve (2 screws/ sleeve). Vial 0 is in the front left (closest to the touch screen) with vials 1, 2, and 3 on the right of vial 0, in that order. Vial 15 is in the back right (farthest from the touch screen).

![](../.gitbook/assets/parts8.jpeg)

![](../.gitbook/assets/parts9.jpeg)

![](../.gitbook/assets/parts10.jpeg)

![](../.gitbook/assets/parts11.jpeg)

## 4) Setup pump rack

The Fluidics Platform is a separate module than the Vial Platform, typically is placed next to the Vial Platform. For this next part, we are setting up a pump rack that goes on top of the Fluidics Platform.

![](../.gitbook/assets/parts12.jpeg)

First we want to set up the components for the pump rack. The parts for this is located in the Fluidic Box Components Bag (Red Dot).

![](../.gitbook/assets/parts13.jpeg)

We want to fasten (w/ M6 screws) in aluminum extrusion into 3D printed part for the front pieces first. The front piece are the ones with the longer feet. See below:

![](../.gitbook/assets/parts14.jpeg)

![](../.gitbook/assets/parts15.jpeg)

Next, insert back piece. **Make sure the two feet are offset in the same direction.** Do not screw the screws in yet. We will screw those in when we mount everything together with the acrylic piece.

![](../.gitbook/assets/parts16.jpeg)

![](../.gitbook/assets/parts17.jpeg)

Repeat for the other side.

![](../.gitbook/assets/parts18.jpeg)

Next, line up the acrylic piece to the back holes and fasten together with M6 screws.

![](../.gitbook/assets/parts19.jpeg)

![](../.gitbook/assets/parts20.jpeg)

Screw in 10-32 screws to the feet of the mounts to fasten the pump rack on top of the Fluidics Box. Repeat to fasten all **four** mounts

![](../.gitbook/assets/parts21.jpeg)

![](../.gitbook/assets/parts22.jpeg)

## 5) Plug in Power + Communications to Fluidics Platform

Next, let’s setup the fluidics box. The fluidic box requires several connections:

* Two Power Entry Cables (one for 12V Power, other for 5V)
* Serial Communication Cable (To communicate with Raspberry Pi in Vial Platform)

Power the 5V power in the Fluidic Box from the USB port of the Raspberry Pi.

![](../.gitbook/assets/parts23.jpeg)

![](../.gitbook/assets/parts24.jpeg)

Connect Serial Communication Cable between the Vial Platform and the Fluidics Platform.

![](../.gitbook/assets/parts25.jpeg)

![](../.gitbook/assets/parts26.jpeg)

## 6) **Attach Pump Arrays to the Fluidics Box**

The fluidic box is meant to be flexible, to power whatever fluidic components you want. The standard setup assumes the following setup (back of fluidics box):

![](../.gitbook/assets/parts27.jpeg)

Attach ribbon cables to the appropriate slots on the PCB the pumps are mounted on.

![](../.gitbook/assets/parts28.jpeg)

Top down view of ribbon cable connections.

![](../.gitbook/assets/parts29.jpeg)

Finally, attach the tubing to the appropriate pumps.

![](../.gitbook/assets/parts30.jpeg)

## 7) Label Smart Sleeves with Appropriate Label

Labeling the vials with the appropriate color coded labels help minimize human error (I just print it and tape it on the vial). You can download a PDF of the file [here 17](https://drive.google.com/file/d/1dU9UwHoWeEc\_umC9RTkK3eqjdB1OCjvV/view?usp=sharing). The front left position (row closest to touchscreen) is vial 0.

![](../.gitbook/assets/parts31.jpeg)

![](../.gitbook/assets/parts32.jpeg)

