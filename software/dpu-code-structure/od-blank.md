# OD Blank

## Why

When we start an experiment, the script asks us whether we want to calibrate to blank.

[OD is dependent](../../troubleshooting/vial-troubleshooting/optical-density-od-readings.md) on vial position, vial opacity, media, environmental light conditions, temperature, and more.

Therefore, we take the first OD measurement as a zero and subtract that out from every subsequent measurement.

{% hint style="warning" %}
* Temperature should be fully equilibrated before this
* DO NOT add cells before blanking, whatever OD value the cells + media have will be subtracted from future OD measurements
{% endhint %}

## Details

OD blank is only applied to the calculated OD from calibration, not the raw OD data. The blank is applied for each vial, it just subtracts it out from subsequent measurements for that vial

[https://www.evolver.bio/t/where-or-how-is-od-blank-info-stored/182](https://www.evolver.bio/t/where-or-how-is-od-blank-info-stored/182)
