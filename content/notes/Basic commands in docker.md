---
title: Basic commands in docker
draft: false
tags:
---
Uplink : [[Docker]]

To install docker
```bash
# debian/ubuntu
apt install docker

# arch
pacman -Sy docker

# redhat/fedora
dnf install docker
```

To check if docker is installed
```bash
which docker
```

To check its version
```bash
docker -v
```

To check if docker is started or not
```bash
service docker status
# OR
docker info
```
To start docker
```bash
service docker start
```

To see all images present in your local machine
```bash
docker images
```

To find out images in docker hub
```bash
docker search ubuntu
```

To download images from docker hub to local machine
```bash
docker pull ubuntu
```

To give name to container. This command will do 2 things if we haven't downloaded image from previous command this command will download it and run it 
```bash
docker run -it --name luffy ubuntu /bin/bash
```
here in `-it` `i` is interactive mode and `t` is terminal
`--name` is optional
If we don't give any name to the container docker will generate any random name for it

To check if the service is start or not
```bash
service docker status
```

To start container
```bash
docker start luffy # name of the container 
```

To go inside container
```bash
docker attach luffy # name of the container
```

To see all containers
```bash
docker ps -a
```
`ps` stands for **process status** `-a` for all
it will show all running as well as stopped container

To see only running containers
```bash
docker ps 
```

To stop containers
```bash
docker stop luffy # name of the container
```

To delete containers
```bash
docker rm luffy # name of the container
```

To delete docker images
```bash
docker rmi <IMAGE ID>
```
you can find **IMAGE ID** by running `docker images` command