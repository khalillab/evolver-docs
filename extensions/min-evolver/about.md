# About

## Purpose

The min-eVOLVER was originally conceived of as a minimal apparatus to conduct [phage-assisted continuous evolution (PACE)](../custom-experiments/epace/). Thus it has two bioreactors (eVOLVER [Smart Sleeves](../../hardware/smart-sleeve/)): one for a "host cell reservoir" and one for a "lagoon". It also has six pumps: four for bulk media in and out of the two Smart Sleeves and two for fine control over inducers into the lagoon.

However, base min-eVOLVER can be used for most continuous culture scenarios, such as turbidostat and chemostat. It can also be readily adapted to new experiments.

## Differences from Main eVOLVER

### Software-Hardware Architecture

The software architecture of the min-eVOLVER is similar to the [original eVOLVER](../../software/overview-of-software-architecture.md), with the exceptions that:&#x20;

* The Raspberry Pi server has been replaced with a server run on the connected laptop&#x20;
* A single Arduino SAMD21 actuates all functions and collects vial data through the min-eVOLVER board
