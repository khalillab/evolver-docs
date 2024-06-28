# Optical Density (OD) Readings

## Overview

Optical density (OD) is one of the most integral parts of continuous culture. While chemostats do not innately rely on OD, it is still a useful metric for your evolution. Meanwhile, turbidostats and growth curves heavily rely on OD to function.

However, OD is the most easily disrupted parts of eVOLVER hardware. This guide serves as an initial list of things to check when troubleshooting OD.

{% hint style="warning" %}
Disclaimer: You may find that you are still not getting "good" OD readings after trying solutions in this  guide. We hope that you will search the [forum ](https://www.evolver.bio/)because others may have had your same issue.
{% endhint %}

{% hint style="warning" %}
After trying a fix, before attempting a whole new calibration, prepare a couple of standards in the OD range that you care about and check if you see a difference between them in the raw OD values (in the GUI Setup page or by starting an experiment and going to the data folder).
{% endhint %}

{% hint style="info" %}
For more in-depth information about the OD hardware see [here](../hardware/smart-sleeve/optical-density/).
{% endhint %}

## Most Common Problems

### Variability in OD Sensing Range Between Vials

<figure><img src="../.gitbook/assets/image (65).png" alt=""><figcaption><p>Vial 1 (left) shows a smaller range than vial 2 (right). However, vial 2 is still unable to accurately differentiate values under OD 0.5.</p></figcaption></figure>

1. [Standardize LED/Photodiode distance](../guides/upgrade-base-evolver-hardware.md#strongly-recommended-better-3d-printed-vial-holder)
2. If you already have a version of the 3D printed tube holder with defined OD LED and photodiode distances:
   1. Use the upgrade [guide](../guides/upgrade-base-evolver-hardware.md#guide) to double check your photodiodes and LEDs are correctly placed!
3. Try [OD90 for OD600 0.5-4.5 or OD135 for OD600 0.0-0.5](../hardware/smart-sleeve/optical-density/od90-vs-od135.md)
4. Try different ADC resistor packs
   1. eVOLVERs come with a variety of these
   2. Ask on the forum for help
5. Check that your vial construction is not variable

### Noisy OD Data

1. Stir bars jumping around during OD readings
   1. Decrease stir speed
   2. [Stop stirring during OD readings](https://github.com/FYNCH-BIO/evolver/tree/master/evolver/alternate\_conf\_files)
2. You are near the edge of your calibrated OD range
3. [OD blank](../experiments/starting-an-experiment/od-blank.md) is off enough to make your calibration fail

### Incorrect OD

ie eVOLVER OD is offset from the cuvette or plate reader measured value.&#x20;

1. Bad [OD blank](../experiments/starting-an-experiment/od-blank.md)
   1. Especially because you did not wait for temperatures of the vials to equilibriate
2. Poor quality OD calibration
   1. You can check your OD calibration using the [manual calibration](../guides/manual-calibration-calibrate.py.md) script
   2. Different temperatures require different OD calibrations

### No Change in OD

1. Photodiode or IR LED not working
   1. Replacement [guide](vial-troubleshooting/replacing-photodiodes-and-leds.md)
   2. A failed photodiode will show a raw OD value close to 64,000
   3. A failed IR LED will most likely show a raw OD value much closer to your other vials
   4. Check that they have the long (positive) lead in the correct positive terminal
2. ADC board or motherboard broken&#x20;
   1. Can happen after vial overflow
   2. See motherboard [hardware ](../hardware/motherboard-layout-and-circuitry/)and [troubleshooting](motherboard-troubleshooting.md)

## Other Considerations

Pre-Calibration Considerations

* [LED to photodiode angle](https://www.evolver.bio/t/od-measurements-with-two-photodiodes/99)
* od\_led value in conf.yml file (PWM value)
* [Resistor pack value](https://www.evolver.bio/t/od-led-power-level-vs-resistor-packs/87)
* [Ambient light](https://www.evolver.bio/t/od-oscillating-even-with-no-sample/209)
  * Use the splash guard that comes with your eVOLVER
  * Or make one using black acrylic
  * You may need to recalibrate if you calibrated with ambient light

Experiment Considerations

* Photodiode Temperature - make sure temperature is equilibrated before calibration and before start of experiment
* eVOLVER recently turned on - causes rapid change in values
* [Vial to Vial Sleeve Distance](https://www.evolver.bio/t/baseline-od-readings-change-after-rotating-vial-with-vial-aligner/260) - [Second Forum Post](https://www.evolver.bio/t/preventing-wobbling-of-the-glass-vial-for-better-od-measurements/185)
* Needles or other structures coming below 10mL line (close to OD PD etc)
* Vial volume - a volume of 10mL will totally change OD compared to 30
* Stirring with low vial volume - this will give noisy readings as the funnel created by stirring fluctuates and is more and less reflective

Non-standard changes

* [Low (\~10mL) culture volumes ONLY - readings are affected by stirring](https://www.evolver.bio/t/at-lower-culture-volumes-optical-density-readings-are-affected-by-stirring/367)
* Vial holder reflectiveness - ie white vs black vs metallic
