---
title : Named route with arguments and return value
date : 2021-07-22_Thu 12:41
aliases : [named route, route, argument]
---
Source Type :: #📥/💭<br>
Note Type :: #📝<br>
Topics :: [[Flutter MOC]]<br>
Parent Link :: [[Tricks]]<br>

# Named route with arguments and return value

wrong ✖️
```dart
onTap: () async {
	_counter = await Navigator.of(context).pushNamed(
		'/detail',
		arguments: ReturnValue(_counter, '按我'),
	);
},
```

right ✔️
```dart
onTap: () async {
	await Navigator.of(context).pushNamed(
		'/detail',
		arguments: ReturnValue(_counter, '按我'),
	).then((value) => _counter = value);
},
```