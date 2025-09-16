# OD Calibration via Growth Curve

{% hint style="warning" %}
You need to have finished [temperature calibration](./#temperature-calibration) before doing this step.
{% endhint %}

## Overview

{% hint style="warning" %}
For running ePACE, this calibration is _required_ because S2060 cells have significantly different scattering properties while growing vs during stationary phase.
{% endhint %}

This alternative method of calibrating OD is to be used if experimental raw OD values repeatably follow a different function than calibration OD values. This means that the OD calibration cannot be fixed despite recalibration and attempting to get better OD blanks.

### Similarity to Experimental Conditions

Using this protocol, we can get significantly closer to actual experimental conditions in our OD calibration compared to the normal calibration where we use cells in stationary phase resuspended in 1X PBS.

We also turn off stirring for OD to get more stable OD readings. This is especially important in ePACE where the lagoon is only 10mL and thus the liquid line is very close to the OD sensor level.

{% hint style="info" %}
Consider [reusing the same vial assembly](../epace-with-min-evolver/reusing-vial-assembly-between-experiments.md) between experiments to have the OD calibration conditions line up perfectly with the experimental conditions.
{% endhint %}

## Protocol

1. Prepare _actively growing_ cells of the type you want to calibrate
   1. If cells are in stationary phase when you start this protocol, dilute at least 1:100 and grow for several hours before using for inoculation
   2. This way your cells will be as close as possible to experimental physiology during calibration
2. Load up the stir off for OD read conf.yml file
   1. Location in the folder for the min-eVOLVER's [server](https://github.com/FYNCH-BIO/evolver/blob/min/evolver/alternate_conf_files/stir_off_for_od_read/conf.yml): `/evolver/alternate_conf_files/stir_off_for_od_read/conf.yml`
   2. If necessary, edit the `port` and `serial_port`variables to the correct port for this min-eVOLVER
3. Start the [server](../software-installation-and-startup.md#server-startup)
4. Check that the min-eVOLVER is stirring and turning off during OD readings
5. Set temperature to experimental temperature using [`send_command.py`](../send_command.py.md) and your [temperature calibration spreadsheet](./#temperature-calibration)
   1. A calibrated temperature command is in your calibration file `temperature_calibration.xlsx`&#x20;
   2. Change the temperature in the "Set to ( C )" field for each vial
   3. Copy and paste the command next to "Temperature command:" field. (Change to target your min-eVOLVER's port)&#x20;
6. Assemble two vials and place them inside of the Smart Sleeves
   1. Vials should mimic the experiment as closely as possible
   2. Use stir bars, caps, septa and needles if you will use them in your experiment
   3. For ePACE guide see [here](../epace-with-min-evolver/#vial-setup)
7. \[Optional] Hook up influx and efflux lines to vials for easy volume control
   1. Using [`send_command.py`](../send_command.py.md),
   2. Fill lines with bleach
   3. Wait 30 minutes for sterilization
   4. Flush bleach 3 times through with media
   5. Hook up lines to vial cap - for ePACE guide see [here](../epace-with-min-evolver/#fluidic-lines)
8. Fill vials with the media you will use for experimentation to the fluid levels you will use during experimentation
   1. For ePACE:
      1. Reservoir (left) vial = 30 mL
      2. Lagoon (right) vial = 10 mL
   2. Other experiments: most likely 25 mL in both vials
9. Allow vials to come to temperature (wait at least 20 minutes)
   1. Temperature affects OD readings
10. While vials are heating
    1. Make a copy of `od_calibration_growth_curve.xlsx`&#x20;
       1. Rename with the date and type of calibration
       2. For example: `od_calibration_growth_curve_250101.xlsx`&#x20;
    2. Input the optical density of your standards into the `Standard (OD600)` cells
11. Make sure the od\_led is set to 4095
    1. Either check the server cycling log or send the command:
       1. `python3 send_command.py <port_number> od_led 4095`
12. Record a 'blank' value for media without cells using your external OD reader
    1. Record next to the cell `MEDIA BLANK:` in the upper left of the spreadsheet

{% hint style="info" %}
If using a 96-well plate reader, _always_ use 300uL of sample in the wells to best mimic the optical path length of a cuvette reader.
{% endhint %}

13. After temperature equilibrates, record 3 server values for the media without cells

<figure><img src="../../../.gitbook/assets/image (17) (1) (1).png" alt=""><figcaption><p>Highlighted are the OD sensor values for the first and second vials respectively on a min-eVOLVER.</p></figcaption></figure>

14. Inoculate with growing cells to a low OD - aim for OD < 0.05
15. Pick a time interval for sampling based off of the growth rate of your cells
    1. For example, every 20 minutes for ePACE cells
16. As cells grow, in intervals:
    1. Record sets of 3 raw OD values from the min-eVOLVER server
    2. Simultaneously sample the OD in vial using your external OD reader and record in the `External OD` column
       1. Replace any volume you remove via sampling, either through pumping or manually pipetting back in. This is especially important for the 10mL lagoon used in ePACE.
    3. Collect OD values over the entire range you wish your experiment to work in&#x20;
17. Copy and paste the `Standard (OD600)` and `Median Values` for each vial into `od_data.xlsx`
    1. Do not include empty cells or change the formatting of `od_data.xlsx`&#x20;
    2. If you only have one min-eVOLVER you are calibrating, clear the rest of the rows of data to avoid confusion.
18. In a terminal in the `dpu` environment, install `pandas` using the command
    1. `pip install pandas`
19. Run the following script for fitting a sigmoid function to the curve:
    1. `python3 sigmoid_fit.py`
20. Evaluate the resulting curve fit in the window that pops up

<figure><img src="../../../.gitbook/assets/image (2) (2) (1).png" alt=""><figcaption><p>Fitting curves to OD calibration data for two min-eVOLVERs. While there is some noise, standards generally follow the sigmoid function.</p></figcaption></figure>

21. Copy and paste the values output from `sigmoid_fit.py` in `evolver-min/evolver/calibrations.json` for the correct vial and correct min-eVOLVER

<figure><img src="../../../.gitbook/assets/image (15) (1).png" alt=""><figcaption></figcaption></figure>

22. Replace the values after "coefficients" (shown below)
    1. To avoid confusion, replace everything until the `"raw"`&#x20;

<figure><img src="../../../.gitbook/assets/image (11) (1).png" alt=""><figcaption></figcaption></figure>

