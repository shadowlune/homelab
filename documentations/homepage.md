# Homepage
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/d0602f16-1fc9-4290-bd7b-91e3cf9d942c" width="600">
</p>

## Overview
Homepage is a static, secure and highly customizable application dashboard that integrates with docker containers. 

## Installation
You can pull the image with docker pull and run it using the command-line as follows:
```sh
docker pull ghcr.io/benphelps/homepage:latest
```
You can now run the portainer as a docker container with the pulled image from the previous step.
```sh
docker run -d -p 3000:3000 --name=homepage --restart=always \
  -v /portainer/homepage/config:/app/config \
  -v /var/run/docker.sock:/var/run/docker.sock \
  ghcr.io/benphelps/homepage:latest

```

An alternative way would be to make use of Portainer by clicking the 'Add Container' button and then filling out all the forms as shown below, including name, image, ports, volumes, and restart policy.
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/b03778ff-bcb8-4dd4-b45b-e8756af41139" width="750">
</p>
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/725eb2b7-b7a4-4e30-8fc1-09b63ccd1c8b" width="750">
</p>
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/d11a34ea-bc6b-4b14-abc6-18a6e5ed120f" width="750">
</p>
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/4256ccd4-258b-4a86-b796-e38a8dfe2b69" width="750">
</p>

You should now be able to access it with your Raspberry Pi's IP address on port 3000 after you deploy the container.
<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/44718c20-0299-4642-a6ee-61960d1ca239" width="750">
</p>

## Configurations
You can now configure your dashboard to include all the services that you will be hosting by editing the .yaml files in the folder that we set up earlier at /portainer/homepage/config/ and you can look up the [homepage documentations](https://gethomepage.dev/en/configs/services/) for syntax details.

<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/1978de14-ad74-4190-8bf9-e54a15323ea1">
</p>

This is what be a fully configured homepage dashboard could potentially look like:

<p align="center">
  <img src="https://github.com/shadowlune/homelab/assets/118125336/946f2384-8b36-42cf-93c1-1a8cedf3c9d0">
</p>
