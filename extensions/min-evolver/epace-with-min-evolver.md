# ePACE with min-eVOLVER

Overview

This page only details differences from the general min-eVOLVER experimental [protocol](starting-an-experiment.md). You are also expected to have an understanding of PACE and how it is normally run before doing ePACE.

{% hint style="info" %}
* ePACE described initially in[ Huang, Heins et al. 2022 _Nature Biotech_](https://www.nature.com/articles/s41587-022-01410-2#Sec15)_._
* For general PACE methods see [Miller, Wang 2020 _Nature Protocols_](https://www.nature.com/articles/s41596-020-00410-3)_._
{% endhint %}

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption><p>Two min-eVOLVERs set up for ePACE. They are connected to a dedicated laptop (preliminary picture)</p></figcaption></figure>

### Experimental Overview

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

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption><p>Vials set up for reservoir (left) and lagoon (right).</p></figcaption></figure>

## Fluidic Lines

Hook up pump lines in the configuration shown below

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

## custom\_script.py

Copy the ePACE template under `/dpu/experiment/epace-template/`

### "USER DEFINED GENERAL SETTINGS"

1. Most likely you should not need to alter any settings, other than `EVOLVER_PORT`
2. Use the [`"hybrid"` function](epace-with-min-evolver.md#experimental-overview)
3. Collapse or ignore `growth_curve`, `turbidostat`, and `chemostat` functions

### Alter settings in the `hybrid` function=

`vial 0` is the host cell reservoir

* It is a turbidostat _and_ a chemostat. Read why [here](epace-with-min-evolver.md#experimental-overview).
* We are setting OD for `vial 0`

#### `start_time`&#x20;

chemostats will not pump until this amount of hours has elapsed

#### `rate_config`

1. In vial volumes per hour
2. Reservoir - set to equal the volume you are taking out
3. Lagoon - set to based off of phage replication rate
4. For example:
   1. Setting to `rate_config = [1, 1]`
      1. 30mL into reservoir and 10mL into lagoon per hour
   2. Setting to `rate_config = [0.5, 0.5]`
      1. 15mL into reservoir and 5mL into lagoon per hour

#### Inducer

1. Set `inducer_concentration` to X the final concentration in the lagoon
2. Turn inducer off to start (`inducer_on = False`)
3. Wait for host cells to grow up before starting induction (`inducer_on = True`) and inoculating with phage
4. As of 04/21/23 inducer is only implemented for pump 5

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption><p>Picture of default min-eVOLVER settings as of 04/14/23.</p></figcaption></figure>
