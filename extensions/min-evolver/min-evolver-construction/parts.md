# Parts

## Parts Spreadsheet

Below is a spreadsheet containing all parts required to make a min-eVOLVER.&#x20;

{% hint style="warning" %}
1. Read the notes below the spreadsheet as well.
2. _Don't miss_ the "Consumables / General" tab. These items also need to be acquired before running experiments.
{% endhint %}

{% embed url="https://docs.google.com/spreadsheets/d/1JSuUWUNsro8VO-MzAukn632tOzvQDoVak4M-vvdhMno/edit?usp=sharing" %}

<figure><img src="../../../.gitbook/assets/image (2) (1).png" alt=""><figcaption><p>The parts necessary for the min-eVOLVER main unit. Use the spreadsheet above to discern what each item is. </p></figcaption></figure>

## min-eVOLVER PCB

If you are making a min-eVOLVER Control Board PCB from scratch you have two options (as of 11/20/2024):

1. \[Recommended] Order an assembled PCB from [PCBWay](https://www.pcbway.com/) (guide below) or another manufacturer
2. Buy the parts needed from Digikey, order the [PCB](https://github.com/FYNCH-BIO/hardware/tree/master/min-eVOLVER/min-eV-PCB) from [PCBWay](https://www.pcbway.com/) or another manufacturer, and solder the board yourself
   1. _NOT recommended for anyone not already familiar with surface mount soldering._
   2. An interactive bill of materials (for part placement) can be found [here](https://github.com/FYNCH-BIO/hardware/blob/master/min-eVOLVER/min-eV-PCB/bom/ibom.html). Download it and open it into your browser.

### Ordering an Assembled min-eVOLVER PCB from PCBway

1. Make an account on [PCBWay](https://www.pcbway.com/).
2. On the homepage, scroll down and click on PCB assembly

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

3. Choose the following:
   1. Turnkey, Single pieces, Both sides, fill out the quantity you want, select No "Select PCBway's PCB Order #", uncheck PCB Specifications, and click the green 'Calculate' button.

<figure><img src="../../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

4. Download the following files from [this](https://github.com/FYNCH-BIO/hardware/tree/master/min-eVOLVER/min-eV-PCB/PCBway-order) folder, upload to PCBway, and click "Submit the File Now":
   1. Gerber files: [min-eV-gerbers\_240731.zip](https://github.com/FYNCH-BIO/hardware/blob/master/min-eVOLVER/min-eV-PCB/PCBway-order/min-eV-gerbers_240731.zip)
   2. Parts List (BOM): [BOM\_PCBWay.xlsx](https://github.com/FYNCH-BIO/hardware/blob/master/min-eVOLVER/min-eV-PCB/PCBway-order/BOM_PCBWay.xlsx)
   3. Centroid File: [PCBWAY-min-eV-positions-centroid.csv](https://github.com/FYNCH-BIO/hardware/blob/master/min-eVOLVER/min-eV-PCB/PCBway-order/PCBWAY-min-eV-positions-centroid.csv)

<figure><img src="../../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

5. Wait for PCBway to review your order (1-2 business days) before paying

## Pump PCB

Should be ordered from [PCBWay](https://www.pcbway.com/) or another manufacturer. You can find the .zip of the gerber files [here](https://github.com/FYNCH-BIO/hardware/blob/master/min-eVOLVER/pump-PCB/gerbers/pump_board-gerbers.zip). Assembly is not needed.

## min-eVOLVER Case

Options:

1. We use [Protocase](https://www.protocase.com/) to manufacture the cases
   1. Request a quote for the number of cases you require by emailing Jenn Hurd  (jhurd@protocase.com)
   2. Mention you want to order the previously ordered name and number below:
      1. Boston University min-eV Case Rev2.1 T120324039-205634-1
2. For other manufacturers, give them the .x\_t, .easm, and .step files found [here](https://github.com/FYNCH-BIO/hardware/tree/master/min-eVOLVER/case)
   1. Request sheet metal construction out of 18 gauge steel, ideally a powder coated exterior

## 12V Power Supply

Several 12V power supplies were tested and were selected for reliability and low noise. While most 12V power supplies should work well in the short term, long term usage may vary. Use a different power supply at your own risk.

## Vial Cover

NOT AN OPTIONAL COMPONENT - Protects OD photodiodes from environmental light, which will completely change your OD calibrations. Also protects smart sleeves from spills and splashes.

3D print the latest vial cover to allow for more consistent OD readings. Choose the cheapest _black FDM_ printing on hubs.com, shapeways.com, or a local 3D printing shop and give them the .stl file in the github repository.

## eVOLVER Smart Sleeves

May be purchased from Fynch Bio. If interested in making your own see the main [parts sheet](../../../getting-started/part-sourcing.md) and follow [this](../../../guides/building-a-smart-sleeve.md) assembly guide. This is not recommended for its added complication (you will need to machine the aluminum tube for example), but will save money.

## Consumables / General

Listed in the "Consumables / General" sheet of the above spreadsheet

* Anything not listed as (Optional) is required for a full experiment.
* You need a thermometer for calibrating temperature - we suggest [this](https://www.fishersci.com/shop/products/fisher-scientific-traceable-hi-accuracy-refrigerator-thermometer-5/15078177) one.
* If you plan to run multiple min-eVOLVERs from a computer, you will need to have a USB port available for each one. You can use a USB splitter dongle to accomplish this. Example [here](https://www.amazon.com/Anker-Extended-MacBook-Surface-Notebook/dp/B07L32B9C2/ref=sr_1_5?crid=2RU3G7JIJJ7RM\&keywords=usb%2Bsplitter\&qid=1700599207\&s=electronics\&sprefix=usb%2Bsplitter%2Celectronics%2C70\&sr=1-5\&th=1).
