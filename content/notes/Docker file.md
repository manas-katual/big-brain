---
title: Docker file
draft: false
tags:
---
Uplink : [[Docker]]

Now we have to create container from our own image
Therefore, create one container first

```bash
docker run -it --name luffy ubuntu /bin/bash
```

Now create one file inside the `tmp` directory 
```bash
cd /tmp
touch myfile
```

Now if we want to see the difference between the base image & changes on it then
```bash
docker diff luffy
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
docker commit luffy updateluffy
```
Here, `luffy` is this containers name and `updateluffy` is the new name we gave now

run this to see if it is available or not
```bash
docker images
```

Now create container from this image
```bash
docker run --name sanji -it updateluffy /bin/bash
```

Now inside the container you can see in `/tmp` directory there will be `myfile` or if you downloaded any software also it will be there