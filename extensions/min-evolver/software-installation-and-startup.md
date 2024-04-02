# Software Installation and Startup

## Questions?

Ask questions about this guide on the forum [here](https://www.evolver.bio/t/software-installation-and-startup-questions/493).

{% hint style="info" %}
As with the main eVOLVER, you should have a dedicated computer to run min-eVOLVER. We recommend Macs for their stability and ease software of installation.&#x20;
{% endhint %}

## Software Installation

1. Download files from GitHub repositories for the [dpu](https://github.com/FYNCH-BIO/dpu/tree/min) (experiment code) and [server](https://github.com/FYNCH-BIO/evolver/tree/min) (communicator with min-eVOLVER).

<figure><img src="../../.gitbook/assets/image (15) (3).png" alt=""><figcaption><p>Make sure you are on the 'min' branch (upper left) and click the code button to download the .zip file for the code</p></figcaption></figure>

2. Follow the dpu installation [guide](../../getting-started/software-installation/dpu-installation.md).
   1. We will use the virtual environment made here to run the experiment
   2. Note: as of now, there is no GUI integration. Command line only.
3. Create a server virtual environment
   1. In the command line still, open a new tab or window&#x20;
   2.  If necessary, deactivate the dpu virtual environment with the command below.

       1. `deactivate`

       ![](<../../.gitbook/assets/image (49).png>)
   3. Navigate to the server directory `evolver-min`
   4.  Make a server virtual environment

       1. To avoid confusion with the dpu environment, call your server virtual environment `server-env`

       Mac:

       `python3.9 -m venv server-env`

       `source server-env/bin/activate`

       Windows PowerShell:

       `py -3.9 -m venv server-env`

       `server-env\Scripts\Activate.ps1`
   5.  Use  poetry to install all necessary dependencies.

       ```
       poetry install
       ```

{% hint style="info" %}
If you are setting up more than one min-eVOLVER, simply make an additional folder and label it something like `evolver-min2`. No need to make an additional virtual environment. Any time you need to start a server just use the one you made in the first server folder.&#x20;
{% endhint %}

## Server Startup

{% hint style="info" %}
Optional: for more information about the eVOLVER server you can check [here](../../software/server-raspberry-pi/).
{% endhint %}

{% hint style="info" %}
If using more than one min-eVOLVER, check the [note ](software-installation-and-startup.md#multiple-min-evolvers)at the bottom of this page
{% endhint %}

1. Plug the min-eVOLVER in to your computer using micro-USB and THEN plug it in to the 12V DC power supply.

{% hint style="info" %}
Plugging in the 12V first may make the server not able to connect properly.
{% endhint %}

{% hint style="warning" %}
Whenever possible, avoid plugging / unplugging the min-eVOLVER micro-USB, which is fragile. Instead, leave the micro-USB plugged in and plug / unplug the regular USB to your computer.
{% endhint %}

2. Make sure that you are in the server virtual environment
3. This means navigating to the server folder in a command line window and inputting commands:
   1.  Mac OS:

       `source server-env/bin/activate`
   2.  On Windows PowerShell:

       `server-env\Scripts\Activate.ps1`
4. Navigate to the `/evolver/` folder inside the `evolver-min` server code
5. Attempt to run the server using the following command:
   1. Mac OS: `python3 evolver.py`
   2. Windows Powershell: `py evolver.py`

{% hint style="info" %}
Hereafter, only the Mac OS command will be given. Windows users, swap `python3` with `py`.
{% endhint %}

6. This will tell you the list of min-eVOLVERs plugged in to the computer
7. Exit from the server log using `control + C`
8. Copy the full port address into the `serial_port` variable in the `conf.yml` file for the server
   1. On Mac OS for example: `serial_port: /dev/cu.usbmodem1301`

{% hint style="warning" %}
Be careful to not alter the `conf.yml` file structure, only the variables (after the ":"). Changing the file structure in the wrong way will result in the server failing to run.
{% endhint %}

9. Start the server using `python3 evolver.py`
10. Observe the server for expected behavior
    1. The server cycles once every 20 seconds
    2. If the server is not connected to the min-eVOLVER, commands will fail

<figure><img src="../../.gitbook/assets/image (6) (1) (1) (1).png" alt=""><figcaption><p>An example min-eVOLVER server readout.</p></figcaption></figure>

{% hint style="info" %}
If you want to know more about the server code or how commands work click [here](../../software/server-raspberry-pi/).
{% endhint %}

## Multiple min-eVOLVERs

You can connect multiple min-eVOLVERs to one computer, as long as you have enough USB ports!

1. Make a duplicate min-eVOLVER server code file with a new number ie `evolver-min2`
2. Plug in the new min-eVOLVER and follow the Server Startup guide
   1. The new min-eVOLVER will have a different `serial_port` because it is plugged in to a different USB port
   2. You need to define a different port number (try 5556) in the `conf.yml` file
3. Make sure you're in the right server code folder when starting the new server
4. Use a different command line window for each min-eVOLVER server

{% hint style="warning" %}
Make sure you don't swap your min-eVOLVERs USB ports without meaning to!

* Calibration files are for a specific min-eVOLVER
* `serial_port` numbers on your computer are linked to a specific _USB port_, NOT to a specific min-eVOLVER
* So for example:
  * min-eVOLVER 1 with `serial_port: /dev/cu.usbmodem1201`&#x20;
  * min-eVOLVER 2 with `serial_port: /dev/cu.usbmodem1301`
  * Plugging min-eVOLVER 2 into `/dev/cu.usbmodem1201` will mean that running the min-eVOLVER 1 server will load calibrations for the wrong min-eVOLVER and vice versa
{% endhint %}

## Test min-eV Hardware

### Startup

1. Plug in the micro-USB and then the 12V power supply
2. Start the server
3. In another terminal window, enter the `dpu` virtual environment
4. Navigate to the `/dpu/experiment/` folder

### Familiarize yourself with [send\_command.py](send\_command.py.md) and make sure you can:

1. Send a pump command to all pumps to make sure they actuate
2. Send a command to start and stop stirring
3. Turn temperature off
4. Check the server log as commands go in, these should be received and become the new values in the server cycle

### test\_hardware.py

1. Run a full hardware test using test\_hardware.py
2. Use the command: `python3 test_hardware.py`

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption><p>An example data output from the min-eVOLVER, soon after it has been turned on. This same data can be found continuously in the server window.</p></figcaption></figure>

3. Check that all pumps actuate individually
4. Check that stirring turns off and on
5. Check that OD sensing works as expected (values decrease with OD LED on)
   1. Look at the "`Data from min-eVOLVER`" for the below values
   2. Example values with OD LED OFF: `'od_90': ['65208', '65190']`
   3. Example values with OD LED ON: `'od_90': ['62515', '59678']`
6. Check to see that the temperature values decreased towards `[25000,25000]` over time as the script is running
   1. Example start values: `'temp': ['35514', '35440']`
   2. Example end values: `'temp': ['30618', '31029']`
