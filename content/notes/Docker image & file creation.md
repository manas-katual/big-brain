---
title: Docker image & file creation
draft: false
tags:
---
Uplink : [[Docker]]

## Image method

Now we have to create container from our own image
Therefore, create one container first

```bash
docker run -it --name zoro ubuntu /bin/bash
```

Now create one file inside the `tmp` directory 
```bash
cd /tmp
touch myfile
```

Now if we want to see the difference between the base image & changes on it then
```bash
docker diff zoro
```

In Output it will show something like this
```bash
C /root
A /root/.bash_history
C /tmp
A /tmp/myfile
```
Here, `C` means *change* `A` means *Append/Add* and there is one more which is `D` means *Delete*

Now, create image of this container
```bash
docker commit zoro updatezoro
```
Here, `luffy` is this containers name and `updateluffy` is the new name we gave now

run this to see if it is available or not
```bash
docker images
```

Now create container from this image
```bash
docker run --name sanji -it updatezoro /bin/bash
```

Now inside the container you can see in `/tmp` directory there will be `myfile` or if you downloaded any software also it will be there

## Docker file

- Docker file is basically a text file. It Contains some set of instruction
- Automation of Docker image creation

## Docker components

- `FROM` - for base image this command must be on top of the dockerfile
- `RUN` - To execute commands, it will create a layer in image
- `MAINTAINER` - Author/Owner/Description
- `COPY` - Copy files from local system (docker VM) we need to provide source, destination (we can't download file from internet and any remote repo) 
- `ADD` - Similar to copy but, it provides a feature to download files from internet, also we extract file at docker image site.
- `EXPOSE` - To expose ports such as port 8080 for tomcat, port 80 for nginx etc.
- `WORKDIR` - To set working directory for a container
- `CMD` - Execute commands but during container creation
- `ENTRYPOINT` - Similar to `CMD` but has higher priority over `CMD` first commands will be executed by `ENTRYPOINT` only
- `ENV` - Environment Variables
- `ARG` - Arguments

### Steps to create a docker file

1. First create a file

```bash
vi Dockerfile
```
it should be named only `Dockerfile` no other file name will be accepted

2.  Add instructions in docker file

```bash
FROM debian
WORKDIR /tmp
RUN echo "Hello People !" > /tmp/testfile
COPY testfile1 /tmp
ADD tarfile.tar.gz /tmp
ENV myname onepiece
```

create a file and create a tar file on the host machine which we defined in the `Dockerfile`
```bash
touch testfile1 tarfile
tar -cvf tarfile.tar tarfile
gzip tarfile.tar
rm -rf tarfile
```

3. Build docker file to create image

```bash
docker build -t franky .
```
here `t` means 'tag' and `.` means 'current directory'

4. Run image to create container

```bash
docker run -it --name ussop franky /bin/bash
```

now we can check if file was created or not