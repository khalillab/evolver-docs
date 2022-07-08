---
description: Description of how the DPU (Data Processing Unit) code functions.
---

# DPU Code Structure

This page aims to explain how the server on the Data Processing Unit (DPU) functions. The repository can be found on [Github](https://github.com/FYNCH-BIO/dpu).

## General Information

The DPU is where actual experiment logic and data collection occurs. DPU code is typically ran on a lab computer or laptop connected to the the same router as the eVOLVER. Setpoints for experimental parameters, deciding when to actuate fluidics, and deciding how to vary experimental parameters as a function of time or based on feedback from experimental data is programmed in the DPU.

### File Structure

Within the DPU are 3 main components, the experimental code for running experiments, the calibration code for making fits relating sensor measurements to what they physically are measuring, and the graphing code for the deprecated experiment viewing web app.

### Experiment

There are two main files in the experiment DPU code, `eVOLVER.py`, which is the file that is run to execute an experiment, and `custom_script.py` which is where experimental logic goes.

#### eVOLVER.py

This file handles all of the initialization (creating data directories and initializing files), communications with the server, and lower level details of sending commands and receiving data. Additionally, it handles data transformations based on the calibrations whenever data is received. It then makes a call to `custom_script.py` to carry out the user-desired experiment routine based on the received data.

The DPU uses websockets via [socketio](https://python-socketio.readthedocs.io/en/latest/index.html) to communicate with the eVOLVER server. It functions as a client, connecting to the server when the experiment is running, receiving data periodically, and sending commands to the server based on the experimental design. The `EvolverNamespace` class (which is the socketio client class) has functions which are called when the corresponding event occurs over the websockets connection. For example, the function `on_broadcast` is called when a `broadcast` event occurs from the server.

#### custom\_script.py

This file is where the experimental culture routine is located. At the top of the file is commented code directing the user to modify constant variables to configure the experiment (experiment name, eVOLVER to run on, etc.) Then there are two default experiment functions for running either a turbidostat or a chemostat. It is also possible to write your own custom function to run by changing the `OPERATION_MODE` variable to your custom function name.

### Calibration

The `calibrate.py` script is used to fit sensor data from eVOLVER (generated via the GUI) to experimental values. The script uses websockets to fetch the sensor and experimental data from the server for a previously run calibration, the does the fit according to the users specifications. Arbitrary experimental parameters can be fit to. The script can do constant, linear, sigmoid, and 3D fits.

The GUI will automatically run this script upon completion of a calibration, but it is also possible to run manually via the command line to fetch .png files for the calibrations if desired.

### Graphing

This is the deprecated [Django](https://www.djangoproject.com/) based web-app for viewing experiment data in real-time. To run it, open a terminal and `cd` to `/graphing/src/`. Then execute the following:

`python3 manage.py runserver 0.0.0.0:8080`

You should then be able to open a web browser and navigate to `localhost:8080` to see the application. The app should also be accessible via the internet if the computer is connected to the internet by navigating to `<ip_of_computer>:8080`.

The GUI now allows viewing of the data in real-time - you should not need to use this unless.





