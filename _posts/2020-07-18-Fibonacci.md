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

\begin{align*}
test this equation &=
5 + 2 \\
&= 5+1\\
&= e_i +\pi
\end{align*}
