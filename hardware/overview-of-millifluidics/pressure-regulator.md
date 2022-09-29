---
description: Described initially in Huang, Heins et al. 2022 Nature Biotech
---

# Pressure Regulator

## Description

As IPP devices are sensitive to changes in pressure at valves and in connected media bottles, we developed an 8-channel pressure regulator that can be used to regulate these pressures through the eVOLVER framework. The device consists of sets of two proportional valves that can limit air flow from a high-pressure source and a vent at atmospheric pressure. By connecting an electronic pressure gauge to the output of this valve configuration, it is possible to implement proportional-integral-derivative (PID) control over the valves in order to set the output pressure to any desired level between the input and atmospheric pressure. We validated the functionality of this device by regulating pressure at 1.5 psi over 24 hours, and compared the performance of our device with that of a fixed, manually set regulator (PARKER-WATTS R25-02A) connected to the benchtop air supply (Supplementary Figure 3). The average pressure with PID control was 1.498 psi with an RMS error of 0.0086 psi, while the fixed regulator had an average pressure of 1.706 psi with an RMS error of 0.2220 psi. Large pressure deviations (>0.5 psi) that can affect the performance of the devices were observed with the fixed regulator, but were successfully eliminated with our automated pressure regulator scheme. We further characterized the effects of pressure changes at various locations in the system in order to optimize performance of the IPP devices for the course of a PACE experiment (Supplementary Figure 3).





