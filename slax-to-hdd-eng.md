# How to install slax (debian-based distro) to HDD.
<br>

## Bios : Legacy, Partition type : MBR.
<br>

## Preparations :
- Allocate one partition for root (/).
- Allocate one partition for swap (optional).
<br>

## Steps

1. Boot slax !

<br>
2. Open terminal (xterm) !
<br>
<br>
3. Format partition !

> \# mkfs.ext4 /dev/abc1

<br>
4. Mount partition !

> \# mount /dev/abc1 /mnt

<br>
5. Copy everything from slax root directory (/) to new root !

> \# cp -ax / /mnt

<br>
6. Chroot.

> \# cd /mnt

> \# mount -t proc proc proc/

> \# mount --rbind /sys sys/

> \# mount --rbind /dev dev/

> \# mount --rbind /run run/

> \# chroot /mnt /bin/bash

<br>
7. Edit fstab.

> \# cp /proc/mounts /etc/fstab
> \# mcedit /etc/fstab 

Note :
- Suit your need and preference !

<br>
8. Configure apt source !

Note : 

- Just leave the sources.list file and do "apt update and apt upgrade". 

> \# apt update

> \# apt upgrade

<br>
9. Choose timezone ! 

> \# dpkg-reconfigure tzdata

<br>
10. Configure locales !

> \# dpkg-reconfigure locales

<br>
11. Set hostname !

> \# echo "your_hostname" > /etc/hostname

<br>
12. Configure hosts file.

> \# mcedit /etc/hosts

<br>
13. Install grub package !

> \# apt install grub2

<br>
14. Set root password, make an user and its password !

> \# passwd

> \# useradd USERNAME -m

> \# passwd USERNAME 

<br>
15. Install bootloader to disk !

> \# grub-install /dev/abc

> \# update-grub

<br>
16. Exit chroot !

> \# exit

or Ctrl + D.

<br>
17. Reboot !

> \# systemctl reboot
