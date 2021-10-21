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


## Time Complexity
### The Master Mothod
$$T(n)=aT(\frac{n}{b})+f(n)$$

where $a \geq 1$ and $b > 1$ are constants and $f(n)$ is a positive function.
1. If $f(n)=O(n^{log_b a})$, then $T(n)=\Theta(n^{log_b a} log_2 n)$
2. If $f(n)=O(n^{log_b a-\epsilon})$ for some constants $\epsilon > 0$, then $T(n)=\Theta(n^{log_b a})$
3. If $f(n)=O(n^{log_b a+\epsilon})$ for some constants $\epsilon > 0$, and if $af(\frac{n}{b}) \leq cf(n)$ for some constant c < 1 and all sufficiently large n, then $T(n)=\Theta(f(n))$

+ Example
	+ $a = 9$, $b = 3$, $f(n) = n$, and $n^{log_b a} = n^{log_3 9} = n^2$
	+ $f(n) = n = O(n^{log_b a-\epsilon}) = O(n^{log_3 9-\epsilon})$, where $\epsilon = 1$
	+ $T(n) = \Theta(n^{log_b a}) = \Theta(n^{log_3 9}) = \Theta(n^2)$
	+ Case 1

- Tips
	1. In case