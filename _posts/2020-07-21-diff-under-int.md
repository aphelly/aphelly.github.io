---
layout: post
title: Differentation under the integral sign &#58; A powerful technique
---

Differentation under the integral sign is a very useful and powerful integration technique. Let's see what it can do.

This technique is powered by a simple usage of Leibniz's Rule:

$$
\frac{d}{dt} \int_{a}^{b}f(x,t)dx = \int_{a}^{b}\frac{\partial}{\partial t}(f(x,t)) dx
$$

Let's see some examples.

**Example 1**: Consider

$$
\int_{0}^{1}\frac{x^3-1}{\ln{x}}dx
$$

Let's play around with this integral by doing something we will often do at the beginning of these differentation under the integral sign exercises, which is assigning a new function with a variable $t$ as such:

$$
\begin{align}
f(t)=\int_{0}^{1}\frac{x^t-1}{\ln{x}}dx,\quad t\geq 0
\end{align}
$$

We then differentiate it with respect to the $t$ via applying Leibniz's Rule:

$$
\begin{align*}
\Rightarrow f'(t)&=\frac{d}{dt}\int_{0}^{1}\frac{x^t-1}{\ln{x}}dx\\
&=\int_{0}^{1}\frac{\partial}{\partial t}\left( \frac{x^t-1}{\ln{x}}\right) dx\\
&=\int_{0}^{1}\frac{\partial}{\partial t}\left( \frac{x^t}{\ln{x}}-\frac{1}{\ln{x}}\right)dx\\
&=\int_{0}^{1}\frac{x^t\ln{x}}{\ln{x}}dx\\
&=\int_{0}^{1}x^t dx\\
&=\left[ \frac{x^{t+1}}{t+1} \right]_{0}^{1}\\
&=\frac{1}{t+1}
\end{align*}
$$

We can now integrate $f'(t)$ with respect to $t$ to find an expression for f(t), different to expression (1)

$$
\begin{align*}
f'(t)=\frac{1}{t+1} \\
\Rightarrow f(t)&=\int \frac{1}{t+1} dt\\
&=\ln(t+1)+c, \quad t \geq 0
\end{align*}
$$

Now to evaluate the constant $c$, we refer to the original function $f(t)$ above and search for an initial condition:

$$
\Rightarrow f(0)=\int_{0}^{1}\frac{x^0-1}{\ln{x}}dx=\int_{0}^{1}0dx=0
$$

Therefore, now knowing that $f(0)=0$, we can find $c$:

$$
0=\ln(0+1)+c \Rightarrow c=0
$$

$$
\therefore f(t)=\ln(t+1)=\int_{0}^{1}\frac{x^t-1}{\ln{x}}dx
$$

Notice how we have now derived an expression for evaluating the definite integral for any positive power $t$ in the numerator of the integrand. In this particular example, the power was 3, so we now have our answer

$$
f(3)=\int_{0}^{1}\frac{x^3-1}{\ln{x}}dx=\ln(3+1)=\ln(4)
$$
