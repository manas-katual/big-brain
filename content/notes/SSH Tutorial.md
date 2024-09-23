---
title: SSH Tutorial
draft: false
tags:
---
Uplink : [[Dashboard]]

## Connecting to a server via openssh

Easiest way to access any remote server using ssh is 
```bash
ssh user@ipaddress
```

## Configuring the openssh client

Create a config file
```bash
vim ~/.ssh/config
```

now edit it
```bash
Host myserver
  Hostname 192.168.0.150
  Port 22
  User root

Host homelab
  Hostname 192.168.0.154
  Port 22
  User mk
```
you can name your host whatever you want. You can define as many host as you want

now simply connect like this
```bash
ssh myserver
```

## Using public/private keys

first generate ssh key
```bash
ssh-keygen
```

### Hard way

now follow steps
```bash
cat ~/.ssh/id_rsa.pub
```
It may not be named `id_rsa.pub` for everyone just `ls -l ~/.ssh` to see.
copy the output of `cat`
then connect to the remote server
```bash
ssh mk
```

after that create a file and paste the key
```bash
vim ~/.ssh/authorized_keys
```
if `.ssh` directory doesn't exist create one
now you can connect to the remote server without the password

### Easy way

on the local machine run this
```bash
ssh-copy-id -i ~/.ssh/id_rsa.pub root@192.168.0.150
```
here `-i` stands for input
it will ask for password of remote server and will copy the ssh key to the remote server

## Managing SSH keys

to make multiple ssh keys for different clients
```bash
ssh-keygen -t ed25519 -f ~/.ssh/kali-ssh-id -C "kali-vm"
```
`-t` for type `-f` for file `-C` for comment

after that 
```bash
ssh-copy-id -i ~/.ssh/kali-ssh-id.pub root@192.168.0.150
```