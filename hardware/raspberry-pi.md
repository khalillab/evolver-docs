---
description: >-
  Resources for setting up and interacting with the Raspberry Pi for use in the
  eVOLVER platform.
---

# Raspberry Pi

eVOLVER uses Raspberry Pi for interfacing with the Arduino microcontrollers and for processing user and experimental commands. Hardware and software configurations and calibrations are saved on the RPi.

We provide a pre-configured RPi image that is configured to run all eVOLVER software.

[RPi image for eVOLVER](https://drive.google.com/file/d/1yDQ\_HLA8o-DooAyxWKPMJJNqN8z-LEy3/view)

[General RPi information](https://www.raspberrypi.org/)

[Raspberry Pi Imager](https://www.raspberrypi.com/software/) - Use this to upload the disk image linked above to the RPi SD card. We have a guide for this process [here](../guides/raspberry-pi-configuration.md).

[Guide for uploading a disk image to the RPi SD card via command line](https://www.evolver.bio/t/configuring-a-new-rpi-for-evolver-as-server/210/2) - Only use this if you are comfortable working on a terminal and the upload tool above isn't working for you.

### Setting up a new RPi

If you need to setup a new RPi, download the image linked above and install the Raspberry Pi Imager tool on your personal laptop or computer. Plug in the SD card from the RPi and upload them image onto it (this process might take a while). Afterwards, you can plug the card back into the RPi and [update the server code](../guides/updating-the-evolver-server.md).
