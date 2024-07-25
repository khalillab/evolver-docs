# View the Server Log and Restart Server

## About Server Logs

We use [`supervisor`](http://supervisord.org/running.html) to run and manage the logs for the [eVOLVER server](../software/server-raspberry-pi/). eVOLVERs should come pre-configured with this.

We also provide a utility monitoring and restart script, `evolvercron` and `server_monitor.sh`. To use, add the crontab job line in `evolvercron` into your cron installation.

## View Server Logs

{% hint style="info" %}
To understand what you see in the server log, take a look at the information [here](../software/server-raspberry-pi/#serial-message-structure).
{% endhint %}

1. Connect to your server via the following command (replace `<eVOLVER_IP>` with your eVOLVER's IP)
   1. `ssh pi@<eVOLVER_IP>`
2. Enter the eVOLVER server's password

### \[Option 1] View the server log _live_

1. Enter the supervisor environment via the following command:
   1. `sudo supervisorctl`
2. Use the following command to follow the eVOLVER server log:
   1. `tail -f evolver`
3. `Ctrl+C` to exit

### \[Option 2] View the whole server log file

The [server monitor](https://github.com/FYNCH-BIO/evolver/blob/694ffbd91d6392bb84f2675f95c6fa81add58f03/utils/server\_monitor.sh#L4) stores the log file here: `/var/log/supervisor/`&#x20;

You can either view there or move it to your computer for more analysis

## Restart the eVOLVER Server

1. If you are currently following the eVOLVER server in `supervisorctl`, use `ctrl+C` to exit. Otherwise, follow steps to [view server log](view-the-server-log-and-restart-server.md#view-server-logs).
2. Enter the following command:
   1. `restart evolver`
3. If you quickly follow the server via `tail -f evolver` you should see it restart
