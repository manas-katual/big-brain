---
title: Normal way
draft: false
tags:
---
Uplink : [[Custom-Rom]]

## Build Env Setup

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
sudo apt install python3-kerberos &&
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

---
## Repo Sync

- we will build custom rom of lineageOS same follows for every other custom rom out there
- go to the LineageOS [github](https://github.com/LineageOS) and look for android or manifest repository and follow thier instructions or do this 

To initialize your local repository, use a command like this:
```bash
repo init -u https://github.com/LineageOS/android.git -b lineage-21.0 --git-lfs
```

Then to sync up:
```bash
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags --optimized-fetch --prune
```

---
## Cloning trees

- we need these three things for every device for building rom
	- Device tree
	- Vendor tree
	- Kernel tree
- to find these to to [github](https://www.github.com) and search like this
- for device tree 
	- `device_brand_codename e.g. device_xiaomi_vince`
- for vendor tree
	- `vendor_brand_codename e.g. vendor_xiaomi_vince`
- for kernel tree
	- `kernel_brand_codename e.g. kernel_xiaomi_vince`


> [!NOTE]
> There are also common device tree and common vendor tree for devices also some need to clone hardware repo separately it will be mentioned in the dependencies file

Now clone everything into specific directory and as per your device and manufacturer 

example
```bash
# device tree
git clone https://github.com/vince-labs/device_xiaomi_vince.git -b 14 device/xiaomi/vince

# common device tree
git clone https://github.com/vince-labs/device_xiaomi_msm8953-common.git -b 14 device/xiaomi/msm8953-common

# vendor tree
git clone https://github.com/vince-labs/vendor_xiaomi_msm8953-common.git -b 14 vendor/xiaomi/vince

# common vendor tree
git clone https://github.com/vince-labs/vendor_xiaomi_msm8953-common.git -b 14 vendor/xiaomi/msm8953-common

# kernel tree
git clone https://github.com/vince-labs/kernel_xiaomi_vince.git -b 14 kernel/xiaomi/msm8953

```

---
## Compiling/Building

Now to compile go to the root directory
```bash
cd lineage
. build/envsetup.sh
breakfast device_codename
export USE_CCACHE=1
export CCACHE_EXEC=/usr/bin/ccache
ccache -M 50G
croot
brunch device_codename | tee log.txt
```

For second build onwards:
```shell
source build/envsetup.sh
breakfast guacamoleb
croot
brunch guacamoleb | tee log.txt
```