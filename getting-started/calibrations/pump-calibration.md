# Pump Calibration

1. Fill a large beaker with water and submerge all of the pump lines (inputs and outputs of the pumps), ensuring all of the ends are below the surface of the water.

![](../../.gitbook/assets/PXL\_20220728\_164925874.jpg)

2\. Run the pumps on the Setup page to completely fill the lines with water (about 20s)

3\. Place 16 vials into a rack and place the output ends of the pumps to be calibrated into the vials.

{% hint style="warning" %}
It's best practice to not put the vials into the eVOLVER platform in case you make a mistake and overflow the vials. Keep the rack to the side.
{% endhint %}

![](../../.gitbook/assets/PXL\_20220728\_164720152.jpg)

4\. Select the eVOLVER on the top of the GUI home page to be calibrated

5\. Navigate to the Pump Calibration page

![](<../../.gitbook/assets/Screen Shot 2022-07-28 at 12.39.41 PM.png>)

![](<../../.gitbook/assets/Screen Shot 2022-07-28 at 12.40.09 PM.png>)

6\. Enter a name for the pump calibration

![](<../../.gitbook/assets/Screen Shot 2022-07-28 at 12.40.29 PM.png>)

7\. Select the pump configuration for the eVOLVER. In a standard setup, `IN1` are the media in pumps, and `E` refers to the efflux pumps. If you have another pump array (for a second media input source), it is typically going to be in `IN2`. Click `Start Pump Calibration`. The standard pumps are the `FAST` pumps (\~1 mL/s, black pump heads). If you have the slow flow rate pumps (\~ 1 ml/m, pink pump heads), select the `SLOW` radio button for that array.

{% hint style="info" %}
`IN1` refers to address 0-15, `E` refers to addresses 16-31, and `IN2` refers to addresses 32-47. If you have a different pump array setup you can either calibrate manually by putting a json fit object into the `calibrations.json` file on the RPi server, or reach out on the forum to ask for assistance.
{% endhint %}

![](<../../.gitbook/assets/Screen Shot 2022-07-28 at 12.40.40 PM.png>)

8\. Select all of the vials either by clicking the button on the bottom right or clicking and dragging across the vials on the selector. Click `PUMP IN` (or whatever the pump array you are calibrating) to run the pumps for 10s if the `FAST` radio button was selected or 100s if the `SLOW` radio button was selected.&#x20;

{% hint style="info" %}
The time the pumps will run will be noted in the bottom right of the screen. If you need to stop the pumps early, click `FORCE STOP ALL`.
{% endhint %}

![](<../../.gitbook/assets/Screen Shot 2022-07-28 at 12.40.54 PM.png>)

9\. After the pumps finish pumping, measure how much water was pumped by pouring out the water from each vial into a 25 mL graduated flask (or something similar). Enter this number into the box for each vial. The flow rate will appear on the vial selector on the right side of the screen.

{% hint style="info" %}
Round to the nearest half graduation. The minimum resolution cylinder we recommend for typical eVOLVER pumps should have 0.5 mL graduations.
{% endhint %}

![](../../.gitbook/assets/PXL\_20220728\_165407307.jpg)

![](<../../.gitbook/assets/Screen Shot 2022-07-28 at 1.02.02 PM.png>)

10\. Repeat this process for each pump array you have selected for calibration.

11\. Click the pen button to submit and save the calibration. Then click `Exit` after the calibration is logged.

![](<../../.gitbook/assets/Screen Shot 2022-07-28 at 1.03.19 PM.png>)

12\. Verify the calibration appears on the setup page.

![](<../../.gitbook/assets/Screen Shot 2022-07-28 at 1.03.34 PM.png>)
