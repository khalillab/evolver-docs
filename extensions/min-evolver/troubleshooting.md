# Troubleshooting

## min-eVOLVER Specific

### My min-eVOLVER is plugged in but I can't connect to it via the server code

* If the server code says that the expected min-eVOLVER port is plugged in, check that the `conf.yml` file has the correct port address in it (as detailed in the [setup](software-setup.md#server-startup)).
* As a last resort, [reupload](troubleshooting.md#reupload-the-arduino) the Arduino [code](https://github.com/FYNCH-BIO/evolver-arduino/tree/master/SAMD21/MINEVOLVER)

### The server is cycling (every \~20 seconds there are new values) but all commands are erroring

<figure><img src="../../.gitbook/assets/image (3) (1).png" alt=""><figcaption><p>An example error thrown when the server is running but isn't getting responses from the min-eVOLVER.</p></figcaption></figure>

* This happens when the micro-USB is unplugged and replugged in, but the power supply is not
* Quit the server (ctrl+C), unplug the min-eVOLVER from power and micro-USB, plug the micro-USB back in, then the power supply, and restart the server
* As a last resort, [reupload](troubleshooting.md#reupload-the-arduino) the Arduino [code](https://github.com/FYNCH-BIO/evolver-arduino/tree/master/SAMD21/MINEVOLVER)

### Re-Upload the Arduino Code

Rarely, the Arduino that runs the min-eVOLVER needs to be uploaded with its software again. Follow the Arduino Software Installation [guide](../../guides/arduino-software-installation.md) and upload the min-eVOLVER Arduino [code](https://github.com/FYNCH-BIO/evolver-arduino/tree/master/SAMD21/MINEVOLVER) onto the device.

## OD&#x20;

OD is one of the most useful and most challenging aspects of eVOLVER. However the min-eVOLVER OD system is nearly the same as the main eVOLVER. Check the main OD troubleshooting [page](../../troubleshooting/vial-troubleshooting/optical-density-od-readings.md) for potential causes and fixes.
