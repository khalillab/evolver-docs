---
description: A guide for usage of the eVOLVER GUI to set parameters
---

# Use the GUI to Control Parameters

{% hint style="warning" %}
Before doing using the GUI, all [Software Installation](../getting-started/software-installation/) and [Network Configuration](../getting-started/configuring-computer-and-networking/) should be complete.

Also, make sure to [calibrate](../getting-started/calibrations/) parameters before using them.
{% endhint %}

{% hint style="info" %}
Also Refer to the [JoVE ](https://www.jove.com/t/59652/designing-automated-high-throughput-continuous-cell-growth)paper for a video of using the GUI and the GUI Experiment Start [Guide](../experiments/starting-an-experiment/gui-start-guide.md).
{% endhint %}

Turn on the eVOLVER `5V` power supply by flipping the associated switch. _IMPORTANT: Wait for 5 seconds before turning on the `12V` power supply._

Ensure the correct eVOLVER is selected by consulting the upper right hand corner of the GUI. It will display the eVOLVER name (default is evolver-darwin), followed by the IP address in parentheses. This will be the IP address you assigned it when setting up the router connecting the DPU to the vial platform.

{% hint style="info" %}
**If connected**, the **indicator dot** next to the name should be **green**. If this dot is **red**, you may need to troubleshoot the eVOLVER vial platform connection to the DPU. Consult the eVOLVER DPU [Installation](../getting-started/software-installation/dpu-installation.md) and [Networking Setup](../getting-started/configuring-computer-and-networking/) for details on setting up and troubleshooting this connection. Otherwise consult the [forum](https://www.evolver.bio/) or post a question.
{% endhint %}

![](<../.gitbook/assets/Screen Shot 2022-06-30 at 1.22.47 PM.png>)

In the `PARAMETER` box, ensure the correct calibrations are selected for Temp, OD, and the pumps. Click the box for each to bring up a list of available calibrations for that parameter.

<figure><img src="../.gitbook/assets/image (24) (1).png" alt=""><figcaption></figcaption></figure>

Select all vials by tapping `Select All` in the bottom right corner of the screen. The vial circles on the right side of the display should become **orange**.

You can also click and drag to select as many vials as you want.

Tap the `NEXT →` on the box that says parameter to get to the `Stir` tab. Tap the `-` button or drag the slider to a Stir of 8. Press the `Stir: 8` button to alter the stirring of all vials.

<figure><img src="../.gitbook/assets/image (43) (1).png" alt=""><figcaption></figcaption></figure>

Tap the `NEXT →` on the box that says parameter to get to the`Temperature` tab. Tap the `-` button or drag the slider until the middle button says `37.0 °C` and tap the button. The `EXECUTED COMMANDS` box should state that a stir and then temp command was sent to all vials.

<figure><img src="../.gitbook/assets/image (13) (2).png" alt=""><figcaption></figcaption></figure>

## Pumps

Refer to the [JoVE](https://www.jove.com/v/59652/designing-automated-high-throughput-continuous-cell-growth) video for how to use pumps and sterilize fluidic lines

<figure><img src="../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>
