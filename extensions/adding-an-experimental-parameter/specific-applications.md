# Specific Applications

[Adding pH and Dissolved Oxygen Sensors](https://www.evolver.bio/t/adding-sensors-ph-and-do/353)

## Optogenetic Control During Continuous Culture

[Forum Post](https://www.evolver.bio/t/early-questions-on-optogenetics-extensions/183)

Light inducible protein domains have been used to dynamically control and rapidly prototype genetic networks24,52. Hardware for light inducible systems typically rely on batch culture, limiting experiments to a narrow time window in which all cells across an experiment are in exponential phase. Attempts at coupling continuous culture to light induction have been limited by throughput (1-2 cultures) and reconfigurability. Equipped with components for light induction, eVOLVER would uniquely enable long-term optogenetic perturbations in finely controlled growth phases across a large number of culture vessels. Due to the modularity of eVOLVER hardware components, integrating optogenetic control is straight forward and requires minor modifications to the system. Details on integrating LEDs into eVOLVER is described in more detail as the example modification in Supplementary Note 4.

## Fluorescence Measurements

Bulk fluorescence measurements have previously been demonstrated by Takahashi et al. during continuous culture, without the use of a photomultiplier tube (PMT)7. To recapitulate this setup in eVOLVER, an extra LED-diode pair would be added to the 6th and 7th S/A Slots, similar to adding LEDs for light induction. Additionally, the 3D printed part would be modified to house optical filters for better detection of any fluorescence signal. Potential setbacks in this setup (without a PMT) include potentially a low signal to noise ratio. This can be solved by multiplexing signal from all cultures into a single PMT via fiber optics. The electronics controlling the PMT would communicate back to the same RS485 line to be controlled by the same Raspberry Pi, similar to the auxiliary board. Alternatively, single cell fluorescence measurements would also be made possible by interfacing eVOLVER with a pipetting robot, droplet microfluidics, or using the native pump from the flow cytometer sample directly from the cultures. These systems could interface serially with the Raspberry Pi via RS485/USB or the lab computer via USB.
