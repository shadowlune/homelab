# Portainer
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/c7d827ff-fffb-43e9-b048-1aa81ea6948a" width="500">
</p>

## Overview
Portainer is container management platform that simplifies installation, configuration and organization of docker containers. It offers a web-based graphical user interface that enables all users including beginners to learn and manage docker containers without being overwhelmed by command-lines.

## Installation
You will need to  have docker installed on to your raspberry pi if you haven't already and then pull the portainer image from the docker hub with the following command:
```sh
sudo docker pull portainer/portainer-ce:latest
```
You can now run the portainer as a docker container with the pulled image from the previous step.
```sh
sudo docker run -d -p 9000:9000 -p 9443:9443 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```
You can now access it with your Raspberry Pi's IP address on port 9000 for HTTP or port 9443 for HTTPs and create user.
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/c98cd5f7-f393-414a-8692-3ba3b401ae6a" width="500">
</p>

## Configurations
Once you have created the user, you will click get started to get into your local environment to see the dashboard and the container list you have install.
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/eb054077-1546-445d-8b11-600eeaa86f6e" width="500">
</p>
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/3083d4e2-33d3-40ae-a89d-310dc5903ac0" width="700">
</p>

Under settings and environment, you can enter the raspberry pi ip address into the public ip address. You can now click on the published ports in the container list page without it showing as 0.0.0.0:port_number and will actually bring you to the right web interface of your applications.
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/6f5f34eb-28df-4744-a5ba-5d6d4dc74dd9" width="500">
</p>

Under settings and settings, there's an URL for app template that you can change to easily deploy new containers with ease. I am currently using [pi-hosted](https://raw.githubusercontent.com/pi-hosted/pi-hosted/master/template/portainer-v2-arm64.json) template made by [novaspirit](https://github.com/novaspirit).

<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/93d3e2d2-8764-4313-9212-1c8e08d3e6b6" width="500">
</p>

## Updating
Lastly, you will need to update the portainer as time goes on, you can do it with the following commands:
```sh
sudo docker stop portainer
sudo docker rm portainer
sudo docker rmi portainer:portainer-ce:latest
sudo docker run -d -p 9000:9000 -p 9443:9443 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```

## Additional Documentation
- [Official portainer documentation](https://docs.portainer.io/start/install-ce?hsCtaTracking=a66b69bb-4970-46b7-bc31-cfc8022c7eb2%7C0d5be9a2-9dac-4ab1-9498-4b07566effd3)
- [pi-hosted documentation](https://github.com/novaspirit/pi-hosted) I used this this guide when I first started out with portainers.
