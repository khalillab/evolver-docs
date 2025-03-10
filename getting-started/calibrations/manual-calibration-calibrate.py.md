# Manual Calibration - calibrate.py

{% hint style="info" %}
You can use manual calibration to view past calibrations after they are done. This can be useful for troubleshooting if a vial is not behaving as expected.
{% endhint %}

## About

The GUI will run calibrations automatically upon completion of the calibration protocols. However, you can still manually run a calibration if you would like to change calibration settings. Can be useful if your GUI calibration fails for some reason.

Located in [/dpu/calibration/](https://github.com/FYNCH-BIO/dpu/tree/master/calibration).

## Requirements

1. You have run calibration and logged raw values already
2. You are in your DPU virtual environment in command line. This is set up when you [install ](../software-installation/dpu-installation.md)the DPU.

## Commands

### List raw calibration files on the eVOLVER

**Mac**

```sh
python3 calibration/calibrate.py -a <ip_address> -g
```

For Windows, use py instead of python for all commands.

### Calibrate Temperature

```sh
python3 calibration/calibrate.py -a <ip_address> -n <file_name> -t linear -f <name_after_fit> -p temp
```

### Calibrate OD

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

## Example Procedure to Plot OD90 After Calibration

1. Navigate to the dpu environment in terminal
   1. `cd <your_dpu_address>`
2. Put in the following command to get the exact name of your calibration file
   1. `python3 calibration/calibrate.py -a <ip_address> -g`
3. Do the following command, replacing ip\_address, file\_name, name\_after\_fit:
   1. `python3 calibration/calibrate.py -a <ip_address> -n <file_name> -t sigmoid -f <name_after_fit> -p od_90`
4. Close out of the python file and say no to updating the eVOLVER with new calibration
