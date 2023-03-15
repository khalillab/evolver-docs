# Operating Millifluidics

{% hint style="warning" %}
Always use less than 10 psi inputs into the millifluidics and pressure regulator to avoid breaking them
{% endhint %}

{% hint style="warning" %}
Never use ethanol to sterilize millifluidics as it breaks them. Use bleach to sterilize and flush it with sterile water.
{% endhint %}

## Set Up [Pressure Regulator](../../hardware/overview-of-millifluidics/pressure-regulator.md)

Plug in 5V power supply and 5V fan

### Changing Pressure Settings

Option 1: Manually change via Arduino [code](https://github.com/FYNCH-BIO/evolver-arduino/blob/484d547205d03e82589d435ccad0a765331a3cb6/SAMD21/RS485\_PRESSURE/RS485\_PRESSURE.ino#L21) (hard coded)

* Follow the Arduino Software Installation [guide](../arduino-software-installation.md)
* Unplug the SAMD21 from the pressure regulator before uploading code (otherwise there might not be enough power to the SAMD21 from the USB)
* Upload modified pressure code to SAMD21

Option 2: Add a 'pres' command to the evolver conf.yml and modify conf.yml

### Fluidic Lines

Connect a 8-10 psi air input into the input port (only port on its own in 1.0 design)

Connect regulated line to both sensor (below) and controlled output (white, above) as shown below:

![](<../../.gitbook/assets/image (29).png>)

## Set Up Solenoid Control

Solenoid Bank Diagram (facing holes)

* The solenoids should be normally open and connected to the 8 psi air source. ie Vacuum when closed
* Left = 8 psi
* Right = Vacuum
* Middle = 8 different solenoids, groups of 3 are IPP controls

![](<../../.gitbook/assets/image (6) (2).png>)

Connect solenoid ribbon cable to slot 5 on the fluidics box

Turn on eVOLVER server and fluidics box

### Check that the solenoid bank is correctly set

Run ipp\_cal.py on the server:

* [ssh to server](../updating-the-evolver-server.md)
* Use command:
  * `python3 ipp_cal.py <frequency (hz)> <seconds to run>`
  * For example: `python3 ipp_cal.py 1 100`

## Set Up IPPs

{% hint style="info" %}
IPPs need to be [constructed](constructing-laser-cut-millifluidics.md) and [calibrated](calibrating-ipps.md) before use.

It is recommended to calibrate using a pressurized input line (ie a 1.5 psi bottle). Always use that same pressure on the fluidic input.
{% endhint %}

* Hook IPPs up to a pressurized input bottle for consistency
* Make sure that IPPs are operating as expected and producing the expected flow rate

{% hint style="info" %}
If running a trial experiment with just water, you can put food dye in to the inducer to visualize how much is injected into vials
{% endhint %}
