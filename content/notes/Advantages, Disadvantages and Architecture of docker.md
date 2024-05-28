---
title: Advantages, Disadvantages and Architecture of docker
draft: false
tags:
---
Uplink : [[Docker]]

## Advantages of docker

- No pre-allocation of RAM
- [[CI efficiency]] Docker enables you to build a container image and use that same image across every step of the deployment process.
- Less cost
- It is light in weight
- It can run on Physical hardware/Virtual hardware or on cloud
- You can re-use the image 
- It takes very less to create container
---
## Disadvantages

- Docker is not a good solution for application that requires a rich GUI
- Difficult to manage large amount of containers
- Docker does not provide cross-platform compatibility means if an application is designed to run in a docker container on windows, then it can't run on linux or vice-versa
- Docker is suitable when the development O.S and testing O.S are same if the O.S is different we should use vm 
- No solution for data recovery and backup
---
## Components of docker 
## Docker daemon

- Docker daemon runs on the host O.S 
- It is responsible for running Containers to manage docker services 
- Docker Daemon can Communicate other daemons
---
## Docker client

Docker users can interact with docker through a client
- Docker client uses commands and rest API to communicate with docker daemon 
- When a client runs any sever command on the docker client terminal,  the client terminal sends these docker commands to the docker daemon 
- It is possible for docker client to communicate with more than one daemon
---
## Docker host

Docker host is used to provide an environment to execute and run applications. It contains the docker daemon, images, containers, networks and storage.

---
## Docker hub/Registry

Docker registry manages and stores the docker images.
There are two types of registries in the docker
1. Public Registry &rarr; Public registry is also called as docker hub
2. Private Registry &rarr; It is used to share images within the enterprise
---
## Docker images
- Docker images are the read only binary templates used to create docker containers.
- OR
- Single file with all dependencies and configurations required to run a program
---
## Ways to create images

There are three ways to create images

1. Take image from docker hub
2. Create image from docker file 
3. Create images from existing docker Containers
---
## Container

- Container holds the entire packages that needed to run the application
- In other words we can say that, the image is template and container is a copy of that template 
- Container is like a Virtual machine
- Images become container when they run on docker engine 