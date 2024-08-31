---
title: Cloning device tree, vendor tree & kernel tree
draft: false
tags:
---
Uplink : [[Custom-Rom]]

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
