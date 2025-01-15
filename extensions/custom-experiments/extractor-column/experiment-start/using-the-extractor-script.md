# Using the extractor script

#### Step-wise Process for Setting Up the Script for Extractor Experiments

**1. Select the Type of Experiment**

* Decide whether to run a [**Chemostat**](../../../../experiments/chemostat.md) or [**Turbidostat**](../../../../experiments/turbidostat.md) experiment.
* Ensure you choose the correct type when configuring the script.

**2. Set Parameters for the Experiment**

* The setup process for Chemostat and Turbidostat is identical to non-extractor versions.
* Define the operational parameters as you normally would for the chosen type of experiment.

**3. Specify Extractor and Non-Extractor Vials**

* Identify which vials will be used as extractor and non-extractor vials:
  * **Common Extractor Vials:** 4, 5, 6, 7, 12, 13, 14, and 15.
  * **Common Non-Extractor Vials:** 0, 1, 2, 3, 8, 9, 10, and 11.
* Edit the script to assign these roles to the corresponding vials.

<figure><img src="../../../../.gitbook/assets/Screenshot 2024-08-28 at 4.17.42 PM.png" alt=""><figcaption><p>Extractor setting in script</p></figcaption></figure>

**4. Edit Vial Assignments if Needed**

* If the vial assignments need to be changed during the experiment:
  * Modify the script accordingly.
  * Ensure all changes are accurately reflected in the script.

**5. Restart the Script After Changes**

* If any changes are made to the extractor or non-extractor vial assignments:
  * Stop the current running script.
  * Restart the updated script in the terminal to apply the changes.

**6. Run the Experiment**

* Once the script is set up with the correct parameters and vial assignments:
  * Start running the experiment using the script.

**7. Monitor and Adjust as Necessary**

* During the experiment, monitor the setup to ensure everything functions as expected.
* If adjustments are needed, repeat the steps to edit the script and restart it.

