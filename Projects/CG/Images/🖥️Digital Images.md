---
title : 🖥️Digital Images
date : 2021-09-27_Mon 14:44
aliases : []
---
Source Type :: #📥/📄 <br>
Source Author :: [[@賴祐吉]]<br>
Note Type :: #📝 <br>
Topics :: [[🖥️Computer Graphics MOC]]<br>
Parent Link :: [[🖥️Image]]<br>

---
# 🖥️Digital Images

Many formats exist for storing images on a computer. <br>

+ There are some conflicting goals:
	- The **storage (size)** cost be **minimized**
	- The **amount of information** stored should be **maximized**
	- **Original information** versus **perceptual** equivalence
	- **Tracking ownership** may be important

Most formats you are familiar with are [[🖥️Raster Images|raster images]]. <br>
少數是[[🖥️Vector Images|vector images]]。

## ??
+ Diffusion Curve
	- Use curves to describe the color boundry: the color of both sides.
	- Determine the color of a pixel based on its distance to all curve elements.
	- Generally require to solve a Partial Differential Equation (PDE)（偏微分）
+ Radial Basis Function
	- Use curve/points of constrained colors/samples to describe the image.
	- Using scattering data interpolation to determine the color of each pixel.
+ Thin Plate Spline
	- Deformation
	- Color editing
	- Stylization rendering
