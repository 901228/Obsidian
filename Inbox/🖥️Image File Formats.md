---
title : 🖥️Image File Formats
date : 2021-09-28_Tue 21:48
aliases : []
---
Source Type :: #📥/📄 <br>
Source Author :: [[@賴祐吉]]<br>
Note Type :: #📝 <br>
Topics :: [[🖥️Computer Graphics MOC]]<br>
Parent Link :: [[🖥️File and Compression]]<br>

---
# 🖥️Image File Formats

+ 尺寸
	- All files in some way store width and height
+ 格式
	- black and white image, a grayscale image, a color image, an indexed color image ...
+ Other information
	- Color tables, compression, codebooks, creator information ...
+ All image formats are a trade-off（權衡） between ease of use, size of file, and quality of reproduction（複製？）

## [[🖥️Raster Images|Raster Images]]
## [[🖥️The Simplest File|The Simplest File]]
## [[🖥️Indexed Color|Indexed Color]]

## Image Size
+ 1024\*1024 at 24 bits uses 3 MB ($\frac{1024 \times 1024 \times 24}{1024 \times 1024 \times 8}=3 \ MB$)
+ Encyclopedia Briannica at 300 pixels/inch and 1 bit/pixel requires 25 gigabytes (25K pages)
+ 90 minute movie at 640x480, 24 bits per pixel, 24 frames per second requires 120 gigabytes ($\frac{90 \times 60 \times 24 \times 640 \times 480 \times 24}{8 \times 1024 \times 1024 \times 1024} \approx 120 \ GB$)
+ Application: HDTV, DVD, satellite image transmission, medial image processing, fax ...

## Image Compression
+ **Indexed color** is one form of image compression
	- Special case of ***vector quantization*** - in color space, reducing the range of available colors
+ **Alternative 1:** Store the image in a **simple format** and then compress with your favorite compressor
	- Doesn't exploit image specific information
	- Doesn't exploit perpectual shortcuts
+ **Alternative 2:** Design a specific algorithm fot an image
	- Two historically common compressed file formats: [[🖥️GIF (Graphics Interchange Format)|GIF]] and JPEG
		* [[🖥️GIF (Graphics Interchange Format)|GIF]] should now be replaced with PNG, because [[🖥️GIF (Graphics Interchange Format)|GIF]] id patened and the owner started enforcing the patent（專利）

## [[🖥️GIF (Graphics Interchange Format)|GIF (Graphics Interchange Format)]]