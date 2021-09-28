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
	- Image stored in memory as **2D pixel array**
	- **Easiest** is to use a **simple array** of pixel values
	- Value of each pixel controls color
	- Depth of image is information per pixel
		* &nbsp;1 bit : black and white display
		* &nbsp;8 bits: 256 colors at any given time via colormap
		* 16 bits: <ruby>5<rp> ( </rp><rt>R</rt><rp> ) </rp></ruby>, <ruby>6<rp> ( </rp><rt>G</rt><rp> ) </rp></ruby>, <ruby>5<rp> ( </rp><rt>B</rt><rp> ) </rp></ruby> bits, 2<sup>16</sup> = 65,536 colors
		* 24 bits: <ruby>8<rp> ( </rp><rt>R</rt><rp> ) </rp></ruby>, <ruby>8<rp> ( </rp><rt>G</rt><rp> ) </rp></ruby>, <ruby>8<rp> ( </rp><rt>B</rt><rp> ) </rp></ruby> bits, 2<sup>24</sup> = 16,777,216 colors
	- Some formats store the pixel information in **very different ways**
	- [[#^cd42d4|e.g. a 5x3, floating pointm grayscale image]]

<table align="center">
	<tr align="center">
		<td style="background: #DDDDDD;color: blue;">0.25</td>
		<td style="background: #C0C0C0;color: blue;">0.5</td>
		<td style="background: #DDDDDD;color: blue;">0.25</td>
		<td style="background: #C0C0C0;color: blue;">0.5</td>
		<td style="background: #DDDDDD;color: blue;">0.25</td>
	</tr>
	<tr align="center">
		<td style="background: #FFFFFF;color: blue;">1</td>
		<td style="background: #DDDDDD;color: blue;">0.25</td>
		<td style="background: #000000;color: blue;">0</td>
		<td style="background: #DDDDDD;color: blue;">0.25</td>
		<td style="background: #FFFFFF;color: blue;">1</td>
	</tr>
	<tr align="center">
		<td style="background: #DDDDDD;color: blue;">0.25</td>
		<td style="background: #C0C0C0;color: blue;">0.5</td>
		<td style="background: #DDDDDD;color: blue;">0.25</td>
		<td style="background: #C0C0C0;color: blue;">0.5</td>
		<td style="background: #DDDDDD;color: blue;">0.25</td>
	</tr>
</table>

^cd42d4