---
description: Making culture continuous
---

# Overview of Fluidics

For eVOLVER to be more than a 16-well plate reader, there needs to be control of liquid flow through each vial. The most common hardware for this application is the peristaltic pump, used in continuous culture for almost a century. Novel aspects of eVOLVER include the automated, individual control of these pumps, and modularity for different types and numbers of pumps. This is enabled by an auxiliary fluidic board, separate from the motherboard, that controls up to 48 fluidic actuators. For typical eVOLVER use, this is coupled with 32 pumps (16 for influx, 16 for efflux), 64 lines of tubing (to and from each pump), and 128 barbed connectors (for both ends of each line of tubing). This section of the Wiki will go into detail of how each component works, and options for repair, troubleshooting, swapping, and modifying them in the eVOLVER fluidic hardware framework.



![Modular fluidic control system for the eVOLVER platform. (a) Electronic hardware for fluidic control. The Auxiliary Board enables one Arduino to independently and simultaneously control 48 fluidic elements (e.g. pumps and valves) via three PWM boards. (b) Schematic of system design for basic fluidic control. Serial commands from the Raspberry Pi are sent to the Motherboard and Auxiliary board on the same RS485 communication line. The Auxiliary board interprets the appropriate serial commands and actuates specific pumps for fluids to be metered in and out of a target smart sleeve.](<../../.gitbook/assets/image (2) (1) (3).png>)

