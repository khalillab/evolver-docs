# Experiment Guide

## Pre-setup (days before experiment start)

#### Cultures

* [ ] Grow starting cultures to saturation so that they are ready for inoculation at the beginning of the experiment.
* [ ] Have sampling materials handy: needles with syringes, 96-well plates, silicone plate covers

#### Vials&#x20;

Assemble 20 vials, each with:

1. eV cap with bubbler
2. Twist-on caps closing all ports in the cap
3. Long stir bar
4. O-ring
5. Black rubber stopper

Autoclave 18-20 vials, although only 16 will be used. This ensure that if there are defects (e.g. opacities in the glass vials that interfere with OD readings, or blocked bubblers), backups are autoclaved and ready.

#### Media & tubing

* [ ] Autoclave the emergency efflux tubing (black)
* [ ] Autoclave media, with enough time to cool before starting the experiment.
* [ ] Make and autoclave media splitters, if using different types of media in certain vials.

## Experiment setup

#### Bleach & flush tubing

* [ ] Place the red tubing so that it goes into the waste container (secure it in place with tape/parafilm/clips)
* [ ] Ensure all ends of tubing are in the 3L bucket for tubing
  1. Blue efflux; white IN1 and IN2 IN / OUT&#x20;
* [ ] Pump bleach into tubing:
  1. Go to eVOLVER app > Setup > Next > Next
  2. Select all vials
  3. Toggle IN1 and EFF to ON
  4. Pump bleach through tubing by clicking PUMP 20s x 3 times
  5.  \[IF IN2 USED IN EXPERIMENT] Go to eVOLVER > Calibrations > Set IN2 to SLOW,

      IN1 to N/A, EFF to N/A
  6. Select all vials
  7. Click PUMP x 4 times
* [ ] Leave bleach in the tubing for about 30 minutes. **While waiting, set up the vials.**
* [ ] To flush, connect the clear tubing IN to the appropriate media bottle splitter tubing and then into the correct media bottle
* [ ] Tape clear OUT tubing to 3L bucket so that ends do not drip on each other
* [ ] Crack the media bottle caps to make sure they have airflow (otherwise it creates a vacuum and will dilute the incorrect volume into the vials)
* [ ] Crack the inducer/antibiotics caps to make sure they have airflow (otherwise it creates a vacuum and will dilute the incorrect volume into the vials)
* [ ] Pump sterile media through influx tubing following the same steps as above
* [ ] Flush all the way through tubing at least twice
* [ ] Pull air into efflux tubing (blue) by removing ends from bleach
*   [ ] Avoid touching sterile tubing connectors to dirty surfaces - if you do, spray with 70%

    ethanol

#### Vial setup (while bleaching)

* [ ] Wipe outside of vials with Kimwipe to avoid opacities Make sure eV caps are air tight by making sure:
  * [ ] O-ring is engaged and the caps are all the way screwed on and tight&#x20;
  * [ ] Black rubber plug should be pushed in fully
  * [ ] Cap any tubes that will be unused
* [ ] Insert the vials into the eVOLVER with the black rubber stopper facing the front screen

#### Connect tubing

* [ ] Connect the **black emergency efflux** tubing to each vial&#x20;
* [ ] Place the other ends into the waste container (ensure all ends are in the container and use tape/parafilm/clips if needed to secure it in place)
  * [ ] Tape the tubes so that the ends do not touch the bottom of the sterilized waste container. If they become submerged, the tubes will suck up media should there be an efflux event that creates a vacuum.
* [ ] Connect the <mark style="color:blue;">**blue regular efflux**</mark> tubing to efflux straw (<mark style="color:blue;">**blue tubing to blue on the cap**</mark>)&#x20;
* [ ] Connect media IN1 and inducer IN2 - connect the clear tubing OUT to the appropriate vial, making sure to connect the correct vial to the corresponding color tubing

> Tips for tubing layout:
>
> 1. Keep tubing orderly to avoid contamination when sampling and make changing out vials easily.
> 2. Have the tubes from each section of the vial setup (left, right, middle, back, front) go in different directions before going to their destinations.
> 3. Make sure there are no kinks in the tubing

#### Fill vials

* [ ] Fill vials \~1cm over efflux straw with graphical user interface (GUI) - pick up a vial and use as reference to see how much you’ve filled
* [ ] Test efflux pumps - Run efflux pumps a few seconds and check all tubes to see if liquid is removed
* [ ] Efflux 20s to remove volume down to correct level
* [ ] Check volume levels are correct in all vials

#### Bubbling

* [ ] Plug in <mark style="color:blue;">**blue air tubes**</mark> to bubbler port (<mark style="color:red;">**red tube on cap**</mark>)
* [ ] Turn on gas mixer - switch in back right \*\*?
* [ ] Turn on air and CO2 - turn on / off with tap knob (not using black regulator knob) Check CO2 and air are 60psi
* [ ] Check gas mixer is at correct level
* [ ] Check bubbling is working in all vials

