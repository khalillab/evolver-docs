# Change Your conf.yml File

## Overview

[About the conf.yml file](../software/server-raspberry-pi/configuration-files-conf.yml.md)

Reasons you might want to do this:

1. Changing [broadcast timing](../software/server-raspberry-pi/#conf.yml) - ie how often the s erver cycles
2. [Adding an experimental parameter](../extensions/adding-a-new-experimental-parameter/)

## Guide

{% hint style="info" %}
\[Optional] Before doing this, save the conf.yml file you are using, if you don't already have it saved. You can use the following command in a terminal window:

`scp pi@<your-IP-address>:/home/pi/evolver/evolver/conf.yml`&#x20;
{% endhint %}

1. In a terminal, navigate to the folder in the server files containing the conf.yml file you want to change to
   1. For example if you want to change to the stir pause conf.yml:
      1. `cd <your-directory>/evolver/alternate_conf_files/stir_pause_for_OD_reads`&#x20;
   2. For example if you want to change to the default conf.yml:
      1. `cd <your-directory>/evolver/`
2. Copy over your new conf.yml file (overwriting the old one)
   1. Input the following command:
      1. `scp conf.yml pi@<your-IP-address>:/home/pi/evolver/evolver/`
   2. Input your eVOLVER server's password
3. Restart your eVOLVER server
   1. Input the following command (replaced with your eVOLVER's IP)
      1. `ssh pi@<your-IP-address>`
   2. Input your eVOLVER server's password
   3. Input the following commands to restart the server
      1. `sudo supervisorctl`
      2. `restart evolver`&#x20;
4. Check the server log files to see that it is cycling properly
   1. While still in supervisorctl, input:
      1. `tail -f evolver`
   2. More about the server log [here](view-the-server-log-and-restart-server.md)
