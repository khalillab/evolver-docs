# Troubleshooting Optical Density Readings

[optical-density.md](../../hardware/smart-sleeve/optical-density.md "mention")

## Flow Chart

If not able to read OD above a low level:

* Standardize LED/Photodiode distance

If seeing noisy OD readings:



If OD is not working at all on a single vial:

* &#x20;[replacing-photodiodes-and-leds.md](replacing-photodiodes-and-leds.md "mention")

## Variables

Experiment Considerations

* [Ambient light](https://www.evolver.bio/t/od-oscillating-even-with-no-sample/209)
* Photodiode Temperature (link to characterization)
* eVOLVER recently turned on - causes rapid change in values
* [Vial to Vial Sleeve Distance](https://www.evolver.bio/t/baseline-od-readings-change-after-rotating-vial-with-vial-aligner/260) - [Second Forum Post](https://www.evolver.bio/t/preventing-wobbling-of-the-glass-vial-for-better-od-measurements/185)

Pre-Calibration Considerations

* [LED to photodiode angle](https://www.evolver.bio/t/od-measurements-with-two-photodiodes/99)
* [Depth of photodiode and OD LED into the vial](https://www.evolver.bio/t/how-deeply-the-photodiode-and-ir-led-are-pushed-in-to-the-vial-greatly-affects-od-readings/360)
* od\_led value in conf.yml file (PWM value)
* [Resistor pack value](https://www.evolver.bio/t/od-led-power-level-vs-resistor-packs/87)

Non-standard changes

* [Low (\~10mL) culture volumes ONLY - readings are affected by stirring](https://www.evolver.bio/t/at-lower-culture-volumes-optical-density-readings-are-affected-by-stirring/367)
* Vial holder reflectiveness - ie white vs black vs metallic
