# send\_command.py

## About

Used to send arbitrary commands to a server outside of both the GUI and an experiment.&#x20;

Useful for:

1. Controlling the [min-eVOLVER](./)
2. Sending custom commands if you have [added an experimental parameter](https://app.gitbook.com/o/mbob5Ih2vV4dHZ3RRJui/s/Yy5AdmKzUTn7D8n357Md/\~/changes/85/extensions/adding-new-experimental-parameter)
3. Sending pump commands greater than 20 seconds if you are using the slow (\~1mL/min) pumps or using [IPPs](../../hardware/overview-of-millifluidics/ipps-integrated-peristaltic-pumps.md)

## Usage

{% hint style="warning" %}
You must

1. Start the [server](software-installation-and-startup.md#server-startup) before using send\_command.py, otherwise commands will not go through.
2. In another terminal window, enter into the `dpu` virtual environment and navigate to the folder send\_command.py is in: `/dpu/experiment/`
{% endhint %}

### Send a Command

```
python3 send_command.py <port> <parameter> <value>
```

The `<port>` variable tells the program which eVOLVER to connect to

1. This is designated in the conf.yml file of the eVOLVER under `'port'`
2. It is arbitrary, but we can choose something like 5555

### Commands in the Server Log

When you send a command, you should see it come up in the window you're running the server in. See [here](../../software/server-raspberry-pi/#server-serial-communication) for more information about the eVOLVER server and commands.

#### Annotated Server Log as a Command Comes in

```
Connected dpu as server    # Connection to the send_command.py script
Received COMMAND           # Command received the send_command.py script
stiri,0,0,_!               # Stir command, each vial is turned off
Disconnected dpu as Server
stire,0,0,end              # Response from the min-eVOLVER board. It got the command 
stira,,,_!                 # The server tells the min-eV board it can run the command
```

## Examples

#### To set a parameter on all vials to one value: python3 `send_command.py`

```
For example, to turn stirring ON:
python3 send_command.py 5555 stir 11

Stirring OFF:
python3 send_command.py 5555 stir 0

Temperature OFF:
python3 send_command.py 5555 temp 64000
```

#### To run specific pumps (where s is a number of seconds):&#x20;

`python3 send_command.py 5555 pump s,s,s,s,s,s`

For example:

`python3 send_command.py 5555 pump 0,0,0,0,5,5`

#### To set a non-pump parameter on specific vials:

`python3 send_command.py <port> <parameter> <list_of_values>`

For example:

`python3 send_command.py 5555 temp 30000,31000`
