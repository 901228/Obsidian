---
title : InkWell with backgroundColor
date : 2021-07-24_Sat 16:19
aliases : []
---
Source Type :: #📥/💭 <br>
Note Type :: <br>
Topics :: [[Flutter MOC]]<br>
Parent Link :: [[Tricks]]<br>

---
# InkWell with backgroundColor
```dart
Container(
	color: ,                                             // backgroundColor
	child: Material(
		color: Colors.transparent,                       // transparent
		child: InkWell(
		  child: Container
			child:                                       // child
		  ),
		  onTap: () {},
		),
	),
),
```