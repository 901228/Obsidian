---
title : 🖥️Indexed Color
date : 2021-09-28_Tue 23:05
aliases : []
---
Source Type :: #📥/📄 <br>
Source Author :: [[@賴祐吉]]<br>
Note Type :: #📝 <br>
Topics :: [[🖥️Computer Graphics MOC]]<br>
Parent Link :: [[🖥️Image File Formats]]<br>

---
# 🖥️Indexed Color

+ 24 bits per pixel (<ruby>8<rp> ( </rp><rt>R</rt><rp> ) </rp></ruby>, <ruby>8<rp> ( </rp><rt>G</rt><rp> ) </rp></ruby>, <ruby>8<rp> ( </rp><rt>B</rt><rp> ) </rp></ruby>) are **expensive** to transmit and store
+ It must be possible to represent all those colors, but not in the same image
+ Solution: indexed color
	1. Assume *k* bits per pixel (typically 8)
	2. Define a color table containing 2*<sup >k</sup>* colors (24 bits per color)
	3. Store the index into the table for each pixel (so store k bits for each pixel)
	4. Once common in hardware, now an artifact (256 color display)

<table>
	<tr>
		<td>
			<table>
				<tr>
					<td>0</td>
					<td style="background-color: red; color: transparent;">0000</td>
				</tr>
				<tr>
					<td>1</td>
					<td style="background-color: purple; color: transparent;">1111</td>
				</tr>
				<tr>
					<td>2</td>
					<td style="background-color: magenta; color: transparent;">2222</td>
				</tr>
				<tr>
					<td>3</td>
					<td style="background-color: brown; color: 		transparent;">3333</td>
				</tr>
				<tr>
					<td>4</td>
					<td style="background-color: gray; color: transparent;">4444</td>
				</tr>
				<tr>
					<td>5</td>
					<td style="background-color: cyan; color: transparent;">5555</td>
				</tr>
				<tr>
					<td>6</td>
					<td style="background-color: forestGreen; color: transparent;">6666</td>
				</tr>
				<tr>
					<td>7</td>
					<td style="background-color: yellow; color: transparent;">7777</td>
				</tr>
			</table>
		</td>
		<td>
			<table>
				<tr>
					<td style="background-color: gray;color: cyan;">4</td>
					<td style="background-color: brown;color: cyan;">3</td>
					<td style="background-color: red;color: cyan;">0</td>
					<td style="background-color: magenta;color: cyan;">2</td>
				</tr>
				<tr>
					<td style="background-color: purple;color: cyan;">1</td>
					<td style="background-color: yellow;color: brown;">7</td>
					<td style="background-color: gray;color: cyan;">4</td>
					<td style="background-color: cyan;color: brown;">5</td>
				</tr>
				<tr>
					<td style="background-color: brown;color: cyan;">3</td>
					<td style="background-color: yellow;color: brown;">7</td>
					<td style="background-color: forestGreen;color: cyan;">6</td>
					<td style="background-color: cyan;color: brown;">5</td>
				</tr>
				<tr>
					<td style="background-color: magenta;color: cyan;">2</td>
					<td style="background-color: magenta;color: cyan;">2</td>
					<td style="background-color: purple;color: cyan;">1</td>
					<td style="background-color: purple;color: cyan;">1</td>
				</tr>
			</table>
		</td>
	</tr>
</table>

**Only makes sense if you have lots of pixels and not many colors**