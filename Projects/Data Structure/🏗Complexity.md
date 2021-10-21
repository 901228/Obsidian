---
title : 🏗Complexity
date : 2021-10-21_Thu 15:30
aliases : [complexity, space, time]
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

### Terminologies（數學表達）
#### $O(g(n))$ [Big-Oh]
> **Definition**: for ==some== positive constants $c$ and $n_0$ such that $f(n) \le cg(n)$ $\forall n,\ n \ge n_0$.<br>

+ The function $g(n)$ is an **upper bound** on $f(n)$.

+ For the statement $f(n)=O(g(n))$ to be **informative**, $g(n)$ should be ==as **small** a function of $n$ as possible==.

- Fantastic names
	- $O(1)$ is a **constant**
	- $O(n)$ is called **linear**
	- $O(n^2)$ is called **quadratic**
	- $O(n^3)$ is called **cubic**
	- $O(2^n)$ is called **exponential**

* Ordering
	* $O(1)$ < $O(logn)$ < $O(n)$ < $O(nlogn)$ < $O(n^2)$ < $O(n^3)$ < $O(n^c)$ < $O(2^n)$ < $O(3^n)$ < $O(c^n)$ < $O(n!)$ < $O(n^n)$ < $O(n^{c^n})$

#### $\Omega(g(n))$ [Omega]
> **Definition**: for ==some== positive constants $c$ and $n_0$ such that $f(n) \ge cg(n)$ $\forall n,\ n \ge n_0$.<br>

+ The function $g(n)$ is a **lower bound** on $f(n)$.

+ For the statement $f(n)=\Omega(g(n))$ to be **informative**, $g(n)$ should be ==as **large** a function of $n$ as possible==.

#### $\Theta(g(n))$ [Theta]
> **Definition**: There exist positive constants $c_1$, $c_2$, and $n_0$ such that $c_1g(n) \leq f(n) \leq c_2g(n)$ $\forall n,\ n \ge n_0$.<br>

+ The theta is more **precise** than both big-oh and omega
	+ The function $g(n)$ is both an **upper** and **lower bound** on $f(n)$.

#### $o(g(n))$ [Little-Oh]
> **Definition**: for ==any== positive constants $c$, there exist a constant $n_0$ such that $0 \leq f(n) < cg(n)$ $\forall n,\ n \ge n_0$.<br>

+ 比 Big-Oh 嚴格.
+ Example:
	+ $2n^2 = O(n) \neq o(n)$
	+ => $if\ c = 1, \ n_0\ inexist\ (2n^2 \leq 1n^2\ for\ all\ n)$

#### $\omega(g(n))$ [Little-Omega]
> **Definition**: for ==any== positive constants $c$, there exist a constant $n_0$ such that $0 \leq cg(n) < f(n)$ $\forall n,\ n \ge n_0$.<br>

+ 比 Omega 嚴格.
+ Example:
	+ $\frac{n^2}{2} = \Omega(n) \neq \omega(n)$
	+ => $if\ c = 2, \ n_0\ inexist\ (\frac{n^2}{2} \leq 2n^2\ for\ all\ n)$


### Summary
> $f(n)=\Theta(g(n))\ and\ g(n)=\Theta(h(n))\ imply\ f(n)=\Theta(h(n))$
> $f(n)=O(g(n))\ and\ g(n)=O(h(n))\ imply\ f(n)=O(h(n))$
> $f(n)=\Omega(g(n))\ and\ g(n)=\Omega(h(n))\ imply\ f(n)=\Omega(h(n))$
> $f(n)=o(g(n))\ and\ g(n)=o(h(n))\ imply\ f(n)=o(h(n))$
> $f(n)=\omega(g(n))\ and\ g(n)=\omega(h(n))\ imply\ f(n)=\omega(h(n))$

> $f(n)=\Theta(f(n))$<br>
> $f(n)=O(f(n))$<br>
> $f(n)=\Omega(f(n))$

> $f(n)=\Theta(g(n))\ iff\ g(n)=\Theta(f(n))$

> $f(n)=O(g(n))\ iff\ g(n)=\Omega(f(n))$<br>
> $f(n)=o(g(n))\ iff\ g(n)=\omega(f(n))$