[[Postmarket-OS]]

- first go to reovery and format data
- then wipe everything except microsd card and usb otg
- then format data again
- then go to system and repair FS
- then reboot to bootloader and connect phone to pc
- `fastboot flash boot qcom-msm8953-lk2nd.img`
- then go **lk2nd Fastboot**: Power on the device. After it vibrates, hold Volume Down
- `fastboot flash userdata qcom-msm8953.img`
> [!NOTE]
>You can use system also but userdata is recomended
- or alternatively use pmbootstrap