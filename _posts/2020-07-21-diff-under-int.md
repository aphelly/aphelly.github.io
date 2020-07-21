---
layout: post
title: Differentation under the integral sign &#58; A powerful technique
---

Differentation under the integral sign is a very useful and powerful integration technique. Let's see what it can do.

This technique is powered by a simple usage of Leibniz's Rule:

$$
\frac{d}{dt} \int_{a}^{b}f(x,t)dx = \int_{a}^{b}\frac{\partial}{\partial t}(f(x,t)) dx
$$

Let's see some examples. The following examples were inspired by a variety of YouTube channels. Check our their videos on this topic: [Andrew Dotson](https://www.youtube.com/watch?v=pqP13eLG35U), [blackpenredpen](https://www.youtube.com/watch?v=YO38MCdj-GM), [Flammable Maths](https://www.youtube.com/watch?v=S9LttmTD_14).

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
f'(t)&=\frac{1}{t+1} \\
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

Notice how we have now derived an expression for evaluating the definite integral for any positive power $t$ in the numerator of the integrand. This is another benefit of differentiating under the integral sign. 

In this particular example though, the power was 3, so we now have our answer

$$
f(3)=\int_{0}^{1}\frac{x^3-1}{\ln{x}}dx=\ln(3+1)=\ln(4)
$$

**Example 2**: Consider

$$
\int_{-\infty}^{\infty}\frac{\cos(x)}{x^2+1}dx
$$

We define a new function with a new variable $t$ as the coefficient of $x$ inside the cosine:

$$
\begin{align}
f(t)=\int_{-\infty}^{\infty}\frac{\cos(tx)}{x^2+1}dx
\end{align}
$$

We then evaluate the derivative of the function using Leibniz's Rule:

$$
\begin{align*}
f'(t)&=\frac{d}{dt}\int_{-\infty}^{\infty}\frac{\cos(tx)}{x^2+1}dx\\
&=\int_{-\infty}^{\infty}\frac{\partial}{\partial t}\left( \frac{\cos(tx)}{x^2+1}\right) dx\\
&=\int_{-\infty}^{\infty}\frac{-x\sin(tx)}{x^2+1}dx\\
&=-\int_{-\infty}^{\infty}\frac{x^2\sin(tx)}{x(x^2+1)}dx\\
&=-\int_{-\infty}^{\infty}\frac{(x^2+1-1)\sin(tx)}{x(x^2+1)}dx\\
&=-\int_{-\infty}^{\infty}\frac{(x^2+1)\sin(tx)}{x(x^2+1)}dx+\int_{-\infty}^{\infty}\frac{\sin(tx)}{x(x^2+1)}dx\\
&=-\int_{-\infty}^{\infty}\frac{\sin(tx)}{x}dx+\int_{-\infty}^{\infty}\frac{\sin(tx)}{x(x^2+1)}dx\\
\end{align*}
$$

We now use the general result of the Dirichlet integral and the fact that $\frac{\sin(x)}{x}$ is even (we will prove a version of this in example 3):

$$
\int_{0}^{\infty}\frac{\sin(tx)}{x}dx=\frac{\pi}{2} 
$$

$$
\Rightarrow \int_{-\infty}^{\infty}\frac{\sin(tx)}{x}dx=\pi 
$$

So therefore, we now have:

$$
\begin{align}
f'(t)=-\pi+\int_{-\infty}^{\infty}\frac{\sin(tx)}{x(x^2+1)}dx
\end{align}
$$

Now we have to differentiate again to obtain $f''(t)$:

$$
\begin{align*}
f''(t)&=\frac{d}{dt}\left( -\pi+\int_{-\infty}^{\infty}\frac{\sin(tx)}{x(x^2+1)}dx\right)\\
&=\int_{-\infty}^{\infty}\frac{\partial}{\partial t}\left( \frac{\sin(tx)}{x(x^2+1)}\right) dx\\
&=\int_{-\infty}^{\infty}\frac{x\cos(tx)}{x(x^2+1)}dx\\
&=\int_{-\infty}^{\infty}\frac{\cos(tx)}{x^2+1}dx\\
&=f(t)
\end{align*}
$$

From this observation, we note that the function satisfies the differential equation:

$$
f''(t)=f(t) \Rightarrow f''(t)-f(t)=0
$$

Now to solve this differential equation, we strategically guess the general solution in the form:

$$
f(t)=ce^{\lambda t}
$$

This gives us the following:

$$
f'(t)=\lambda ce^{\lambda t} \Rightarrow f''(t)=\lambda^2 ce^{\lambda t}
$$

Which we can then substitute into the differential equation:

$$
\begin{align*}
\lambda^2 ce^{\lambda t}-ce^{\lambda t}&=0\\
ce^{\lambda t}(\lambda^2-1)&=0\\
\lambda^2-1&=0\\
\lambda=\pm{1}
\end{align*}
$$

Therefore the general solution for this differential equation and its derivative is:

$$
f(t)=c_1e^t+c_2e^{-t}, \quad
f'(t)=c_1e^t-c_2e^{-t}
$$

Now we must find initial conditions in order to find $c_1$ and $c_2$. We do this by substituing $t=0$ into (2) and (3)

$$
f(0)=\int_{-\infty}^{\infty}\frac{\cos(0)}{x^2+1}dx=\int_{-\infty}^{\infty}\frac{1}{x^2+1}dx=\left[\arctan{x}\right]_{-\infty}^{\infty}=\frac{\pi}{2}-\left( -\frac{\pi}{2}\right) =\pi
$$

$$
f'(0)=-\pi+\int_{-\infty}^{\infty}\frac{\sin(0)}{x(x^2+1)}dx =-\pi+\int_{-\infty}^{\infty}0dx=-\pi
$$
