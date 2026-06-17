---
mocs:
    - "[[public-notes/03-resources/tools.moc.md|Tools & Environment]]"
tags:
    - dev/tools
---

# About
This is my personal guide for a minimal installation of arch linux

> [!NOTE]  
> I'm newbie in linux so this is so explanatory for me

## Table Of Contents
[[#About|About]]
- [[#1. Prerequesites|1. Prerequesites]]
- [[#2. Pre-installation|2. Pre-installation]]
	- [[#2. Pre-installation#2.1 Prepare Installation medium|2.1 Prepare Installation medium]]
	- [[#2. Pre-installation#2.2  Boot the live environment|2.2  Boot the live environment]]
- [[#3. First steps: Basic Stuff|3. First steps: Basic Stuff]]
	- [[#3. First steps: Basic Stuff#3.1 Keyboard|3.1 Keyboard]]
	- [[#3. First steps: Basic Stuff#3.2 Internet Connection|3.2 Internet Connection]]
	- [[#3. First steps: Basic Stuff#3.3 Update system clock|3.3 Update system clock]]
	- [[#3. First steps: Basic Stuff#3.4 verify drivers and boot mode|3.4 verify drivers and boot mode]]
- [[#4. partition, format and mount your disks|4. partition, format and mount your disks]]
	- [[#4. partition, format and mount your disks#4.1 Create your partition scheme|4.1 Create your partition scheme]]
		- [[#4.1 Create your partition scheme#Old Scheme (Windows + arch)|Old Scheme (Windows + arch)]]
		- [[#4.1 Create your partition scheme#New Scheme (Only Arch)|New Scheme (Only Arch)]]
	- [[#4. partition, format and mount your disks#4.2 Format|4.2 Format]]
	- [[#4. partition, format and mount your disks#4.3 Mount|4.3 Mount]]
- [[#5. Install packages|5. Install packages]]
	- [[#5. Install packages#5.1 Rank Mirrors|5.1 Rank Mirrors]]
	- [[#5. Install packages#5.2 Install base packages|5.2 Install base packages]]
- [[#6. Configure the System|6. Configure the System]]
	- [[#6. Configure the System#6.1 gen the fstab file|6.1 gen the fstab file]]
	- [[#6. Configure the System#6.2 chroot|6.2 chroot]]
	- [[#6. Configure the System#6.3 Timezone|6.3 Timezone]]
	- [[#6. Configure the System#6.4 set locales|6.4 set locales]]
	- [[#6. Configure the System#6.5 manage system users|6.5 manage system users]]
	- [[#6. Configure the System#6.6 set the host name (name of your pc)|6.6 set the host name (name of your pc)]]
- [[#7. Install bootloader (grub)|7. Install bootloader (grub)]]
	- [[#7. Install bootloader (grub)#7.1 for a windows multi-boot system|7.1 for a windows multi-boot system]]
- [[#8. Install Graphincs Drivers|8. Install Graphincs Drivers]]
	- [[#8. Install Graphincs Drivers#11. Active some services|11. Active some services]]
- [[#12. Exit from the installation an reboot|12. Exit from the installation an reboot]]
- [[#13. Post installation|13. Post installation]]
	- [[#13. Post installation#13.1 display server|13.1 display server]]
	- [[#13. Post installation#13.2 Install your desktop environment (de) or window manager (wm)|13.2 Install your desktop environment (de) or window manager (wm)]]
	- [[#13. Post installation#13.3 Additional packages|13.3 Additional packages]]
	- [[#13. Post installation#14. Post installation|14. Post installation]]
	- [[#13. Post installation#Credits|Credits]]


# 1. Prerequisites
1. Disable Secure Boot. It can be enabled after installation
2. Disable Fast Boot
3. Disable Hibernation.
4. If You are dual booting. Check if the EFI or the boot partition of windows is more than 100MB as it may cause problems.

# 2. Pre-installation
## 2.1 Prepare Installation medium
1. Install the Latest Arch-Linux ISO file from Arch (https://archlinux.org/download/)[ISO]
3. Burn it into a usb
4. You can use Balena Etcher, Rufus if you are on windows. If you are on Arch read the arch wiki to create an Arch USB USB flash installation medium

## 2.2  Boot the live environment
1. Plug the USB into a USB port and go into the BIOS by smashing that F2 or F12 or Del button and change the boot priority so that the Arch USB is on number 1. Save and Exit


# 3. First steps: Basic Stuff
You will be logged in on the first virtual console as the root user

## 3.1 Keyboard
1. Set the keymap 
```bash
loadkeys es
```

2. Set your Keyboard Layout. Example for latin-american-spanish layout
```bash
localectl set-keymap la-latin1
```

## 3.2 Internet Connection
Ensure your network interface is listed and enabled
```bash
ip link
```
+ For wireless and WWAN, make sure the card is not blocked with rfkill.
+  Ethernet—plug in the cable.
+ Wi-Fi—authenticate to the wireless network using iwctl.

```
$ iwctl
[iwd]# device list
[iwd]# station device scan
[iwd]# station device get-networks
[iwd]# station device connect SSID
[iwd]# exit
```
Check if it is connected by pinging a website
```
ping -c 1 gnu.org
```

## 3.3 Update system clock
Example for Colombia
```bash
timedatectl set-timezone "America/Bogota"
```

## 3.4 verify drivers and boot mode

```bash
ls /sys/firmware/efi/efivars/
cat /sys/firmware/efi/fw_platform_size
```

# 4. partition, format and mount your disks

## 4.1 Create your partition scheme
I recommend you to use gparted throughout the gparted distro live usb to partition your disks, especially when you're dealing with multiple os in your pc

other alternative is to partition your disk running `cfdisk` command

There are many partitions schemes that you can use as reference, you should google for a scheme that fit with your needs. In my case i'm working with the following scheme: (output of `lsblk` command)

you should check the space for your swap partition accordingly with your hardware specs (google it)

### Old Scheme (Windows + arch)

> [!NOTE]  
> The scheme right below is for dual boot (windows + arch, sdb is and ssd and sda is an hdd)

```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda      8:0    0 931.5G  0 disk 
├─sda1   8:1    0 871.1G  0 part /home
├─sda2   8:2    0     8G  0 part [SWAP]
└─sda3   8:3    0  52.4G  0 part /
sdb      8:16   0 223.6G  0 disk 
├─sdb1   8:17   0   100M  0 part /boot/efi
├─sdb2   8:18   0    16M  0 part 
├─sdb3   8:19   0   223G  0 part 
└─sdb4   8:20   0   512M  0 part 
```

where:
* `sda1` is my `/home` part
* `sda2` is my `swap` part
* `sda3` is my `/` (root) partition
* `sdb1` is the where in installed the `grub`
* Other sdb* partitions are for windows

### New Scheme (Only Arch)
Update, I have removed Windows, leaving arch linux as my unique os, the my partitions now looks like this:
```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda      8:0    0 931.5G  0 disk 
└─sda1   8:1    0 931.5G  0 part /home
sdb      8:16   0 223.6G  0 disk 
├─sdb1   8:17   0   100M  0 part /boot/efi
├─sdb2   8:18   0 157.5G  0 part /home/jfmonsa/Desktop/extstorage
├─sdb3   8:19   0    16G  0 part [SWAP]
└─sdb4   8:20   0    50G  0 part /      8:0    0 931.5G  0 disk 
```
+ sda is hhd, sdb is ssd
## 4.2 Format
```bash
mkfs.ext4 /dev/sda1 #for /home
mkfs.ext4 /dev/sda3 #for root ( / )

#swap format
mkswap /dev/sda2
swapon /dev/sda2
```

## 4.3 Mount
```bash
mount /dev/sda3 /mnt #mount root partition
mount /dev/sda1 /mnt/home #mount /home partition
```
If we are in a multiple-os pc , don't format the /boot/efi partition. only mount it
```bash
mkdir -p /mnt/boot/efi
mount /dev/sdb1 /mnt/boot/efi
```

# 5. Install packages

## 5.1 Rank Mirrors
1. Archlinux uses servers to get the packages we need to install. Having good mirrors means packages install faster as well may prevent packages from out of date due to server being out of sync

2. Create a backup of your current mirrorlist
```bash
cp /etc/pacman.d/mirrorlist /etc/pacman.d/mirrorlist.bak
```

3. Get the fastest mirrors for you
```bash
pacman -Sy
pacman -S pacman-contrib
rankmirrors -n 10 /etc/pacman.d/mirrorlist.bak > /etc/pacman.d/mirrorlist
```

## 5.2 Install base packages
```bash
$ pacstrap -K /mnt base linux linux-firmware linux-headers base-devel  vim git  dhcpcd man
```
If you need add the following packages

+ For wireless: `networkmanager wpa_supplicant network-manager-applet`
+ For Bluetooth: `bluez bluez-utils`
+ For intel CPU: `intel-ucode`
+ For amd CPU: `amd-ucode`


# 6. Configure the System

## 6.1 gen the fstab file
generate and fstab file that contains our UUID(house address) of our drives.
```bash
genfstab -U /mnt >> /mnt/etc/fstab
```
## 6.2 chroot
Change the root to your new system
run `arch-chroot /mnt`

## 6.3 Timezone
```bash
#To show all Regions
ls /usr/share/zoneinfo/ 
# To show cities example with canada
$ ls /usr/share/zoneinfo/Canada/
# Replace Region with Country and city with city
$ ln -sf /usr/share/zoneinfo/Region/City /etc/localtime       
$ hwclock --systohc
```

## 6.4 set locales
```bash
vim /etc/locale.gen
```
search your language and uncomment in my case I uncommented the lines `en_US.UTF-8`
```bash
locale-gen
echo LANG=en_US.UTF-8 > /etc/locale.conf
export LANG=en_US.UTF-8
```

## 6.5 manage system users
```bash
#set root password
passwd
#create a normal (non-super-user) replace with your preferred user name
useradd -m user_name
ls -l /home
passwd user_name #password for the prev user
usermod -aG wheel user_name #adding user to groups
# is the same as edit sudoers
# Uncomment %wheel ALL=(ALL:ALL) ALL
# Also add     Defaults timestamp_timout=0              // just prompts user to type password again after a long time

visudo
```

## 6.6 set the host name (name of your pc)
in my case my hostname is `main-pc`

```bash
echo main-pc > /etc/hostname 
cat /etc/hostname
```
then edit the file /etc/hosts
```bash
vim /etc/hosts
```
add the following lines:
```
127.0.0.1     localhost
::1           localhost
127.0.1.1     Archfish.localdomain    localhost
```

# 7. Install bootloader (grub)
> [!NOTE]  
>  if you're working with a multi-distro pc (sever[]()al   linux distros), dont install the grub, only run `grub-update` in the other main distro

> [!NOTE]  
>  os-prober only if you are dual booting with windows

```bash
pacman -S grub efibootmgr dosfstools mtools os-prober
grub-install --target=x86_64-efi --bootloader-id=grub_uefi --recheck
grub-mkconfig -o /boot/grub/grub.cfg
install os-prober
```
## 7.1 for a windows multi-boot system
the edit the following file `vim /etc/default/grub` and uncomment the following line 
```bash
#GRUB_DISABLE_OS_PROBER=false
```

# 8. Install Graphincs Drivers
+ For nvidia: https://github.com/QuantiniumX/Guide-to-install-Arch-Linux/blob/main/Graphics/Nvidia.md

## 11. Active some services
```bash
sudo pacman -S networkmanager wpa_supplicant dhcpcd
systemctl enable dhcpcd.service
systemctl enable NetworkManager.service
# optional
systemctl enable wpa_supplicant.service
```

# 12. Exit from the installation an reboot
```bash
exit #exit from chroot
umount -lR /mnt
reboot
```

# 13. Post installation
## 13.1 display server
To have a graphical environment you must install a display manager, the most common option is `xorg`, but there is other much interesting project called `wayland` which is a very new project with little support

to install xorg:
```bash
set-keymap la-latin1 # set keyboard again xd

pacman -Sy archlinux-keyring && pacman -Su # solve some isues with pacman

sudo pacman -Syu # update your system
sudo pacman -S xorg-apps xorg-server xorg-xinit

sudo pacman -S gnome gdm #install your display manager, you could use the more customizable lightdm

sudo systemctl enable gdm
```

## 13.2 Install your desktop environment (de) or window manager (wm)
```
sudo pacman -S awesome
```
I'm currently using `awesomewm` as my wm but you can use whatever you want.

list of de's:

* gnome, kde, lxqt, lxde

list's of window managers:
* awesomewm (beginners) (hyper-customizable)
* qtile (beginners)
* bspwm (hyper-customizable)
* i3 (hyper-customizable)
* sway (i3 for wayland)
* xmonad (written in Haskell)
* dwm

read [this](https://itsfoss.com/best-window-managers/) to get an idea of what a wm is

## 13.3 Additional packages

## 14. Post installation

## Credits
+ I Updated this personal guide base on https://github.com/QuantiniumX/Guide-to-install-Arch-Linux