---
title: Docker hub
draft: false
tags:
---
Uplink : [[Docker]]

Docker hub is where we can push our custom docker images mad by us to do that follow the steps
```bash
docker run -it --name deku ubuntu /bin/bash
```

Now after creating a docker container install softwares or any make any changes to that container for example
```bash
touch file1 file2 file3
cd /tmp
touch filex filey filez
```

build image
```bash
docker commit deku image1
```

Now create account in [Dockerhub](https://hub.docker.com)

After creating account run this
```bash
docker login
```
enter your username and password

Now give tag to your name
```bash
docker tag image1 dockerusername/piro1
```

Now we can see this image in docker hub account

After this anyone can pull the image from docker hub
```bash
docker pull dockerusername/piro1
```

```bash
docker run -it --name kirito dockerusername/piro1 /bin/bash
```


## Some useful commands

Stop all running containers 
```bash
docker stop $(docker ps -a -q)
```
`$` means it will run continue in loop and delete one by one and `q` stands for quit 

Delete all stopped containers
```bash
docker rm $(docker ps -a -q)
```

Delete all images
```bash
docker rmi -f $(docker images -q)
```