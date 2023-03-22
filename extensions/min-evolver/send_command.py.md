# send\_command.py

## About

Used to send arbitrary commands to a server outside of both the GUI and an experiment.&#x20;

Useful for:

1. Controlling the [min-eVOLVER](./)
2. Sending custom commands if you have [added an experimental parameter](../adding-an-experimental-parameter/)
3. Sending pump commands greater than 20 seconds if you are using the slow (\~1mL/min) pumps or using [IPPs](../../hardware/overview-of-millifluidics/ipps-integrated-peristaltic-pumps.md)

## Usage

{% hint style="warning" %}
You must

1. Start the [server](software-setup.md#server-startup) before using send\_command.py, otherwise commands will not go through.
2. In another terminal window, enter into the `dpu` virtual environment&#x20;
{% endhint %}

```
python3 send_command.py <port> <parameter> <value>
```

The 'port' variable tells the program which eVOLVER to connect to. This is designated in the conf.yml file of the eVOLVER under 'port'. It is arbitrary, but we can choose something like 5555

To set a parameter on all vials to one value: python3 `send_command.py`

```
For example, to turn stirring ON:
python3 send_command.py 5555 stir 11

For example, to turn stirring OFF:
python3 send_command.py 5555 stir 0

For example, to turn temperature OFF:
python3 send_command.py 5555 temp 64000
```

To run specific pumps (where s is a number of seconds):&#x20;

* `python3 send_command.py pump s,s,s,s,s,s`

For example:

```
python3 send_command.py 5555 pump 0,0,0,0,5,5
```

To set a non-pump parameter on specific vials:

`python3 send_command.py <port> <parameter> <list_of_values>`

```
For example:
python3 send_command.py 5555 temp 30000,31000
```
