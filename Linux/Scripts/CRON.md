---
tags:
  - network
  - cron script wakeonlan truenas dietpi proxmox
---
## Former Cronjob Table
| Server | Purpose | Code |
| ---- | ---- | ---- |
| Proxmox | Nightly Shutdown | 30 23 * * * /usr/sbin/shutdown -h now |
| Dietpi | Weekend Wakeup | 50 6 * * 0,6 sh /home/dietpi/wol.sh |
| Dietpi | Weekday Wakeup | 50 5 * * 1,2,3,4,5 sh /home/dietpi/wol.sh |
| Truenas | Nightly Shutdown | 30 23 * * * shutdown -h now |
| Truenas | Clear the DS Store fles | 0 7 * * *  find . -name ".DS_Store" -delete |



Truenas also has this to set powersave
```shell
crontab -e

@reboot echo "powersave" | tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor >/dev/null 2>&1
```


You can also rather than the five  Stars
you can do this - "@reboot COMMAND "

https://crontab-generator.org/
https://crontab.guru/


more text here

Weekend Wake up is at 6:50 AM
Weekday Wake up is at 5:50 AM
```bash
#This will wakeup my Proxmox/Truenas/Nextcloud about when I wake up
#Weekend Schedule                    
50 6 * * 0,6 sh /home/dietpi/wol.sh
#Weekday Schedule
50 5 * * 1,2,3,4,5 sh /home/dietpi/wol.sh
```
