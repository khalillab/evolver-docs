---
description: List of things to do to setup and run an eVOLVER experiment.
---

# Starting an Experiment

_For a video guide and full written protocol for setting up an eVOLVER experiment, check out the 2019 JoVE_ [_paper_](https://www.jove.com/t/59652/designing-automated-high-throughput-continuous-cell-growth)_. Note that some information, such as using the GUI, is out of date._

## Page under construction

## Checklist

Before starting experiment prep:

1. Finished Getting Started Page
2. Calibrations
   1. Temperature (must be first, affects OD cals)
   2. OD
   3. Pump calibrations
3. Should things not be as expected
   1. [eVOLVER Maintenance](../../troubleshooting/evolver-maintenance.md)
   2. [Vial Troubleshooting](../../troubleshooting/vial-troubleshooting/)

## Sample Experimental Workflow

{% hint style="info" %}
Starting eVOLVER experiments takes hours and it is important to supervise your experiment for the first few hours. Therefore, front-loading as much prep work as possible to the days before the experiment is strongly recommended.
{% endhint %}

{% hint style="warning" %}
Consider running a test experiment with just water or the wild type strain before you devote time to making everything perfect. If you are running an experiment with modified code this is especially essential.&#x20;
{% endhint %}

### Day 0:

Prepare media - especially if using a [20L carboy](carboy-media-prep.md) so it can cool overnight

[Prepare vials](preparing-vials.md)

[Sterilize fluidic lines](sterilizing-lines.md)

Make sure vials / pumps are behaving as expected

* Are all vials stirring, getting up to temperature, all pumps pumping, etc?
* Especially check that efflux is running long enough to remove enough culture from vials

Start overnight cultures

### Day 1:

[Load vials and set initial conditions](loading-vials-and-setting-initial-conditions.md)

Start experiment via [GUI](gui-start-guide.md) or [Command Line](command-line-start-guide.md)

Inoculate cultures into vials

Monitor experiment for correct behavior

* Are the cells growing?
* Is the experiment diluting as expected?
* Are all pumps working?

### Day 2 - Onwards:

Monitor media levels - make sure that there is more than enough media to make it to the next time you check the experiment

Monitor biofilming on the vials - this can cause increased OD over time&#x20;

{% hint style="warning" %}
If something goes wrong, check the [Experiment Troubleshooting](../../troubleshooting/experiment-troubleshooting/) pages
{% endhint %}

Finally, end the experiment and [clean up](cleaning-up-after-experiment.md)

## Relevant Forum Posts

[Considerations for your first eVOLVER experiment](https://www.evolver.bio/t/considerations-for-your-first-evolver-experiment/83)

