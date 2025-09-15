# Starting an Experiment

{% hint style="warning" %}
You should have completed both [setup](software-installation-and-startup.md) and [calibrations](calibrations/) before proceeding to an experiment.
{% endhint %}

{% hint style="info" %}
**Highly recommended**:

1. Read the main [Experiment](../../experiments/starting-an-experiment/) pages for helpful information not listed here and an example experimental workflow.
2. Run an experiment with water before doing so with cells, especially if you change the code
{% endhint %}

## Questions?

Ask about experiments in the relevant category on the [forum](https://www.evolver.bio/c/min-evolver/min-evolver-experiment/23).

## Setup

1. [Prepare vials](../../experiments/starting-an-experiment/preparing-vials.md)
2. [Start the server](software-installation-and-startup.md#server-startup)&#x20;
3. [Sterilize the fluidic lines](../../experiments/starting-an-experiment/sterilizing-lines.md)
   1. Instead of the GUI, use `send_command.py`
   2. The slow pumps (pink) will need to be run for >200 seconds to fully flush the lines

{% hint style="info" %}
You will have one command line window for each server and each experiment running. It can also be helpful to have a separate window for `send_commands.py`

For example for two min-eVOLVER experiments:

* 2 server windows (server environment)
* 2 experiment windows (`dpu` environment)
* 1`send_commands.py` window (`dpu` environment)
{% endhint %}

<figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption><p>An example fluidics layout for basic chemostat or turbidostat. If necessary, inducer can be programmed to be controlled via the low flow-rate pumps (not shown).</p></figcaption></figure>

4. [Load the vials](../../experiments/starting-an-experiment/loading-vials-and-setting-initial-conditions.md)
   1. Use `send_command.py` to fill the vials to appropriate volumes

{% hint style="warning" %}
Do not inoculate cells until after starting the experiment if you want accurate readings. There is innate variability in the OD of the vials (among other things) and we will blank to your vials during experiment start.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (55).png" alt=""><figcaption><p>Vials set up for a basic chemostat or turbidostat.</p></figcaption></figure>

5. Use `send_command.py` to set to correct temperature
   1. A calibrated temperature command is in your calibration file `temperature_calibration.xlsx`
   2. Temperature affects OD readings and we need a good initial OD to act as a "blank"
6. Allow min-eVOLVER to come to temperature

## Running the Experiment

{% hint style="warning" %}
Make sure that your eVOLVER computer is set to never sleep. If your computer falls asleep while you're running an experiment, you will not be collecting data during that time. See more info [here](troubleshooting.md#server-disconnecting-during-an-experiment).
{% endhint %}

In a separate window from your server command line, follow the command line start [guide](../../experiments/starting-an-experiment/command-line-start-guide.md).

1. If running more than one min-eVOLVER at a time: you need a separate experiment folder and command line window for each min-eVOLVER (and different port number)
2. Start the experiment using the command:
   1. `python3 eVOLVER.py -i localhost:<your_min-eV_port>`
   2. `python3 eVOLVER.py -i localhost:5555`

## Ending an Experiment

1. [Clean up](../../experiments/starting-an-experiment/cleaning-up-after-experiment.md) the experiment
2. Data is in the [data files](../../software/dpu/experiment-data-files.md)
