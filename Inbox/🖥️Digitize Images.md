---
title : 🖥️Digitize Images
date : 2021-09-27_Mon 16:27
aliases : []
---
Source Type :: #📥/📄 <br>
Source Author :: [[@賴祐吉]]<br>
Note Type :: #📝 <br>
Topics :: [[🖥️Computer Graphics MOC]]<br>
Parent Link :: [[]]<br>

---
# 🖥️Digitize Images

## Ideal Images vs Digital Images
### Ideal Images
+ The information stored in images is often **continuous** in nature
+ consider the **ideal photograph**
	- It captures the intensity of light at a **particular set of points** coming from a **particular set of directions** (it's called irradiance（輻照度）)
	- The intensity of light arriving at the camera can **be any positive real number**, and it **mostly varies smoothly over space**
	- Where so you see spatial（空間上的） discontinuous in a photograph？

### Digital Images
+ Computers works with **discrete（離散）** pieces of information.
+ Digitize a continuous image
	- Break the continuous space into small areas - pixels
	- Use a single value for each pixel - the pixel value (no color, yet)
	- No longer continuous in space or intensity
+ This process is fraught with danger, as we shall see

![[digitize.png]]

## Discretization Issues
+ Can only store a **finite number of pixels** -> spatial space
	- Choose your target physical image size, choose your resolution (pixel per inch, or dots per inch (dpi))