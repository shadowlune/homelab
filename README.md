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
- You can install the Raspberry Pi OS Lite for a more minimal linux terminal instead of having a desktop environment.

After decided what OS you wish to install, you can go to the advance settings to change the following in advance:
- hostname (the raspberrypi name, default is raspberry pi)
- SSH (Default is disabled, you can enable it if you wish to control from another computer)
- username and password (the login credentials to get into the OS)
- locale settings (time zone and keyboard layout according to your preference)
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/bf78f544-506f-4a37-aef9-b5c77b7341cc" width="500">
</p>
