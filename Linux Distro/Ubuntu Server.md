---
tags:
  - ubuntu
  - network
  - netplan
  - staticip
  - server
  - dhcp
  - linux
  - homelab
---
## Netplan  [[Network]] Config File
```bash
sudo nano /etc/netplan/00-installer-config.yaml
```

> [!Example]
> Example Configuration 
> ```yaml
> network:
>   version: 2
>   ethernets:
>     enp120:
>       addresses:
>       - 192.168.5.100/20
>       gateway4: 192.168.0.1
>       nameservers:
>         addresses:
>         - 192.168.0.100
>         - 192.168.0.101
> ```

```bash
sudo netplan apply
```

To Turn DHCP back on with Netplan
```yaml
network:
  version: 2
  ethernets:
    enp120:
      dhcp4: true
```

```bash
sudo netplan apply
```


[[Ubuntu]] server is a stable server version used in [[homelab]] and [[server]] environments
