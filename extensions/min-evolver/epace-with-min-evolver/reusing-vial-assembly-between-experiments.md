# Reusing vial assembly between experiments

## Overview

Advantages:

* Saves time from assembling, autoclaving, and setting up new vials
* Avoids vial to vial variation
  * Using the same vial in your OD calibration and all experiments makes OD more accurate

## Questions

Do you sterilize the septa before each needle insertion?

## Materials

* Vials set up for ePACE
  * Including septa
* 20% bleach in an eVOLVER bottle
* Sterile DI water (or Milli Q water) in an eVOLVER bottle
* 4 inch needle
* 50mL syringe

## Protocol

### Considerations

1. Be cautious about over filling
2. Stir should be on to properly mix liquids
   1. Stir pausing is fine
3. Number of seconds pumped in pump commands are for a 30mL reservoir and 10mL lagoon. If you change these volumes, make sure to define your own number of seconds pumped.
4. As always, any spills on the min-eVOLVER should be immediately cleaned
   1. If you think something got on an electronic part, unplug the min-eVOLVER, wipe, and allow to dry

### Sterilization

{% hint style="info" %}
20% bleach is used because otherwise it would require a lot more volume to be pumped before bleach concentration was high enough
{% endhint %}

1. Hook up 20% bleach bottle to influx
2. Dilute cultures with bleach - run fast pumps for 80 seconds and slow pumps for 300 seconds
   1. `python3 send_command.py 5555 pump 80,80,80,80,300,300`&#x20;
3. Fill both reservoir and lagoon with bleach over efflux line
   1. Remove vials from Smart Sleeves to keep an eye on fluid levels
   2. `python3 send_command.py 5555 pump 0,0,20,15,0,0` &#x20;
4. Check fluid levels
5. Ensure all tubing is filled with bleach
6. Sterilize at least 30 minutes
7. Do not allow bleach to sit in vials for more than a day
   1. Use the below protocol to replace bleach with sterile DI water

### Remove Bleach

1. Unhook tubing from bleach bottle
2. Clear bleach from tubing and pump bleach to efflux line in vials
   1. `python3 send_command.py 5555 pump 20,40,20,20,300,300`&#x20;
3. Remove bleach from vials
   1. Insert a 4 inch needle and 50mL syringe through the sampling port
   2. Try and get almost all of the bleach
   3. Avoid scratching your vial with the needle as this can change the OD calibration
4. Hook up sterile DI water bottle to influx
5. Fill both reservoir and lagoon with sterile DI water over efflux line
   1. `python3 send_command.py 5555 pump 0,0,70,60,0,0` &#x20;
   2. Remove vials from Smart Sleeves to keep an eye on fluid levels
6. Dilute residual bleach
   1. `python3 send_command.py 5555 pump 80,80,80,80,300,300`
7. Vials can now be safely stored for more than one day without bleach corrosion

### Prep Vials for Experiment

1. Day of the experiment, sterilize with bleach again via the above protocol
2. Sterilize septa at sampling port
   1. Using a pipette, place a single drop of bleach on the septa through the sampling port and allow to sterilize during vial bleaching before experiment
   2. Avoid adding too much bleach as it will run down the sides of the vial and change the OD calibration
3. Flush vial with sterile media using the Remove Bleach protocol
4. Follow ePACE experiment setup [protocol](experiment-setup.md)
