# OD90 vs OD135

## Definition

The two photodiodes on the eVOLVER are at 90 degrees and 135 degrees from the IR LED.

## Recommendations

* Try OD135 for OD600 < 0.5
  1. There will likely be vials that max out between OD600 0.5 and 1.0
* Try OD90 for OD600 > 0.5
  1. Some eVOLVER systems are able to read OD90 up to OD600 of 4 or 5
  2. This may require optimization of the internal resistor pack
* Switching between currently requires [manual OD calibration](../../../getting-started/calibrations/manual-calibration-calibrate.py.md) (can be applied to an existing GUI calibration you have on your eVOLVER)
* See [this ](https://www.evolver.bio/t/od-calibration-issues-signal-maxed-out/447)forum post for an example
