---
layout: post
title: Integration by parts &#58; An unconventional proof
---

In this post, we prove integration by parts by employing a double integral.

Let  $T$  be the region on the  $x-y$  plane inside the triangle with vertices $(a,a), (b,a), (b,b)$,  as shown below. 

Note that the line joining $(a,a)$ and $(b,b)$ is $y=x$.

<p align="center">
  <img src="https://github.com/aphelly/aphelly.github.io/blob/master/images/intparts.PNG?raw=true" />
</p>

Define the functions

$$
F'(x) = f(x), \quad a \leq x \leq b
$$

$$
G'(y) = g(y), \quad a \leq y \leq b
$$

and

$$
h(x,y)=f(x)g(y)
$$

Now, we will integrate the function $h(x,y)$ over the domain $T$. Let this integral be denoted as $H$:

$$
H=\iint\limits_{T} h(x,y) \hspace{1mm}  dA  = \iint\limits_{T} f(x)g(y) \hspace{1mm} dy dx 
$$

The definite integral H can be evaluated two different ways using different bounds to describe the domain T. 

**Method 1:** Using the bounds

$$
\quad a \leq y \leq x, \quad a \leq x \leq b
$$

$$
\begin{align*}
\Rightarrow	H &= \int_{a}^{b} \int_{a}^{x} f(x)g(y) dy dx\\
	&= \int_{a}^{b} \left[ f(x)G(y)\right] _{y=a}^{y=x} dx \\
	&= \int_{a}^{b} f(x) \left( G(x)-G(a) \right) dx\\
	&= \int_{a}^{b} f(x)G(x) dx - \int_{a}^{b} f(x)G(a) dx
	&= \int_{a}^{b} f(x)G(x) dx - \left[  F(x)G(a)\right]_{x=a}^{x=b} \\
	&= \int_{a}^{b} f(x)G(x) dx - G(a)F(b) + G(a)F(a)\\
\end{align*}
$$

**Method 2:** Using the bounds

$$
\quad y \leq x \leq b, \quad a \leq y \leq b
$$

$$
\begin{align*}
	\Rightarrow	H &= \int_{a}^{b} \int_{y}^{b} f(x)g(y) dx dy \\
	&= \int_{a}^{b} \left[ F(x)g(y)\right] _{x=y}^{x=b} dy \\
	&= \int_{a}^{b} g(y) \left( F(b)-F(y) \right) dy\\
	&= \int_{a}^{b} F(b)g(y) dy - \int_{a}^{b} F(y)g(y) dy \\
	&= \left[  F(b)G(y)\right]_{y=a}^{y=b} - \int_{a}^{b} F(y)g(y) dy \\
	&= F(b)G(b) - F(b)G(a)- \int_{a}^{b} F(y)g(y) dy \\
\end{align*}
$$

We now can equate the two expressions for H, derived in **Method 1** and **Method 2**:
$$
\begin{align*}
	\int_{a}^{b} f(x)G(x) dx - G(a)F(b) + G(a)F(a) &= F(b)G(b) - F(b)G(a)- \int_{a}^{b} F(y)g(y) dy \\
	\int_{a}^{b} f(x)G(x) dx &= F(b)G(b) - F(a)G(a) - \int_{a}^{b} F(y)g(y) dy \\
\Rightarrow	\int_{a}^{b} f(x)G(x) dx &= \left[ F(x)G(x) \right]_{a}^{b}  - \int_{a}^{b} F(y)g(y) dy \qed \\
\end{align*}
$$

Awesome! This was quite an unconventional proof for integration by parts.
