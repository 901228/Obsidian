---
title : 🍃Android emulator CPU HIGH usage
date : 2021-08-23_Mon 22:00
aliases : [emulator]
---
Source Type :: #📥/📄 <br>
Source URL :: <br>
Note Type :: #📝 <br>
Topics :: [[🍃Flutter MOC]]<br>
Parent Link :: [[🍃Tricks]]<br>

---
# 🍃Android emulator CPU HIGH usage

## 1.
Add/Update these lines: 
```
hw.audioInput=no
hw.audioOutput=no
hw.GPS = no
hw.battery=no
```

On _Linux/Mac_ the file is located at `~/.android/avd/<AVD_Name>.avd/config.ini`. <br>
On _Windows_ the file is located at `C:\Users\<username>\.android\avd\<AVD_Name>.avd\config.ini`

## 2.
going to AVD `settings` - `Advanced` - change the `OpenGL ES renderer` to `Desktop native OpenGL` and restart the AVD. Now it uses like 2-3% of my CPU resources. Hope this helps someone.

## 3.
Snapshots -> Settings -> Auto-save current state to Quickboot - NO.

## 4.
chose `Hardware` Graphics Renderer instead of `Auto`.

## ==5.==
`AVD Manager` -> `Actions` -> `More(triangle)` -> `Cold Boot now`