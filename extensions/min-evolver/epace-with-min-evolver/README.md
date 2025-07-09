# ePACE with min-eVOLVER

## Overview

This page only details differences from the general min-eVOLVER experimental [protocol](../starting-an-experiment.md). You are also expected to have an understanding of PACE and how it is normally run before doing ePACE.

{% hint style="info" %}
* ePACE described initially in[ Huang, Heins et al. 2022 _Nature Biotech_](https://www.nature.com/articles/s41587-022-01410-2#Sec15)_._
* For general PACE methods see [Miller, Wang 2020 _Nature Protocols_](https://www.nature.com/articles/s41596-020-00410-3)_._
{% endhint %}

{% hint style="warning" %}
For running ePACE, OD calibration via [growth curve](../calibrations/od-calibration-via-growth-curve.md) is _required_ because S2060 cells have significantly different scattering properties while growing vs during stationary phase.
{% endhint %}

## Implementing Controlled Host Cell Density in Reservoirs

{% hint style="info" %}
This section constitutes changes from [Huang, Heins et al. 2022 _Nature Biotech_](https://www.nature.com/articles/s41587-022-01410-2#Sec15)_._
{% endhint %}

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
