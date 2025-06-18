# Light Calibration

## Overview

Light is calibrated a single vial at a time using an external light probe and data logger.

Files for calibration can be found in the calibration folder of your photo-eVOLVER DPU

{% hint style="info" %}
Before attempting this protocol you should have completed the full photo-eVOLVER [setup](setup-phototroph-evolver.md) and [smart sleeve](photo-evolver-smart-sleeves/photo-evolver-smart-sleeve-construction-guide.md) construction.
{% endhint %}

## Materials

* Light meter and probe
  1. Our light meter is the LI-COR [LI-1500](https://www.licor.com/products/light/light-logger)
  2. Our light probe is the Walz US-SQS/L omnidirectional light [probe](https://www.walz.com/products/light/us-sqs_l/introduction.html)
* 3D printed calibration cap

## Protocol

1. Make sure you are using the calibration conf.yml not the experiment conf.yml
   * Experiment conf.yml will have pauses that cause missing values in the light calibration.
   * See [here](../../../guides/change-your-conf.yml-file.md) for how to change to the calibration conf.yml
2. Get a clean glass vial and fill to 25mL with water
3. Set up probe in vial using calibration cap
4. Alter `calibration_vals` in `calibrate_light.py`
5. Start logger
   * Turn on via mini-USB power cable plug on top
   * Choose 500hz sampling rate
   * Press "START"
   * New file > Label with vial number > OK > Water probe
   * `Should be changing values now`
6. Run `calibrate_light.py`
   * `python3 calibrate_light.py --ip <evolver_IP> --vial <vial_num> --lights <space_separated_list_of_lights>`
   * `<space_separated_list_of_lights>` refers to which light types you want to calibrate (light1, light2, light3)
   * Sets eVOLVER light for that vial to each value
   * Separates values in the LI-1500 log by turning off the light
7. Press the START/STOP button to stop logging
8. Repeat calibration for each vial, moving the light probe and glass vial
   1. The vial number in the file name should increase automatically
   2. You can overwrite logger files where you mess up
9. Copy the `light_cal_template` folder in `/dpu/calibrations/` and rename with the name of this light calibration
10. Plug logger in to the computer via USB
11. Transfer files over to folder you made
12. Run `analyze_light_cal.ipynb`&#x20;

    1. Change the constants in the Jupyter Notebook
    2. The fit\_name should reflect which light you are calibrating

    <figure><img src="../../../.gitbook/assets/image (77).png" alt=""><figcaption></figcaption></figure>
13. Transfer your final calibration file to your experiment template folder
14. The calibration file should be named `light{}_cal.txt` where {} is replaced with the light number to be recognized by the eVOLVER DPU script
