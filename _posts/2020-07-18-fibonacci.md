---
layout: post
title: Linear Algebra &#58; A Supreme Display of its Power with Fibonacci Numbers
---

The Fibonacci numbers are a famous sequence of numbers in mathematics. A few beginning terms of the sequence are:

$$
\left\lbrace 0, 1, 1, 2, 3, 5, 8, 13, 21, ...\right\rbrace 
$$

The first two terms are 0 and 1, and each subsequent term is given by the sum of the previous two terms. Formally, if we let $\left\lbrace f_n\right\rbrace$ (where $n \in \mathbb{N} \cup \left\lbrace 0 \right\rbrace  $) represent the Fibonacci sequence, we have the recurrence relation given by:

$$
\begin{align*}
f_0=0, \quad f_1=1\\
f_n=f_{n-1}+f_{n-2}\quad \text{for} \quad n\geq 2\\
\end{align*}
$$

In this exercise, we derive an explicit formula for the $n^{\text{th}}$ Fibonacci number, $f_n$, using linear algebra methods. This formula, known as Binet's formula, will allow us to compute $f_n$ without having to use the recurrence relation and finding all the previous terms that come before it in the sequence, i.e. no need to know $f_{n-1}, f_{n-2}$ to know $f_n$. 

First of all, we express the following system of equations derived from the recurrence relation via matrices:

$$
\left\{
\begin{array}{ll}
	f_{n+1}=f_n+f_{n-1}\\
	f_n=f_n
\end{array}
\right.
\Rightarrow 
\begin{bmatrix}
f_{n+1}\\
f_n
\end{bmatrix}
=\begin{bmatrix}
1 & 1\\
1 & 0
\end{bmatrix}
\begin{bmatrix}
f_n\\
f_{n-1}
\end{bmatrix}
$$

Letting 
$$A=\begin{bmatrix}
1 & 1\\
1 & 0
\end{bmatrix}$$
, we have:

$$\begin{bmatrix}
	f_{n+1}\\
	f_n
\end{bmatrix}
=A
\begin{bmatrix}
f_n\\
f_{n-1}
\end{bmatrix}
$$

This relationship holds for all Fibonacci numbers from $f_1$. Now, consider using this relationship recursively:


