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

Setting up encryption on our luks lvm partiton

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

Mount the drives:

```bash
cryptsetup open /dev/sdx luks_lvm
```

- `cryptsetup`: This is the command used to manage disk encryption on Linux systems.
- `open`: This subcommand is used to open (unlock) a LUKS-encrypted partition.
- `/dev/sdx`: This is the path to the LUKS-encrypted partition you want to open. Replace `sdx` with the actual partition identifier on your system.
- `luks_lvm`: This is the name you are assigning to the unlocked device mapper device. You can choose a different name if preferred.

For home partition

```bash
cryptsetup open /dev/sdx arch-home
```
