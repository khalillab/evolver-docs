# min-eVOLVER

## Software Setup

1. Download files from GitHub (no link yet)
2. Follow the dpu installation [guide](../getting-started/software-installation/dpu-installation.md).
   1. We will use the virtual environment made here to run the experiment
   2. Note: as of 2/14/23, no GUI integration. Command line only.
   3. Use the min-eVOLVER DPU branch
3. Create a server virtual environment
   1. Following the virtual environment portion of the dpu guide
   2. In the terminal still, deactivate the dpu virtual environment with the command below.
      1. `deactivate`
   3. Navigate to the server directory you just downloaded and unzipped: `cd <path_to_server>`
   4. Follow the guide from step 7
   5. Replace instances of `dpu` with `server`

## Server Startup

Check that the server runs properly

1. Make sure that you are in the server virtual environment
   1. This means navigating to the correct folder in a terminal of your choice and inputting commands:
      1.  Mac OS:

          `source server-env/bin/activate`
      2.  On Windows PowerShell:

          `server-env\Scripts\Activate.ps1`
2. Navigate to the `/evolver/` folder inside the server code
3. Open up the Arduino software and find the port number
   1. Under Tools>Port, look at the ports
   2. Plug the SAMD21 into the computer
   3. The new one is the SAMD21
   4. Copy the full port address into the `serial_port` variable in the `conf.yml` file for the server
      1. On Mac OS for example: `serial_port: /dev/cu.usbmodem1301`
   5. Do not have the Serial Monitor open in the Arduino software
4. Start the server using `python3 evolver_server.py`
   1. Observe the server for expected behavior

## Hardware Setup



## Starting an Experiment

{% hint style="info" %}

{% endhint %}

1. Start the server (using the Server Startup guide above)&#x20;
2. Open a new command line window
3. When starting an experiment you will need to be in the dpu virtual environment.
   1. In terminal, navigate to the folder you installed this into and enter the command:
      * On Mac OS:
        * `source dpu-env/bin/activate`
      * On Windows PowerShell:
        * `dpu-env\Scripts\Activate.ps1`
4. In command line, navigate to your experiment folder
   1. This should be in `dpu/experiment`
      1. Consider making a new folder here for each experiment
   2. Alter settings in `custom_script.py`
      1. `EVOLVER_PORT` set correct port of the min-eV.
      2. Set initial temp and stir settings
      3. `custom_script.py` has basic settings for running chemostat and turbidostat experiments, but you can also customize. To learn more click [here](../software/dpu-code-structure/custom\_script.py.md).
   3. Start the experiment using the command:
      1. `python3 eVOLVER.py -i localhost:<your_eV_port>`
      2. `python3 eVOLVER.py -i localhost:5555`
