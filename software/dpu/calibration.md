---
description: An overview of what happens in the software during a calibration
---

# Calibration

{% hint style="info" %}
For GUI calibration _guides_ see [here](../../getting-started/calibrations/).
{% endhint %}

## Procedure

{% hint style="info" %}
Communication between the computer and the server is done via [websockets](../server-raspberry-pi/#websockets-communications).

For more about commands and microcontroller - server communication via serial see [here](../server-raspberry-pi/#server-serial-communication).
{% endhint %}

### Temperature calibration example:

1. GUI connects to the server via [websockets](../server-raspberry-pi/#websockets-communications)
2. The user has the GUI sends a temperature off command: `tempi,4095,4095,4095,4095,4095,4095,4095,4095,4095,4095,4095,4095,4095,4095,4095,4095,_!`
3. The server passes this to the Arduinos and the temperature Arduino enacts that command
4. The server receives temperature data broadcast from the server
5. The user waits for temperatures to equilibrate in the vials
6. The user measures values from an independent temperature probe for each vial and records these in the GUI
7. The user has the GUI record 3 values at this temperature from the server
8. Steps 2 - 7 are repeated for two higher temperature values
9. When 3 values for 3 different temperatures have been collected, the GUI saves the raw sensor data and the temperature probe data on the server in [calibrations.json](https://github.com/FYNCH-BIO/evolver/blob/master/evolver/calibrations.json)

<figure><img src="../../.gitbook/assets/image (63).png" alt=""><figcaption><p>A new calibration save in calibrations.json before fit is performed (no data under fits).</p></figcaption></figure>

10. The GUI uses [calibrate.py](https://github.com/FYNCH-BIO/dpu/blob/master/calibration/calibrate.py) (guide [here](../../getting-started/calibrations/manual-calibration-calibrate.py.md)) to fit raw sensor data from the eVOLVER to experimental temperature probe values (in this case a linear regression)
    1. calibrate.py uses websockets to fetch the sensor and experimental data from the server for a previously run calibration, then does the fit according to the users specifications
    2. The GUI will automatically run this script upon completion of a calibration, but it is also possible to run [manually ](../../getting-started/calibrations/manual-calibration-calibrate.py.md)via the command line to fetch .png files for the calibrations if desired.
11. The GUI adds the calibration fit values to calibrations.json
12. The user can now select this calibration as the active one via the GUI Setup page

