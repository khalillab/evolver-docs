# Server Troubleshooting

{% hint style="info" %}
For more information about the server software, see [here](../software/server-raspberry-pi/).
{% endhint %}

## Overview

If a parameter is not working properly, often the first place to check for issues is the server

## Guide

1. Monitor the server log file
   1. Guide [here](../guides/view-the-server-log-and-restart-server.md)
2. Any time you are troubleshooting the server, make sure to save your calibrations.json file in a secure location before going further
3. If the log file is not updating (via `evolver tail -f`)
   1. If you have manually edited the conf.yml file, most likely you have made an error somewhere there
      1. This could be formatting or a typo
      2. Copy a conf.yml that you know works (for example to [base eVOLVER conf.yml](https://github.com/FYNCH-BIO/evolver/blob/master/evolver/conf.yml))
         1. Using the server update [guide ](../guides/updating-the-evolver-server.md)as a reference
         2. ONLY copy the conf.yml to `home/pi/evolver/evolver/`
         3. Otherwise you will overwrite your calibration files
      3. Restart the server
         1. Stop following the server using `ctrl+C`
         2. Type `restart evolver`
         3. &#x20;`evolver tail -f`
      4. The server log should now be updating each cycle
   2. &#x20;If not, and you have not recently updated the evolver.py or other python files, [update them](../guides/updating-the-evolver-server.md)

## Relevant Forum Posts

[Directly Connecting to Rpi over USB](https://howchoo.com/pi/raspberry-pi-gadget-mode)

[Sudden Server Disconnections](https://www.evolver.bio/t/sudden-disconnections/295/6)

[Using Raspberry Pi 4 as a server](https://www.evolver.bio/t/troubleshooting-setting-up-raspberry-pi-4-as-evolver-server/186)

[ssh Connection Refused](https://www.evolver.bio/t/fixing-ssh-connection-refused-issues/354)

