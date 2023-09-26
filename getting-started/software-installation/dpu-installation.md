---
description: Process for installation of the Data Processing Unit (DPU)
---

# DPU Installation

You can run eVOLVER experiment culture routines directly on the command line, or through the Electron graphical interface. This page documents how to install the DPU for use on the command line.

{% hint style="info" %}
We recommend running the DPU through the GUI for most use cases. Please see the [Electron App (GUI) Installation](electron-app-gui-installation.md) documentation and the [GUI Start Guide](../../experiments/starting-an-experiment/gui-start-guide.md) for more information.
{% endhint %}

{% hint style="warning" %}
Even if you plan to use the GUI to run your experiments, you still need to go through these steps!
{% endhint %}

{% hint style="success" %}
If you are unfamiliar with working on a command line terminal or cannot use the Electron GUI for your application, check out the [Command Line / Terminal Usage](../../guides/command-line-usage.md) guide!
{% endhint %}

## (Mac only) Homebrew and openssl/sqlite installation

In Terminal, install homebrew:

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Afterwards, run the two following commands:

`brew install openssl`

`brew install sqlite`

## Install Python 3.9

_Python 3.9 is required for dpu operation_

Mac:

```
brew install python@3.9
```

Windows

1\. Go to the official [python website](https://www.python.org/downloads/release/python-3913/) to download python 3.9.&#x20;

2\. Follow [these instructions](https://docs.python.org/3.9/using/windows.html) to install python on your machine.

3\. If you have multiple versions of python3 on your machine, you can set up an [alias](https://martinfritz.medium.com/work-with-multiple-versions-of-python-on-windows-10-eed1e5f52f07) to manage the usage between the different versions.

## DPU Installation

1\. Navigate to the [DPU Github page](https://github.com/FYNCH-BIO/dpu)

2\. Click `Releases` on the right side of the page

![](<../../.gitbook/assets/Screen Shot 2022-04-20 at 11.06.45 AM.png>)

3\. Click the Source Code link (zip) to download the latest release.

{% hint style="warning" %}
The release name/number will be different from the screenshot below! You will typically want the latest release, which should be at the top of the page.
{% endhint %}

![](<../../.gitbook/assets/Screen Shot 2022-04-20 at 11.10.25 AM.png>)

4\. Move the downloaded .zip file (which should be in your `Downloads` directory for your browser) to the location where you want your experiments to run. `Documents` or `Desktop` are good locations. This is also where your data will be saved.

{% hint style="danger" %}
Do not leave the DPU zip file in your Downloads directory. Please move to appropriate location.
{% endhint %}

5\. Unzip the file.

6\. Open a terminal. On Mac, you can use the built in `Terminal` application (press CMD + Space then type terminal to find it). I recommend [iTerm2](https://iterm2.com/) if you want a terminal with some quality of life enhancements. On Windows, you can use PowerShell.

7\. We use [poetry](https://python-poetry.org/) to manage our python dependencies. Go to their website to download and install it on your machine.&#x20;

* If you are using a Mac and have installed homebrew (described above) you can run the following command: `brew install poetry`
* Windows Powershell:

```powershell
(Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | py -
```

{% hint style="info" %}
If you have installed Python through the Microsoft Store, replace `py` with `python` in the command above.
{% endhint %}

8\. Navigate to the DPU directory you just downloaded and unzipped:

* Use this command: `cd <path_to_dpu>`
* Replace the `<path_to_dpu>` with the location you put your dpu

9\. Create a new [virtual environment](https://docs.python.org/3/library/venv.html) then activate it with the following command:

Mac:

`python3.9 -m venv venv`

`source venv/bin/activate`

Windows PowerShell:

`py -3.9 -m venv venv`

`venv\Scripts\Activate.ps1`

10\. Use  poetry to install all necessary dependencies.

```
poetry install
```

If you can't find poetry on Windows "`poetry : The term 'poetry' is not recognized as the name of a cmdlet`" and it is installed, use the following command (replace `<Your_User_Name>` with your user name)

`C:\Users\<Your_User_Name>\AppData\Roaming\Python\Scripts\poetry.exe install`

{% hint style="warning" %}
You must activate the virtual environment when running DPU scripts from the command line. If you close a terminal or re-open it, you'll need to run `. venv/bin/activate`(Mac) or `venv\Scripts\Activate.ps1` (Powershell) again while in the dpu directory.
{% endhint %}

{% hint style="info" %}
You can activate the dpu environment automatically on a Mac or Linux machine by adding a line in your shell run commands (rc) file typically located in your home directory located at `~/.zhrc` (Mac) or `~/.bashrc` (Linux):

`source <path to dpu>/venv/bin/activate`

swapping out `<path to dpu>` with the actual path on your machine to the dpu.
{% endhint %}

{% hint style="info" %}
If you have issues with the dpu setup, reach out to us on the [forum!](https://www.evolver.bio/)
{% endhint %}
