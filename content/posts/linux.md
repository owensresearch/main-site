---
author: "Justin Owens"
date: 2021-01-03
title: "Linux Notes"
---

# SSH Key Based Login

## Setup SSH Keys
1. Use PuttyGen to generate public/private key pair.
2. Copy the OpenSSH Public Key from the PuttyGen window (the save public key will not export in correct format).
3. Paste the Public key into the file ~/home/.ssh/authorized_keys
4. Export Private Key using the save button within PuttyGen (we need the .ppk file).
5. Attach this Private Key to Putty.exe under Auth. 
6. Make sure you're using username@x.x.x.x as the SSH target.


## Disable Sudo Password
`sudo visudo -f /etc/sudoers`  
Add `username ALL=(ALL) NOPASSWD:ALL` to bottom of file replacing username with the user in question.

# Change Repo

`/etc/apt/sources.list`

### Default Debian 10 Buster Sources

```
deb http://deb.debian.org/debian buster main
deb-src http://deb.debian.org/debian buster main

deb http://deb.debian.org/debian-security/ buster/updates main
deb-src http://deb.debian.org/debian-security/ buster/updates main

deb http://deb.debian.org/debian buster-updates main
deb-src http://deb.debian.org/debian buster-updates main
```
> *Don't forget `apt update` after making changes..*
{.is-info}


https://wiki.debian.org/SourcesList

# Linux Single User Mode

## GRUB
1. Press "e" to modify GRUB.
2. Add `single init=/bin/bash` at end of linux line.
3. Mount filesystem with `mount -rw -o remount /`

## Bring Network Up
```
ifconfig eth0 xxx.xxx.xxx.xxx netmask xxx.xxx.xxx.x up

route add default gw xxx.xxx.xxx.x

ip route list
```