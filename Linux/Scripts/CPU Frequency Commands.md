shows every core CPU frequency refreshing

```bash
watch -n.5 "grep \"^[c]pu MHz\" /proc/cpuinfo"
```

shows the main core CPU frequency 
```bash
watch "lscpu | grep MHz"
```

to check the scaling
```bash
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```

Add this to a [[CRON]] for Proxmox devices to set powersave on reboot
```shell
crontab -e

add this line

@reboot  echo "powersave" | tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor >/dev/null 2>&1
```