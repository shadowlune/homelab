# Raspberry Pi Home Server
This repository is a collection of tutorials for hosting variety of server applications on Raspberry Pi 400 using Docker and Portainer.
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/f1bbca61-1616-406a-955b-1dcb9a8da494" width="700">
</p>

## Prerequisite
- Raspberry Pi 400 or any other Raspberry Pi you have available
- Micro SD card
- Power supply
- Display (Optional)
- HDMI Cable (Optional)
- External Hard Drive (Optional)

## Installing the Operating System with [Raspberry Pi Imager](https://www.raspberrypi.com/software/)
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/757d4739-85bb-4796-a87c-42bfa93a02c8" width="500">
</p>

Beginner to command-line interface (CLI)
- Getting the complete kit for Raspberry Pi 400 would be ideal since everything has been installed for you, all you have to do is just plug in the power supply and monitor and you are good to go.
- If you decided you want to use your own Micro SD card, you can download the imager from the link above and install the Raspberry Pi OS Full to get a desktop environment.
- If you don't happen to have a separate computer to install the imager, you can still install it by using network boot simply by holding shift after you plug in power supply and ethernet cable once it's being turned on. It should prompt the installation of the operating system via the raspberry pi imager.

For those familiar with the command-line interface (CLI)
- You can install the Raspberry Pi OS Lite for a more minimal Linux terminal instead of having a desktop environment.

After decided what OS you wish to install, you can go to the advance settings to change the following in advance:
- hostname (the raspberrypi name, default is raspberry pi)
- SSH (Default is disabled, you can enable it if you wish to control from another computer)
- username and password (the login credentials to get into the OS)
- locale settings (time zone and keyboard layout according to your preference)
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/bf78f544-506f-4a37-aef9-b5c77b7341cc" width="500">
</p>

## Post-installation
You should always update your raspberry pi with the following code to get the latest packages to upgrade.
```sh
sudo apt update && sudo apt upgrade -y
```
For those who are using the full version, you can click icon on the top right and click install updates.
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/896beb32-1985-4c08-85b4-4e4759e45fb6" width="500">
</p>

## Installing docker
First you will need to get the docker script from docker and install it with the following code:
```sh
curl -sSL https://get.docker.com | sh
```
You will also need to use the follow code if you don't want to use sudo everytime you want to use docker command.
```sh
sudo usermod -aG docker $USER
```
After installing, you will have to reboot for the changes made to take effect.
```sh
sudo reboot
```
After rebooting, you can test with the following code to check if it's properly installed, as shown in the screenshot below.
```sh
docker run hello-world
```
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/cb4444b4-3893-4947-8d8c-adbbe01403fb" width="500">
</p>

## Self-hosted Applications
Here's a list of services that I currently host on my Raspberry Pi and how to install them:
- [Adguard Home](https://github.com/shadowlune/homelab/blob/main/adguardhome.md) (DNS Server)
- [Firefly III](https://github.com/shadowlune/homelab/blob/main/firefly.md) (Personal Finance Manager)
- [Homepage](https://github.com/shadowlune/homelab/blob/main/homepage.md) (Docker Dashboard)
- [MySQL](https://github.com/shadowlune/homelab/blob/main/uptimekuma.md) (SQL Database)
- [Nginx Proxy Manager](https://github.com/shadowlune/homelab/blob/main/nginx.md) (Reverse Proxy)
- [Portainer](https://github.com/shadowlune/homelab/blob/main/portainer.md) (Docker GUI)
- [Plex](https://github.com/shadowlune/homelab/blob/main/plex.md) (Media Server)
- [Shell in a Box](https://github.com/shadowlune/homelab/blob/main/shellinabox.md) (Web SSH)
- [Uptime Kuma](https://github.com/shadowlune/homelab/blob/main/uptimekuma.md) (Docker container Uptime)
- [Vaultwarden](https://github.com/shadowlune/homelab/blob/main/vaultwarden.md) (Password Manager)
- [Whoogle](https://github.com/shadowlune/homelab/blob/main/whoogle.md) (Ad-free Search Engine)
- [Wireguard](https://github.com/shadowlune/homelab/blob/main/wireguard.md) (VPN Tunnel)
