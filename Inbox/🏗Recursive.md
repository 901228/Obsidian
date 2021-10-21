---
title : 🏗Recursive
date : 2021-10-21_Thu 15:17
aliases : []
---
Source Type :: #📥/📄 <br>
Note Type :: #📝 <br>
Topics :: [[🏗Data Structure MOC]]<br>
Parent Link :: [[🏗Data Structure MOC]]<br>

---
# 🏗Recursive
**Advantages:** To express a complex process very clearly.

## Category
### Direct Recursion
```cpp
function A() {
	...
	
	A();
	
	...
}
```

### Indirect Recursion
```cpp
function A() {
	...
	
	B();
	
	...
}

function B() {
	...
	
	A();
	
	...
}
```

### Tail Recursion
```cpp
function A() {
	...
	
	A();
}
```

## Pros and Cons
| Recursion              | Non-Recursion         |
| ---------------------- | --------------------- |
| Codes are more compact | Codes are complicated |
| East to understand     | Hard to read          |
| ==Time-consuming==     | Time-saving           |

