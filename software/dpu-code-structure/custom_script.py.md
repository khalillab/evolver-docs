---
description: Detailed description of the custom_script.py file.
---

# custom\_script.py

This file contains all experimental design parameters and logic. It is commented to help guide users in customizing their experiment with minimal actual programming required beyond setting some variable values.

### General Information

The logic of running a continuous culture experiment should be structured such that any actions are based on the `elapsed_time` of the experiment and on the latest received data. The functions are not called continuously in a loop - they are only called when new data is received from the server, which is set by the `broadcast_timing` on the RPi (default is every 20s).

For example, if a sinusoidal temperature profile is desired, the `custom_function` should check the `elapsed_time` , use that time to calculate the appropriate temp, then send that command via the `update_temperature` function in the `eVOLVER` object that is passed to the function.

It is possible to change this file mid experiment! Simply stop the eVOLVER script (press ctrl + c twice on the terminal running the experiment or stop the experiment in the GUI) and restart it. The experiment will continue where it left off with any changes you made to the script now being implemented.

#### Sending commands

It is best practice to calculate the values desired for all vials before sending the command so they can all be updated at once as opposed to one at a time. This minimizes the number of messages sent to the server and how many commands the server has to send via serial to the Arduiono microcontrollers. Serial communications are shared between all the parameters and are relatively slow, so best to be efficient with the commands!

#### User Defined General Settings

At the top of the file are a block of variables, which includes the name of the experiment, and the port (not necessary for most users to modify unless you have a more complicated setup or IT needs). eVOLVER IP is specified on the command line (or experimental params if running through the GUI).

{% hint style="info" %}
Be sure to set the `VOLUME` variable! It is needed to accurately calculate the appropriate amount of time to run the pumps to hit a desired OD wiht a dilution in the t-stat and to hit a desired rate (volumes / hour) in the c-stat.
{% endhint %}

#### Initial Values

The next block of variables are where the user should set any initial values such as `STIR`, `TEMP`, and any other parameters. This is also where the `OPERATION_MODE` is set. This value should match the name of another function within the file, which will be called every `broadcast` event from the server, i.e. it should notate the name of the users desired experimental routine.

#### turbidostat

One of the default `custom_functions` provided, this function executes logic to perform a turbidostat on the eVOLVER.

`time_out` refers to the amount of time to run the efflux pump extra - this prevents overflows by ensuring the efflux pump runs at least a few seconds longer than the influx. If you have a large turbidostat window (i.e. big dilutions > 10ml) you could consider increasing this value for extra safety.

`pump_wait` is the minimum amount of time to wait between pump events. This is to allow enough time for averaging of the OD to occur to determine if the OD dropped below the necessary threshold for the t-stat window, preventing over-dilutions.

`MESSAGE` holds the fluidic message that will be sent to the server. The default length should be 48, only change this if you also change the value in `conf.yml` on the server. By default, positions 0 - 15 correspond to the influx pump array, 16 - 31 to the efflux pump array, and 32-47 are for a third array if you have one installed or for any other connected fluidic devices (like solenoids for millifluidics).

`ODSet` is the variable keeping track of what OD the algorithm should currently be targeting. Once the OD reaches the upper range, ODSet will be set to the lower range, which will trigger subsequent logic to dilute the vial to hit that lower target. Upon the OD reaching this target, it will set the OD to the upper limit again. See this [forum post](https://www.evolver.bio/t/regarding-odset-in-turbidostat/242) for more information.

#### chemostat

One of the default `custom_functions` provided, this function executes logic to perform a chemostat on the eVOLVER.

`rate_config` refers to the flow rate for each vial, in volumes per hour. It should be a list of length equal to the number of vials (default 16).

`start_OD` refers to the minimum OD required before starting the chemostat algorithm. Set to 0 to start at any positive OD.

`start_time` refers to the minimum amount of time that needs to pass before starting the chemostat. Set to 0 to start immediately.

`bolus`  refers to the amount of liquid that will pump every pump event in mL. For example, a bolus of 0.5 means that eVOLVER will  dilute 0.5 mL every pump event, evenly dispersed throughout the hour at a period that hits the desired V/h set by the `rate_config` variable.

eVOLVER does not send a command every time one of the pumps needs to actuate for the c-stat! Instead, we send a single command that contains the periodicity and amount of time to run for each vial. This information is handled by the microcontroller. This minimzes the communications between the DPU, server, and microcontrollers and ensures accurate pump timings for each vial.

#### Make your own!

If you want to make your own custom function, write it in this file and set the `OPERATION_MODE` variable at the top of the file to match your function name. Your function will be called every `broadcast` by the `EvolverNamespace` class in `eVOLVER.py`.

