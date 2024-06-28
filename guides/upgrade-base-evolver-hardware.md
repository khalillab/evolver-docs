# Upgrade Base eVOLVER Hardware

## \[Strongly Recommended] Better 3D Printed Vial Holder

{% hint style="warning" %}
Warning: you will need to recalibrate both OD and temperature after swapping in the new part
{% endhint %}

#### Info

If your eVOLVER is stock from Fynch, then you do not have the upgraded part (as of April 2024).

Download the latest version [here](https://github.com/FYNCH-BIO/hardware/tree/master/Smart%20Sleeve/tube-holder). Compare to the version online [here](https://github.com/FYNCH-BIO/hardware/blob/master/Smart%20Sleeve/tube-holder/Tube%20Holder\_V5.2.STL) to determine which version you have.

#### Benefits

* \[Versions >= 5.1.1] More consistent OD calibration
  * You can tell if you have this part by pulling out the OD LED or photodiode from your vial holder and seeing if there is a smaller circle of plastic inside the hole
    * If there is simply a flat area on the bottom of the hole, you have an older version
  * Because of variation in depth of photodiode and OD LED. See [here](https://www.evolver.bio/t/how-deeply-the-photodiode-and-ir-led-are-pushed-in-to-the-vial-greatly-affects-od-readings/360)
  * Otherwise you will have vials with poor calibrations
* \[Versions >= 5.2] More resistant to overflow
  * You can tell if you have this part because there are triangle-shapes around the screws holding the Smart Sleeve together.&#x20;
  * On the old 3D printed part (v5.1.1 and below), overflows could easily short the heating resistors
  * The latest version has cutaways to prevent this

#### Guide

1. Print out your vial holder by downloading the latest version [here](https://github.com/FYNCH-BIO/hardware/tree/master/Smart%20Sleeve/tube-holder)
   1. Send the .stl file to a manufacturer (such as hubs.com) and choose FDM printing
   2. Choose black plastic (optics change otherwise)
2. Remove any extra plastic in the photodiode and LED holes
3. Use [this](building-a-smart-sleeve.md) guide to help you rebuild your Smart Sleeve with the new vial holder
4. Make sure to _firmly_ push the OD LED and photodiodes all the way in (see figure below)
5. [Recalibrate](../getting-started/calibrations/) temperature and OD

<figure><img src="../.gitbook/assets/image (64).png" alt=""><figcaption><p>OD LED (A) and photodiode (B) depth into the 3D printed smart sleeve holder. (C) View inside the aluminum tube -- neither LED nor photodiode poke all the way into the aluminum tube.</p></figcaption></figure>

## Stronger Stirring

More stirring leads to better aeration and thus better growth in many cases. Try this stir bar for more vigorous stirring: [Length 20 mm, Diameter 3 mm (# SBM-2003-MIC)](https://www.stirbars.com/list.php?category=Stir%20Bars\&subCat=Micro%20PTFE\&sessionID=eel7i7mvvdo1r965d2dp0e6le0).

Try different stir speeds to see if you can get stable and intense stirring.
