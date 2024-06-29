---
title: Installing Arch Linux
draft: false
tags:
---
Uplink : [[Arch linux]]

## Download

First step is to download arch linux iso
[Download](https://archlinux.org/download/)

## Verify

Second Verifying iso
Download b2sums.txt, sha256sums.txt and text ending with iso.sig 
then go to that directory and run this commands

first for b2sums.txt
```bash
b2sum -c b2sums.txt --ignore-missing
```

second for sha256sums.txt
```bash
sha256sum -c sha256sums.txt --ignore-missing
```

now last step to verify if the iso isn't downloaded from any malicious website

> [!NOTE] 
> must have installed GnuPG on the system

first run this command to download and import the public key to verify the signature
```bash
gpg --auto-key-locate clear,wkd -v --locate-external-key pierre@archlinux.org
```

next we will use this command to check if the signature is valid
```bash
gpg --verify <the file ending with .iso.sig>
```

## Flashing

after that flash using any tool you want
for e.g. `dd command`
```bash
sudo dd if=./arch.iso of=/dev/sdx bs=4M status=progress
```
use this command to check your usb drive `lsblk`

Also make sure you have disabled secure boot in bios

## Now installation

### Connect Wifi

either connect with ethernet or wifi 
ethernet is easy just have to plug ethernet to machine
for wifi follow steps

```bash
iwctl
```

now we will be inside iwd and run this
```bash
device list
```

```bash
station wlan0 connect WIFINAME
```
wlan0 is device id which we got from `device list` previously
and enter the password of wifi

after that exit
```bash
exit
```

now to check if wifi is working
```bash
ping www.google.com
```

### SSH Connection

now this step is optional if you want to ssh into this machine for installation

first start the ssh service
```bash
systemctl start sshd
```

next set password
```bash
passwd
```
this step is necessary to ssh into this machine

after that ssh this machine from another machine using this command
```bash
ssh root@ipaddress
```
you can see your ip address by using this command `ip a s`

### Partitioning

Now it's time for partitioning disks

first check drives by running
```bash
lsblk
```

we will be using `gdisk` to partition
```bash
gdisk /dev/sdx
```

Inside of gdisk, you can print the table using the `p` command.

To create a new partition use the `n` command. The below table shows 
the disk setup I have for my primary drive

| partition | first sector | last sector | code | Type       |
| --------- | ------------ | ----------- | ---- | ---------- |
| 1         | default      | +512M       | ef00 | EFI        |
| 2         | default      | +4G         | ef02 | Boot       |
| 4         | default      | +50G        | 8309 | Linux luks |
| 5         | default      | default     | 8302 | Linux Home |

If you have a second drive for your home disk, then your table would be as 
follows.

To find the codes I used `L` after the `last sector` and type the partition you want like `efi` it will tell you the code

after partitioning type `w` to write it

### Encryption

Load the encryption modules to be safe.

```bash
modprobe dm-crypt
modprobe dm-mod
```

Setting up encryption on our luks partiton

```bash
cryptsetup luksFormat -v -s 512 -h sha512 /dev/sdx
```

Enter in your password and **Keep it safe**. There is no "forgot password" here.

If you have a home partition, then initialize this as well

```bash
cryptsetup luksFormat -v -s 512 -h sha512 /dev/sdx
```

- `cryptsetup`: This is the command used to manage disk encryption on Linux systems.
- `luksFormat`: This subcommand initializes a LUKS partition on the specified device.
- `-v`: This option stands for "verbose" mode, which will provide more detailed output during the encryption process.
- `-s 512`: Specifies the key size in bits. In this case, it sets the key size to 512 bits.
- `-h sha512`: Specifies the hash algorithm to use for key derivation. Here, `sha512` (SHA-512) is chosen, which is a secure hash algorithm.
- `/dev/sdx`: This represents the device (e.g., a hard disk or a partition) on which the LUKS encryption will be applied. Replace `sdx` with the actual device identifier (like `sda`, `sdb`, etc.)

After entering this command it will tell to give a password

### Mounting

First we need to decrypt and Mount the drives:

```bash
cryptsetup open /dev/sdx luks_lvm
```

- `cryptsetup`: This is the command used to manage disk encryption on Linux systems.
- `open`: This subcommand is used to open (unlock) a LUKS-encrypted partition.
- `/dev/sdx`: This is the path to the LUKS-encrypted partition you want to open. Replace `sdx` with the actual partition identifier on your system.
- `luks_lvm`: This is the name you are assigning to the unlocked device mapper device. You can choose a different name if preferred.

After this we need to create a physical volume using lvm 
```bash
pvcreate /dev/mapper/luks_lvm
```

followed by a volume group named `arch`
```bash
vgcreate arch /dev/mapper/luks_lvm
```

then we can create a logical volume for our swap
```bash
lvcreate -n swap -L 4G -C y arch
```
here `-n` means name,
`-L` means size, `[+|-]Size[kKmMgGtTpPeE]`
`-C` means contiguous allocation and `y` for yes 

now to create a root volume
```bash
lvcreate -n root -l +100%FREE arch
```
`-l` for dynamic allocation of storage `[+|-]LogicalExtentsNumber[%{VG|FREE|ORIGIN}]`

Now we will decrypt and mount for home partition

```bash
cryptsetup open /dev/sdx arch-home
```

Now setting up our file system

first partition we will format for EFI 
```bash
mkfs.fat -F32 /dev/sda1
```

second partition we will format for boot
```bash
mkfs.ext4 /dev/sda2
```

For our root and home file system we will use btrfs

for root
```bash
mkfs.btrfs -L root /dev/mapper/arch-root
```

for home
```bash
mkfs.btrfs -L home /dev/mapper/arch-home
```

last swap
```bash
mkswap /dev/mapper/arch-swap
```

Now mounting all partitions

first enabling swap
```bash
swapon /dev/mapper/arch-swap
swapon -a
```
`swap -a` to mark it as available

mount root
```bash
mount /dev/mapper/arch-root /mnt
```

make directory
```bash
mkdir -p /mnt/{home,boot}
```

now we can mount `boot` and `home`
```bash
mount /dev/sda2 /mnt/boot
mount /dev/mapper/arch-home /mnt/home
```

last to make a `efi` directory
```bash
mkdir /mnt/boot/efi
```

and mount `efi`
```bash
mount /dev/sda1 /mnt/boot/efi
```
check by using `lsblk`

Now finally installing arch
```bash
pacstrap -K /mnt base linux linux-firmware
```

> [!TIP] Pro Tip
> before running pacstrap for faster download enable parallel downloads

```bash
vim /etc/pacman.conf
```
edit this file by uncommenting `ParallelDownloads 30` you can set any number of parallel downloads

then update by `pacman -Syy`

After this we have to save our file system to our newly installed system
this can be done by using `genfstab` command
```bash
genfstab -U -p /mnt > /mnt/etc/fstab
```
`-U` means generate fstab entries by using UUID's
`-p` means generate output suitable for parsing

now we can chroot into our new arch linux
```bash
arch-chroot /mnt /bin/bash
```

let's first download some important packages
```bash
pacman -S base-devel
```
this package provides some features for software development

then install any text editor
```bash
pacman -S neovim nano emacs
```

now we need to edit a file to configure our linux to decrypt our volumes when it starts up
```bash
nvim /etc/mkinitcpio.conf
```
now scroll down to `hooks` section and add `encrypt lvm2` in between `block` and `filesystems` then go ahead and save and exit

then we need to download and install `lvm2` package for the hook to be available
```bash
pacman -S lvm2
```
this will also regenerate our linux image

next we will setup our bootloader 
```bash
pacman -S grub efibootmgr
```

after that we need to install grub onto our boot partiton
```bash
grub-install --efi-directory=/boot/efi
```

first run this command to get the UUID of the luks partition
```bash
blkid /dev/sda3
```
and copy the UUID

open the grub config file
```bash
nvim /etc/default/grub
```
we will set some kernel parameters to our boot configuration
edit this to line to look like something this 
```bash
GRUB_CMDLINE_LINUX_DEFAULT="loglevel=3 quiet root=/dev/mapper/arch-root cryptdevice=1f6446de-23ee-486f-a38b-c1138b323ccc:luks_lvm"
```
paste the UUID we copied earlier into the `cryptdevice=`

after this we will setup our encrypted system so that we only have to use our password once
first create a folder
```bash
mkdir /secure
```

then we will create a key
for root
```bash
dd if=/dev/random of=/secure/root_keyfile.bin bs=512 count=8
```

for home
```bash
dd if=/dev/random of=/secure/home_keyfile.bin bs=512 count=8
```

next we will lock down the permission so that only root user can use this
```bash
chmod 000 /secure
```

its also a good idea to change the permission of initramfs as it will also contain the key file
```bash
chmod 600 /boot/initramfs-linux*
```

with our key file created we then need to add them to each of our partitions respectively
```bash
# for root
cryptsetup luksAddKey /dev/sda3 /secure/root_keyfile.bin

# for home
cryptsetup luksAddKey /dev/sda4 /secure/home_keyfile.bin
```

with our key files created
next to make sure the kernel can access them open
```bash
nvim /etc/mkinitcpio.conf
```
head down to the `FILES=()` and add this
```bash
FILES(/secure/root_keyfile.bin)
```
this will make sure the bootloader has access to this file when system starts up

next we will add to the home partition
first copy the UUID
```bash
blkid /dev/sda4
```
then open
```bash
nvim /etc/crypttab
```

in this go down and put everything like this
```bash
arch-home      UUID=<uuid>    /secure/home_keyfile.bin
```
the first column is for mount point second is for UUID and third points to our home's key file(password)

after adding this regenerate our linux image 
```bash
mkinitcpio -p linux
```

then we need to initialize our grub configuration
```bash
grub-mkconfig -o /boot/grub/grub.cfg
```

then another directory to our EFI
```bash
grub-mkconfig -o /boot/efi/EFI/arch/grub.cfg
```
this will enable grub for both bios and uefi system

some final setup

timezone
```bash
ln -sf /usr/share/zoneinfo/Asia/Kolkata /etc/localtime
```
you can always look for your time zone

seting up NTP
open
```bash
nvim /etc/systemd/timesyncd.conf
```

Add in the NTP servers
```bash
[Time]
NTP=0.arch.pool.ntp.org 1.arch.pool.ntp.org 2.arch.pool.ntp.org 3.arch.pool.ntp.org 
FallbackNTP=0.pool.ntp.org 1.pool.ntp.org
```

Enable timesyncd
```bash
systemctl enable systemd-timesyncd.service
```

Locale
```bash
nvim /etc/locale.gen
```

uncomment the UTF8 lang you want
```bash
en_IN UTF-8
```

```bash
locale-gen
```

```bash
nvim /etc/locale.conf
```

```bash
LANG=en_IN.UTF-8
```

hostname
```bash
nvim /etc/hostname
```
give any name to your host

set root password
```bash
passwd
```

next install zshell (optional)
```bash
pacman -S zsh
```

now we will create a user
```bash
useradd -m -G wheel -s /bin/zsh mk
```

creating password for user
```bash
passwd mk
```

setting default editor
```bash
export EDITOR=nvim
```

then open sudoers file to make your user powerfull
```bash
visudo
```

uncomment this line
```bash
%wheel ALL=(ALL:ALL) ALL
```

configuring network
```bash
pacman -S networkmanager
systemctl enable NetworkManager
```

if you want you can install desktop environment
```bash
pacman -S gnome
```

then enable display manager
```bash
systemctl enable gdm
```

after that installing microcode
```bash
# for intel processors
pacman -S intel-ucode

#for amd processors
pacman -S amd-ucode
```

after this we need to regenerate our grub config
```bash
grub-mkconfig -o /boot/grub/grub.cfg
grub-mkconfig -o /boot/efi/EFI/arch/grub.cfg
```

now everything is done exit the chroot
```bash
exit
```

then unmount all the drives
```bash
umount -R /mnt
```

and reboot
```bash
reboot now
```
