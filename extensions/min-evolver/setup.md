# Setup

## Software Installation

1. Download files from GitHub (no link yet)
2. Follow the dpu installation [guide](../../getting-started/software-installation/dpu-installation.md).
   1. We will use the virtual environment made here to run the experiment
   2. Note: as of 2/14/23, no GUI integration. Command line only.
   3. Use the min-eVOLVER DPU branch
3. Create a server virtual environment
   1. In the terminal still, deactivate the dpu virtual environment with the command below.
      1. `deactivate`
   2. Navigate to the server directory
      1. The evolver server file is named evolver-min
   3. Follow the dpu installation guide from step 7
   4. Replace instances of `dpu` in commands with `server`

## Server Startup

1. Plug the min-eVOLVER into your computer using micro-USB
2. Make sure that you are in the server virtual environment
   1. This means navigating to the correct folder in a terminal of your choice and inputting commands:
      1.  Mac OS:

          `source server-env/bin/activate`
      2.  On Windows PowerShell:

          `server-env\Scripts\Activate.ps1`
3. Navigate to the `/evolver/` folder inside the evolver-min server code
4. Attempt to run the server
   1. `python3 evolver.py`
   2. Exit from the command using control+C
5. This will tell you the list of min-eVOLVERs plugged in to the computer
6. Copy the full port address into the `serial_port` variable in the `conf.yml` file for the server
   1. On Mac OS for example: `serial_port: /dev/cu.usbmodem1301`
7. Start the server using `python3 evolver.py`
   1. Observe the server for expected behavior

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption><p>An example min-eVOLVER server readout.</p></figcaption></figure>

## Multiple min-eVOLVERs

You can connect multiple min-eVOLVERs to one computer, as long as you have enough USB ports!

1. Make a duplicate min-eVOLVER server code file with a new number ie `evolver-min2`
2. Plug in the new min-eVOLVER and follow the Server Startup guide
   1. The new min-eVOLVER will have a different `serial_port`
   2. You need to define a different port number (try 5556) in both the `conf.yml` file and the `custom_script.py` (see [here](starting-an-experiment.md#software))
3. Make sure you're in the right server code folder when starting the new server
   1. Use a different command line window for each min-eVOLVER server
