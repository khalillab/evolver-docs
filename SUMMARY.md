# Table of contents

* [eVOLVER Documentation Wiki](README.md)

## General

* [About Us](general/about-us.md)
* [eVOLVER Community](general/evolver-community/README.md)
  * [Code of Conduct](general/evolver-community/code-of-conduct.md)

## Getting Started

* [Buying eVOLVER](getting-started/buying-evolver.md)
* [Unboxing and Setting Up](getting-started/unboxing-and-setting-up.md)
* [Configuring Computer and Networking](getting-started/configuring-computer-and-networking/README.md)
  * [Router Setup](getting-started/configuring-computer-and-networking/router-setup.md)
* [Calibrations](getting-started/calibrations/README.md)
  * [Pump Calibration](getting-started/calibrations/pump-calibration.md)
* [Consumables](getting-started/consumables.md)

## Experiments

* [Starting an Experiment](experiments/starting-an-experiment/README.md)
  * [Carboy Media Prep](experiments/starting-an-experiment/carboy-media-prep.md)
  * [Prepare Vials](experiments/starting-an-experiment/prepare-vials.md)
  * [GUI Start Guide](experiments/starting-an-experiment/gui-start-guide.md)
  * [Command Line Start Guide](experiments/starting-an-experiment/command-line-start-guide.md)
* [Growth Curve](experiments/growth-curve.md)
* [Chemostat](experiments/chemostat.md)
* [Turbidostat](experiments/turbidostat.md)
* [FAQs + Tips and Tricks](experiments/faqs-+-tips-and-tricks.md)

## Guides

* [Building a Smart Sleeve](guides/building-a-smart-sleeve.md)
* [Making media bottles and splitters](guides/making-media-bottles-and-splitters.md)
* [Software Installation](guides/software-installation/README.md)
  * [DPU Installation](guides/software-installation/dpu-installation.md)
  * [Electron App (GUI) Installation](guides/software-installation/electron-app-gui-installation.md)
  * [Arduino Software Installation](guides/software-installation/arduino-software-installation.md)
  * [Raspberry Pi Configuration](guides/software-installation/raspberry-pi-configuration.md)
* [Updating the eVOLVER Server](guides/updating-the-evolver-server.md)
* [Fluidics Customization](guides/fluidics-customization.md)
* [Part Sourcing](guides/part-sourcing.md)
* [Command Line Usage](guides/command-line-usage.md)

## Troubleshooting

* [Troubleshooting Overview](troubleshooting/troubleshooting-overview.md)
* [eVOLVER Maintenance](troubleshooting/evolver-maintenance.md)
* [Experiment Troubleshooting](troubleshooting/experiment-troubleshooting/README.md)
  * [Contamination](troubleshooting/experiment-troubleshooting/contamination.md)
  * [Vial Overflow, Pump Failure, and Spills](troubleshooting/experiment-troubleshooting/vial-overflow-pump-failure-and-spills.md)
  * [Running Out of Media](troubleshooting/experiment-troubleshooting/running-out-of-media.md)
  * [Miscellaneous](troubleshooting/experiment-troubleshooting/miscellaneous.md)
* [Vial Troubleshooting](troubleshooting/vial-troubleshooting/README.md)
  * [Troubleshooting Optical Density Readings](troubleshooting/vial-troubleshooting/troubleshooting-optical-density-readings.md)
  * [Replacing Photodiodes and LEDs](troubleshooting/vial-troubleshooting/replacing-photodiodes-and-leds.md)
  * [Heating Element](troubleshooting/vial-troubleshooting/heating-element.md)
  * [Stirring](troubleshooting/vial-troubleshooting/stirring.md)
* [Motherboard Troubleshooting](troubleshooting/motherboard-troubleshooting.md)
* [Fluidics Troubleshooting](troubleshooting/fluidics-troubleshooting.md)
* [GUI Troubleshooting](troubleshooting/gui-troubleshooting.md)
* [Server Troubleshooting](troubleshooting/server-troubleshooting.md)
* [Arduino Troubleshooting](troubleshooting/arduino-troubleshooting.md)

