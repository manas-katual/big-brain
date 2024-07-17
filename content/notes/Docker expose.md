---
title: Docker expose
draft: false
tags:
---
Uplink : [[Docker]]

```bash
docker run -td --name techserver -p 80:80 ubuntu
```
here `t` means terminal and `d` means daemon `p` means publish/port and `80:80` before `:` is host machine port number and after `:` is containers port number

```bash
docker ps
```

```bash
docker port techserver
```
to see which ports are open

```bash
docker exec -it techserver /bin/bash
```
this is like `docker attach` but the difference is it will create a new session or process

then inside container
```bash
apt-get update 
```

for installing apache server
```bash
apt-get install apache2 -y
```

now to create a simple web server follow the steps
```bash
cd /var/www/html
```

```bash
echo "Hello people" > index.html
```

```bash
service apache2 start 
```

after this open any browser and enter the ip address of hostmachine to access the webserver which we just created 
e.g
```
192.168.0.102:80
```

## Difference between docker attach and docker exec

Docker ==exec== creates a new process in the container's environment while ==docker attach== connect the standard input/output of the main process inside the container to corresponding standard input/output error of current terminal.

`pid` ===> process id
`ppid` ===> parent process id

==Docker exec== is specifically for running new things in a already started container be it a shell or some other process.

## What is the difference between ==expose== and ==publish== a docker ?

Basically you have three options :-

1. Neither specify ==expose== nor ==-p==
2. Only specify ==expose==
3. Specify ==expose== and ==-p==

1) If you specify neither ==expose== nor ==-p==, the service in the container will only be accessible from inside the container itself
2) if you ==expose== a port, the service in the container is not accessible from outside docker but from inside other containers, So this is good for inter-container communication 
3) if you ==expose== and ==-p== a port, the service in the container is accessible from anywhere, even outside docker.
4) if you do ==-p== and do not ==expose== docker does and implicit expose this is because if a port is open to the public, it is automatically open to the other containers. Hence `-p` includes expose 