# Setup Phototroph eVOLVER

## Base eVOLVER Requirements

1. Buy an eVOLVER [base](../../../getting-started/buying-evolver.md)
2.

## Phototroph eVOLVER Hardware Setup

The following are different from the base eVOLVER [setup](../../../getting-started/unboxing-and-setting-up.md):

1. [Smart sleeve construction](photo-evolver-smart-sleeves/photo-evolver-smart-sleeve-construction-guide.md)
2. Additional fluidics
   1. [Emergency efflux](../../../guides/emergency-efflux.md)
   2. Bubbling splitter
   3. \[Optional] Additional slow pump rack for inducers
3. Vials (recommended to get parts for at least two sets)
   1. [5-port nylon tube cap](../../../hardware/vial-caps/5-and-7-port-nylon-tubing-caps-construction-protocol.md)
   2. [Bubbler](../../custom-fluidics/bubblers-in-vial-aeration/bubbler-construction-protocol.md) (plugs in to cap)
   3. Long thin stir bars - required otherwise bubbles will stick and throw off OD readings
4. Bubbler cleaning apparatus (recommended for saving time)
5. Light meter and probe
   1. Our light meter is the LI-COR [LI-1500](https://www.licor.com/products/light/light-logger)
   2. Our light probe is the Walz US-SQS/L omnidirectional light [probe](https://www.walz.com/products/light/us-sqs_l/introduction.html)

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
