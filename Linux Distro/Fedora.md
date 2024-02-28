
Currently [[Fedora]] is my favorite Desktop to run. I prefer the Workstation edition that features [[GNOME]] with a few [[GNOME Extension|Extensions]] installed. 
 
[[Fedora]] - and some [[DNF]] settings

[Good Video from TechHut Youtube](https://www.youtube.com/watch?v=RrRpXs2pkzg) Last updated May 12 2022 for Fedora 36

### Fix DNF Speed:
``` shell
sudo nano /etc/dnf/dnf.conf 
```
Entere in these:GNOME Tour and Greeter
```shell
fastestmirror=True 
max_parallel_downloads=10 
defaultyes=True
keepcache=True
```
### RPM Fusion Enable
Enabling the [RPM Fusion](https://rpmfusion.org/Configuration) repositories:

### Codec for Media
Installing plugins for playing movies and music
```shell
sudo dnf groupupdate multimedia --setop="install_weak_deps=False" --exclude=PackageKit-gstreamer-plugin
```

### [[Flatpak Lists|Flatpak]]
[flatpak.org](https://flatpak.org/setup/Fedora) to setup Fedora via the appstore.
OR
```shell
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

### Final Steps
Setup your [[SSH Key Notes|SSH Keys]] on your new system

### Setup [[Aliases]]
Aliases make the terminal a bit easier to use. 

### Fedora Colors
HEX \#0B57A4![[FedoraHex.png]]

[[Shell Changes]] like adding Fish rather than Bash
