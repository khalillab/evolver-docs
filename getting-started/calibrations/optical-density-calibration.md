---
description: >-
  The goal of this tutorial is to learn how to efficiently generate OD
  calibration curves for each Smart Sleeve in a 16 vial eVOLVER setup.
---

# Optical Density Calibration

{% hint style="danger" %}
You must complete [temperature calibrations ](temperature-calibration.md)before doing OD. Temperature effects OD and if there are big differences between vials, you will need to recalibrate all vials once you do a temperature calibration.
{% endhint %}

## About

**Why are OD measurements important?**

The turbidity (cloudiness) of the culture typically correlates to how many cells are in a culture. By using a simple LED and photodiode pair, we can quantify how many cells are in the population, track how the culture is growing over time, and observe the culture changing over the course of the experiment.&#x20;

**Why is calibration necessary?**

Readings sent from the Raspberry Pi to the computer/server are the raw voltage values measured by the Arduino in the Motherboard. In other words, to make sense of what these readings are, we need a calibration file that converts this to a useable optical density measurement.&#x20;

**Is calibration different between different organisms?**

Yes. Cells with different size and shapes scatter differently and would result in unique calibration curves. eVOLVER is set up such that one could easily use the appropriate calibration files for each experiment/organism.

**Is calibration different between different temperatures?**

Yes. Temperature effects the photodiode sensors that we use to measure OD. If you plan to use different temperatures we suggest doing a new calibration for each one.

## Prepare the day before:

* 16 assembled glass vials:
  * Glass vials  (Chemglass, CG-4902-08)
  * Vial screw caps
  * Octagon magnetic stir bars (Fisher, 14-513-57)
* 300 mL of saturated culture of desired organism
  * If calibrating to ODs above 1.5, you may need more cells
* 300 mL of 1X PBS (Phosphage Buffered Saline)

{% hint style="info" %}
Check your Smart Sleeves with a vial containing water vs a culture of an arbitrary OD to make sure that you see some change in the Setup page of the GUI. Otherwise you will need to change the photodiode or OD LED.
{% endhint %}

## OD Standard Preparation

{% hint style="info" %}
Before preparing standards, turn eVOLVER on and [set all vials ](../../guides/use-the-gui-to-control-parameters.md)to the temperature you will use this calibration at (ie 37C for E coli and 30C for yeast) and set stirring to 8.
{% endhint %}

**Wash cells and resuspend in 1X PBS to avoid cell growth**

1. Spin down saturated cultures in 50mL or 250mL centrifuge tubes.
   1. 2500 rcf for 5 minutes should be fine for bacteria or yeast
2. Pour off media and resuspend cells in 50mL 1X PBS
3. Spin down cells in a 50mL conical tube
4. Resuspend well in 50mL 1X PBS

**Find OD of Concentrated Cell Stock and Make Standards**

{% hint style="info" %}
The cell stock will likely be much too dense to measure undiluted. For example, OD600 absorbance values on our plate reader above about 0.5 are inaccurate and we can expect this stock to be above an OD of 4.
{% endhint %}

5. Measure the OD of cell stock using a dilution series
   1. Dilute 200uL of cells into 1800uL of 1X PBS (1:10)
   2. Dilute the 1mL of the 1:10 dilution into 1mL 1X PBS (1:20)
   3. Make 1:40 and 1:80 dilutions
6. Measure OD of dilutions and a _1X PBS blank_
   1. It is recommended to use 300uL of dilution if using plate reader to provide a similar read length to the cuvette
   2. Use absorbance at 600nm for most bacteria and yeast
7. If the measured OD of the lowest dilution is above 0.5, make further dilutions to bring it below 0.5

{% hint style="info" %}
**Use** [**this**](https://docs.google.com/spreadsheets/d/1mrmWbOMNhthNafGRZVcuHpOfvZxxA8NoWAqzd2bzuNM/edit?usp=sharing) **spreadsheet to make calculations.** Make a copy on your own Google Drive or download for use in Excel.
{% endhint %}

8. Calculate OD of concentrated cell stock
   1. Input ODs for dilution and 1X PBS blank into the spreadsheet
   2. Enter calculated OD into 'OD of Cell Stock'
      1. Use a dilution that is roughly between 0.1 and 0.5
9. Calculate and make OD standards
   1. Optional: alter the series of standards to include more ODs in the range you care about
   2. Get 16 vials and add a stir bar to each
   3. Add calculated amount of 1X PBS and cell stock to each vial
   4. Mix by swirling or putting in eVOLVER with stirring on

**Measure OD of Standards**

10. Make dilutions for standards above 0.5 OD
    1. Use a 96-well plate to ease dilutions and transfer to plate reader &#x20;
11. Measure ODs and calculate original OD from dilution OD
    1. An example calculation, including the 1X PBS blank is included at the bottom of the spreadsheet
12. Adjust standards if necessary
13. Cap vials containing standards and place in eVOLVER to equilibrate to temperature while stirring
    1. Keep track of which vial is which OD
    2. This may take >30 minutes
    3. Each vial is labelled with its latest temperature in the `SETUP` page of the GUI

{% hint style="info" %}
Don't immediately throw out your standards after finishing calibration! You could need to make another calibration should one or more vials be off.
{% endhint %}

## Calibrate OD using the GUI

13. On the eVOLVER app home screen, make sure you are connected to your eVOLVER (green symbol next to active eVOLVER), then choose `CALIBRATIONS` and then `O.D.`

<figure><img src="../../.gitbook/assets/image (3) (1) (2) (1).png" alt=""><figcaption></figcaption></figure>

14. Give the calibration a name (a standard suggestion is `YYMMDD_YourInitials_od`) and _click_ enter.
15. Click on the white box by the `S0`. The display should now have an overlay with `Sample 0` on top of a box with a keypad. Input the OD values of each sample.
    1. You can input the OD values using the keyboard, then hit enter to increase the vial selected.
16. Click `Start OD Calibration ▷`.&#x20;

<figure><img src="../../.gitbook/assets/image (14) (2).png" alt=""><figcaption></figcaption></figure>

17. Press `▷`. After the eVOLVER has logged the vials in one configuration, click the forward arrow. Move vials into their new positions, as seen on the right side of the GUI.
18. Click `VIEW COLLECTED DATA` to monitor the smoothness of the curves as you calibrate. If a particular value is a big outlier, consider rewinding to that vial position and doing it again. Don't worry your other work will be saved!
19. Continue until all sixteen sets of values have been saved for each standard in each vial.
20. Click the pen button to submit and save the calibration. Then click `Exit` after the calibration is logged.
21. To validate the calibration was logged on the eVOLVER, from the touch screen home tap `Setup` and then tap the box next to `OD:` and a list of calibrations should come up. Select your recent one from the list. If not present, it was not logged to the eVOLVER.

{% hint style="info" %}
Before doing an experiment it is recommended to further validate your calibration (after you have selected it on the `SETUP` page) by [starting an experiment](../../experiments/starting-an-experiment/gui-start-guide.md) and logging a few values for each vial at a known OD.
{% endhint %}
