---
title: Build Env Setup
draft: false
tags:
---
Uplink : [[Custom-Rom]]

Settting up Build Environment

Ubuntu 22.04
```bash
sudo su
```

This command will add a ppa repository and install all the dependencies
```bash
add-apt-repository ppa:openjdk-r/ppa && apt-get update && sudo apt-get install git-core gnupg flex bison build-essential zip curl zlib1g-dev gcc-multilib g++-multilib libc6-dev-i386 libncurses5 lib32ncurses5-dev x11proto-core-dev libx11-dev lib32z1-dev libgl1-mesa-dev libxml2-utils xsltproc unzip fontconfig && exit
```

Cloning Akhil Narang Scripts
This command will make a bin directory set the PATH variable and clone and setup the build environment
```bash
mkdir ~/bin && PATH=~/bin:$PATH && cd ~/bin && curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo && chmod a+x ~/bin/repo && git clone https://github.com/akhilnarang/scripts.git scripts && cd scripts && bash setup/android_build_env.sh && cd
```

For new ubuntu releases
```bash
sudo apt install python3-kerberos
sudo apt update && sudo apt upgrade
```

and download this deb [package](https://t.me/c/2175653732/161) and install it
```bash
dpkg -i repo_2.15.4-2_all.deb
```

and install all this packages
```bash
sudo apt install aptitude -y && sudo aptitude install libncurses5 -y && sudo apt install git -y && sudo apt install neofetch && sudo apt install zip -y && sudo apt install rsync -y && sudo apt install bison -y && sudo apt install libssl-dev -y && sudo apt install clang -y && sudo apt install apktool -y && sudo apt install patchelf -y && sudo apt install git-lfs -y
```
