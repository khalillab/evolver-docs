---
description: Detailed description of the eVOLVER.py file.
---

# eVOLVER.py

This file is where the `main` function resides for the experimental DPU code, ie it is the script that is run to carry out an experiment on eVOVLER.

To start an experiment on the command line, run the following command:

```
python3 eVOLVER.py
```

If you would like to see the help menu:

```
python3 eVOLVER.py -h
```

Which will bring up something similar to the following:

```
usage: eVOLVER.py [-h] [-y] [-l LOG_NAME] [-i IP_ADDRESS] [-v | -q]

Run an eVOLVER experiment from the command line

optional arguments:
  -h, --help            show this help message and exit
  -y, --always-yes      Answer yes to all questions (i.e. continues from existing experiment, overwrites existing data and blanks OD measurements)
  -l LOG_NAME, --log-name LOG_NAME
                        Log file name directory (default: /Users/heinsz/git_repos/dpu/experiment/template/data/evolver.log)
  -i IP_ADDRESS, --ip-address IP_ADDRESS
                        IP address of eVOLVER to run experiment on.
  -v, --verbose         Increase logging verbosity level to DEBUG (default: INFO)
  -q, --quiet           Disable logging to file entirely
```

{% hint style="info" %}
If an `eVOLVER_parameters.json` file is present, eVOLVER will use this file for all t-stat/c-stat paremeters, including temp and stir. If not, it will default to the variable inside the script that the user can specify manually.
{% endhint %}

## General Information

This file contains the lower level functions that deal with communications and carrying out commands that the user specifies in the `custom_script`. Additionally, this file handles experiment initialization and data collection, setting up data directories, and doing data transformations based on calibrations.

When the script is ran, a connection is first established with the server, then the `initialize_exp` function is run which creates all data directories and requests the active calibrations from the server. Active calibrations are calibrations with the `active` field set to `true`. There should be only 1 active calibration of a given type. Active calibrations are set via the GUI, but they can be set programatically (see the [setactivecal](https://github.com/FYNCH-BIO/evolver/blob/master/evolver/evolver\_server.py#L169) event on the server).

The eVOLVER code then enters a infinite loop which does nothing except reset the socketio conection occasionally to prevent buildup of broadcast messages. Because the `custom_functions` are tied to the `broadcast` even to the server, the main thread does not need to do anything besides wait for server websocket events.

## EvolverNamespace Class

This is a socketio class responsible for handling communications with the server on the RPi. Each function beginning with `on_` is called when the corresponding event occurs on the websocket connection. For example, if the `connect` event occurs, the `on_connect` function will run.&#x20;

This class is also being used as the eVOLVER experiment class. <mark style="color:red;">**TODO:**</mark> Ideally this would be a second class and not be tacked onto the socketio class - it will be updated in a future version.

The start time and OD blank information is stored as a class variable. Additionally, all low level functions for interacting with the eVOLVER RPi are located here.

### broadcast event

Upon receipt of a broadcast event and new data from the eVOLVER RPi, the `on_broadcast` function is called. This will log the experiment time, do data transformations based on calibration data, save the resulting data, and then call the `custom_functions` in `custom_script.py`. This function is set within `custom_script.py`.



