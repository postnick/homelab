---
tags:
  - network
  - server
  - linux
  - useful
Date: 2024-01-11
---
[Technotim](https://docs.technotim.live/posts/keepalived-ha-loadbalancer/)

apt install keepalived

Need to do this on both devices. 
Filename = /etc/keepalived/keepalived.conf

## Install
``` bash
sudo apt update 
sudo apt install keepalived 
sudo apt install libipset13
```

edit config file
```bash
sudo nano /etc/keepalived/keepalived.conf
```

```bash
#Primary Device 
#Be sure to check your ethernet name and SPACES MATTER
vrrp_instance VI_1 {
  state MASTER
  interface eth0
  virtual_router_id 55
  priority 150
  advert_int 1
  unicast_src_ip 192.168.1.2 #This is your Device IP
  unicast_peer {
    192.168.1.3 #This is your other devices IP
  }
  
  authentication {
    auth_type PASS
    auth_pass RazorSky
  }
  
  virtual_ipaddress {
    192.168.1.5/24  #This is your Shared IP
  }
}
```

```bash
#Secondary Backup Device
vrrp_instance VI_1 {
  state BACKUP
  interface eth0
  virtual_router_id 55
  priority 100
  advert_int 1
  unicast_src_ip 192.168.1.3 #This is your Device IP
  unicast_peer {
    192.168.1.2 #This is your other devices IP
  }
  
  authentication {
    auth_type PASS
    auth_pass RazorSky
  }
  
  virtual_ipaddress {
     192.168.1.5/24  #This is your Shared IP
  }
}
```

## Enable Services
```bash
sudo systemctl enable --now keepalived.service
```
Stopping the Service
```shell
sudo systemctl stop keepalived.service
```
Getting the status
	If this doesn't work. you probably did the wrong ETH device name in the config file. 
```bash
sudo systemctl status keepalived.service
```