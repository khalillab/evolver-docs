# Experiment Data Files

From the [forum](https://www.evolver.bio/t/explanation-of-data-folders/154):

In each experiment folder, you’ll find a number of different sub-folders and files. Here, I’ll describe the folders and files as of the dpu 1.0.1 version. If you are using a different version, your files and folders may be slightly different.

One important note is that not all folders are used in all experiment types. You can also create new folders to record other types of data for custom types of experiments (more on that in another post). These folders are created in _initialize\_exp()_ in evolver.py, if you want to see how that works.

**Common Folders**:

OD: contains .txt files where each row is \[ timepoint (h) , OD ] using the calibration to transform photodiode readings to OD600 equivalents. It is updated every loop through the software (\~20 secs).

OD90 (or OD135): contains .txt files where each row is \[ timepoint (h) , raw photodiode value ] without transforming the data. This could be used to apply a different calibration after the experiment (e.g. if you started the experiment with the wrong calibration selected). It is updated every loop through the software (\~20 secs).

temp: contains .txt files where each row is \[ timepoint (h) , temperature ] using the calibration to transform thermistor readings to Celsius equivalents. It is updated every loop through the software (\~20 secs).

temp\_config: contains .txt files where each row is \[ timepoint (h) , temperature target ] in Celsius. It is only updated when a new temperature command is sent from the custom\_script, so it won’t have very many lines for most experiments.

**Tubidostat Related Folders:**\
These folders are only updated in turbidostat mode, and are not used for chemostat mode.

ODset: contains .txt files where each row is \[ timepoint (h) , target OD ]. It is updated once when the upper OD threshold is reached (changes target to lower threshold), and once when the lower density threshold is reached (changes target to upper threshold). This makes it a good choice for segmenting turbidostat data into growth curves.

pump\_log: contains .txt files where each row is \[ timepoint (h) , pump time(s) ]. It is updated at every pump event, and generally records the amount of time the influx pump was turned on for, though in some older versions a bug caused the efflux pump time to be recorded instead.

* Since it records when a pump event is _sent_ to eVOLVER, the dilution won’t show up in the OD data right away, making it a poor choice to use to segment OD data into growth curves. Furthermore, if two dilutions are needed to reach a lower threshold (i.e. you switched out a bottle and there’s some air in the lines) pump log will be updated twice in short succession, complicating the process further.
* Chemostat pump events do not get listed here, as they use a recurring function on the Arduino, to reduce the load of commands sent to eVOLVER. Pump commands sent from outside the DPU (i.e. from the Electron app or MATLAB script) also do not get recorded in pump\_log files.

growthrate: contains .txt files where each row is \[ timepoint (h) , growth rate (h^-1) ] using ODset to segment data and a linear fit to log transformed OD data. It is updated every time the upper OD threshold is reached.

* The first growth rate measurement is fit on the data from the first timepoint to the first dilution, which means inoculation and lag phase can throw off this value.
* You may want to calculate growth rate offline after the expt. The growth rate calculated here has been optimized for robustness over accuracy, in order to enable feedback control.

**Chemostat Related Folders:**\
These folders are only updated in chemostat mode, and are not used for turbidostat mode.

chemo\_config: contains .txt files where each row is \[ timepoint (h) , chemo\_phase, period (s) ]. It is updated every time the chemostat dilution rates are changed. The second value can be used to keep track of updates if designing a custom chemostat experiment that changes or fluctuates between dilution rates. The third value is the period of time, in seconds, between pump events. Note that these pump events do not get recorded in pump\_log.

**Other Files:**\
evolver.log: some versions of the DPU will store a log of things that happen during the experiment, like errors or verbal descriptions of certain commands (i.e. changes to chemostat rates).\
XX\_cal.txt : some versions of the DPU will store .txt versions of the calibrations locally on your computer.\
EXP\_NAME\_DATE\_TIME.txt: this is a .txt record of your custom script, created each time you restart an experiment. This way if you change the code partway through, you have a record of each iteration of the code.
