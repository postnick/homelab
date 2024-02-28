---
Last Update: 2024-01-18
tags:
  - nfs
  - "#nano"
  - "#linux"
  - "#samba"
  - homelab
  - truenas
  - "#network"
---
How to add [[NFS]] shares from [[Truenas]] to auto start with your computer
Open the [[Terminal]]

[Auto Mount NFS Share](https://linuxize.com/post/how-to-mount-an-nfs-share-in-linux/)

## NFS install

Create the directory your want to mount your NFS Mount in. 
```bash
	mkdir /home/nick/Truenas
```

Open up the FSTAB file
```bash
	sudo nano /etc/fstab
```

Type or Paste this line into the bottom. 
```shell
#For Truenas using IP Address
truenas.post.home:/mnt/ZDISK/NAS /home/nick/Truenas nfs4 _netdev,auto 0 0
``` 

Exit [[Nano]] and Paste this code blow. 

```bash
	sudo systemctl daemon-reload
#AND
	sudo mount -a
```

## [Samba install](https://linuxconfig.org/how-to-mount-a-samba-shared-directory-at-boot)
```shell
touch ~/.smb
sudo apt install cifs-utils
```
and save your file like this:
```shell
username=nick
password=password
```

Then in the /etc/fstab
```shell
#Lower CASE ON THE samba side
//192.168.0.30/Truenas_NAS /home/nick/Truenas cifs credentials=/home/nick/.smb,noperm,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

To Test this out
```shell
sudo mount -a
#IF it works you won't see an error
```
