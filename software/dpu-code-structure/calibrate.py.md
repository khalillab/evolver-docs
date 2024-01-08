# calibrate.py

{% hint style="warning" %}
**Advanced Users Only**:

Currently called by the GUI

Use GUI for calibrations in most cases
{% endhint %}

## About

The GUI will run calibrations automatically upon completion of the calibration protocols. However, you can still manually run a calibration if you would like to change calibration settings. Can be useful if your GUI calibration fails for some reason.

## Requirements

1. You have run calibration and logged raw values already
2. You are in your DPU virtual environment in command line. This is set up when you [install ](../../getting-started/software-installation/dpu-installation.md)the DPU.

## Commands

#### List raw calibration files on eVOLVER

**Mac**

```sh
python3 calibration/calibrate.py -a <ip_address> -g
```

For Windows, use py instead of python for all commands.

#### Calibrate Temperature

```sh
python3 calibration/calibrate.py -a <ip_address> -n <file_name> -t linear -f <name_after_fit> -p temp
```

#### List raw OD JSON files logged on evolver

**OD135**

```sh
python3 calibration/calibrate.py -a <ip_address> -n <file_name> -t sigmoid -f <name_after_fit> -p od_135
```

**OD90 (Check to ensure mode is configured properly)**

```sh
python3 calibration/calibrate.py -a <ip_address> -n <file_name> -t sigmoid -f <name_after_fit> -p od_90
```

**3D FIT (Check to ensure mode is configured properly)**

```sh
python3 calibration/calibrate.py -a <ip_address> -n <file_name> -t 3d -f <name_after_fit> -p od_90,od_135

```
