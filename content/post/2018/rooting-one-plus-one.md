---
title: "Rooting One Plus One"
date: 2018-02-15T14:33:39+05:30
author: Sahil Ahuja
tags: [ "root", "android" ]
categories: [ "blog", "guide" ]
---
# How to root OnePlus One

1. Install TWRP recovery [steps](https://forums.oneplus.net/threads/oneplus-one-how-to-unlock-bootloader-install-custom-recovery-and-root.64487/)
1. Install Lineage OS 14.1 based on Android 7 and GApps using the "Install" option on TWRP via sd card. [Link](https://forum.xda-developers.com/oneplus-one/orig-development/official-lineageos-14-1-oneplus-one-t3543489) to the guide.

## A few lessons learnt along the way

- Ensure the USB wire being used can also transfer data
- Useful commands:
    ```sh
    adb devices -l
    fastboot devices
    fastboot oem unlock
    fastboot flash recovery /path/on/laptop/recovery.img
    adb push /path/on/laptop/supersu-v2.82.zip /sdcard/
    adb devices -l
    ```
