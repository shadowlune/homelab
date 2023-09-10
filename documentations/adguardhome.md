# Adguard Home
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/526bacad-6b4d-4338-b8c8-48782c4ed423" width="500">
</p>

## Overview
AdGuard Home is a network-wide Domain Name System (DNS) resolver tailored to improve your home network's functionality and user experiences. It serves multiple different role, including filtering out intrusive ads and trackers, functioning as a DHCP server to efficiently distribute IP addresses, and enabling DNS rewrites to seamlessly translate domain names into their corresponding IP addresses. This simplifies resource access, eliminating the need to memorize specific IP addresses and port numbers when accessing your home server resources.

## Installation
You can pull the image with docker pull and run it using the command-line as follows:
```sh
docker pull adguard/adguardhome
```
You can now run the portainer as a docker container with the pulled image from the previous step.
```sh
docker run -d --name=adguardhome --restart=always \
  -v /portainer/AdguardHome/config:/opt/adguardhome/conf \
  -v /portainer/AdguardHome/work:/opt/adguardhome/work \
  -p 53:53/tcp -p 53:53/udp \
  -p 67:67/udp -p 68:68/udp \
  -p 4080:80/tcp -p 4443:443/tcp -p 4443:443/udp -p 3000:3000/tcp \
  -p 853:853/tcp \
  -p 784:784/udp -p 853:853/udp -p 8853:8853/udp \
  -p 5443:5443/tcp -p 5443:5443/udp \
  adguard/adguardhome
```
If you plan on using it as your DHCP server to distribute IP address on your home network, you will have to do it on the host network.
```sh
sudo docker run -d --name=adguardhome --network host \
  -v /portainer/AdguardHome/config:/opt/adguardhome/conf \
  -v /portainer/AdguardHome/work:/opt/adguardhome/work \
  adguard/adguardhome
```

An alternative way would be to make use of Portainer by clicking the 'Add Container' button and then filling out all the forms as shown below, including name, image, ports, volumes, and restart policy.
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/b03778ff-bcb8-4dd4-b45b-e8756af41139" width="750">
</p>
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/294ae418-52e1-488f-a402-b894913065fb" width="750">
</p>
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/55a39336-3fff-470b-839f-ed4a0ca18eaa" width="750">
</p>
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/4256ccd4-258b-4a86-b796-e38a8dfe2b69" width="750">
</p>

## Configurations
You can now configure your AdGuard Home by going to your raspberry pi's IP address on port 3000.
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/791df9f9-460f-46d9-80cd-12fe8f516e61">
</p>
I would highly suggest that if you plan on using Nginx Proxy Manager later that you change the port 80 to a port that you don't use because it might interfere with the reverse proxy.
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/7866b5dd-a4b8-492a-af4e-a8d137bc6120">
</p>
You will then setup your username and password for AdGuard Home.
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/300d40cb-06eb-42fc-ae11-81060b550df5">
</p>
You have finally finish the configuration and you can open the dashboard and start playing around with all the different features.
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/450d7155-e50c-4160-9292-bf4b32cd7397">
</p>

## DHCP Server
AdGuard Home also has the ability to act as a DHCP server to distribute IP to network devices, which is easier to filter the ads and tracker since it will route everything through the raspberry pi instead of your internet service provider's router. However, this will only work if you installed it on the host network and you will need to turn off the DHCP from your ISP router before enabling the DHCP server with AdGuard Home.

Here is an example where I have set a range of IP address to distribute from 192.168.183.112 to 192.168.183.143 with the gateway IP address being 192.168.183.2.

<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/d7c6fbf1-1a71-45ed-83ba-59db505c947f">
</p>

## DNS Rewrites
DNS rewrites is part of the Filters section of AdGuard Home where you can use words to replace the IP address that you wish to reach on your home network. I mainly use this alongside with the Nginx Proxy Manager to force secure connection to the hosted services. Below are examples where I would setup the services I used by naming them accordingly and pointing them the raspberry pi's IP address. I will show how to direct it to the different ports and enforced secured connections in the [Nginx Proxy Manager](https://github.com/shadowlune/homelab/blob/main/documentations/nginxproxymanager.md) documentation.

<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/e27fde9e-583d-43e5-a0ee-57499d3327f6">
</p>

## Updating
Lastly, you will need to update the adguard as time goes on, you can do it with the following commands:
```sh
sudo docker stop adguardhome
sudo docker rm adguardhome
sudo docker rmi adguard/adguardhome
sudo docker run -d --name=adguardhome --network host \
  -v /portainer/AdguardHome/config:/opt/adguardhome/conf \
  -v /portainer/AdguardHome/work:/opt/adguardhome/work \
  adguard/adguardhome
```

## Additional Documentation
- [Adguard github documentation](https://github.com/AdguardTeam/AdguardHome)
- [Docker hub Documentation](https://hub.docker.com/r/adguard/adguardhome)
