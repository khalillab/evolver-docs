# Smart Sleeve

![](<../../.gitbook/assets/image (28).png>)

## Description

The programmable Smart Sleeve is the foundational unit on which the eVOLVER is built (Fig. 2 and Supplementary Fig. 1). The Smart Sleeve is comprised of all the sensors and actuators required to control the culture conditions inside a 40 mL borosilicate glass vial. At the core is an aluminum sleeve, which surrounds the vial and is used to control temperature via two resistive heaters and a thermistor integrated within. Near the base of the vial sits a 3D printed part that houses and aligns the optical density LED and photodiode. Below that sits a fan motor equipped with magnets to rotate a stir bar within the vial. The Smart Sleeve represents one of the most easily customized features of the eVOLVER: by changing which sensors and actuators are used and their layout, the user may develop culture vessels that fit their experimental needs. For a detailed description of the sensors and actuators used to control stirring, temperature, and optical density in Smart Sleeves featured in this study, as well as strategies for modifying the Smart Sleeve to fit experimental needs, refer to Supplementary Note 4. Liquid handling is also controlled at the level of the individual culture vessel, yet these components are housed in a separate fluidic module, described in Supplementary Note 5. The sensors and actuators on each sleeve are integrated in a small printed circuit board (PCB), termed the Component Mount Board (CMB). We designed the CMB such that we can easily solder electrical connections and efficiently manage/package wiring from the sensors. The CMB is a very simple PCB, containing only a few resistors, and is straightforward to redesign and inexpensive to manufacture, if needed. The simplicity in the CMB leads to robustness in the system. For example, any accidental overflow and spillage from the vials (e.g. from clogged fluid lines or user error) should minimally impact the rest of the system, as critical components are located at the Motherboard rather than the sleeve itself. Ribbon cables provide a modular way to connect the integrated Smart Sleeves to the Motherboard. The CMB is designed to rest atop a 3D printed piece, which houses optical density and temperature components (see Supplementary Note 4). The printed part can be fabricated with Nature Biotechnology: doi:10.1038/nbt.4151 5 any commercial or DIY 3D printer, readily available at almost any university or hacker space, and customized to the requirements of the user. For example, if a user wanted to change the mode of optical density detection between scattering and absorption, they could redesign the 3D printed part housing the LED-diode pair such that it would have the correct offset angle for the desired mode of measurement.

Vial

Vial Holder

Vial Sleeve

Vial Cap

Vial Board