> #### Gas Setup
>
> * New air / CO2 pressures = 60psi
> * New flow rate = 0.8 L/min
> * How to modify flow rate
>   * Press ‘S’ to go to settings
>   * Navigate to ‘Flow Rate Sigma’
>   * Press ‘S’
>   * Use arrow keys to the right of ‘S’ to change flow rate
>   * Press ‘S’ to set
>   * Press ‘M’ to get back to main screen
> * Trick if gas mixer is not reaching high enough / correct CO2% (within \~10 seconds)
>   * Lower flow rate so that the mixer puts out correct CO2%
>   * If this doesn’t work (ie CO2% is too high now), then lower CO2% until it is regulated, then raise CO2% back to target
>   * Then, change flow rate to final flow rate
> * Trick if gas mixer is not reaching high enough / correct CO2% (within \~10 seconds)
>   * Lower flow rate so that the mixer puts out correct CO2%
>   * If this doesn’t work (ie CO2% is too high now), then lower CO2% until it is regulated, then raise CO2% back to target
>   * Then, change flow rate to final flow rate

#### Set up code

* [ ] Copy the experiment folder for the experiment to be run, and rename the folder
* [ ] Check that parameters in custom\_script.py are correct or modify

#### Experiment start&#x20;

* [ ] Check in GUI setup page that vials temperatures are done equilibrating - wait for 10 extra minutes to make sure
* [ ] Check antibiotic media lines to make sure they are full, if they are unused for a while (ie during experiment start)
  * [ ] \*
* [ ] Make sure all vials are fully pushed into vial sleeves&#x20;
* [ ] Navigate in terminal to your experiment folder (`cd your_experiment_directory`)
* [ ] Start experiment: `/python3 eVOLVER.py -i 192.168.1.114`
* [ ] Calibrate to blank: y
* [ ] Wait for at least one round of data&#x20;
* [ ] Pause experiment (Control + C)&#x20;
* [ ] Inoculate through sampling port&#x20;
* [ ] Replace stopper
* [ ] Resume experiment (Enter/Return)&#x20;
* [ ] Double check
  * [ ] Stoppers are all pushed in
  * [ ] Vial direction - stopper is towards the touch screen&#x20;
  * [ ] All vials are fully pushed into vial sleeves&#x20;
  * [ ] Inoculated OD is roughly (+/- 0.1) what you expect

> #### Prevent bubbles forming overnight in media line
>
> * Inducer / antibiotic bottles should be on the table - prevents pressure on lower volume inducer drawing media down
> * Tape splitters to table so that they don’t fall off and create a pressure sucking media down
> * Make sure to tighten the luer lock connections until you can’t any more
> * They may make a small click
> * Luer lock connections to double check tightness of:
>   * Media bottle to splitter
>   * Splitter to influx tubing
>   * Influx tubing to vial

## Experiment takedown

#### Terminate experiment

1. Take picture of OD curve graph&#x20;
2. Control + C
3. Control + C&#x20;

#### Vials & caps

* [ ] Fill 2 x 5L plastic buckets with 10% bleach solution (one for tubing and one for washing caps)
* [ ] Disconnect tubing from each vial and place the ends in one of the 5L buckets
* [ ] Unscrew and discard cells in 10% bleach solution
* [ ] Remove all luer stoppers on all eVOLVER caps so that fluid flows freely through
* [ ] Soak vials with bleach solution and rinse quickly with DI water, then place upside down to dry on a red rack
* [ ] Using a 10mL syringe, pump 10% bleach solution through each port of the caps
* [ ] Leave caps in bleach water in bucket for 20-30 minutes
* [ ] Pour bleach out of bucket and rinse caps thoroughly with DI water (can swirl bucket)&#x20;
* [ ] Using a 10mL syringe, pump DI water through each port
* [ ] Lay caps on a Kimwipe to dry overnight
* [ ] Take vials to autoclave room to go in dishwasher (they can go in together on rack)

#### Tubing

* [ ] Dip the black emergency efflux tubing in 10% bleach (in the washing caps bucket) then rinse with water and set to dry on trolley
* [ ] Unscrew caps from media bottles and place the media bottle input connector tube in the 5L bucket for tubing
* [ ] Ensure all ends of tubing are in the 5L bucket for tubing, except for the red efflux tubing with ends in the waste carboy
* [ ] Pump bleach into tubing:
  1. Go to eVOLVER app > Setup > Next > Next
  2. Select all vials
  3. Toggle IN1 and EFF to ON
  4. Pump bleach through tubing by clicking PUMP 20s x 3 times
  5.  \[IF IN2 WAS USED IN EXPERIMENT] Go to eVOLVER > Calibrations > Set IN2 to

      SLOW, IN1 to N/A, EFF to N/A
  6. Select all vials
  7. Click PUMP x 4 times
* [ ] Leave bleach in tubing for \~30 minutes
* [ ] Fill bucket with \~1-2L DI water
* [ ] Pump DI water through tubing following the same steps as above&#x20;
* [ ] Empty tubing by removing from water pumping air in as above

#### Waste container

* [ ] Pour bleach into the waste container and swish around until it changes to a light yellow color (if it’s taking too long, pour more bleach in)
* [ ] Empty bleached solution into sink

