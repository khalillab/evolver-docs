# Setup Phototroph eVOLVER

## Hardware Setup

The following are different from the base eVOLVER [setup](../../../getting-started/unboxing-and-setting-up.md):

1. [Smart sleeve construction](photo-evolver-vials/photo-evolver-smart-sleeve-construction-guide.md)
2. Fluidics construction
3. Vial caps (get parts for at least two sets)
   1. [5-port nylon tube cap](../../../hardware/vial-caps/5-and-7-port-nylon-tubing-caps-construction-protocol.md)
   2. [Bubbler](../../custom-fluidics/bubblers-in-vial-aeration/bubbler-construction-protocol.md)
4. Bubbler cleaning apparatus (highly recommended)

## OD Considerations

We pause stirring and phototroph growth lights when we take OD. Without this, OD would be nonfunctional. Stirring causes bubbles be pulled downwards and the growth lights completely saturate the OD sensor.

### Additional Calibration Procedures

1. Switch to calibration conf.yml before doing calibration
   1. Because this will give us data every 20 seconds and greatly speed up calibration
2. Settings during calibration should mimic the experiment therefore:
   1. Phototroph growth lights off
   2. Stirring off
3. Vial setup for calibration (also mimic the experiment)
   1. Prepare standards in caps with a bubbler
   2. Use long stir bars
4. When moving standards, give a swirl once every other time
   1. This is to make sure cells don’t settle and change the OD
5. Finally, switch back to experiment conf.yml when ready for experiment
