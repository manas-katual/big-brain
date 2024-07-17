---
title: Docker Volume
draft: false
tags:
---
Uplink : [[Docker]]

- Volume is simply directory inside our container.
- Firstly, We have to declare this directory as a volume and then share volume.
- Even if we stop container, we can still access the volume.
- Volume will be created in one container.
- You can declare a directory as a volume only while creating container.
- You can't create volume from existing container.
- You can share one volume across any number of containers.
- Volume will not be included when you update an image.
- You can map volume in two ways
	- Container <----> Container
	- Host <----> Container

## Benefits of volume
- Decoupling (no relation) Container from storage.
- Share volume among different containers.
- Attach Volume to containers.
- On deleting container volume does not delete.

## Creating volume from docker file

Create a `Dockerfile` and write
```bash
FROM ubuntu
VOLUME ["/myvolume1"]
```

Then create image from this `Dockerfile`
```bash
docker build -t chopper .
```
`-t` is tag(name) which we gave `myimage`

Now create a container from this image and run
```bash
docker run -it --name zimbie chopper /bin/bash
```

Now by running `ls` you can see `sharefolder` we created.

Now, share volume with another container
Container1 <----> Container2
```bash
docker run -it --name nami(new one) --privileged=true --volume-from zimbie(old one) ubuntu /bin/bash
```
`privileged=true` means new container will also have all rights to the volume

Now after creating container 2 that is 'nami' in our case `myvolume1` will be visible whatever you do in one volume, can see from other volume.

e.g.
```bash
touch /myvolume1/test.txt
docker start zimbie
docker attach zimbie
ls /myvolume1/
```
now you can see `test.txt` file

## Creating volume from CLI

```bash
docker run -it --name naruto -v /myvolume2 ubuntu /bin/bash
```

run the following commands
```bash
ls
cd /myvolume2
touch fifth
ls
exit
```

Now create one more container and share `myvolume2`
```bash
docker run -it --name kakashi --privileged=true --volumes-from naruto ubuntu /bin/bash
```

now you are inside container
```bash
ls
```

now create one file inside this volume and then check in `naruto` you can see that file
```bash
cd /myvolume2
touch sixth
exit
```

## Host to container sharing

we can create a directory first which we want to share
```bash
mkdir hostshare
```

then run
```bash
docker run -it --name sasuke -v /root:/sharefolder --privileged=true ubuntu /bin/bash
```
before `:` that is directory of host machine after `:` that is containers directory

now cd into `sharefolder` you can see all files of host machine
```bash
touch newtestfile
exit
```

Now check in the hosts `/root` directory you can see the files

## Some other commands

```bash
docker volume ls
docker volume create <volumename>
docker volume rm <volumename>
docker volume prune # it removes all unused docker voumes
docker volume inspect <volumename>
docker container inspect <voumename>
```

