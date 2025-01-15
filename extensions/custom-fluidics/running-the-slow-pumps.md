# Running the slow pumps

The slow pumps are currently operated independently of the main eVOLVER GUI and pump liquid at a rate of X mL/min.

The eVOLVER slow pumps currently operate exclusively through the [command line](../../guides/command-line-usage.md). The navigate to the `run_slow_pumps.py` file similarly to starting an experiment via command line.

In the run\_slow\_pumps.py script you only need to modify one of two lines for time settings, one for modifying specific pumps and the other for modifying all pumps

<figure><img src="../../.gitbook/assets/Screenshot 2024-08-28 at 4.11.57 PM.png" alt=""><figcaption><p>Modify specific pumps timing</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screenshot 2024-08-28 at 4.10.16 PM.png" alt=""><figcaption><p>Modify all pumps timing</p></figcaption></figure>

Traditionally it takes about 200-300 seconds to fill the lines with liquid using the slow pumps, however this is dependent on the length of tubing.
