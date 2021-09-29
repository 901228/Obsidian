---
title : 🖥️Image Compression
date : 2021-09-29_Wed 19:55
aliases : []
---
Source Type :: #📥/📄 <br>
Source Author :: [[@賴祐吉]]<br>
Note Type :: #📝 <br>
Topics :: [[🖥️Computer Graphics MOC]]<br>
Parent Link :: [[🖥️File and Compression]]<br>

---
# 🖥️Image Compression

## Intro
+ **Indexed color** is one form of image compression
	- Special case of ***vector quantization*** - in color space, reducing the range of available colors
+ **Alternative 1:** Store the image in a **simple format** and then compress with your favorite compressor
	- Doesn't exploit image specific information
	- Doesn't exploit perpectual shortcuts
+ **Alternative 2:** Design a specific algorithm fot an image
	- Two historically common compressed file formats: [[🖥️GIF (Graphics Interchange Format)|GIF]] and JPEG
		* [[🖥️GIF (Graphics Interchange Format)|GIF]] should now be replaced with PNG, because [[🖥️GIF (Graphics Interchange Format)|GIF]] id patened and the owner started enforcing the patent（專利）

## Two Observations on Images
+ In natural images, **low frequencies** are **more common** than high frequencies
	- That is, **more bits** should be allocated to low frequencies
+ The human visual system is **less sensitive to high frequencies**
	- That is, it is **more important to preserve low frequencies** than high frequencies

<big style="font-weight: 1000;">=> low frequencies are more important</big>
