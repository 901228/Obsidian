---
title : 🍃Genymotion Installation
date : 2021-08-23_Mon 23:20
aliases : [emulator]
---
Source Type :: #📥/📄 <br>
Source URL :: https://docs.genymotion.com/desktop/latest/01_Get_started.html<br>
Note Type :: #📝 <br>
Topics :: [[🍃Flutter MOC]]<br>
Parent Link :: [[🍃Tricks]]<br>

---
# ==It's not working==
# 🍃Genymotion Installation

## Step 1.
```
$ sudo apt insuall virtualbox
$ sudo apt install linux-headers-<kernel version>-generic
$ sudo apt --reinstall install virtualbox-dkms
$ dmesg | grep -i vboxdrv
```

## Step 2.

Download the Linux package corresponding to your system. <br>
Install Genymotion.

```
$ cd ~/Download
$ chmod +x genymotion-3.X.X-linux_x64.bin
$ sudo ./genymotion-3.X.X-linux_x64.bin
```