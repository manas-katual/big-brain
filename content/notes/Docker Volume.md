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
VOLUME ["/sharefolder"]
```

Then create image from this `Dockerfile`
```bash
docker build -t myimage .
```
`-t` is tag(name) which we gave `myimage`

Now create a container from this image and run
```bash
docker run -it --name container1 myimage /bin/bash
```

Now by running `ls` you can see `sharefolder` we created.

Now, share volume with another container
Container1 <----> Container2
```bash
docker run -it --name container2(new one) --privileged=true --volume-from container1(old one) ubuntu /bin/bash
```

Now after creating container 2 `sharefolder` will be visible whatever you do in one volume, can see from other volume.

e.g.
```bash
touch /sharefolder/test.txt
docker start container1
docker attach container1
ls /sharefolder/
```
now you can see `test.txt` file
