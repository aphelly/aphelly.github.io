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

$$\int e^{2t}\sin{t} dt$$

Integration by parts

$$\begin{aligned}
\int e^{2t}\sin{t} dt 
&= \int \frac{d}{dt}(e^{2t})\sin{t} dt \\
&= \frac{1}{2}e^{2t}\sin{t}-\int\frac{1}{2}e^{2t}\cos{t} dt\\
&= \frac{1}{2}e^{2t}\sin{t}-\frac{1}{2}\int\frac{d}{dt}\left(\frac{1}{2}e^{2t}\right)\cos{t}dt\\
&=\frac{1}{2}e^{2t}\sin{t}-\frac{1}{2} \left(\frac{1}{2}e^{2t}\cos{t}+\int\frac{1}{2}e^{2t}\sin{t}dt\right)\\
&=\frac{1}{2}e^{2t}\sin{t}-\frac{1}{4}e^{2t}\cos{t}-\frac{1}{4}\int e^{2t}\sin{t}dt\end{aligned}$$

Now we can let $$I=\int e^{2t}\sin{t} dt$$ and rearrange for it using
both sides

$$\begin{aligned}
I 
&= \frac{1}{2}e^{2t}\sin{t}-\frac{1}{4}e^{2t}\cos{t}-\frac{1}{4}I\\
\frac{5}{4}I 
&= \frac{1}{2}e^{2t}\sin{t}-\frac{1}{4}e^{2t}\cos{t}\\
\Rightarrow I &=\frac{4}{5}\left(\frac{1}{2}e^{2t}\sin{t}-\frac{1}{4}e^{2t}\cos{t}\right)\\
&= \frac{2}{5}e^{2t}\sin{t}-\frac{1}{5}e^{2t}\cos{t} \\
&= \frac{e^{2t}}{5}(2\sin{t}-\cos{t})+c\end{aligned}$$

Complex exponential

$$\begin{aligned}
\int e^{2t}\sin{t} dt &= \int e^{2t} \operatorname{Im}({e^{it}})dt \\
&= \operatorname{Im} \left(\int e^{2t}e^{it} dt \right)\\
&= \operatorname{Im} \left(\int e^{(2+i)t} dt \right)\\
&= \operatorname{Im} \left(\frac{1}{2+i} e^{(2+i)t}\right)\\
&= \operatorname{Im} \left(\frac{2-i}{5} e^{2t}e^{it}\right)\\
&= \frac{e^{2t}}{5} \operatorname{Im}((2-i)e^{it}) \\
&= \frac{e^{2t}}{5} \operatorname{Im}((2-i)(\cos{t}+i\sin{t}))\\
&=\frac{e^{2t}}{5} \operatorname{Im}(2\cos(t)+2i\sin{t}-i\cos{t}+\sin{t})\\
&=\frac{e^{2t}}{5}(2\sin{t}-\cos{t}) +c \end{aligned}$$
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
