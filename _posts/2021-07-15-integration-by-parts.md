---
layout: post
title: Integration by parts &#58; An unconventional proof
---

In this post, we prove integration by parts by employing a double integral.

Let $T$ be the region on the $x-y$ plane inside the triangle with vertices $(a,a), (b,a), (b,b)$, as shown below. Note that the line joining $(a,a)$ and $(b,b)$ is $y=x$.

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
H=\iint\limits_{T} h(x,y) \hspace{1mm} \dd A  = \iint\limits_{T} f(x)g(y) \hspace{1mm} \dd y \dd x 
$$

The definite integral H can be evaluated two different ways using different bounds to describe the domain T. 

\textbf{Method 1:} Using the bounds

$$
\quad a \leq y \leq x, \quad a \leq x \leq b
$$

$$
\begin{align*}
\Rightarrow	H &= \int_{a}^{b} \int_{a}^{x} f(x)g(y) \dd y \dd x\\
	&= \int_{a}^{b} \left[ f(x)G(y)\right] _{y=a}^{y=x} \dd x \\
	&= \int_{a}^{b} f(x) \left( G(x)-G(a) \right) \dd x\\
	&= \int_{a}^{b} f(x)G(x) \dd x - \int_{a}^{b} f(x)G(a) \dd x
\end{align*}
$$

$$
\begin{align*}
	&= \int_{a}^{b} f(x)G(x) \dd x - \left[  F(x)G(a)\right]_{x=a}^{x=b} \\
	&= \int_{a}^{b} f(x)G(x) \dd x - G(a)F(b) + G(a)F(a) \stepcounter{equation}\tag{\theequation}\label{myeq1}\\
\end{align*}
$$

\textbf{Method 2:} Using the bounds

$$
\quad y \leq x \leq b, \quad a \leq y \leq b
$$

$$
\begin{align*}
	\Rightarrow	H &= \int_{a}^{b} \int_{y}^{b} f(x)g(y) \dd x \dd y \\
	&= \int_{a}^{b} \left[ F(x)g(y)\right] _{x=y}^{x=b} \dd y \\
	&= \int_{a}^{b} g(y) \left( F(b)-F(y) \right) \dd y\\
	&= \int_{a}^{b} F(b)g(y) \dd y - \int_{a}^{b} F(y)g(y) \dd y \\
	&= \left[  F(b)G(y)\right]_{y=a}^{y=b} - \int_{a}^{b} F(y)g(y) \dd y \\
	&= F(b)G(b) - F(b)G(a)- \int_{a}^{b} F(y)g(y) \dd y \stepcounter{equation}\tag{\theequation}\label{myeq2} \\
\end{align*}
$$

We now can equate the two expressions for H, Equation (1) and Equation (2):
$$
\begin{align*}
	\int_{a}^{b} f(x)G(x) \dd x - G(a)F(b) + G(a)F(a) &= F(b)G(b) - F(b)G(a)- \int_{a}^{b} F(y)g(y) \dd y \\
	\int_{a}^{b} f(x)G(x) \dd x &= F(b)G(b) - F(a)G(a) - \int_{a}^{b} F(y)g(y) \dd y \\
\Rightarrow	\int_{a}^{b} f(x)G(x) \dd x &= \left[ F(x)G(x) \right]_{a}^{b}  - \int_{a}^{b} F(y)g(y) \dd y \qed \\
\end{align*}
$$
