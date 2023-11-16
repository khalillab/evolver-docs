# min-eVOLVER

## About

The min-eVOLVER is a minimal, mini version of the main eVOLVER. It runs in the same software ecosystem with minimal changes to the code. However, the min-eVOLVER controls two eVOLVER Smart Sleeves and six pumps, making it simpler, smaller, and less costly.

<figure><img src="../../.gitbook/assets/image (53).png" alt=""><figcaption><p>min-eVOLVER set up for a basic turbidostat on both vials.</p></figcaption></figure>

## Software Architecture

The software architecture of the min-eVOLVER is similar to the [original eVOLVER](../../software/overview-of-software-architecture.md), with the exceptions that:&#x20;

* The Raspberry Pi server has been replaced with a server run on the connected laptop&#x20;
* A single Arduino SAMD21 actuates all functions and collects vial data through the min-eVOLVER board

{% hint style="warning" %}
Currently the min-eVOLVER does not use the eVOLVER GUI. All experiments must be started with the command line. Sending commands without an experiment is done through [send\_command.py](send\_command.py.md).
{% endhint %}

## Questions or Comments?

If you have questions not answered by the wiki please ask in the relevant min-eVOLVER category on the [forum](https://www.evolver.bio/c/min-evolver/20).
