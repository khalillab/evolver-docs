---
description: Process for installation of the Data Processing Unit (DPU)
---

# DPU Installation

You can run eVOLVER experiment culture routines directly on the command line, or through the Electron graphical interface. This page documents how to install the DPU for use on the command line.

{% hint style="info" %}
We recommend running the DPU through the GUI for most use cases. Please see the [Electron App (GUI) Installation](electron-app-gui-installation.md) documentation and the [GUI Start Guide](../../experiments/starting-an-experiment/gui-start-guide.md) for more information.
{% endhint %}

{% hint style="info" %}
If you are unfamiliar with working on a command line terminal, but cannot use the Electron GUI for your application, check out the[ Command Line Usage](../../guides/command-line-usage.md) guide!
{% endhint %}

{% hint style="warning" %}
Even if you plan to use the GUI to run your experiments, you still need to go through these steps!
{% endhint %}

## (Mac only) Homebrew and openssl/sqlite installation

To install homebrew:

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Afterwards, run the two following commands:

`brew install openssl`

`brew install sqlite`

## (Windows only) Install Python

Windows does not come with Python installed

You have multiple options, but here are two:

1. Install python from the [Windows store](https://learn.microsoft.com/en-us/windows/python/beginners)
2. Install python through [Anaconda or miniconda](https://docs.conda.io/projects/conda/en/stable/user-guide/install/download.html#anaconda-or-miniconda)

## DPU Installation

1. Navigate to the [DPU Github page](https://github.com/FYNCH-BIO/dpu)
2. Click `Releases` on the right side of the page

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

7\. Navigate to the DPU directory you just downloaded and unzipped:

* Use this command: `cd <path_to_dpu>`

{% hint style="info" %}
Windows users: you need python installed. If you install python and are met with 'python3 not found' try `python`, `py`, or `ipython` instead.
{% endhint %}

8\. Create a new [virtual environment](https://docs.python.org/3/library/venv.html) then activate it with the following command:

`python3 -m venv dpu-env`

`source dpu-env/bin/activate`

On Windows PowerShell:

`dpu-env\Scripts\Activate.ps1`

9\. Use `pip` to install all necessary dependencies.

First upgrade pip:

`python3 -m pip install --upgrade pip`

Then install everything:

`python3 -m pip install .`

{% hint style="info" %}
If you have issues with the setup script, reach out to us on the [forum!](https://www.evolver.bio/)
{% endhint %}

10\. You can now deactivate the virtual environment with the command below. You will only need to activate it again manually if you plan to run the DPU from the command line - the GUI use the environment automatically.

`deactivate`
