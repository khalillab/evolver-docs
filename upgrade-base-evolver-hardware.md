# Upgrade Base eVOLVER Hardware

## Vial Cap Upgrades

{% hint style="info" %}
As of 25/01/15, FynchBio gives the cap that only accommodates needles. This cap does not have a tight seal on the vial and thus does not enable emergency efflux.
{% endhint %}

### Benefits / Options

1. Better seal to vial - enables emergency efflux (see below) away from vial if too much is pumped in
2. More ports available
3. Reusable connectors - can use luer connectors to connect to eVOLVER tubing

See [here](hardware/vial-caps/) for more information and construction protocols.

## Emergency Efflux

Protect your eVOLVER hardware with a sealed vial and additional efflux line dedicated to preventing vial overflows.

Guide [here](guides/emergency-efflux.md).

## Bubbling

Many organisms require additional gas exchange outside of what eVOLVER stirring can provide. Others require custom gas mixes for growth. In-vial bubblers provide this.

Guide [here](extensions/custom-fluidics/bubblers-in-vial-aeration/). _Please cite Daniel Hart's paper when it comes out!_

## Stop Stir While Taking OD

This is a measure that is _necessary_ if you are bubbling, but can improve OD in general by decreasing noise.

To do this, [swap](guides/change-your-conf.yml-file.md) in a conf.yml with stir stopped for OD reads. Example conf.yml [here](https://github.com/FYNCH-BIO/evolver/tree/master/evolver/alternate_conf_files/stir_pause_for_OD_reads).

{% hint style="warning" %}
_You will need to calibrate OD with stir off._

1. It is recommended to switch to the normal conf.yml with 20 second broadcast\_timing for calibration to receive data more quickly. During experiment, switch back to the stir stopping conf.yml
2. Swirl the vials when moving standards to make sure cells do not settle.
{% endhint %}
