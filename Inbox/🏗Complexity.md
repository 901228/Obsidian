---
title : 🏗Complexity
date : 2021-10-21_Thu 15:30
aliases : []
---
Source Type :: #📥/📄 <br>
Note Type :: #📝 <br>
Topics :: [[🏗Data Structure MOC]]<br>
Parent Link :: [[🏗Data Structure MOC]]<br>

---
# 🏗Complexity

## Space Complexity
+ Fixed part
	+ instrustion space
	+ space for simple variables
	+ space for constant
	+ etc.
+ Variable part
	+ Space needed by referenced variables
	+ The recursion stack space

$$S(P)=\stackrel{fixed\ part}{c}+\stackrel{variable\ part}{S_p}$$

## Time Complexity

$$T(P)=\stackrel{compile\ time}{c}+\stackrel{run\ time}{T_p}$$

- Ways to determine the run time
	- Measurement（直接測量）
	- Analysis

### $O(g(n))$ [Big-O]
There exist positive constants $c$ and $n_0$ such that $f(n) \le cg(n)\ \forall \{ n|n \ge n_0\}$.
### $\Omega(g(n))$ [Omega]
### $\Theta(g(n))$ [Theta]
### $o(g(n))$ [little-o]
### $\omega(g(n))$ [little-omega]