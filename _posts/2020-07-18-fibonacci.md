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

$$
\begin{align*}
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
&= \hspace{0.2cm} ...\\
&=
A^n
\begin{bmatrix}
f_{1}\\
f_{0}
\end{bmatrix}=A^n
\begin{bmatrix}
1\\
0
\end{bmatrix}
\end{align*}
$$

where we iterated all the way back to the two starting terms $f_1=1$ and $f_0=0$.

We end up with the relationship:

$$
\begin{align}
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
\end{bmatrix}
\end{align} 
$$

We now wish to diagonalise the matrix A so that we can more easily compute  $n^{\text{th}}$ powers of A, and hence be able to obtain an explicit formula for $f_n$ without heavy matrix power computation.

To diagonalise A, we wish to find an invertible matrix P that will give us a diagonal matrix D such that

$$
D=P^{-1}AP
$$

To find this matrix P, we first need to compute the eigenvalues of the matrix A. The characteristic equation of A is given by:

$$
\begin{align*}
\det(\lambda I-A)&=0\\
\begin{vmatrix}
\lambda-1 & -1\\
-1 & \lambda
\end{vmatrix}
&=0\\
\lambda(\lambda - 1)-1&=0\\
\lambda^2-\lambda-1&=0
\end{align*}
$$

We can know solve the characteristic equation to find the eigenvalues of A. Since the discriminant of the above characteristic polynomial is $(-1)^2-4(1)(-1)=5>0$, we expect two distinct eigenvalues, $\lambda_1$ and $\lambda_2$.

$$
\begin{align*}
\lambda&=
\frac{-(-1)\pm \sqrt{(-1)^2-4(1)(-1)}}{2(1)}\\
&=\frac{1 \pm \sqrt{5}}{2}
\end{align*}
$$

$$
\Rightarrow \lambda_1=\frac{1 + \sqrt{5}}{2}=\varphi, \quad
\lambda_1=\frac{1 - \sqrt{5}}{2}=\psi
$$

where $\varphi$ is the golden ratio, and $\psi$ is a different constant related to the golden ratio. 

Note that here is another constant often referred to as the golden ratio conjugate, or the silver ratio, which is given by the symbol $\Phi$. It is related to the constant $\psi$ which we defined here by the relation $\Phi=-\psi$, but we won't be referring to it for this exercise. 

If we define 

$$\mathbf{x}=\begin{bmatrix}
x_1\\
x_2
\end{bmatrix}
$$

then $\mathbf{x}$ is an eigenvalue of A corresponding to an eigenvalue $\lambda$ if and only if $\mathbf{x}$ is a nontrivial solution of 

$$(\lambda I-A)\mathbf{x}=\mathbf{0}$$

That is, in matrix form:

$$
\begin{align}
\begin{bmatrix}
\lambda-1 & -1\\
-1 & \lambda
\end{bmatrix}
\begin{bmatrix}
x_1\\
x_2
\end{bmatrix}=
\begin{bmatrix}
0\\
0
\end{bmatrix}
\end{align}
$$

For the case of the eigenvalue $\lambda_1=\varphi$, this becomes

$$
\begin{bmatrix}
\varphi-1 & -1\\
-1 & \varphi
\end{bmatrix}
\begin{bmatrix}
x_1\\
x_2
\end{bmatrix}=
\begin{bmatrix}
0\\
0
\end{bmatrix}
$$

We can find the general solution for $x_1$ and $x_2$ by perfoming Gauss-Jordan elimination to find the reduced row echelon form of the matrix:

$$
\begin{bmatrix}
\varphi-1 & -1 &0\\
-1 & \varphi & 0
\end{bmatrix}
$$

First of all, we will make use of the useful property that $\varphi-1=\frac{1}{\varphi}$, which gives us the resultant matrix:

$$
\begin{bmatrix}
\frac{1}{\varphi} & -1 &0\\
-1 & \varphi &0
\end{bmatrix}
$$

Multiply first row by a factor of $\varphi$

$$
\begin{bmatrix}
1 & -\varphi &0\\
-1 & \varphi &0
\end{bmatrix}
$$

Add the first row to the second row

$$
\begin{bmatrix}
1 & -\varphi &0\\
0 & 0 &0
\end{bmatrix}
$$

We therefore see that $x_1$ is a leading variable, and $x_2$ is a free variable. Thus, we let $x_2=t$ where $t \in \mathbb{R}$, and for $x_1$, we have from the reduced row echelon form matrix that:

$$
x_1-\varphi x_2=0 \quad \Rightarrow \quad x_1=\varphi t
$$

Putting everything together, 

$$
\Rightarrow \begin{bmatrix}
x_1 \\
x_2
\end{bmatrix}
=\begin{bmatrix}
\varphi t \\
t
\end{bmatrix}
=t\begin{bmatrix}
\varphi \\
1
\end{bmatrix},\quad t \in \mathbb{R}
$$

Thus, it follows that

$$
\begin{bmatrix}
\varphi \\
1
\end{bmatrix}
$$

is a basis for the eigenspace corresponding to the eigenvalue $\lambda_1=\varphi$. Therefore, any multiple of this vector is an eigenvector of A corresponding to the eigenvalue $\lambda_1$. Now, we repeat this process for $\lambda_2=\psi$.

For $\lambda_2=\psi$, the result (2) becomes:

$$
\begin{bmatrix}
	\psi-1 & -1\\
	-1 & \psi
\end{bmatrix}
\begin{bmatrix}
	x_1\\
	x_2
\end{bmatrix}=
\begin{bmatrix}
	0\\
	0
\end{bmatrix}
$$

Similar to before, solving for $x_1$ and $x_2$ requires us to perform Gauss-Jordan elimination on the matrix:

$$
\begin{bmatrix}
\psi-1 & -1 &0\\
-1 & \psi & 0
\end{bmatrix}
$$

First of all, we will make use of the relationship that $\psi-1=-\varphi$ to simplify the matrix to:

$$
\begin{bmatrix}
-\varphi & -1 &0\\
-1 & \psi & 0
\end{bmatrix}
$$

Multiply the first row by a factor of $-\frac{1}{\varphi}$

$$
\begin{bmatrix}
1 & \frac{1}{\varphi} &0\\
-1 & \psi & 0
\end{bmatrix}
$$

Add the first row to the second row

$$
\begin{bmatrix}
1 & \frac{1}{\varphi} &0\\
0 & \frac{1}{\varphi}+\psi & 0
\end{bmatrix}
$$

We will now make use to the relationship $\frac{1}{\varphi}=-\psi$ to simplify the matrix:

$$
\begin{bmatrix}
1 & -\psi &0\\
0 & 0 & 0
\end{bmatrix}
$$

Similarly to before, we observe that $x_1$ is a leading variable, and $x_2$ is a free variable. Thus, we let $x_2=s$ where $s \in \mathbb{R}$, and for $x_1$, we have from the reduced row echelon form matrix that:

$$
x_1-\psi x_2=0 \quad \Rightarrow \quad  x_1=\psi s
$$

Putting everything together, 

$$
\Rightarrow \begin{bmatrix}
x_1 \\
x_2
\end{bmatrix}
=\begin{bmatrix}
\psi s \\
s
\end{bmatrix}
=s\begin{bmatrix}
\psi \\
1
\end{bmatrix},\quad s \in \mathbb{R}
$$

Thus, it follows that

$$
\begin{bmatrix}
\psi \\
1
\end{bmatrix}
$$

is a basis for the eigenspace corresponding to the eigenvalue $\lambda_2=\psi$. Therefore, any multiple of this vector is an eigenvector of A corresponding to the eigenvalue $\lambda_2$.
