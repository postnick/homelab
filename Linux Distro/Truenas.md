https://www.youtube.com/watch?v=Hdw1ELFaZH8

*This totorial will allow you to use your install drive as well as a ZFS disk on truenas.

[Raid Owl Video](https://www.youtube.com/watch?v=Hdw1ELFaZH8)

[Reddit Thread](https://www.reddit.com/r/truenas/comments/lgf75w/scalehowto_split_ssd_during_installation/)


I have had a scale installation on two 500"GB" ssds. Which is quite a waste given that you can't share anything on the boot-pool. With a bit of digging around I figured out how to partition the install drives and put a second storage pool on the ssds.

First, a bunch of hints and safety disclaimers:

You follow this on your own risks. I have no clue what the current state of scale is wrt to replacing failed boot drives etc and have no idea if that will work with this setup in the future.
Neither scale nor zfs respect your disks, if you want to safe-keep a running install somewhere remove the disk completely.
Don't ask me how to go from a single disk install to a boot-pool mirror with grub being installed and working on both disks. I tried this until I got it working, backed up all settings and installed directly onto both ssds.
Here's a rescue image with zfs included for the probable case something goes to shit:
https://github.com/nchevsky/systemrescue-zfs/tags
The idea here is simple. I want to split my ssds into a 64gb mirrored boot pool and ~400GB mirrored storage pool.

create a bootable usb stick from the latest scale iso (e.g with dd)

boot from this usb stick. Select to boot the Truenas installer in the first screen (grub). This will take a bit of time as the underlying debian is loaded into ram.

When the installer gui shows up chose shell out of the 4 options     

We're going to adjust the installer script:

If you want to take a look at it beforehand it's in this repo under "/usr/sbin/truenas-install"
https://github.com/truenas/truenas-installer

```sh
# to get working arrow keys and command recall type bash to start a bash console:
bash    
# find the installer script, this should yield 3 hits
find / -name truenas-install
# /usr/sbin/truenas-install is the one we're after
# feel the pain as vi seems to be the only available editor
vi /usr/sbin/truenas-install
```
We are interested in the create_partition function, specifically in the call to create the boot-pool partition
```sh
line ~3xx:    create_partitions()
...
# Create boot pool
if ! sgdisk -n3:0:0 -t3:BF01 /dev/${_disk}; then
    return 1
fi
```
move the courser over the second 0 in -n3:0:0 and press x to delete. Then press 'i' to enter edit mode. Type in '+64GiB' or whatever size you want the boot pool to be. press esc, type ':wq' to save the changes:
```sh
# Create boot pool
if ! sgdisk -n3:0:+64GiB -t3:BF01 /dev/${_disk}; then
    return 1
fi
```
You should be out of vi now with the install script updated. let's run it and install truenas scale:
```sh
/usr/sbin/truenas-install
```
The 'gui' installer should be started again. Select '[]install/upgrade' this time. When prompted to select the drive(s) to install truenas scale to select your desired ssd(s). They were sda and sdb in my case. Set a password or don't (I didn't because im not on a us-keyboard layout and hence my special characters in passwords are always the wrong ones when trying ot get in later). I also didn't select any swap. Wait for the install to finish and reboot.

Create the storage pool on the remaining space:
Once booted connect to the webinterface and set a password. Enable ssh or connect to the shell in System -> Setting. That shell keep double typing every key press so I went with ssh.

figure out which disks are in the boot-pool:
```sh
zpool status boot-pool
# and 
fdisk -l   
```
should tell you which disks they are. They'll have 3 or 4 partitions compared to disks in storage pools with only 2 partitions. In my case they were /dev/sda and /dev/sdb

next we create the partitions on the remaining space of the disks. The new partition is going to be nr 4 if you don't have a swap partition set up, or nr 5 if you have:

```sh
# no swap
#For SATA Drives
sgdisk -n4:0:0 -t4:BF01 /dev/sdb
#For NVME Drives
sgdisk -n4:0:0 -t4:BF01 /dev/nvme0n1
# swap
#For SATA Drives
sgdisk -n5:0:0 -t4:BF01 /dev/sdb
#For NVME Drives
sgdisk -n5:0:0 -t4:BF01 /dev/nvme0n1
```
update the linux kernel table with the new partitions
```sh
partprobe
```
and figure out their ids:
```sh
#For Sata Drives
fdisk -lx /dev/sdX
#For NVME Drive
fdisk -lx /dev/nvme0n1
```
finally we create the new storage pool called ssd-storage (name it whatever you want):
```sh
#NVME P4 with no swap. 
zpool create -f ssd-storage /dev/nvme0n1p4
```
export the newly created pool:
```sh
zpool export ssd-storage
```
and go back to the webinterface and import the new ssd-storage pool in the storage tab.

If something goes horribly wrong boot up the rescue image and destroy all zpools on the desired boot disks. Then open up gparted and delete all partitions on the boot disks. If you reboot between creating the storage partitions and creating the zpool the server might not boot because some ghostly remains of an old boot-pool linger in the newly created partitions. boot the rescue disk and create the storage pool from there. They are (currently) compatible.

## Fix a ZPOOL 
```shell
export PATH=$PATH:/usr/sbin  
```
After runing this, the ZPOOL should just work?  - Sources needed? 


## Increasing [[ZFS ARC]] Size

First you need to SUDO SU to get into an elevated session
then type 
```bash
zpool status
```

after that works you can paste in this code whitch is about 24 gigs in BYTES
31.2 Total GB - 4GB for Services = 27.2GB for ZFS Arc

$$
27.2 GB * 1024 MB * 1024 KB * 1024 B = 29205777612 bytes
$$

```bash
#For 32 GB ram
echo 29205777612 > /sys/module/zfs/parameters/zfs_arc_max

#For 16 gig of ram system
echo 12992276070 > /sys/module/zfs/parameters/zfs_arc_max
```



## Performance Testing

To **test the write speed** of your TrueNAS array, you can use various methods. Here are some options:

1. **`fio` Command**:
    
    - `fio` is a versatile benchmarking tool that can test both individual disks and pools.
    - To test individual disks, you can run:
        ```shell
        fio --name=mytest --ioengine=sync --rw=write --bs=1M --numjobs=1 --size=10G --runtime=60s --time_based
        ```
    - Adjust the parameters (such as `--size`, `--runtime`, etc.) as needed.
2. **`dd` Command**:
    
    - While `dd` can give you a rough idea, it’s not the most accurate method.
    - Example:
        
        ```shell
        dd if=/dev/zero of=/mnt/pool/test.dd bs=1M count=1024; sync
        ```
        
    - Replace `/mnt/pool/test.dd` with an appropriate path on your system.
3. **`diskinfo` Command**:
    
    - Use `diskinfo` to get basic information about your disks.
    - Example:
        ```shell
        diskinfo -t /dev/adaX
        ```
    - This provides transfer rates for different parts of the disk (outside, middle, inside).
4. **Network Speed Testing**:
    - If you suspect network limitations, test with `iperf` from a Windows VM to the TrueNAS VM.
    - This rules out network bottlenecks.
5. **Archiving Performance**:
    - Create a dataset with no compression (compression is the default).
    - Transfer more data than your system’s RAM to avoid caching.

Remember that these tests provide approximate results, and real-world performance may vary. Ensure your system meets your requirements and monitor it during actual usage. 🚀