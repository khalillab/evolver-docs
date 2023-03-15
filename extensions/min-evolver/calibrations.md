# Calibrations

## Overview

* [Calibrations](../../getting-started/calibrations/) are important for the eVOLVER to match its sensors inputs with its actuator outputs
* The min-eVOLVER is not yet compatible with the normal eVOLVER GUI
* Therefore, calibrations must be done manually (ie via recording of values and fitting of lines in excel).

{% hint style="info" %}
Each min-eVOLVER needs its own calibration files. These are kept inside of the experiment folder for each min-eVOLVER run (ie in `dpu/experiment/experiments/<your_experiment_folder>`)
{% endhint %}

## Before Calibration

1. Complete the [setup](setup.md) page
2. Gather materials (see below)
3. Start cells for OD calibration the night before
4. Calibrate temperature before OD

{% hint style="warning" %}
Temperature calibration should be done before OD calibration because the OD sensors are effected by temperature. Calibrate OD at the temperature you intend to run experiments at. (For example 37C for bacteria and 30C for yeast)
{% endhint %}

## Materials

* Glass eVOLVER vials (6X)
* eVOLVER vial caps (6X)
* Digital temperature probe (we use a [Fisherbrand™ Traceable™ Hi-Accuracy 0.01° Refrigerator Thermometer](https://www.fishersci.com/shop/products/traceable-hi-accuracy-0-01-refrigerator-thermometer/S98174))
* 20mL pipette or a small graduated cylinder
* 200mL cells at OD600 > 2

## Temperature Calibration

### About

* During temperature calibrations we will be sending values to the min-eVOLVER
* The min-eVOLVER then tries to change the output values from the temperature sensor to match our input value by increasing or decreasing the heater.

### Procedure

1. Make a copy of `temperature_calibration.xlsx` and label with the date.
   1. This can be found in `/dpu/calibration/`
2. Fill eVOLVER vials with 15-20mL of water and put in stir bars
3. Send the following temperature command to the min-eVOLVER using [`send_command.py`](send\_command.py.md):
   1. `python3 send_command.py <port_number> temp 31000`
4. Wait for the temperature to equilibrate (using a digital temperate probe)

{% hint style="info" %}
While waiting for equilibration you can start calibrating pumps.
{% endhint %}

6. Record the equilibrated temperature (in Celsius) in the space in the spread sheet for the correct vial
7. Repeat steps 3 - 5 for the other three values
8. Ideally the resulting plot will be linear, with little variation of the points from the line
9. Copy and paste the values under "Copy + Paste" in `temp_cal.json`
   1. Replace the values _and comma_ after "coefficients" (shown below)

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

9. You're done! Make sure to use this temperature calibration whenever you use this min-eVOLVER by keeping `temp_cal.json` in the folder for the experiment you are running.

## Pump Calibration

1. Make a copy of `pump_calibration.xlsx` and label with the date.
   1. This can be found in `/dpu/calibration/`
2. Fill a beaker with \~200mL of water and submerge all pump input and outputs in the water
3. Fill the pump lines by sending the following pump command to the min-eVOLVER using [`send_command.py`](send\_command.py.md):
   1. `python3 send_command.py <port_number> pump 30,30,30,30,300,300`
4. Wait for the pump lines to fill
5. Calibrate the fast (grey) pumps
   1. Leave the inputs in water and put the outputs in eVOLVER vials
   2. Send the command:
      1. `python3 send_command.py <port_number> pump 20,20,20,20,0,0`
   3. Measure the resulting water output (either using a 20mL autopipette or using a small graduated cylinder)
   4. Input the values into the excel spreadsheet
6. Calibrate the slow (pink) pumps
   1. Leave the inputs in water and put the outputs in 1.5mL Eppendorf tubes
      1. It may be helpful to remove the plastic Luer lock on the tube end
      2. Make sure that the tubing is still full (send another command if not)
   2. Send the command:
      1. `python3 send_command.py <port_number> pump 0,0,0,0,50,50`
   3. Measure the resulting water output (using a 1mL pipette)
   4. Input the values into the excel spreadsheet (in mL)
7. Copy and paste the values under "Copy + Paste" in `pump_cal.json`
   1. Replace the values __ after "coefficients" (shown below)

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

## OD Calibration

### About

OD calibration allows for the min-eVOLVER to accurately read ODs of the cells growing inside. While not completely essential with running chemostats (pump timings are all that matter), good OD calibrations are necessary for turbidostats to give accurate results.

### Procedure

1. Set the min-eVOLVER to the temperature your experiment will be at
   1. Open your temperature calibration file
   2. Change the temperature in the "Set to ( C )" field
   3. Copy and paste the command next to "Temperature command:" field. (Change to target your min-eVOLVER's port)&#x20;
2. Make a copy of `od_calibration.xlsx` and label with the date _and temperature_
   1. This can be found in `/dpu/calibration/`
3. Make a dilution series of your cells into 6 eVOLVER vials
   1. The suggested number of vials is 6, but you can do more should you need a wider range or prefer more accuracy
   2. Each dilution should be at least 15mL to make sure liquid level is above the OD sensor
   3. Do a range of values between just media and pure cells
   4. An example range is included in `od_calibration.xlsx` but these values are not fixed
4. Measure OD600 values on a plate or cuvette reader
   1. If using a plate reader, measure using 300uL
   2. Record these values as the standard values in the spreadsheet&#x20;
5. Heat dilutions to temperature
   1. In an incubator or simply waiting for them to come to temperature in the min-eVOLVER before reading
   2. If worried about cell growth changing OD readings, do a last minute OD reading
6. Cap the vials
   1. This prevents ambient light from changing readings
7. Make sure the od\_led is set to 4095
   1. Either check the server cycling or send the command:
      1. `python3 send_command.py <port_number> od_led 4095`
8. Record 3 server values for each dilution
   1. Cycle through the dilutions in an orderly fashion
   2. For example:
      1. Label the vials 1 - 6
      2. Start with vial 1 in smart sleeve 1 and vial 2 in smart sleeve 2
      3. Then rotate so that vial 6 is in sleeve 1 and vial 1 is in sleeve 2
      4. Repeat for all vials

{% hint style="info" %}
After changing which dilution is being read, wait for the server to cycle a couple of times before recording values. Values are averaged and the values from the old dilution could still be in the mix.
{% endhint %}

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption><p>Highlighted are the OD sensor values for the first and second vials respectively on a min-eVOLVER.</p></figcaption></figure>

9. Copy and paste the values under "Copy + Paste" in `od_cal.json`
   1. Replace the values __ after "coefficients" (shown below)