## Hardware

* [Overview of Hardware Architecture](hardware/overview-of-hardware-architecture.md)
* [Overview of Fluidics](hardware/overview-of-fluidics/README.md)
  * [Tubing](hardware/overview-of-fluidics/tubing.md)
  * [Luer Connectors](hardware/overview-of-fluidics/luer-connectors.md)
  * [Fluidics Box](hardware/overview-of-fluidics/fluidics-box.md)
  * [Pump Arrays](hardware/overview-of-fluidics/pump-arrays.md)
* [Overview of Millifluidics](hardware/overview-of-millifluidics.md)
* [Smart Sleeve](hardware/smart-sleeve/README.md)
  * [🌪 Stirring](hardware/smart-sleeve/stirring.md)
  * [Temperature](hardware/smart-sleeve/temperature.md)
  * [Optical Density](hardware/smart-sleeve/optical-density.md)
* [Motherboard Layout and Circuitry](hardware/motherboard-layout-and-circuitry/README.md)
  * [🌡 Arduino](hardware/motherboard-layout-and-circuitry/arduino.md)
  * [Sensor/Actuator Board Slots](hardware/motherboard-layout-and-circuitry/sensor-actuator-board-slots.md)
  * [Pulse Width Modulation (PWM) Boards](hardware/motherboard-layout-and-circuitry/pulse-width-modulation-pwm-boards.md)
  * [Analog-to-Digital Converter (ADC) Boards](hardware/motherboard-layout-and-circuitry/analog-to-digital-converter-adc-boards.md)
* [Raspberry Pi](hardware/raspberry-pi.md)
* [Chassis](hardware/chassis.md)
* [Known Issues](hardware/known-issues.md)

## Software

* [Overview of Software Architecture](software/overview-of-software-architecture.md)
* [Arduino Code Structure](software/arduino-code-structure.md)
* [Server Code Structure](software/server-code-structure/README.md)
  * [Calibration Files](software/server-code-structure/calibration-files.md)
  * [Configuration Files (conf.yml)](software/server-code-structure/configuration-files-conf.yml.md)
* [DPU Code Structure](software/dpu-code-structure/README.md)
  * [eVOLVER.py](software/dpu-code-structure/evolver.py.md)
  * [custom\_script.py](software/dpu-code-structure/custom\_script.py.md)
  * [Experiment Data Files](software/dpu-code-structure/experiment-data-files.md)
  * [OD Blank](software/dpu-code-structure/od-blank.md)
* [Known Issues](software/known-issues.md)

## Extensions

* [Overview](extensions/overview.md)
* [Custom Experiments](extensions/custom-experiments/README.md)
  * [Morbidostat](extensions/custom-experiments/morbidostat.md)
* [Adding an Experimental Parameter](extensions/adding-an-experimental-parameter/README.md)
  * [Power Supply](extensions/adding-an-experimental-parameter/power-supply.md)
  * [Specific Applications](extensions/adding-an-experimental-parameter/specific-applications.md)
  * [Custom Calibration Code](extensions/adding-an-experimental-parameter/custom-calibration-code.md)
* [Interfacing with Other Systems](extensions/interfacing-with-other-systems.md)

## Contributing

* [Guidelines for Contribution](contributing/guidelines-for-contribution.md)
* [Reporting a Bug / Hardware Failure](contributing/reporting-a-bug-hardware-failure.md)
* [Documentation](contributing/documentation/README.md)
  * [Making a Forum Post](contributing/documentation/making-a-forum-post.md)
  * [How to Edit the Wiki](contributing/documentation/how-to-edit-the-wiki.md)
* [Software Development](contributing/software-development.md)
* [Hardware Development](contributing/hardware-development.md)
