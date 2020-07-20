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

With this integral, observe that we will be very happy if there was a way for the $\ln(x)$ part of the integrand to cancel out. Let's play around with this integral by doing something we will often do at the beginning of these differentation under the integral sign exercises, which is assigning a new function with a variable $t$ as such:

$$
f(t)=\int_{0}^{1}\frac{x^t-1}{\ln{x}}dx, t\geq 0
$$

