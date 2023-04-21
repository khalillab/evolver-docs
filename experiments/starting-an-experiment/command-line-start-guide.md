# Command Line Start Guide

{% hint style="info" %}
If you are new to command line / bash, you can start [here](../../guides/command-line-usage.md)!
{% endhint %}

## Overview

Reasons you might use command line experiment start:

1. Doing a custom experiment
2. Unable to install GUI or getting errors you aren't able to fix easily (post on the forum first)

## Protocol

{% hint style="warning" %}
Set your computer to never fall asleep to prevent experiments from being halted.
{% endhint %}

1. In a command line window, enter the dpu virtual environment.
   1. Navigate to the DPU directory
      * Use this command: `cd <path_to_dpu>`
   2. Enter the command:
      * On Mac OS:
        * `source dpu-env/bin/activate`
      * On Windows PowerShell:
        * `dpu-env\Scripts\Activate.ps1`
2. Navigate to your experiment folder
   1. This should be in `dpu/experiment`
3. Copy the template folder and rename it for each experiment
   1. Navigate into your new experiment folder
4. Alter settings in `custom_script.py`
   1. `EVOLVER_PORT` = set correct IP of the eVOLVER
   2. Set initial temp and stir settings
   3. `custom_script.py` has basic settings for running chemostat and turbidostat experiments, but you can also customize. To learn more click [here](../../software/dpu-code-structure/custom\_script.py.md).
5. Start the experiment using the command:
   1. `python3 eVOLVER.py -i <your_evolver's_IP_address>`
   2. `python3 eVOLVER.py -i 192.168.1.9`
6. [Calibrate to blank](../../software/dpu-code-structure/od-blank.md)
   1. Temperature should be fully equilibrated before this
   2. DO NOT add cells before blanking, whatever OD value the cells + media have will be subtracted from future measurements
7. Stop the experiment using the keyboard shortcut `control+C`
   1. One `control+C` pauses the experiment from recording data
   2. Two `control+C` stops the experiment
8. To change parameters mid-experiment or restart from blank data files:
   1. Stop the experiment fully
   2. Change parameters in `custom_script.py`
   3. Restart the experiment
      1. Continue to keep your data
         1. Overwrite to make new blank data files and throw away your old experiment. NOTE: you will lose your OD blank and will need to make a new one (a hassle if you have already inoculated with cells)
9. You can run experiments on more than one eVOLVER at a time
   1. Create a new experiment folder (different `custom_script.py`) and change IP
   2. Follow this procedure in an additional command line window

## Ending an Experiment

1. [Clean up](cleaning-up-after-experiment.md) the experiment
2. Data is in the [data files](../../software/dpu-code-structure/experiment-data-files.md)
