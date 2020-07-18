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

The Fibonacci numbers are a famous sequence of numbers in mathematics. A
few beginning terms of the sequence are:
{0,1,1,2,3,5,8,13,21,...}
The first two terms are 0 and 1, and each subsequent term is given by
the sum of the previous two terms. Formally, if we let
{*f*<sub>*n*</sub>} (where *n* ∈ ℕ ∪ {0}) represent the Fibonacci
sequence, we have the recurrence relation given by:
$$\\begin{aligned}
f_0=0, \\quad f_1=1\\\\
f_n=f\_{n-1}+f\_{n-2}\\quad \\text{for} \\quad n\\geq 2\\\\\\end{aligned}$$
In this exercise, we derive an explicit formula for the *n*<sup>th</sup>
Fibonacci number, *f*<sub>*n*</sub>, using linear algebra methods. This
formula, known as Binet’s formula, will allow us to compute
*f*<sub>*n*</sub> without having to use the recurrence relation and
finding all the previous terms that come before it in the sequence, i.e.
no need to know *f*<sub>*n* − 1</sub>, *f*<sub>*n* − 2</sub> to know
*f*<sub>*n*</sub>.

First of all, we express the following system of equations derived from
the recurrence relation via matrices:
$$\\left\\{
\\begin{array}{ll}
    f\_{n+1}=f_n+f\_{n-1}\\\\
    f_n=f_n
\\end{array}
\\right.
\\Rightarrow 
\\begin{bmatrix}
f\_{n+1}\\\\
f_n
\\end{bmatrix}
=\\begin{bmatrix}
1 & 1\\\\
1 & 0
\\end{bmatrix}
\\begin{bmatrix}
f_n\\\\
f\_{n-1}
\\end{bmatrix}$$
Letting $A=\\begin{bmatrix}
1 & 1\\\\
1 & 0
\\end{bmatrix}$, we have:
$$\\begin{bmatrix}
    f\_{n+1}\\\\
    f_n
\\end{bmatrix}
=A
\\begin{bmatrix}
f_n\\\\
f\_{n-1}
\\end{bmatrix}$$
This relationship holds for all Fibonacci numbers from *f*<sub>1</sub>.
Now, consider using this relationship recursively:
$$\\begin{aligned}
\\begin{bmatrix}
f\_{n+1}\\\\
f_n
\\end{bmatrix}
&=A
\\begin{bmatrix}
f_n\\\\
f\_{n-1}
\\end{bmatrix}\\\\
&=A\\left( 
A
\\begin{bmatrix}
f\_{n-1}\\\\
f\_{n-2}
\\end{bmatrix}
\\right) \\\\
&=A^2
\\begin{bmatrix}
f\_{n-1}\\\\
f\_{n-2}
\\end{bmatrix}\\\\
&=A^2\\left( 
A
\\begin{bmatrix}
f\_{n-2}\\\\
f\_{n-3}
\\end{bmatrix}
\\right) \\\\
&=A^3
\\begin{bmatrix}
f\_{n-2}\\\\
f\_{n-3}
\\end{bmatrix}\\\\
&= ...\\\\
&=
A^n
\\begin{bmatrix}
f\_{1}\\\\
f\_{0}
\\end{bmatrix}=A^n
\\begin{bmatrix}
1\\\\
0
\\end{bmatrix}\\end{aligned}$$
where we iterated all the way back to the two starting terms
*f*<sub>1</sub> = 1 and *f*<sub>0</sub> = 0.

We end up with the relationship
$$\\begin{aligned}
\\begin{bmatrix}
f\_{n+1}\\\\
f_n
\\end{bmatrix}
=A^n
\\begin{bmatrix}
1\\\\
0
\\end{bmatrix}
\\quad
\\text{, where}
\\quad
A=\\begin{bmatrix}
1 & 1\\\\
1 & 0
\\end{bmatrix}\\end{aligned}$$
We now wish to diagonalise the matrix A so that we can more easily
compute *n*<sup>th</sup> powers of A, and hence be able to obtain an
explicit formula for *f*<sub>*n*</sub> without heavy matrix power
computation.
