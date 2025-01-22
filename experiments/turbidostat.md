---
description: >-
  Turbidostats are automated culturing systems used to maintain a constant cell
  density in microbial cultures.
---

# Turbidostat

## Algorithm

1. OD is constantly monitored
2. When OD goes above the an upper OD threshold
3. A dilution is calculated to bring OD to the lower threshold
   1. Dilutions are capped at 20 seconds to avoid vial overflow
4. Both influx and efflux pumps are run simultaneously for the calculated length
5. Efflux pumps are run extra to make sure volume stays constant
   1. The efflux straw sets volume&#x20;

## Turbidostat Dilution

### Pumps

* Influx and efflux are both run at the same time
* Like chemostat, vial volume is set by efflux straw height
  * Efflux is run extra time to make sure that enough volume is removed
* Pumps run at roughly 0.75mL/second
* Pump calibration is important for turbidostat otherwise dilutions will not hit the lower OD threshold accurately

### Dilution Calculation Example

Dilution is calculated [here](https://github.com/FYNCH-BIO/dpu/blob/1ea8fe36a6a7cdbcf4e5a872c43abfdf53acaf35/experiment/template/custom_script.py#L124C17-L124C85) in the code and is modeled as a mass balance equation

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

#### Example Dilution

`time_in = -(np.log(lower_thresh[x]/average_OD) *VOLUME)/flow_rate[x]`

```python
average_OD = 1 # OD
lower_threshold = 0.5 # OD
VOLUME = 25 # mL
flow_rate = 0.75 # mL/second
time_in = -(np.log(0.5/1)*25)/0.75 = 23.1 # seconds
```

_However, the mox dilution is 20 seconds to avoid overflow._

## Growth Rate

### Calculation

Calculated in eVOLVER.py in [this](https://github.com/FYNCH-BIO/dpu/blob/1ea8fe36a6a7cdbcf4e5a872c43abfdf53acaf35/experiment/template/eVOLVER.py#L483) function and stored in your data folder during an experiment.

When there is a turbidostat dilution, it fits a line to the log of the OD data since the last growth curve (ie last turbidostat dilution) time. The slope of that line is reported as the growth rate in 1/h.

### Doubling Time

Convert growth rate to doubling time (in hours) via ln(2)/growthrate.\


## More Info

See [custom\_script](../software/dpu/custom_script.py.md) and the [GUI start guide](starting-an-experiment/gui-start-guide.md) for information.
