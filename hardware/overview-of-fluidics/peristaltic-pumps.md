---
description: Just like the digestive system!
---

# Peristaltic Pumps

## Standard components

The standard eVOLVER peristaltic pumps (since \~2020) sourced by Fynch Bio are selected specifically to eVOLVER use. Previous pumps used with eVOLVER during its early development tended to wear out quickly and have variable flow rates, primarily due to the mechanism for rotating the rollers against the tubing to drive pump flow. The motor shaft directly turned the rollers through friction, which led to slippage and abrasion over time. The current pumps do not have drirect contact between the motor shaft and rollers, instead driving roller rotation through a gear reduction system.

<figure><img src="../../.gitbook/assets/Screen Shot 2023-06-06 at 12.08.26 PM.png" alt=""><figcaption></figcaption></figure>

This gear system drives a roller casing with fixed roller axles contained in the pump head. In this way, the pump action does not rely on friction and thus much more accurate and durable than previous pumps.

<figure><img src="../../.gitbook/assets/Screen Shot 2023-06-06 at 12.10.01 PM.png" alt="" width="192"><figcaption></figcaption></figure>

Inside the pump head, the pump tubing can be removed and inspected. The tubing is 2x4mm Pharmed BPT, which has similar chemical compatibility as the silicone tubing for the rest of eVOLVER fluidics, and is rated to over 1000 hours of operating life. Learn more here: [https://www.biopharm.saint-gobain.com/components/fluid-transfer/pharmed-bpt-tubing](https://www.biopharm.saint-gobain.com/components/fluid-transfer/pharmed-bpt-tubing)

<figure><img src="../../.gitbook/assets/Screen Shot 2023-06-06 at 12.10.13 PM.png" alt="" width="227"><figcaption></figcaption></figure>



## Troubleshooting and repair

Because the current pump style has been introduced so recently, very few of them have failed from wear and tear. Based on our experience with other pump styles, the most likely failure mode will be collapse or tear of the tubing inside the pump head, or shearing of the tubing on the barb outside the head. This can be solved by replacing the pump head (contact Fynch Bio) or replacing the tubing.&#x20;

{% hint style="warning" %}
Pharmed BPT can be purchased from Saint-Gobain suppliers. However, the tubing should be 2mm ID and 4mm OD, and there is not enough tolerance to allow for similar non-metric sizes (like 1/16"x1/8"). 2x4mm Pharmed tubing is difficult to find in the US, and we are working on finding a reputable supplier for it. In the meantime, these alternatives from McMaster-Carr have been tested to seal and pump properly: [https://www.mcmaster.com/5102K11/](https://www.mcmaster.com/5102K11/) and [https://www.mcmaster.com/7027N11/](https://www.mcmaster.com/7027N11/)
{% endhint %}

The induction motor inside the pump is very unlikely to fail through normal use. If there is a liquid spill on the pump array and some pumps are not spinning, the most likely cause is corroded contacts with the pump array PCB. While the pumps themselves will be fine, they should be removed and replaced to a new PCB, ordered from Fynch or PCBWay. This will require removing solder, which can be tricky.

## Swapping and modifying

The pump heads can be rotated 90 degrees in any direction, should your bench setup require changing the direction your pumps face.

The low-flow pumps available through Fynch use an additional gear reduction box to reduce the speed of pump action by a factor of 45. This is useful for addition of inducers, antibiotics, or other media feeds that require a small and precise bolus.

Plenty of other peristaltic pumps are suitable for eVOLVER, so long as they operate at 12V.

The flow rate of eVOLVER pumps (and any pump with an induction motor) is somewhat modifiable through PWM modulation. This effectively reduces the voltage going to the pump, which will slow its rotation, down to the point where the coils can't generate enough torque to consistently turn the shaft. This happens about halfway through the PWM range (around 2000), where you can get the pumps to run at about 1/3 speed. This is rarely necessary for experiments, so it has not been optimized, but is a potential feature for users to explore.
