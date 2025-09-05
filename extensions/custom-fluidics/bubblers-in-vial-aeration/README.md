# Bubblers / In-Vial Aeration

_**Please cite Daniel Hart's paper when it comes out!**_

## Overview

An in-vial aerator, which can be hooked up to a gas stream of your choice. Normal stir bar-based mixing in the eVOLVER does not provide enough gas exchange in many situations. These bubblers produce small bubbles that greatly increase gas exchange.

<figure><img src="../../../.gitbook/assets/image (53).png" alt="" width="375"><figcaption><p>Bubbler (right) epoxied in to universal cap. Efflux tube (left) is above bubbler.</p></figcaption></figure>

## Requirements

### Cap with Nylon Tubing

Allows the nylon tube of the bubbler to slot into cap. See [here](../../../hardware/vial-caps/) for options.

### Long Stir Bars

The normal eVOLVER stir bars allow large bubbles to adhere if you are bubbling. This creates lots of noise in OD readings. It is therefore necessary to use thinner stir bars that don't allow such large bubbles to stick to them. We have found these to be the only ones that work with bubbling: [Length 20 mm, Diameter 3 mm (# SBM-2003-MIC)](https://www.stirbars.com/list.php?category=Stir%20Bars\&subCat=Micro%20PTFE\&sessionID=eel7i7mvvdo1r965d2dp0e6le0).

#### Long Stir Bar Jittering and Low Stir Stability

These stir bars are unfortunately prone to jitter and not stir. This is a function of at least the following:

1. Distance to magnets on the fan used for stirring
   1. The newest eVOLVERs have a bigger distance to the fan because of the 3D printed magnet holder and 1/4" acrylic spacers
   2. Try ordering thinner acrylic spacers&#x20;
2. Shape and smoothness of the glass vial bottom - try several glass vials and see if there is

Please let us know on the forum if you find other stir bars that work with bubbling. However, several people have looked and not found any.

### Stop Stir During OD Reads

While bubbling, you must stop stirring while taking OD readings to allow bubbles to float to the surface. Otherwise, bubbles will create too much variability in OD readings and make your OD calibration useless.

#### During OD Calibration

While calibrating OD, we mimic experimental OD readings as much as possible. To do this:

1. Turn off stirring via the GUI
2. Calibrate with long stir bars (see above) and caps with bubblers
3. Swirl OD standards at least every other time you move them to avoid cell sedimentation

#### During Experiments

Load a conf.yml onto the server that pauses stir whenever an OD measurement is taken

1. Guide [here](../../../guides/change-your-conf.yml-file.md) | example stir pause conf.yml file [here](https://github.com/FYNCH-BIO/evolver/blob/master/evolver/alternate_conf_files/stir_pause_for_OD_reads/conf.yml)
2. This decreases data acquisition rate (20 seconds to 60 seconds), but greatly increases OD accuracy

## Considerations

### Variability Between Bubblers

The assumption is that there will be variability between the bubblers that you make -- even though you will screen them before putting them in a vial cap! This is compensated for by bubbling _much more_ than we need for a given microbe's gas consumption needs. Worse bubblers will not be a problem if the worst bubbler you have provides more than enough gas exchange.

### Biofilming

Aerators are great substrates for biofilming. If your strain biofilms, make sure you swap in new bubblers when bubbles noticeably diminish. See [Cleaning Protocol](./#cleaning-protocol).

{% hint style="info" %}
Because of biofilming, it is useful to have another set of caps/bubblers that can be swapped in without interrupting your experiment. Ideally, you would pre-autoclave these and keep them sterile in aluminum foil. Pause the experiment, check if the vials need to be changed because of biofilm and swap sterile caps and/or vials in.
{% endhint %}

### Media Type Affects Bubble Size

Bubblers will produce different sized bubbles depending on media type. This is related to the amount of salts, proteins, carbohydrates, etc that are in the media. These can act as surfactants to create smaller bubbles. Therefore, largest bubbles will be in water and smallest bubbles will be in rich media, as can be seen below:

\<Add picture of bubbler in water vs algae media vs LB>
