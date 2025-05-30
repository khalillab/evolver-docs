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

Guide [here](extensions/custom-fluidics/bubblers-in-vial-aeration/).

## Stop Stir While Taking OD

This is a measure that is _necessary_ if you are bubbling, but can improve OD in general by decreasing noise.

To do this, swap in a [conf.yml](guides/change-your-conf.yml-file.md) with stir stopping.

_You will need to calibrate with stir off._ Swirl the vials when moving standards to make sure cells do not settle.
