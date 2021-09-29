---
title : 🖥️The Simplest File
date : 2021-09-28_Tue 22:35
aliases : []
---
Source Type :: #📥/📄 <br>
Source Author :: [[@賴祐吉]]<br>
Note Type :: #📝 <br>
Topics :: [[🖥️Computer Graphics MOC]]<br>
Parent Link :: [[🖥️Image File Formats]]<br>

---
# 🖥️The Simplest File

+ Assumes that the **color depth is known** and **agreed on（達成一致？）**
+ Store **width, height, and data** for every pixel in **sequence**
+ This is how you normally **store an image** in memory

```c++
class Image {
	unsigned int width;
	unsigned int height;
	unsigned char* data; 
}
```

<div style="border: 0.1em solid currentColor; padding-top:1em;">
<table align="center">
	<caption style="font-size: 0.8em;">data in rectangular array</caption>
	<tr>
		<td>0<sub>r,g,b</sub></td>
		<td>1<sub>r,g,b</sub></td>
		<td>2<sub>r,g,b</sub></td>
	</tr>
	<tr>
		<td>3<sub>r,g,b</sub></td>
		<td>4<sub>r,g,b</sub></td>
		<td>5<sub>r,g,b</sub></td>
	</tr>
	<tr>
		<td>6<sub>r,g,b</sub></td>
		<td>7<sub>r,g,b</sub></td>
		<td>8<sub>r,g,b</sub></td>
	</tr>
</table>
<center>↓</center>
<table align="center">
	<caption style="font-size: 0.8em;">data in linear array</caption>
	<tr>
		<td>0<sub>r</sub></td>
		<td>0<sub>g</sub></td>
		<td>0<sub>b</sub></td>
		<td>1<sub>r</sub></td>
		<td>1<sub>g</sub></td>
		<td>1<sub>b</sub></td>
		<td>2<sub>r</sub></td>
		<td>2<sub>g</sub></td>
		<td>2<sub>b</sub></td>
		<td>3<sub>r</sub></td>
		<td>3<sub>g</sub></td>
		<td>3<sub>b</sub></td>
	</tr>
</table>
</div>

+ **Unsigned** because width and height are positive, and **unsigned char** because it is the best type for raw 8 bits data
+ Note that you require **some implicit scheme（格式）** for laying out a rectangular array into a linear one