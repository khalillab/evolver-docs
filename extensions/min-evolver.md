# min-eVOLVER

## Software Setup

1. Download files from GitHub
2. Follow the dpu installation [guide](../getting-started/software-installation/dpu-installation.md).
   1. We will use the virtual environment made here to run the experiment
3. Follow the dpu installation [guide](../getting-started/software-installation/dpu-installation.md), but alter it for the server
   1. In the terminal still, deactivate the dpu virtual environment with the command below.
      1. `deactivate`
   2. Navigate to the server directory you just downloaded and unzipped: `cd <path_to_server>`
   3. Follow the guide from step 7
   4. Replace instances of `dpu` with `server`

## Hardware Setup



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

## Starting an Experiment

{% hint style="info" %}

{% endhint %}

1.  When starting an experiment you will need to be in the dpu virtual environment.

    In terminal, navigate to the folder you installed this into and enter the command:

    * On Mac OS:
      * `source dpu-env/bin/activate`
    * On Windows PowerShell:
      * `dpu-env\Scripts\Activate.ps1`
