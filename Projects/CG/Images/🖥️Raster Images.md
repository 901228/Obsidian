---
title : 🖥️Raster Images
date : 2021-09-27_Mon 14:53
aliases : []
---
Source Type :: #📥/📄 <br>
Source Author :: [[@賴祐吉]]<br>
Note Type :: #📝 <br>
Topics :: [[🖥️Computer Graphics MOC]]<br>
Parent Link :: [[🖥️Digital Images]]<br>

---
# 🖥️Raster Images

+ A raster（光柵） is a regular grid of pixels (picture elements)
+ Raster image formats store the **color** at each pixel, and maybe some **other information**
	- **Easiest** is to use a **simple array** of pixel values
	- Some formats store the pixel information in **very different ways**
	- [[#^cd42d4|e.g. a 5x3, floating pointm grayscale image]]

| <span style="background: #DDDDDD;color: transparent;">0.25</span> | <span style="background: #C0C0C0;color: transparent;">0.50</span> | <span style="background: #DDDDDD;color: transparent;">0.25</span> | <span style="background: #C0C0C0;color: transparent;">0.50</span> | <span style="background: #DDDDDD;color: transparent;">0.25</span> |
|:-----------------------------------------------------------------:|:-----------------------------------------------------------------:|:-----------------------------------------------------------------:|:-----------------------------------------------------------------:|:-----------------------------------------------------------------:|
| <span style="background: #FFFFFF;color: transparent;">1.00</span> | <span style="background: #DDDDDD;color: transparent;">0.25</span> | <span style="background: #000000;color: transparent;">0.00</span> | <span style="background: #DDDDDD;color: transparent;">0.25</span> | <span style="background: #FFFFFF;color: transparent;">1.00</span> |
| <span style="background: #DDDDDD;color: transparent;">0.25</span> | <span style="background: #C0C0C0;color: transparent;">0.50</span> | <span style="background: #DDDDDD;color: transparent;">0.25</span> | <span style="background: #C0C0C0;color: transparent;">0.50</span> | <span style="background: #DDDDDD;color: transparent;">0.25</span> |

| 0.25 | 0.5  | 0.25 | 0.5  | 0.25 |
|:----:|:----:|:----:|:----:|:----:|
|  1   | 0.25 |  0   | 0.25 |  1   |
| 0.25 | 0.5  | 0.25 | 0.5  | 0.25 |

^cd42d4