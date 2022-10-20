---
description: Process for configuring a Raspberry Pi for eVOLVER
---

# Raspberry Pi Configuration

Please see the [Raspberry Pi](../hardware/raspberry-pi.md) infrastructure page for additional information on the RPi we use for the eVOLVER.

{% hint style="danger" %}
Be sure to [update the server code](updating-the-evolver-server.md) on the RPi after following this guide, or you will have issues communicating with the server through the DPU or with actuating/sensing connected components!
{% endhint %}

[RPi Imager Guide](raspberry-pi-configuration.md#using-raspberry-pi-imager) - **Recommended**

[Command Line Guide (Mac/UNIX only)](raspberry-pi-configuration.md#using-command-line-utilities-mac-unix-only)

### Using Raspberry Pi Imager

**1.** Download the pre-configured eVOLVER RPi image [here](https://drive.google.com/file/d/1yDQ\_HLA8o-DooAyxWKPMJJNqN8z-LEy3/view?usp=sharing).

**2.** Download and install the [Rapberry Pi Imager Tool](https://www.raspberrypi.com/software/).

![](<../.gitbook/assets/Screen Shot 2022-05-31 at 1.30.16 PM.png>)

**3.** Plug an 8GB micro-SD for the RPi into an adapter, then into a the computer.

**4.** Click the `Choose OS` button, then scroll to the bottom and click `Use Custom`.

![](<../.gitbook/assets/Screen Shot 2022-05-31 at 1.37.44 PM.png>)

![](<../.gitbook/assets/Screen Shot 2022-05-31 at 1.38.41 PM.png>)

**5.** In the popup at the dropdown at the bottom of the window, select `All files(*.*)`. Then select the image file downloaded in Step 1.

![](<../.gitbook/assets/Screen Shot 2022-05-31 at 1.42.01 PM.png>)

**6.** Click the `Choose Storage` button and select the SD Card.

![](<../.gitbook/assets/Screen Shot 2022-05-31 at 1.58.53 PM.png>)

**7.** Click the `Write` button. A notification might appear warning about erasing all existing data on the card. Click `Yes`. If it asks for your computer password afterwards, enter it. It might take a while to finish (\~40m).&#x20;

**8.** When it completes, you can plug the SD card into the RPi. You will need to [update the server code](updating-the-evolver-server.md) and potentially the `conf.yml` with the latest code from GitHub.&#x20;

### Using command line utilities (Mac/UNIX only)

**1.** Download the pre-configured eVOLVER RPi image [here](https://drive.google.com/file/d/1yDQ\_HLA8o-DooAyxWKPMJJNqN8z-LEy3/view?usp=sharing).

**2.** Plug the SD card into the computer.

**3.** Open a terminal of your choice (I recommend [iTerm2](https://iterm2.com/)).

**4.** Run the following command:

`diskutil list`

Identify the SD card name from this (it should be obvious). Next run:

`diskutil unmountdisk <diskname>`

where \<diskname> is the name you identified from the previous command - it should look like

`/dev/disk3/` or something similar.

**5.** Use the `dd` command to copy the image onto the SD card:

`sudo dd bs=4m if=<diskimage.img> of=<diskname>`

{% hint style="warning" %}
Be sure to change the two arguments above! `if` should point to the image you downloaded from step 1, and `of` should be the diskname.
{% endhint %}

This command can take a while, and it doesn't show any status or progress updates - be patient. If it fails, try decreasing the `bs` argument to `1m` instead of `4m` - this will slow things down but will decrease the chance of failure. If you still have issues reach out on the [forum](https://www.evolver.bio/).

**6.** When it completes, you can plug the SD card into the RPi. You will need to [update the server code](updating-the-evolver-server.md) and potentially the `conf.yml` with the latest code from GitHub.

## Backing Up Raspberry Pi (Make a Custom Image)

Writing an image to save your full Raspberry Pi configuration.&#x20;

Useful to save time when reimaging your Raspberry Pi if you want to go back to your custom Python code and calibrations as quickly as possible.&#x20;

Follow this guide: [https://www.tomshardware.com/how-to/back-up-raspberry-pi-as-disk-image](https://www.tomshardware.com/how-to/back-up-raspberry-pi-as-disk-image)
