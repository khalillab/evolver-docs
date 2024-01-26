---
description: High-level description of hardware architecture
---

# Overview of Hardware Architecture

1. Smart Sleeve
2. Motherboard
   1. SAMD21 Arduino Microcontrollers
   2. Characterized SA Boards
      1. PWM Board
      2. ADC Board
3. Auxiliary Board

## **General Overview**

The eVOLVER hardware framework contains three levels of organization: (1) programmable sensors and actuators (e.g. Smart Sleeve components, pumps/fluidic control elements) (2) a Motherboard and microcontrollers, and (3) a Raspberry Pi. At the level of individual culture vessels, Smart Sleeves enable individual control over several experimental parameters in the culture.&#x20;

Specifically, each sleeve contains sensors and actuators (e.g. heaters, LEDs, thermometer/thermistor) that measure and adjust aspects of the culture environment of a glass vial housed within. At the next level of organization, the Motherboard, Arduino microcontrollers, and other core electronic boards form a robust hardware infrastructure that communicates internally and coordinates activity of each individual Smart Sleeve to control each experimental parameter.&#x20;

At the final level of organization, a Raspberry Pi forms a link to the outside world by relaying information and commands to and from a computer/server, permitting the same computer/server to run many eVOLVER devices across a network. Layered on top of the hardware framework, control software enables programmable feedback between parameters and orchestrates experiments at an abstract level, providing an easy method of customization that is shareable with other users. Below we present the core hardware framework as well as the particular configuration enabling the experiments described in this study.

![This is for the old motherboard / smart sleeve which had 7 slots for customization of sensor/actuator (SA) boards. The current motherboard / smart sleeve combination has 8.](<../.gitbook/assets/image (15) (2).png>)

## **Smart Sleeve**

The Smart Sleeve houses each culture vial and contains all the necessary sensors and actuators to regulate desired culture parameters. An aluminum sleeve surrounds the vial, which is mounted into a 3D printed part that houses a printed circuit board (PCB) called the Component Mount Board (CMB). The CMB contains a variety of different sensors and actuators needed to regulate culture conditions. As the most flexible component in the eVOLVER Framework, the Smart Sleeve can be re-designed to regulate other culture conditions based on the user's end application.&#x20;

## **Motherboard**

The Motherboard is responsible for housing custom PCBs and Arduino microcontollers that control user defined culture conditions by routing signals to and from an array of Smart Sleeves. Custom PCBs are plugged into SA (sensor/actuator) slots, of which there are 8. Using the routing system, these custom PCBs can collect data from CMB sensors or deliver power to CMB actuators. For example, in the base eVOLVER setup, there is a SA slot dedicated to individually powering heaters across all 16 Smart Sleeves.

### **SAMD21 Arduino**

On the Motherboard are 4 SAMD21 Arduinos, each of which is responsible for regulating a single culture parameter. To do so, each SAMD21 board is electrically connected to 2 SA slots since many culture conditions require both a sensor and actuator. To regulate temperature, for example, a single SAMD21 will leverage its SA slot pair to sense the temperature for each Smart Sleeve and provide the necessary power to each Smart Sleeve heater to maintain the user-defined temperature for each culture vial. This modular design enables functional parallelization of culture parameters, providing a high degree of flexibility to users when designing hardware for experiments.

### **Characterized SA Boards**

FynchBio has designed and characterized the PWM Board and ADC Board, two PCBs that plug into Motherboard's SA slots. These boards are designed to power actuators and collect sensor data for existing CMB components and should be sufficient to handle custom reconfigurations.

#### PWM Board

The PWM Board is designed to power 16 actuators, in parallel, by amplifying the SAMD21 voltage ouptut using the Motherboard's voltage source. The PWM Board leverages pulse-width modulation (PWM) signals to power actuators, allowing digital signals to better approximate analog signals. This is essential because analog signals provide precise control of actuators, rather than simple ON/OFF dynamics with digital signals.&#x20;

**ADC Board**

The ADC board is a 16-1 de-multiplexer that collects data from 16 sensors and filters it before sending it to its cognate SAMD21 Arduino. Specifically, the ADC Board reads the output voltage from a basic voltage divider circuit integrated with the sensor on the CMB. After analog signals are collected, they are filtered to remove noise, sent to the SAMD21 Arduino through an input pin, and finally converted to a digital signal for downstream data processing.

## Auxillary Board

Akin to the Motherboard, the Auxillary Board is a custom PCB designed to control a peristalitc pump array to handle fluidic functions. This includes removing waste and adding nutrients/chemicals to cultures. The Auxillary Board contains a single SAMD21 Arduino, which connects to 3 PWM Boards to actuate 48 peristaltic&#x20;
