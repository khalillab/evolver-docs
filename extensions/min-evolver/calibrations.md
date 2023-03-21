# Calibrations

## Overview

* [Calibrations](../../getting-started/calibrations/) are important for the eVOLVER to match its sensors inputs with its actuator outputs
* The min-eVOLVER is not yet compatible with the normal eVOLVER GUI
* Therefore, calibrations must be done manually (ie via recording of values and fitting of lines in excel).

{% hint style="info" %}
Each min-eVOLVER needs its own calibration files. These are kept inside of the server folder for each min-eVOLVER run (ie in `evolver-min/evolver/calibrations.json`)
{% endhint %}

## Before Calibration

1. Complete the [setup](setup.md) page
2. Gather materials (see below)
3. Start cells for OD calibration the night before
4. Calibrate temperature before OD

{% hint style="warning" %}
Temperature calibration should be done before OD calibration because the OD sensors are effected by temperature. Calibrate OD at the temperature that you intend to run experiments. (For example 37C for bacteria and 30C for yeast)
{% endhint %}

## Materials

* Glass eVOLVER vials (6X)
* eVOLVER vial caps (6X)
* Digital temperature probe (we use a [Fisherbrand™ Traceable™ Hi-Accuracy 0.01° Refrigerator Thermometer](https://www.fishersci.com/shop/products/traceable-hi-accuracy-0-01-refrigerator-thermometer/S98174))
* 20mL pipette or a small graduated cylinder
* 200mL cells at OD600 > 2

## Temperature Calibration

### About

* During temperature calibrations we will be setting the min-eVOLVER temperature to various 'raw' (uncalibrated) values
* We will then measure the actual temperatures that the min-eVOLVER vials reach using a temperature probe
* We then fit a line correlating the raw values to temperatures in degrees Celsius&#x20;

### Procedure

1. Make a copy of `temperature_calibration.xlsx` and label with the date.
   1. This can be found in `/dpu/calibration/`
2. Fill eVOLVER vials with 15-20mL of water, put in stir bars, and place in aluminum sleeves.
3. Turn on the min-eVOLVER and start the server as in [setup](setup.md).
4. In the dpu virtual environment, send the following temperature command to the min-eVOLVER using [`send_command.py`](send\_command.py.md):
   1. `python3 send_command.py <port_number> temp 31000`
5. Wait for the temperature to equilibrate (using a digital temperate probe)

{% hint style="info" %}
While waiting for equilibrations you can start calibrating pumps.
{% endhint %}

6. Record the equilibrated temperature (in Celsius) in the space in the spread sheet for the correct vial
7. Repeat steps 3 - 6 for the other three values
8. Ideally the resulting plot will be linear, with little variation of the points from the line
9. Copy and paste the values under "Copy + Paste" in `evolver-min/evolver/calibrations.json` for the correct min-eVOLVER
   1. Replace the values _and comma_ after "coefficients" (shown below)
   2. WARNING: do not alter the format of the `calibrations.json` file. Doing this, (accidentally adding an extra square bracket or comma for example) could easily give errors during experiments.

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

## Pump Calibration

1. Make a copy of `pump_calibration.xlsx` and label with the date.
   1. This can be found in `/dpu/calibration/`
2.  Fill a large beaker with water and submerge all pump input and outputs in the water

    ![](../../.gitbook/assets/PXL\_20220728\_164925874.jpg)
3. Fill the pump lines by sending the following pump command to the min-eVOLVER using [`send_command.py`](send\_command.py.md):
   1. `python3 send_command.py <port_number> pump 30,30,30,30,300,300`

{% hint style="info" %}
If you need the pumps to stop before the time is up, send the command:

`python3 send_command.py <port_number> pump 0`
{% endhint %}

4. Wait for the pump lines to fill
5. Calibrate the fast (grey) pumps
   1. Leave fluidic inputs in water and put the outputs in eVOLVER vials
   2. Send the command:
      1. `python3 send_command.py <port_number> pump 20,20,20,20,0,0`
   3. Measure the resulting water output (either using a 20mL autopipette or using a small graduated cylinder)
   4. Input the values into the excel spreadsheet
   5. If you see significant variability, make sure all inputs are in water and try again

![](<../../.gitbook/assets/image (10).png>)

6. Calibrate the slow (pink) pumps
7. Leave the inputs in water and put the outputs in 1.5mL Eppendorf tubes
   1. It may be helpful to remove the plastic Luer lock on the tube end
   2. Make sure that the tubing is still full (send another command if not)
8. Send the command:
   1. `python3 send_command.py <port_number> pump 0,0,0,0,40,40`
9. Measure the resulting water output (using a 1mL pipette)
10. Input the values into the excel spreadsheet (in mL)
11. Copy and paste the values under "Copy + Paste" in `evolver-min/evolver/calibrations.json` for the correct min-eVOLVER
    1. Replace the values __ after "coefficients" (shown below)

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

## OD Calibration

### About

* OD calibration allows for the min-eVOLVER to accurately read ODs of the cells growing inside.
* While not completely essential with running chemostats, good OD calibrations are essential for turbidostats to give accurate results.

### Procedure

1. Set the min-eVOLVER to the temperature your experiment will be at
   1. Open your temperature calibration file
   2. Change the temperature in the "Set to ( C )" field for each vial
   3. Copy and paste the command next to "Temperature command:" field. (Change to target your min-eVOLVER's port)&#x20;
2. Follow the OD calibration [tutorial ](../../getting-started/calibrations/optical-density-calibration.md)for the main eVOLVER until it asks to begin calibration via GUI
   1. We will use this to make 8 standards, rather than 16
   2. This will be less vials to deal with
3. Heat dilutions to temperature
   1. Ideally, the vials will be stirring and continuously at the correct temperature
      1. Stirring because cells will settle otherwise
      2. At temperature because it effects the OD sensor
   2. However, the min-eVOLVER only has 2 vials, so we must find a way to make sure the vials are at temperature before reading the OD values
   3. We can either do this by
      1. Waiting for vials to come to temperature in the min-eVOLVER vials (slow)
      2. Keeping vials in an incubator until ready for reading (faster)
         1. Make sure cells are suspended before reading values either through keeping in a shaking incubator or through pipetting or swirling
4. While dilutions are heating
   1. Make a copy of `od_calibration.xlsx` with the date
   2. Input the optical density of your standards into the `Standard (OD600)` cells
5. Make sure the od\_led is set to 4095
   1. Either check the server cycling log or send the command:
      1. `python3 send_command.py <port_number> od_led 4095`
6. Record 3 server values for each dilution
   1. Cycle through the dilutions in an orderly fashion
   2. For example:
      1. Label the vials 1 - 8
      2. Start with vial 1 in smart sleeve 1 and vial 2 in smart sleeve 2
      3. Then rotate so that vial 8 is in sleeve 1 and vial 1 is in sleeve 2
      4. Repeat for all vials

{% hint style="info" %}
After changing which dilution is being read, wait for the server to cycle a couple of times before recording values. Values are averaged and the values from the old dilution could still be in the mix.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (49).png" alt=""><figcaption><p>Highlighted are the OD sensor values for the first and second vials respectively on a min-eVOLVER.</p></figcaption></figure>

9. Copy and paste the `Standard (OD600)` and `Median Values` for each vial into `od_data.xlsx`
   1. Do not include empty cells or change the formatting of `od_data.xlsx`&#x20;
   2. If you only have one min-eVOLVER you are calibrating, clear the rest of the rows of data to avoid confusion.
10. In a terminal in the dpu environment, install `pandas` using the command
    1. `pip install pandas`
11. Run the following script for fitting a sigmoid function to the curve:
    1. `python3 sigmoid_fit.py`
12. Evaluate the resulting curve fit in the window that pops up

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption><p>Fitting curves to OD calibration data for two min-eVOLVERs. While there is some noise, standards generally follow the sigmoid function.</p></figcaption></figure>

9. Copy and paste the values output from `sigmoid_fit.py` in `evolver-min/evolver/calibrations.json` for the correct vial and correct min-eVOLVER

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

10. Replace the values __ after "coefficients" (shown below)
    1. To avoid confusion, replace everything until the `"raw"`&#x20;

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>
