# Troubleshooting

## Server Troubleshooting

### My min-eVOLVER is plugged in but I can't connect to it via the server code

* If the server code says that the expected min-eVOLVER port is plugged in, check that the `conf.yml` file has the correct port address in it (as detailed in the [setup](software-installation-and-startup.md#server-startup)).
* As a last resort, [reupload](troubleshooting.md#reupload-the-arduino) the Arduino [code](https://github.com/FYNCH-BIO/evolver-arduino/tree/master/SAMD21/MINEVOLVER)

### The server is cycling (every \~20 seconds there are new values) but all commands are erroring

<figure><img src="../../.gitbook/assets/image (3) (1) (2).png" alt=""><figcaption><p>An example error thrown when the server is running but isn't getting responses from the min-eVOLVER.</p></figcaption></figure>

* This happens when the micro-USB is unplugged and replugged in, but the power supply is not
* Quit the server (ctrl+C), unplug the min-eVOLVER from power and micro-USB, plug the micro-USB back in, then the power supply, and restart the server
* As a last resort, [reupload](troubleshooting.md#reupload-the-arduino) the Arduino [code](https://github.com/FYNCH-BIO/evolver-arduino/tree/master/SAMD21/MINEVOLVER)

### Correct 'serial\_port' but Server is Not Starting

I have found this happens when the Arduino IDE program (used for putting min-eVOLVER code on the control board) Serial Monitor is open and connected to the SAMD21. Close the Serial Monitor and you will be able to start the server.&#x20;

<figure><img src="../../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>

### Re-Upload the Arduino Code

Rarely, the Arduino that runs the min-eVOLVER needs to be uploaded with its software again. Follow the Arduino Software Installation [guide](../../guides/arduino-software-installation.md) and upload the min-eVOLVER Arduino [code](https://github.com/FYNCH-BIO/evolver-arduino/tree/master/SAMD21/MINEVOLVER) onto the device.

## Experiment Troubleshooting

### Disconnecting During an Experiment

The most common reason for this is the computer is falling asleep. Make sure your computer is set to not fall asleep.

{% hint style="info" %}
If your computer is managed by an IT department, they will sometimes control these settings remotely. Therefore, you will set your computer to never sleep, but will come back with the setting changed. In this case, contact your IT department.&#x20;

On Mac: Alternatively, you can type the command `caffeinate` into a terminal window and your computer will never sleep
{% endhint %}

## OD

OD is one of the most useful and most challenging aspects of eVOLVER. However the min-eVOLVER OD system is nearly the same as the main eVOLVER. Check the main OD troubleshooting [page](../../troubleshooting/vial-troubleshooting/optical-density-od-readings.md) for potential causes and fixes.
