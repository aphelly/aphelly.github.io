---
layout: post
title: Fibonacci Numbers via Linear Algebra
---

In this post, we attempt to derive an explicit formula for the Fibonacci numbers via linear algebra techniques.

The Fibonacci numbers are a famous sequence of numbers in mathematics. A few beginning terms of the sequence are:

$$
\left\lbrace 0, 1, 1, 2, 3, 5, 8, 13, 21, ...\right\rbrace 
$$

The first two terms are 0 and 1, and each subsequent term is given by the sum of the previous two terms. 

**<span>Fibonacci Numbers via Linear Algebra</span>**

The Fibonacci numbers are a famous sequence of numbers in mathematics. A
few beginning terms of the sequence are:
\[\left\lbrace 0, 1, 1, 2, 3, 5, 8, 13, 21, ...\right\rbrace\] The first
two terms are 0 and 1, and each subsequent term is given by the sum of
the previous two terms. Formally, if we let
\(\left\lbrace f_n\right\rbrace\) (where
\(n \in \mathbb{N} \cup \left\lbrace 0 \right\rbrace\)) represent the
Fibonacci sequence, we have the recurrence relation given by:
\[\begin{aligned}
f_0=0, \quad f_1=1\\
f_n=f_{n-1}+f_{n-2}\quad \text{for} \quad n\geq 2\\\end{aligned}\] In
this exercise, we derive an explicit formula for the \(n^{\text{th}}\)
Fibonacci number, \(f_n\), using linear algebra methods. This formula,
known as Binet’s formula, will allow us to compute \(f_n\) without
having to use the recurrence relation and finding all the previous terms
that come before it in the sequence, i.e. no need to know
\(f_{n-1}, f_{n-2}\) to know \(f_n\).

First of all, we express the following system of equations derived from
the recurrence relation via matrices: \[\left\{
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
\end{bmatrix}\] Letting \(A=\begin{bmatrix}
1 & 1\\
1 & 0
\end{bmatrix}\), we have: \[\begin{bmatrix}
    f_{n+1}\\
    f_n
\end{bmatrix}
=A
\begin{bmatrix}
f_n\\
f_{n-1}
\end{bmatrix}\] This relationship holds for all Fibonacci numbers from
\(f_1\). Now, consider using this relationship recursively:
\[\begin{aligned}
\begin{bmatrix}
f_{n+1}\\
f_n
\end{bmatrix}
&=A
\begin{bmatrix}
f_n\\
f_{n-1}
\end{bmatrix}\\
&=A\left( 
A
\begin{bmatrix}
f_{n-1}\\
f_{n-2}
\end{bmatrix}
\right) \\
&=A^2
\begin{bmatrix}
f_{n-1}\\
f_{n-2}
\end{bmatrix}\\
&=A^2\left( 
A
\begin{bmatrix}
f_{n-2}\\
f_{n-3}
\end{bmatrix}
\right) \\
&=A^3
\begin{bmatrix}
f_{n-2}\\
f_{n-3}
\end{bmatrix}\\
&= ...\\
&=
A^n
\begin{bmatrix}
f_{1}\\
f_{0}
\end{bmatrix}=A^n
\begin{bmatrix}
1\\
0
\end{bmatrix}\end{aligned}\] where we iterated all the way back to the
two starting terms \(f_1=1\) and \(f_0=0\).

We end up with the relationship \[\begin{aligned}
\begin{bmatrix}
f_{n+1}\\
f_n
\end{bmatrix}
=A^n
\begin{bmatrix}
1\\
0
\end{bmatrix}
\quad
\text{, where}
\quad
A=\begin{bmatrix}
1 & 1\\
1 & 0
\end{bmatrix}\end{aligned}\] We now wish to diagonalise the matrix A so
that we can more easily compute \(n^{\text{th}}\) powers of A, and hence
be able to obtain an explicit formula for \(f_n\) without heavy matrix
power computation.
