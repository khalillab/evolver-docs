# Troubleshooting

My min-eVOLVER is plugged in but I can't connect to it via the server code

* If the server code says that the expected min-eVOLVER port is plugged in, check that the conf.yml file has the correct port address in it (as detailed in the [setup](setup.md#server-startup)).
* As a last resort, [reupload](troubleshooting.md#reupload-the-arduino) the Arduino code

The server is cycling (every \~20 seconds there are new values) but all commands are erroring

* Quit the server (ctrl+C), unplug the min-eVOLVER from power and micro-USB, plug everything back in, and restart the server
* As a last resort, [reupload](troubleshooting.md#reupload-the-arduino) the Arduino code

## Reupload the Arduino Code

Sometimes the Arduino that runs the min-eVOLVER needs to be uploaded with its software again. This can happen when power is unplugged suddenly. Follow the Arduino Software Installation [guide](../../guides/arduino-software-installation.md) and upload the min-eVOLVER Arduino [code](https://github.com/FYNCH-BIO/evolver-arduino/tree/master/SAMD21/MINEVOLVER) onto the device.
