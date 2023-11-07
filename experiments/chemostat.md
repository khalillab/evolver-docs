---
description: Process and considerations for running a chemostat.
---

# Chemostat

## Code Breakdown and Explanation of Flow Rates

This section is assuming you already have gone through the [growth curve tutorial](growth-curve.md), which outlines basic parts of the script, and lets one run an initial pilot experiment.&#x20;

Here, I will explain chemostat functionality. This is the segment where the chemostat function begins on [custom\_script.py](https://github.com/FYNCH-BIO/dpu/blob/master/experiment/template/custom\_script.py#L161)

```python
def chemostat(eVOLVER, input_data, vials, elapsed_time):
    OD_data = input_data['transformed']['od']

    ##### USER DEFINED VARIABLES #####
    start_OD = [0] * 16 # ~OD600, set to 0 to start chemostate dilutions at any positive OD
    start_time = [0] * 16 #hours, set 0 to start immediately
    # Note that script uses AND logic, so both start time and start OD must be surpassed

    OD_values_to_average = 6  # Number of values to calculate the OD average

    chemostat_vials = vials #vials is all 16, can set to different range (ex. [0,1,2,3]) to only trigger tstat on those vials
```

* **OD\_data:** The `OD_data` variable saved from the transformed values from the input\_data variable. The data is transformed via calibration scripts called from `eVOLVER.py`.&#x20;
* **start\_OD:** This variable determines if you want the culture to be above a certain OD before starting dilutions
* **start\_time**: This variable determines when the dilutions should start. If set to 0, the dilutions start immediately
* **OD\_values\_to\_average**: The script will average N recorded OD values before it triggers the dilution via the **`start_OD`** variable.
* **chemostat\_vials**: Modify this script to to turn off vials (e.g. pumps). There is a known bug on the rate definition that might not turn off the pumps there (see below).

#### The peristaltic pumps are fixed flow rates, does that mean I have to use different pumps for each flow rate setting?

No, with the eVOLVER setup, we approximate continuous perfusion by frequent small boluses of media. By doing this, a faster pump can achieve tunable, slower net flow rates. In our experience, this compromise does not significantly impact the culture conditions of common laboratory microbes.&#x20;

Here is an example calculation one would make:

* The culture volume is 30 mL/ vial.
* The typical pumps eVOLVER comes with have a fixed flow rate of 0.5 - 1.0 mL/s. We typically recommend a minimum bolus of 0.5 mL per dilution, meaning 60 boluses would turnover the culture once.&#x20;
  * FynchBio also sells slower pumps that flow at \~1 mL/ min&#x20;
* If we want our culture to double every 3 hours, the pumps will fire every 3 minutes (180 min/ 60 boluses). In a chemostat, nutrient is limiting thus growth rate == dilution rate.
* A doubling time of 3hr has a growth rate of 0.231/hr via the following equation:

$$
gr = ln(2)/doublingTime
$$

Below, we set the script such that the cultures will all have a 3 hour doubling:

```python
    rate_config = [0.231] * 16 #to set all vials to the same value, creates 16-value list
    stir = [8] * 16
    #UNITS of 1/hr, NOT mL/hr, rate = flowrate/volume, so dilution rate ~ growth rate, set to 0 for unused vials
```

If one wanted to set the V0-3 at a doubling time of 3 hours but the rest of the 14 vials with a doubling time of 6 hours, the rate\_config would be set as the following:

```python
rate_config = [0.231,0.231,0.231,0.231,0.46,0.46,0.46,0.46,0.46,0.46,0.46,0.46,0.46,0.46,0.46,0.46]
```

**NOTE** (5/12/2023)**:** There is a bug that does not turn OFF pumps if defined to 0 on rate\_config variable.

### Code for interfacing with eVOLVER GUI

Below is code that grabs values from the GUI and populates it in the code. If you aren't using the GUI, please ignore this portion of the code:

```
if eVOLVER.experiment_params is not None:
    rate_config = list(map(lambda x: x['rate'], eVOLVER.experiment_params['vial_configuration']))
    stir = list(map(lambda x: x['stir'], eVOLVER.experiment_params['vial_configuration']))s
    start_time= list(map(lambda x: x['startTime'], eVOLVER.experiment_params['vial_configuration']))
    start_OD= list(map(lambda x: x['startOD'], eVOLVER.experiment_params['vial_configuration']))
```

### **Rest of the Chemostat Configuration Settings**

```
#Tunable settings for bolus, etc. Unlikely to change between expts
bolus = 0.5 #mL, can be changed with great caution, 0.2 is absolute minimum

##### End of Chemostat Settings #####

flow_rate = eVOLVER.get_flow_rate() #read from calibration file
period_config = [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0] #initialize array
bolus_in_s = [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0] #initialize array

```

**The following parameters initialize variables that will calculate how much time to turn the pumps ON to maintain the flow rate set in `rate_config`**

* **Bolus Size:** The minimum volume that the pumps are allowed to turn on. Please take great caution in tuning this parameter. For example, the \~1 mL/s pumps are sensitive to the bolus size since 0.5 mL would mean the pumps are turning ON for only 0.5 seconds. Lower values could induce variability to the amount pumped. Note: Fynch Bio provides[ slower pumps](https://www.fynchbio.com/accessories/peristaltic-pump-1mlmin-1) that would require this bolus size to be tuned.
* **flow\_rate:** get the calibrated flow rates for each pump
* **period\_config:** how often to pump (seconds)
* **bolus\_in\_s:** how long to pump during a given pump event (seconds)

### Chemostat Pump Commands

When we set vials to a new flow rate in the chemostat function, we see the experiment script send a comma separated pump command. Each pump assigned to the a chemostat gets a command that looks like this:

`1.18|144`

Which is in the format of:

`bolus_in_s|period_config`

If the above pump was influx, its corresponding efflux pump would be `2.36|144` because we pump out double the time to avoid overflows.
