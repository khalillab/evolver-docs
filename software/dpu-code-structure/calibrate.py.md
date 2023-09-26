# calibrate.py

## Advanced Users Only

Mostly deprecated

Use GUI for calibrations in most cases

### Run calibration code (after the raw values have been logged on the eVOLVER)

The GUI will run calibrations automatically upon completion of the calibration protocols. However, you can still manually run a calibration if you would like to change calibration settings.

#### List raw calibration files on eVOLVER

**Mac**

```sh
python calibration/calibrate.py -a <ip_address> -g
```

For Windows, use py instead of python for all commands.

#### Calibrate Temperature

```sh
python calibration/calibrate.py -a <ip_address> -n <file_name> -t linear -f <name_after_fit> -p temp
```

#### List raw OD JSON files logged on evolver

**OD135**

```sh
python calibration/calibrate.py -a <ip_address> -n <file_name> -t sigmoid -f <name_after_fit> -p od_135
```

**OD90 (Check to ensure mode is configured properly)**

```sh
python calibration/calibrate.py -a <ip_address> -n <file_name> -t sigmoid -f <name_after_fit> -p od_90
```

**3D FIT (Check to ensure mode is configured properly)**

```sh
python calibration/calibrate.py -a <ip_address> -n <file_name> -t 3d -f <name_after_fit> -p od_90,od_135

```
