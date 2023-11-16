---
description: >-
  Process for installing the Arduino IDE and necessary eVOLVER Arduino
  libraries.
---

# Arduino Software Installation

If you have any questions or hit a roadblock, check [this post](https://www.evolver.bio/t/installing-arduino-libraries-and-uploading-code/156) on the forum.

### 1. Download the Arduino IDE

[Their website](https://www.arduino.cc/en/software) should be fairly easy to navigate.

![](<../.gitbook/assets/Screen Shot 2022-05-31 at 12.01.04 PM.png>)

### 2. Install SAMD libraries

The Sparkfun website has [a very good blog](https://learn.sparkfun.com/tutorials/samd21-minidev-breakout-hookup-guide/setting-up-arduino) on this. For more details, please refer to that link. The following is information copied from there.

> Navigate to your board manager ( **Tools** > **Board** > **Boards Manager…** ), then find an entry for **Arduino SAMD Boards (32-bits ARM Cortex-M0+)** . Select it, and install the latest version.

![](../.gitbook/assets/samd21.png)

### 3. Install the Sparkfun libraries for the SAMD21

> First, open your Arduino preferences ( **File** > **Preferences** ). Then find the **Additional Board Manager URLs** text box, and paste the below link in

```
https://raw.githubusercontent.com/sparkfun/Arduino_Boards/master/IDE_Board_Manager/package_sparkfun_index.json
```

![](../.gitbook/assets/prefs.png)

> Then hit “OK”, and travel back to the **Board Manager** menu. You should (but probably won’t) be able to find a new entry for **SparkFun SAMD Boards** . If you don’t see it, close the board manager and open it again.

![](../.gitbook/assets/board\_manager.png)

### 4. Choose the correct BOARD and PORT to upload into

1. Plug the SAMD21 into your computer via a data transfer micro-USB cable.
2. The boards used in eVOLVER are the SAMD21 Mini boards.
3. The port changes based on which USB the Arduino is connected to. The wrong port is typically the most common reason why the Arduino won’t upload.
   1. If you are unsure which port is the correct one, plug and unplug the SAMD21 board and see which port appears and disappears.

**Choosing the board:**

![Selecting the SAMD21 Mini in the Board Manager out of available boards.](../.gitbook/assets/choosing\_board.jpeg)

**Choosing the port:**

![You should see the SAMD21 come up on the Ports list if it is plugged in.](../.gitbook/assets/port.png)

### 5. Download the Arduino scripts and copy eVOLVER libraries into Arduino folder

1. Download the scripts from our [Github Page](https://github.com/FYNCH-BIO/evolver-arduino)
   1. Download by clicking "Code" and downloading as a zip file
2. Extract the files from the zipped file
3. Copy the [libraries folder](https://github.com/FYNCH-BIO/evolver-arduino/tree/master/libraries) into your local Arduino libraries folder
   1. For example, on my computer, it is under **Documents > Arduino > libraries**

![](../.gitbook/assets/libs\_evo.png)

### **6. Upload script to Arduino!**

This should be all. Open up the files and upload your scripts to the microcontroller via microUSB! The program should tell you that it has uploaded successfully.

{% hint style="warning" %}
A quick tip: there are many poorly designed microUSB cables out there (e.g. just for charging). Be careful to use one that you know works. If you can’t upload, try another cable. If it still fails, take a look at this [guide](https://learn.sparkfun.com/tutorials/samd21-minidev-breakout-hookup-guide/troubleshooting).
{% endhint %}

![](../.gitbook/assets/script\_upload.jpeg)
