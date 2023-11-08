# Configuration Files (conf.yml)

{% embed url="https://github.com/FYNCH-BIO/evolver/blob/master/evolver/conf.yml" %}

## Summary

This is the configuration file for the eVOLVER server. The server uses this file to notate what kinds of experimental parameters are connected, how they should be used, and configurations for running the server itself.

It is a YAML file. YAML is a "_human-friendly, cross language, Unicode based data serialization language designed around the common native data types of dynamic programming languages_". You can read more about YAML [here](https://yaml.org/spec/1.2.2/).

## Parameter Explanations

{% embed url="https://docs.google.com/spreadsheets/d/1yUO_DxTS0hi0ieF49wMkXmHYaZIrrflN_vwyP01K5V0/edit?usp=sharing" %}

## Other Parameters in conf.yml

### `broadcast_timing` (in seconds)

How often the server will cycle (run through all of parameters in its list)

## Customizing conf.yml

{% hint style="danger" %}
Edit the conf.yml file at your own risk. It is made to be human-readable, but small changes in the formatting will cause the server not to run.
{% endhint %}

#### Adding 'wait' commands or increasing number of parameters greatly

If you use 'wait' commands (see below) or add many commands for the server to run through, you will need to increase the `broadcast_timing` or the server will not finish its cycle before starting a new one. This will cause your last few commands to be never run.

## Advanced conf.yml: Subcommands

{% hint style="info" %}
More complex conf.yml files including 'pre' and 'post' commands are complicated to repeatedly alter, so storing them allows easy switching to files for different purposes.
{% endhint %}

subcommand = a command added to the command queue when another command is run

An example subcommand:

```
- param: 'od_led'
  value: ['0', '0', '0', '0', '0', '0', '0', '0', '0', '0', '0', '0', '0', '0', '0', '0']
```

'pre' or 'post' command = a list of subcommands to be added to the command queue before or after the main parameter command

'values' = a keyword referencing the current value of a parameter in the conf file (for example, the subcommand)

```
- param: 'temp'
  value: 'values'
```

'wait' = a special type of subcommand that makes the server pause for that many seconds (for example so that a command can execute)

```
- param: 'wait'
  value: 15
```

### Examples of potential alternate conf files

* Calibration conf - (default conf) broadcast\_timing parameter should be low to speed up calibration
* stir\_pause\_on\_od - prevents stirring from affecting OD. Important if bubbling or in low volume applications
* odled\_normally\_off - OD LED will be normally off unless OD is read to prevent the IR light affecting other light sensors
