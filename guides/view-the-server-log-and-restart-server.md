# View the Server Log and Restart Server

## About Server Logs

We use [`supervisor`](http://supervisord.org/running.html) to run and manage the logs for the [eVOLVER server](../software/server-raspberry-pi/). eVOLVERs should come pre-configured with this.

We also provide a utility monitoring and restart script, `evolvercron` and `server_monitor.sh`. To use, add the crontab job line in `evolvercron` into your cron installation.

## View Server Logs

1. Connect to your server via the following command (replace `<eVOLVER_IP>` with your eVOLVER's IP)
   1. `ssh pi@<eVOLVER_IP>`
2. Enter the eVOLVER server's password
3. Enter the supervisor environment via the following command:
   1. `sudo supervisorctl`
4. Use the following command to follow the eVOLVER server log:
   1. `tail -f evolver`

{% hint style="info" %}
To understand what you see in the server log, take a look at the information [here](../software/server-raspberry-pi/#serial-message-structure).
{% endhint %}

## Restart the eVOLVER Server

1. If you are currently following the eVOLVER server in `supervisorctl`, use `ctrl+C` to exit. Otherwise, follow steps 1-3 in the above [guide](view-the-server-log-and-restart-server.md#view-server-logs).
2. Enter the following command:
   1. `restart evolver`
3. If you quickly follow the server via `tail -f evolver` you should see it restart
