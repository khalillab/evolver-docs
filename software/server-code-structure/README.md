---
description: Description of how the Raspberry Pi eVOLVER server code functions.
---

# Server Code Structure

This page aims to explain how the server on the Raspberry Pi functions. The repository can be found on [Github](https://github.com/FYNCH-BIO/dpu).

## General Information

The server acts as the brain for the physical eVOLVER unit - it manages all of the SAMD21 Arduino microcontrollers and communications from the user via the DPU or GUI interface.

In addition to managing communications between connected components and the user, it also stores and manages configuration and calibration data for a given eVOLVER. The RPi also can have other utilities run on it such as this [monitor script](https://github.com/FYNCH-BIO/evolver/blob/master/utils/server\_monitor.sh), which can detect if the server gets hung up and restart it.

## File Explanations

### evolver.py and evolver\_server.py

The two main python scripts for the server are `evolver.py` and `evolver_server.py`. The first, `evolver.py` sets up the websockets server and get it running in it's own background thread so that in the main thread the server can communicate with the SAMD21 micro controllers continuously and send off data as needed. The main logic of the server lives in `evolver_server.py`.

The timing of broadcasts is handled in `evolver.py`, while all subsequent logic is handled in `evolver_server.py`.

### conf.yml

The server uses this file to notate what kinds of experimental parameters are connected, how they should be used, and configurations for running the server itself.

Read more about this file [here](configuration-files-conf.yml.md).

{% hint style="danger" %}
You can modify this file manually (it is meant to be human readable), but be careful not to break the structure or the server will not run.&#x20;
{% endhint %}

### calibrations.json

This file contains all calibrations for the eVOLVER. Calibrations have a generalized format, so theoretically you can calibrate any number or types of parameters and have the downstream DPU or GUI be able to fetch and use them.

The file is a list of dictionaries. Each item has a name, measured data (the values collected from a platereader or thermometer for example), the calibration type, and a key-value pair for raw and fits. Raw and fits both contain lists of raw data collection and fits, respectively. Fits has an element called coefficients which contains the fit parameters for whatever function was used, as well as the params that it needs.

The schema can be found on [Github](https://github.com/FYNCH-BIO/evolver/blob/master/cal\_schema.json). To read more about the file, read [here](broken-reference).

{% hint style="info" %}
Don't confuse this file with `calibration.json` - this is a legacy file that will be phased out soon.
{% endhint %}

## Server Serial Communication

{% hint style="info" %}
Check [this](../../guides/view-the-server-log-and-restart-server.md) guide to view the serial communications in real time. This is a useful troubleshooting tool.
{% endhint %}

### Serial Message Structure

The RPi communicates to and from the SAMD21 microcontrollers via serial. The structure of the message :

`<ADDRESS><MESSAGE_TYPE>,<VALUES>,<END_CHARACTER>`

`<ADDRESS>` is the address or name of the SAMD21. It allows all of the connected microcontrollers to decide if the message is for them.

`<MESSAGE_TYPE>` is typically a single character designating how the message should be handled.

**r:** recurring message - sent every broadcast iteration on the RPi to ensure that the correct values are being maintained by the SAMD21 microcontrollers.

**i:** immediate command - sent when a one-off command is to be executed. Functionally handled the same on the SAMD21 microcontrollers. The server will not re-send these commands in a recurring manner (useful for something like a pump event).

**e:** echo response - Sent from the SAMD21 to the RPi as a way to acknowledge receipt of a command or message. The values should match what the server sent.

**b:** data response for broadcast - Sent from thhe SAMD21 to the RPi as a response to getting a recurring or immediate command if the SAMD21 has data to report (temp, OD). Values will contain raw ADC values typically.

**a:** acknowledge response - Sent from the RPi to the SAMD21, signalling that it has registered success of serial communications and signalling whatever previous command was sent to be executed.&#x20;

`<VALUES>` is a comma separated list of values either being sent to the SAMD21 as inputs to set an experimental condition level, or as raw ADC values from the SAMD21 to the RPi.

`<END_CHARACTER>` is a way to denote the end of the message. For messages going **to** the SAMD21 **from** the RPi, this will be `_!`. For messages going **to** the RPi **from** the SAMD21, this will be `end`.

### Serial Communications Process

We use a communication structure similar to the [TCP 3-way handshake](https://en.wikipedia.org/wiki/Handshaking).&#x20;

1. The RPi will first send a message to the SAMD21 containing the desired values to be set (`<MESSAGE_TYPE>` of i, or r).&#x20;
2. The SAMD21 then needs to respond with a `<MESSAGE_TYPE>` or b or e.&#x20;
3. The RPi will respond with a `<MESSAGE_TYPE>` of a (for acknowledge). When the SAMD21 receives this message it will execute the command from step 1.

This process is used in order for the server to have a way to know if commands are successfully being sent to the desired SAMD21. For each response from the SAMD21, the lengths of the `<VALUES>` is checked to be consistent with what is in the server configuration file. The server also checks that messages it sends out conform to the proper length. If any anomalies or problems are detected, an `EvolverSerialError` is thrown.

{% hint style="warning" %}
Failed commands will be communicated back to the DPU via websockets in a future version.
{% endhint %}

### Example Annotated Server Logs as a Command Comes in

#### Recurring od\_90 Command Set in the conf.yml File

```
# Recurring (i) od_90 command, requesting average of 500 values for each Smart Sleeve:
od_90r,500,_!

# Broadcast (b) data response from the SAMD21
od_90b,53722,48267,50671,41662,62813,63373,60965,60209,50271,49000,51695,56800,61598,62685,60486,62862,end

# Acknowledge (a) the server tells the SAMD21 Arduino board it received the data
od_90a,,_!
```

#### Immediate Stir Off Command from the DPU

```
Connected dpu as server                    # Connection to the DPU (GUI or experiment script)
Received COMMAND                           # The following command was from the DPU (not conf.yml)
stiri,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,_!   # Immediate (i) stir command, each vial is turned off
Disconnected dpu as Server                 # DPU disconnects after its job is done
stire,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,end  # Echoed (e) response from the SAMD21 Arduino board. It got the command 
stira,,,,,,,,,,,,,,,,,_!                   # Acknowledge (a) the server tells the SAMD21 Arduino board it can execute the command
```

## Websockets Communications

The eVOLVER server uses websockets via [socketio](https://python-socketio.readthedocs.io/en/latest/index.html) to communicate with the DPU and GUI interfaces. Please see their documentation for more information on how websockets work. In brief, functions in the server are decorated with

```
@sio.on('<event_name>', namespace = '/dpu-evolver')
```

to indicate that the function should be run when a given event occurs over the websocket. The function definition itself also needs the `async` keyword in front of it (asyncronous).

To send out messages to connected clients (DPU/GUI), the server uses a `socketio.AsyncServer` object `sio`. For example, to send data to the clients:

```
await sio.emit('commandbroadcast', data, namesapce = '/dpu-evolver')
```

where data is a dictionary (json) containing the data to send. Note that any function that calls the `emit` function needs to have the keyword `async` in it's definition. This also propogates up to all functions that call that function as well.

{% hint style="info" %}
Be careful with the async/await keywords - read up on the [socketio documentation](https://python-socketio.readthedocs.io/en/latest/index.html) if you want to write your own custom communication events. Improper usage of these keywords and functions can cause the server to hang up or not run at all.
{% endhint %}

## Relevant information

[View server log and restart server](../../guides/view-the-server-log-and-restart-server.md)

[How to update the server](../../guides/updating-the-evolver-server.md)

[Raspberry Pi hardware page](../../hardware/raspberry-pi.md)

[Server troubleshooting](../../troubleshooting/server-troubleshooting.md)
