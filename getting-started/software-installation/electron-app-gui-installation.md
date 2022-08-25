---
description: Process for installing the Electron App (GUI) for eVOLVER.
---

# Electron App (GUI) Installation

For all operating systems, navigate to the [releases](https://github.com/FYNCH-BIO/evolver-electron/releases) section of the Electron App GitHub page.

1. [Mac](electron-app-gui-installation.md#mac-installation)
2. [Windows](electron-app-gui-installation.md#windows-installation)
3. [Linux](electron-app-gui-installation.md#linux-installation)

### Mac Installation

1\. Download the `evolver-electron-X.X.X.dmg` file, where X denotes the version number in the latest release. The latest release should be the first one you see at the top of the page.

![](<../../.gitbook/assets/Screen Shot 2022-04-11 at 3.16.43 PM.png>)

2\. When the download finishes, open the file (it should be in your `Downloads` directory) and drag the eVOLVER app into your `Applications` directory.

![](<../../.gitbook/assets/Screen Shot 2022-04-12 at 11.02.17 AM.png>)

{% hint style="danger" %}
FIRST TIME INSTALLATION - DO THE FOLLOWING NEXT STEPS!
{% endhint %}

3\. Open the eVOLVER app from the `Applications` directory.

4\. Using an editor of your choice (TextEdit, Nano, Vim, TextWrangler, etc.) open the file `config.json` located at `/Users/<your username>/Library/Application Support/eVOLVER/config.json`

{% hint style="info" %}
You may need to enable the ability to view hidden files if you are trying to find this file in a Finder window. With a Finder window open, press **Command + Shift + . (period)** to make hidden files appear. You can press the keys again afterwards to make them disappear.
{% endhint %}

{% hint style="info" %}
If you are attempting to modify this file via a terminal, be sure to escape the space character in `Application Support` with a `\`.  It should look like this: `/Users/<your username>/Library/Application\ Support/eVOLVER/config.json`
{% endhint %}

![](<../../.gitbook/assets/Screen Shot 2022-04-12 at 11.16.22 AM.png>)

5\. Add a line in this file between the braces: `"dpu-env": "/Users/<your username>/Document/dpu/dpu-env"`

{% hint style="danger" %}
If you add this line to the beginning of the block, be sure to add a comma at the end! If you add it to the end, put a comma on the line before it.
{% endhint %}

{% hint style="info" %}
If you installed the DPU in a different location, be sure to reflect that in this line. The electron app uses this to find the correct python binary/venv to run the DPU
{% endhint %}

![](<../../.gitbook/assets/Screen Shot 2022-04-12 at 11.31.17 AM.png>)

6\. Save the file and you're done!

### Windows Installation

1\. Download the `evolver-electron-X.X.X.exe` file, where X denotes the version number in the latest release. The latest release should be the first one you see at the top of the page.

![](<../../.gitbook/assets/Screen Shot 2022-04-12 at 11.55.13 AM.png>)

{% hint style="warning" %}
Chrome may flag the download, just select "Keep". ![](<../../.gitbook/assets/image (34).png>)
{% endhint %}

2\. Open the .exe file.

{% hint style="warning" %}
In Windows 10, Microsoft Defender prevents the app from starting immediately. Simply click "More info" and then "Run Anyway" to get around this. ![](<../../.gitbook/assets/image (6).png>)
{% endhint %}

{% hint style="danger" %}
FIRST TIME INSTALLATION - DO THE FOLLOWING NEXT STEPS!
{% endhint %}

3\. Using an editor of your choice open the file `config.json` located at `C:\Users\<Your-UserName>\AppData\Roaming\eVOLVER\`

{% hint style="info" %}
You may need to [enable ](https://support.microsoft.com/en-us/windows/view-hidden-files-and-folders-in-windows-97fbc472-c603-9d90-91d0-1166d1d9f4b5)the ability to view hidden files if you are trying to find this file in a File Explorer window.
{% endhint %}

![](<../../.gitbook/assets/image (47).png>)

4\. Add a line in this file between the braces: `"dpu-env": "C:\\Users\\<Your-UserName>\\Desktop\\dpu\\dpu-env"`

Note the escaped `\` , be sure to put double `\\` throughout the path.

{% hint style="danger" %}
If you add this line to the beginning of the block, be sure to add a comma at the end! If you add it to the end, put a comma on the line before it.
{% endhint %}

{% hint style="info" %}
If you installed the DPU in a different location, be sure to reflect that in this line. The electron app uses this to find the correct python binary/venv to run the DPU.
{% endhint %}

![](<../../.gitbook/assets/Screen Shot 2022-07-22 at 12.50.12 PM.png>)

5\. Save the file and you're done!

### Linux Installation

1\. Download the `evolver-electron-X.X.X.AppImage` or `evolver-electron-X.X.X.deb` file, where X.X.X denotes the version number in the latest release. The latest release should be the first one you see at the top of the page.

![](../../.gitbook/assets/linux\_wiki\_picture.jpg)

{% hint style="info" %}
Selection of either .deb or .AppImage is largely based on personal preference and computer environment, each presenting slight pros and cons. If you are unfamiliar with installing Linux packaged software, use this link to learn more about what is applicable to you. Briefly, .deb files are natively designed for Ubuntu and will compile the entire application, along with necessary dependecies, onto the local machine. An AppImage file contains everything necessary to run the program, requiring you to execute the file when you want to run program.&#x20;
{% endhint %}

2\. If downloading `evolver-electron-X.X.X.deb,` open your `Downloads` directory and right-click `evolver-electron-X.X.X.deb` to open the file with `Software Install` .&#x20;

3\. A new window should open, allowing you to install the eVOLVER GUI. Click `Install` and follow the onscreen instructions to install the eVOLVER GUI.

![](../../.gitbook/assets/linux\_wiki\_2.png)

{% hint style="danger" %}
FIRST TIME INSTALLATION - DO THE FOLLOWING NEXT STEPS!
{% endhint %}

4\. Open the eVOLVER app by either clicking `Show Applications` from the home screen or through the command line. To open via command line, open Terminal and enter to access installed applications:

```shell
cd ~/usr/bin
```

Run the eVOLVER GUI by entering:

```shell
evolver
```

5\. Using an editor of your choice, open the file `~/.config/eVOLVER/config.json` .&#x20;

6\. Add a line in this file between the braces to denote the location of the installed DPU virtual environment:&#x20;

`"dpu-env": <path_to_dpu>`&#x20;

![](<../../.gitbook/assets/Screen Shot 2022-04-12 at 11.31.17 AM (1).png>)

{% hint style="danger" %}
If you add this line to the beginning of the block, be sure to add a comma at the end! If you add this line to the end, put a comma on the line before it.
{% endhint %}

7\. Save the file and you're done!
