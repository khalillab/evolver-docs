# ePACE with min-eVOLVER

## Overview

This page only details differences from the general min-eVOLVER experimental [protocol](../starting-an-experiment.md). You are also expected to have an understanding of PACE and how it is normally run before doing ePACE.

{% hint style="info" %}
* ePACE described initially in[ Huang, Heins et al. 2022 _Nature Biotech_](https://www.nature.com/articles/s41587-022-01410-2#Sec15)_._
* For general PACE methods see [Miller, Wang 2020 _Nature Protocols_](https://www.nature.com/articles/s41596-020-00410-3)_._
{% endhint %}

## Experimental Overview

#### Problem: PACE host cells overgrow

* In previous PACE experiments, host cells would increase growth rate as the experiment wore on
* This caused problems with phage replication in the lagoon and the selection plasmid breaking
* Solution: controlling host cell density in cell reservoirs

#### Implementing Controlled Host Cell Density in Reservoirs

* We control cell density in eVOLVER by running a turbidostat, which checks cell density and dilutes the culture if it is over a threshold.
* In PACE we remove volume from the cell reservoir and transfer it to the lagoon
  * This changes our turbidostat's volume
  * The amount we dilute will therefore be incorrect (adding 5mL of media to 30mL decreases OD less than adding 5mL of media to 20mL)
  * We rely on host cells to get to a threshold cell density before we dilute
  * They may not reach this threshold before we remove more volume
  * This causes a feedback loop of little volume being added and more being taken out
  * Therefore our turbidostat will get lower and lower volume and eventually break
* Solution: put in the amount of volume we take out of the cell reservoir

#### Chemostat and Turbidostat on the Same Vial&#x20;

* We implement a "hybrid" function
* The "hybrid" function uses both a turbidostat and a chemostat on the host cell reservoir
* Turbidostat for keeping the cells from overgrowing
* Chemostat for keeping volume constant

## Vial Setup

{% hint style="info" %}
Levels of liquid in the vials are set by the height of the efflux needle.
{% endhint %}

Needles used were all 16ga

Reservoir volume = 30 mL

* Efflux needle = 3" needle in the tallest vial cap port
* Media in = 2" needle in the shortest port
* Vial to Vial = 3" needle in the _second_ tallest port

Lagoon volume = 10 mL

* Efflux needle = 4" needle in the _second_ tallest vial cap port
* Vial to Vial = 3" needle in the lowest port
* Inducer = 4" needle in the tallest port or 2" needle in the second lowest

{% hint style="info" %}
To have high accuracy when using the low volume pumps it is important to avoid individual drops. Therefore we want needles to abut inside of the vials to get a constant stream of fluid when pumping.
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (7) (1).png" alt=""><figcaption><p>Vials set up for reservoir (left) and lagoon (right).</p></figcaption></figure>

## Fluidic Lines

Hook up pump lines in the configuration shown below

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>

## Alter Settings in custom\_script.py

1. Copy the whole ePACE template folder (`/dpu/experiment/epace-template/`)
2. Rename the copied folder to your experiment name
3. Change the `EVOLVER_PORT` to your eVOLVER's port
4. Alter `USER DEFINED VARIABLES` using the guide below:

<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption><p>ePACE user defined variables as of 2023-11-20</p></figcaption></figure>

### `lower_thresh` and `upper thresh`

* The lower and upper OD threshold of the turbidostat that is running on the reservoir vial
* Format: `[vial 0, vial 1]`

### `start_time`&#x20;

* chemostats will not pump until this amount of hours has elapsed
* Useful to allow cells in reservoir to grow up before starting experiment

### `rate_config`

* Format: `rate_config = [reservoir, lagoon]`
* In vial volumes per hour (V/h)

#### For the Reservoir

* Replaces volume in turbidostat that is removed via vial to vial
* Must be greater than the volume you are taking out
* Turbidostat controls will separately preventing reservoir from increasing in OD too much
* Do not set too high or your cells will be unable to grow fast enough and wash out

#### For the Lagoon

* Set based off of phage replication rate

#### Example Settings:

1. If you have a 30mL reservoir and 10mL lagoon
2. Setting to `rate_config = [1, 1]`
   1. 30mL media into reservoir and 10mL from reservoir into lagoon per hour
3. Setting to `rate_config = [0.4, 1.2]`
   1. If we set lagoon rate to 1.2 V/h, we should not set reservoir rate to lower than 0.4 V/h to avoid draining the reservoir
   2. 1.2 V/h \* 10mL = 12mL/h into lagoon
   3. 0.4 V/h \* 30mL = 12mLh into reservoir

### Inducer

`inducer_on`

* Turn inducer off to start (`inducer_on = False`)
* Wait for host cells to grow up before starting induction (`inducer_on = True`) and inoculating with phage

`inducer_concentration`

* Times greater (X) the concentration of your inducer in its bottle compared to its final concentration in the lagoon
* Format `[pump 5, pump 6]`

#### For example:

1. Your arabinose stock is 1 M
2. The final lagoon concentration you want is 10 mM
3. Therefore 1000 mM / 10 mM = 100 X your final concentration
4. If you are not using another inducer, `inducer_concentration` `= [100, 0]`

## Optional Settings

_You do not need to alter these settings_

### Swapping Lagoon and Reservoir Vials

If you do want to alter these variables, you also need to swap the vial locations in the turbidostat and chemostat settings of:

* `lower_thresh` and `upper thresh`
* `rate_config`

#### `reservoir_vial`&#x20;

* Vial number of host cell reservoir
* It is a turbidostat _and_ a chemostat. Read why [here](./#experimental-overview).

#### `lagoon_vial`&#x20;

* Vial number of lagoon
* Only a chemostat, can have up to two inducers&#x20;
