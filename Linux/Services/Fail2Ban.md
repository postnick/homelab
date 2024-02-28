---
tags:
  - linux
  - useful
  - "#server"
  - Security
---
Fail2Ban is an #SSH filter

On my fail2ban Honeypot Use these commands to see how many failed attempts we have. 

```shell
sudo fail2ban-client status sshd
```


```shell
sudo zgrep 'Ban' /var/log/fail2ban.log*
```


# Shell Script to display results
```shell
#!/bin/bash
zgrep 'Ban' /var/log/fail2ban.log*
fail2ban-client status sshd
```