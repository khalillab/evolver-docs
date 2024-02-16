# Vial Overflow, Pump Failure, and Spills

Vial overflow is one of the most common problems to plague eVOLVER experiments. Overflow events can cause damage to internal components such as the PCB motherboard, sensor actuator (SA) boards, power supplies, etc. If you experience overflow during an experiment, it is important to immediately stop the eVOLVER and evaluate potential causes of overflow, as well as any damage that the overflow may have caused.

If you catch an overflow that happened recently (i.e. an overflow that happened overnight), the best thing you can do after stopping the experiment is turn off and unplug the eVOLVER, determine the extent of overflow spilling, and wash any components that have media on them. There are no components on the vial board or motherboard that retain significant charge (i.e. no batteries or large capacitors), so they are safe to wash gently in soap and water. Once clean, they should be dried quickly with a paper towel.

The main reason for electronics failure after an overflow is current shorting through media (most microbial media is salty and conductive), or connections and copper corroding from media that has been left to dry. If you can clean off all the media immediately after an overflow, you will have a much better chance of saving electrical components, and saving yourself many headaches down the road.

If you did not catch an overflow quickly, or a large amount of media spilled, follow the workflow below.

## Troubleshooting Workflow for Overflow

### Inspecting internal components

Overflowed media can enter into the vial platform through the ports that connect the Smart Vials to the motherboard. This can cause damage to the internal circuitry, which is should first be evaluated by visually inspecting the motherboard, SA boards, power supplies, and Raspberry Pi. Damage to any of these components can look like burned or melted spots or loose/broken connections. If you see visible damage to any of these parts, they will need to be fully replaced. See pages below for specific instructions on how to replace these various parts.

[motherboard-troubleshooting.md](../motherboard-troubleshooting.md "mention")

## Old evolver pumps (solid black plastic head)

[Pump is not actuating / spinning](https://www.evolver.bio/t/how-can-i-verify-the-pump-is-correctly-actuating-and-spinning/100/6)

## Relevant Forum Posts

[Pump failure and spill, lessons learned](https://www.evolver.bio/t/pump-failure-and-spill-lessons-learned/125)
