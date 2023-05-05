---
description: Process and considerations for running a growth curve.
---

# Growth Curve

## Why is running the growth curve algorithm a good first experiment?

When setting up eVOLVER for the first time, we recommend performing a simple growth curve as a starting experiment. The growth curve algorithm functions similar to the turbidostat algorithm, except the feedback between any experimental parameters are turned OFF (or [deleted in the code](https://github.com/FYNCH-BIO/dpu/blob/master/experiment/template/custom\_script.py#L37)). That way, you won't have to worry about any leaks or overflow issues from pumps misbehaving while testing the system.

## What parts of the setup does the algorithm test?

The growth curve algorithm tests the following before running a more intensive experiment:

* Continuous communication from the eVOLVER to the DPU (lab computer)
* Power settings appropriately set on the lab computer (e.g. sleep settings)
* OD calibration during an actively growing culture&#x20;
* Stirring stability
* Detection of any noisy from ambient light
* Temperature stability

What the growth curve experiment does NOT test:

* Pump actuation and calibrations
* Media line setup and sterility

## Code Setup and Introduction

There are just [two scripts](https://github.com/FYNCH-BIO/dpu/tree/master/experiment/template) that you need to run eVOLVER (`eVOLVER.py` and `custom_script.py`).  &#x20;

1. `eVOLVER.py` generally contains most of the infrastructural code to communicate with eVOLVER and interpret raw data coming from the system. Basic users should not need to modify this file.
2. `custom_script.py` includes several basic functions (growth curve, chemostat, and turbidostat) but is where the user should customize/ write their own scripts.&#x20;

For those of you familiar with Python, I highly encourage reading through the scripts (>1000 lines of code) after this tutorial. Let's quickly walk through [custom\_script.py](https://github.com/FYNCH-BIO/dpu/blob/master/experiment/template/custom\_script.py) before we talk about any of the experimental setup.&#x20;

#### Importing libraries&#x20;

For those familiar with coding and Python, the first few lines in the script is for importing libraries and logging files.

```python
#!/usr/bin/env python3

import numpy as np
import logging
import os.path
import time

# logger setup
logger = logging.getLogger(__name__)

```

#### Initial settings&#x20;

The next part of the code goes through inital settings one would want the eVOLVER to start at. These are sent at the start of the experiment when the script is initiated. Please refer to our API for examples on how to modulate the settings mid experiment.&#x20;

There are initial three parameters in this eVOLVER script that defined: temperature, stir, and what mode this script will run.&#x20;

```python
##### USER DEFINED GENERAL SETTINGS #####

# If using the GUI for data visualization, do not change EXP_NAME!
# only change if you wish to have multiple data folders within a single
# directory for a set of scripts
EXP_NAME = 'data'

# Port for the eVOLVER connection. You should not need to change this unless you have multiple applications on a single RPi.
EVOLVER_PORT = 8081

##### Identify pump calibration files, define initial values for temperature, stirring, volume, power settings

TEMP_INITIAL = [30] * 16 #degrees C, makes 16-value list
#Alternatively enter 16-value list to set different values
#TEMP_INITIAL = [30,30,30,30,32,32,32,32,34,34,34,34,36,36,36,36]

STIR_INITIAL = [8] * 16 #try 8,10,12 etc; makes 16-value list
#Alternatively enter 16-value list to set different values
#STIR_INITIAL = [7,7,7,7,8,8,8,8,9,9,9,9,10,10,10,10]

VOLUME =  25 #mL, determined by vial cap straw length
OPERATION_MODE = 'growth_curve' #use to choose between 'turbidostat' and 'chemostat' functions
# if using a different mode, name your function as the OPERATION_MODE variable

##### END OF USER DEFINED GENERAL SETTINGS #####
```

Each position in the array corresponds to the vial it is updating (e.g. first position is typically called via an index of 0 in Python and thus is updating vial 0). For example, if one would want to set the temperature for Vials 0 - 3 to 37C but the rest to 30C, the array would look like the following:

```python
TEMP_INITIAL = [37,37,37,37,30,30,30,30,30,30,30,30,30,30,30,30]
```

If one wanted to run a turbidostat script instead of the growth curve script, one would replace the OPERATION\_MODE variable:

```python
OPERATION_MODE = 'turbidostat'
```

If you wrote a custom modality named "new\_super\_cool\_script", you would define it as a function and call it in a similar way. For example:

<pre class="language-python"><code class="lang-python"><strong>def new_super_cool_script():
</strong>    print('hello world')
</code></pre>

You would define it as the following:

```python
OPERATION_MODE = 'new_super_cool_script'
```

#### Making sure eVOLVER.py is run as main script

Let's skip the turbidostat and chemostat scripts for now (for another lesson) and jump straight till the end of the script. The following is just to indicate that the user should not be running this script from the command line

```python
if __name__ == '__main__':
    print('Please run eVOLVER.py instead')
    logger.info('Please run eVOLVER.py instead')
    
```

That's all the code you need to run the growth curve!

## eVOLVER Setup

For this experiment, we will need:

* Autoclaved vials (with stir bar and caps)
* Sterile growth media

#### Protocol:

1. Fill autoclaved vials with 30 mL of sterile media and place in eVOLVER Smart Sleeves.
2. Set the desired temperature for the eVOLVER (using the GUI) to preheat the vials
3. Wait for \~30 minutes
4. Start experiment using the [command-line-start-guide.md](starting-an-experiment/command-line-start-guide.md "mention") or [gui-start-guide.md](starting-an-experiment/gui-start-guide.md "mention")
5. Spike in cells (1 mL of saturated culture) and watch the OD spike on the traces.
6. Let the cells grow until saturated.

## FAQ

* OD traces are noisy in bursts of \~10 - 12 hours:
  * This is most likely noise from light during the working hours of the day. Try placing a box over the system to block out ambient light. If works better, than try making a shield for the eVOLVER
* OD readings are really noisy/ don't make much sense:
  * Verify that the stir vortex is not interferring with the OD sensors. This might happen if low volume is used (\~20 mL) or stir settings are too high. A good way to debug this is to turn off stirring manually (via 12 V switch) and see if the measurement is better. NOTE: Toggling 12V switch will turn off STIR and TEMP.
  * Switch out the LED and or photodiode&#x20;
* All measurements stop after a few hours:
  * Check computer power saving settings. Make sure the system does not go to sleep.

