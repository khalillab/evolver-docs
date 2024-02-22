# Adding A New Experimental Parameter

## 0. Design questions before you start

### Does the new experimental parameter require sensing, actuation, or both?

#### Examples

* Sensing only: optical sensor (photodiode, phototransistor) for new spectra, pH sensor
* Actuation only: optical stimulation w/ new LED
* Both: fluorescence measurements (LED/optical sensor pair), feedback driven optical stimulation

### Additional Questions

* Can new hardware be fitted onto vial?
  * Hardware CAD files can be found [here](https://github.com/FYNCH-BIO/hardware).
* Can the eVOLVER provide necessary power to control actuator?
  * The base eVOLVER can provide 5V or 12V [PWM](https://en.wikipedia.org/wiki/Pulse-width\_modulation) signal to the vials.
  * Otherwise, look into changing the [power supply](power-supply.md).
* Is the signal you are sensing strong enough to be sensed using the components you will use?

The best way to answer these questions is to go through the datasheets of components you are interested in integrating and breadboarding with the eVOLVER Motherboard. This will help you also establish and tune dynamic ranges for new sensing capabilities. Additionally, you can explore swapping in new power supplies for components with higher power consumption specs. Once you've established compatibility and feasibility, you can begin integrating a new experimental parameter for eVOLVER.

## Low Level (Hardware/Arduino)

### 1. Add appropriate boards (PWM/ADC) to SA slots in eVOLVER Motherboard.

* Each Arduino is connected to 2 SA slots so that culture parameters that require sensing/actuation can share data, but Arduino is still capable of controlling each SA slot individually.
* If parameter requires only sensing or actuation, then its best to pair with parameters that also require sensing or actuation (i.e. stir) for efficient usage of Arduinos
* If the experimental parameter is sensing a culture condition, plug in a ADC Board
* If the experimental parameter is applying a stimulus to the culture, plug in a PWM Board

### 2. Program Arduino to collect serial data and/or regulate actuators.

* All Arduinos communicate with Raspberry Pi along same serial line and either look for tags/add tags associated with the parameter they’re responsible for controlling
* GitHub [repo](https://github.com/FYNCH-BIO/evolver-arduino) and wiki [docs](../../software/arduino.md) more information regarding how to program Arduinos

### 3. Add new hardware components to Smart Sleeve

* Smart Sleeve 3D printed housing may need to be redesigned to fit components
* Solder component leads to correct Component Mount Board (CMB) pins, which is set by slot position of SA slot(s)
  * E.g. If using SA slot 8, make sure that components leads are wired to position 8 on CMB

### High Level (Server/DPU)

### 4. Add experimental parameter to eVOLVER server configuration file (conf.yml) with relevant configurations

* If parameter is for actuating, 'fields\_outgoing' set to 17 (see example below):

```
  temp:
    recurring: true
    fields_expected_outgoing: 17
    fields_expected_incoming: 17
    value: ['4095', '4095', '4095', '4095', '4095', '4095', '4095', '4095', '4095', '4095', '4095', '4095', '4095', '4095', '4095', '4095']
```

* If parameter is for sensing, fields\_outgoing set to 2 (see example below):

```
experimental_params:
  od_90:
    recurring: true
    fields_expected_outgoing: 2
    fields_expected_incoming: 17
    value: '1000'
```

### 5. Adjust DPU software to take advantage of new experimental parameter in continuous culture algorithms

* [DPU section](../../software/dpu-code-structure/) of wiki goes in more depth on how to create culture control algorthms
* Basically, you need to create a new method in the `EvolverNamespace class`, which can be called in your custom control code
* Example below using default stir parameter:

```python
def update_stir_rate(self, stir_rates, immediate = False):    
    data = {'param': 'stir', 'value': stir_rates, 
    'immediate': immediate, 'recurring': True}    
    logger.debug('stir rate command: %s' % data)    
    self.emit('command', data, namespace = '/dpu-evolver')
```



{% hint style="info" %}
Make sure that the name you are using for the experimental parameter is consistent throughout this process. eVOLVER will pull a list of experimental parameters from the conf.yml to sort through incoming serial data and tag outgoing serial commands. Inconsistencies with naming will lead to issues later on!
{% endhint %}
