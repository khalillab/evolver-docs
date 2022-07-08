# Known Issues

{% hint style="info" %}
Please report any issues you come across in the appropriate [Github repository](https://github.com/FYNCH-BIO/) and consider making a post on the [forum](https://www.evolver.bio/)!
{% endhint %}



* Arduino addressing (ask Ezira)
* List of rules

## Experiments

Need a way to re-blank OD during the middle of an experiment

1. Currently have to make a new experiment
2. Sometimes you need to change a vial's position

Remote access / backup of experiment

* Also alerts for

## Server

Need easy editing / swapping of conf.yml files

* Some experiments require pausing of certain parameters
* Therefore they need to send pre/post commands that are executed before a given main command is executed
* So they have long broadcast times and need their conf.yml files to be swapped out
* Also important that humans don't edit conf.yml (can easily mess formatting up)

Pumps run for a second when server is restarted

* Can cause unintended media spillage

Commands will not be properly sent if they are too long

* Solution: increase serial\_timeout in conf.yml

## Calibrations

Calibrations require command line

Calibrations should be saved automatically in the dpu

* This way server troubleshooting / issues with the rPi do not effect them

Last vial adjusted each round in an OD calibration (usually vial 15) can have higher error

* Because the server gives old values

## Flexibility / Extensions to eVOLVER

Addition of experiment parameters (pH, light, etc) requires many manual changes to code

* GUI needs to be manually adapted for each new parameter. Templates for a new calibration and parameter control are needed

## Analysis

A shared library of tools for analyzing eVOLVER data in python

* No need for each new user to reinvent the wheel for importing eVOLVER files and doing more complicated analysis on them than the GUI graphing will provide
* Also having the dpu software output data into a single csv file (not broken up by vial / variable) for easy analysis would be good -- definitely would need to be in long format (ie vial as a variable)
