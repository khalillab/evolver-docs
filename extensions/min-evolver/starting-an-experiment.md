# Starting an Experiment

{% hint style="warning" %}
You should have completed both [setup](setup.md) and [calibrations](calibrations.md) before proceeding to an experiment.
{% endhint %}

## Hardware

![](<../../.gitbook/assets/image (41).png>)

{% hint style="danger" %}
Do not plug the pumps in to the vial ports. If the pumps are actuated, this can break the min-eVOLVER board.&#x20;
{% endhint %}

1. [Prepare vials](../../experiments/starting-an-experiment/preparing-vials.md)
2. [Sterilize the fluidic lines](../../experiments/starting-an-experiment/sterilizing-lines.md)
   1. Instead of the GUI, use send\_command.py
   2. The slow pumps (pink) will need to be run for >200 seconds to fully flush the lines
3. [Load the vials](../../experiments/starting-an-experiment/loading-vials-and-setting-initial-conditions.md)
4. Do not start&#x20;

## Software

1. [Start the server](setup.md#server-startup)&#x20;
2. In another window, enter the dpu virtual environment.
   1. In terminal, navigate to the folder you [installed](../../getting-started/software-installation/dpu-installation.md) this into (likely your dpu folder)
   2. Enter the command:
      * On Mac OS:
        * `source dpu-env/bin/activate`
      * On Windows PowerShell:
        * `dpu-env\Scripts\Activate.ps1`
3. In command line, navigate to your experiment folder
   1. This should be in `dpu/experiment`
   2. Consider making a new folder here for each experiment&#x20;
4. Alter settings in `custom_script.py`
   1. `EVOLVER_PORT` = set correct port of the min-eV.
   2. Set initial temp and stir settings
   3. `custom_script.py` has basic settings for running chemostat and turbidostat experiments, but you can also customize. To learn more click [here](../../software/dpu-code-structure/custom\_script.py.md).
5. Start the experiment using the command:
   1. `python3 eVOLVER.py -i localhost:<your_eV_port>`
   2. `python3 eVOLVER.py -i localhost:5555`

## Ending an Experiment

1. [Cleanup](../../experiments/starting-an-experiment/cleaning-up-after-experiment.md) the experiment
2. Data is in the [data files](../../software/dpu-code-structure/experiment-data-files.md)
