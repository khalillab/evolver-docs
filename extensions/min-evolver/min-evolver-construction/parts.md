# Parts

## Requirements for Construction

1. Soldering iron + solder  - pumps will need to be soldered in place
2. Ability to through-hole solder
   1. Can be self-taught quickly through YouTube videos
3. Screw drivers
   1. Phillips #1 (short handle)
   2. Flat head #1.5 or smaller

## Parts Spreadsheet

Below is a spreadsheet containing all parts required to make a min-eVOLVER.&#x20;

{% hint style="warning" %}
1. Read the notes below the spreadsheet as well.
2. _Don't miss_ the "Consumables / General" tab. These items also need to be acquired before running experiments.
{% endhint %}

{% embed url="https://docs.google.com/spreadsheets/d/1JSuUWUNsro8VO-MzAukn632tOzvQDoVak4M-vvdhMno/edit?usp=sharing" %}

<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption><p>The parts necessary for the min-eVOLVER main unit. Use the spreadsheet above to discern what each item is. </p></figcaption></figure>

## min-eVOLVER PCB

If you are making a min-eVOLVER Control Board PCB from scratch you have two options (as of 10/24/2023):

1. Buy the parts needed from Digikey and order the PCB from [PCBWay](https://www.pcbway.com/) or another manufacturer
2. Order an assembled PCB from [PCBWay](https://www.pcbway.com/) or another manufacturer

_Option 2 is NOT recommended for anyone not already familiar with surface mount soldering._

The PCBWay bill of materials (BOM) can be found in the third tab of the above spreadsheet.

You can find the gerber files [here](https://github.com/FYNCH-BIO/hardware/tree/master/Accessories/min-evolver/min-eV-PCB/gerbers).

## Pump PCB

Should be ordered from [PCBWay](https://www.pcbway.com/) or another manufacturer. You can find the gerber files [here](https://github.com/FYNCH-BIO/hardware/tree/master/Accessories/min-evolver/pump-PCB/gerbers).

## 12V Power Supply

Several 12V power supplies were tested and were selected for reliability and low noise. While most 12V power supplies should work well in the short term, long term usage may vary. Use a different power supply at your own risk.

## Tube Holder

{% hint style="warning" %}
(As of 10/24/2023) If you ordered your vials from Fynch, they will come with a 3D printed tube holder that does not have defined OD LED and photodiode positions. It is highly recommended that you instead print the latest (as of writing v5.1.1) tube holder to allow for more consistent OD readings. Choose the cheapest _black FDM_ printing on hubs.com, shapeways.com, or a local 3D printing shop and give them the .stl file in the github [repository](https://github.com/FYNCH-BIO/hardware/blob/master/Smart%20Sleeve/tube-holder/Tube%20Holder\_V5.1.1.STL).
{% endhint %}

## Vial Cover

NOT AN OPTIONAL COMPONENT - Protects OD photodiodes from environmental light, which will completely change your OD calibrations. Also protects smart sleeves from spills and splashes.

3D print the latest vial cover to allow for more consistent OD readings. Choose the cheapest _black FDM_ printing on hubs.com, shapeways.com, or a local 3D printing shop and give them the .stl file in the github repository.

## eVOLVER Smart Sleeves

May be purchased from Fynch Bio. If interested in making your own see the main [parts sheet](../../../getting-started/part-sourcing.md) and follow [this](../../../guides/building-a-smart-sleeve.md) guide. This is not recommended for its added complication, but will save money.

## Consumables / General

Listed in the "Consumables / General" sheet of the above spreadsheet

* Anything not listed as (Optional) is required for a full experiment.
* You need a thermometer for calibrating temperature, we have suggested the one we use.
