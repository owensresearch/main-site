---
author: "Justin Owens"
date: 2020-06-18
title: "PiHole w/ DoH"
---

# Creating a PiHole VM w/ DoH to Cloudflare  
This is a brief guide on creating a new PiHole server that resolves DNS via Cloudflare over HTTPS.  It is assumed that the audience already has a working knowledge of their vender specific network equipment and virtualization platform in addition to some experience with Ubuntu Linux.

# Prep Work  

> **Automatic Updates**   
The entire reason I am building a PiHole server today is because I used a development copy of Ubuntu for the last one and I didn’t utilize automatic updates.  I set it up and forgot about it until one day I was no longer able to update PiHole and the Web UI essentially broke.  At the time of this post, 20.04 LTS is available with support until April 2025.  It is recommended to use a release such as this and enable automatic updates.
1. Deploy a new LTS Ubuntu image.  
2. Establish network connectivity; 1.1.1.1 can be used for DNS for now.  
3. `sudo apt update` and `sudo apt upgrade`  
4. `sudo apt install unattended-upgrades`  
5. `sudo nano /etc/apt/apt.conf.d/50unattended-upgrades`  
6. Remove the `//` before `"${distro_id}:${distro_codename}-updates";`  
7. `sudo nano /etc/apt/apt.conf.d/20auto-upgrades` and copy the below example:  
```
APT::Periodic::Update-Package-Lists "1";  
APT::Periodic::Download-Upgradeable-Packages "1";  
APT::Periodic::AutocleanInterval "7";  
APT::Periodic::Unattended-Upgrade "1";  
```
8. `sudo reboot` to give a fresh start before getting into PiHole install.  
> More info on enabling automatic updates can be found here https://libre-software.net/ubuntu-automatic-updates/  


# Install PiHole
- Here is a link to PiHole's github page https://github.com/pi-hole/pi-hole/#one-step-automated-install
- Assuming you trust them and/or me you can use this script `curl -sSL https://install.pi-hole.net | bash`
- Follow the prompts on your Ubuntu server.  As before, for now we can just select Cloudflare as our upstream DNS.  The defaults for everything should be fine.

## Create Cron Job to Automatically Update PiHole Package
1. `sudo apt install cron` and `sudo systemctl enable cron`
2. `sudo crontab -e`
3. Add `0 3 * * * sudo pihole -up` to the bottom of the file.
- PiHole will now update every morning at 3AM.


# Install Cloudflare DoH Daemon
1. Follow this guide https://docs.pi-hole.net/guides/dns-over-https/
2. Recommend to use the Manual Way.

## Update Cron for Cloudflare Daemon
`0 3 * * 0 sudo cloudflared update`  
`0 3 * * 0 sudo systemctl restart cloudflared`  
 - This updates cloudflared at 3AM every Sunday.