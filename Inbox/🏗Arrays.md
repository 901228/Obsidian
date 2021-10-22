---
title : 🏗Arrays
date : 2021-10-21_Thu 16:50
aliases : [array]
---
Source Type :: #📥/📄 <br>
Note Type :: #📝 <br>
Topics :: [[🏗Data Structure MOC]]<br>
Parent Link :: [[🏗Data Structure MOC]]<br>

---
# 🏗Arrays
**Definition:** a set of pairs <index, value>.
- In C/C++, the index is starting at 0.

|   1    |   2    |   3    |   4    | ... |           n            |
|:------:|:------:|:------:|:------:|:---:|:----------------------:|
| <0, 1> | <1, 5> | <2, 4> | <3, 7> | ... | <n-1, V<sub>n-1</sub>> |

A<sub>1</sub> = A\[0\] = 1<br>
A<sub>4</sub> = A\[3\] = 7<br>
...<br>
A<sub>n</sub> = A\[n-1\] = V<sub>n-1</sub>

## Location of elements in an array

> **l<sub>s</sub>** = location of A<sub>1</sub><br>
> **d** &nbsp;= size of an element (size of data type)

==Location of A<sub>n</sub> = &A\[n-1\] = l<sub>s</sub> + (n-1) \* d==

## 2D array (matrix)

A<sub>i,j</sub> = A\[i-1\]\[j-1\]<br>

+ Ways to store a matrix in the memory
	+ Row-major (e.g., C++)
	+ Column-major

### Row-major
<table>
	<tr align="center">
		<td></td>
		<td style="background: #FFFF00;">col 1</td>
		<td style="background: #FFFF00;">col 2</td>
		<td style="background: #FFFF00;">col 3</td>
	</tr>
	<tr align="right", style="background: #00FF00;">
		<td style="background: #FFFF00;">row 1 =></td>
		<td>-27</td>
		<td>3</td>
		<td>4</td>
	</tr>
	<tr align="right", style="background: #FF8800;">
		<td style="background: #FFFF00;">row 2 =></td>
		<td>6</td>
		<td>82</td>
		<td>-2</td>
	</tr>
	<tr align="right", style="background: #FF3355;">
		<td style="background: #FFFF00;">row 3 =></td>
		<td>109</td>
		<td>-64</td>
		<td>11</td>
	</tr>
	<tr align="right", style="background: #0088FF;">
		<td style="background: #FFFF00;">row 4 =></td>
		<td>12</td>
		<td>8</td>
		<td>9</td>
	</tr>
	<tr align="right", style="background: #FF77FF;">
		<td style="background: #FFFF00;">row 5 =></td>
		<td>48</td>
		<td>27</td>
		<td>47</td>
	</tr>
</table>
<p style="font-size: 2em;">↓</p><br>
<table>
	<tr align="center">
		<td style="width: 4em; background: #00FF00;">-27</td>
		<td style="width: 4em; background: #00FF00;">3</td>
		<td style="width: 4em; background: #00FF00;">4</td>
		<td style="width: 4em; background: #FF8800;">6</td>
		<td style="width: 4em; background: #FF8800;">82</td>
		<td style="width: 4em; background: #FF8800;">-2</td>
		<td style="width: 4em; background: #FF3355;">109</td>
		<td style="width: 4em; background: #FF3355;">-64</td>
		<td style="width: 4em; background: #FF3355;">11</td>
		<td style="width: 4em; background: #0088FF;">12</td>
		<td style="width: 4em;">...</td>
	</tr>
</table>

#### Location
> **m** &nbsp;= numbers of rows<br>
> **n** &nbsp;= numbers of columns<br>
> **l<sub>s</sub>** = location of A<sub>1</sub><br>
> **d** &nbsp;= size of an element (size of data type)

A<sub>i,j</sub> = l<sub>s</sub> + \[ (i-1) \* n + (j-1) \] \* d

### Column-major
反過來

## Triangular Matrix
如果只有要用到一個**正方形矩陣**以對角線切出的一半三角形區域，則使用 Triangular Matrix 以一維陣列儲存較為節省空間。
### Lower-Triangular Matrix

![[Lower-Triangular Matrix.png]]

> #### Row-major
$\begin{split}
\forall i \geq j,\,Location(A_{i,j})
& = l_s + \bigg[\Big(\frac{1 + (i - 1)}{2} \times (i - 1)\Big) + (j - 1)\bigg] \times d \\
& = l_s + \bigg[ \frac{i \times (i - 1)}{2} + j - 1 \bigg] \times d
\end{split}$

> #### Column-major
$\begin{split}
\forall i \geq j,\,Location(A_{i,j})
& = l_s + \Big[\frac{(1+m)}{2} \times m - \frac{\big(1+(m-j+1)\big)}{2} \times (m-j+1) + (i-j) \Big] \times d \\
& = l_s + \Big[ i+m \times (j-1) - \frac{j \times (j-1)}{2} - 1 \Big] \times d
\end{split}$
![[Triangular Matrix.excalidraw]]