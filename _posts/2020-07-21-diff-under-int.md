---
layout: post
title: Differentiation under the integral sign&#58; A sneaky technique
---

Differentiation under the integral sign is a very useful and powerful integration technique. Let's see what it can do.

This technique is powered by a simple usage of Leibniz's Rule:

$$
\dv{t} \int_{a}^{b}f(x,t) \dd{x} = \int_{a}^{b}\pdv{t}(f(x,t)) \dd{x}
$$

Let's see some examples. The following examples were inspired by a variety of YouTube channels. Check our their videos on this topic: [Andrew Dotson](https://www.youtube.com/watch?v=pqP13eLG35U), [blackpenredpen](https://www.youtube.com/watch?v=YO38MCdj-GM), [Flammable Maths](https://www.youtube.com/watch?v=S9LttmTD_14).

**Example 1**: Consider

$$
\int_{0}^{1}\frac{x^3-1}{\ln{x}} \dd{x}
$$

Let's play around with this integral by doing something we will often do at the beginning of these differentation under the integral sign exercises, which is assigning a new function with a variable $t$ as such:

$$
\begin{align*}
f(t)=\int_{0}^{1}\frac{x^t-1}{\ln{x}} \dd{x},\quad t\geq 0
\end{align*}
$$

We then differentiate it with respect to the $t$ via applying Leibniz's Rule:

$$
\begin{align*}
\Rightarrow f'(t)&=\dv{t}\int_{0}^{1}\frac{x^t-1}{\ln{x}}\dd{x}\\
&=\int_{0}^{1}\pdv{t}(\frac{x^t-1}{\ln{x}}) \dd{x}\\
&=\int_{0}^{1}\pdv{t}(\frac{x^t}{\ln{x}}-\frac{1}{\ln{x}})\dd{x}\\
&=\int_{0}^{1}\frac{x^t\ln{x}}{\ln{x}}\dd{x}\\
&=\int_{0}^{1}x^t \dd{x}\\
&=\left[ \frac{x^{t+1}}{t+1} \right]_{0}^{1}\\
&=\frac{1}{t+1}
\end{align*}
$$

We can now integrate $f'(t)$ with respect to $t$ to find an expression for f(t), different to expression (1)

$$
\begin{align*}
f'(t)&=\frac{1}{t+1} \\
\Rightarrow f(t)&=\int \frac{1}{t+1} \dd{t}\\
&=\ln(t+1)+c, \quad t \geq 0
\end{align*}
$$

Now to evaluate the constant $c$, we refer to the original function $f(t)$ above and search for an initial condition:

$$
\Rightarrow f(0)=\int_{0}^{1}\frac{x^0-1}{\ln{x}}\dd{x}=\int_{0}^{1}0\dd{x}=0
$$

Therefore, now knowing that $f(0)=0$, we can find $c$:

$$
0=\ln(0+1)+c \Rightarrow c=0
$$

$$
\therefore f(t)=\ln(t+1)=\int_{0}^{1}\frac{x^t-1}{\ln{x}}\dd{x}
$$

Notice how we have now derived an expression for evaluating the definite integral for any positive power $t$ in the numerator of the integrand. This is another benefit of differentiating under the integral sign. 

In this particular example though, the power was 3, so we now have our answer

$$
f(3)=\int_{0}^{1}\frac{x^3-1}{\ln{x}}\dd{x}=\ln(3+1)=\ln(4)
$$

**Example 2**: Consider

$$
\int_{-\infty}^{\infty}\frac{\cos(x)}{x^2+1} \dd{x}
$$

We define a new function with a new variable $t$ as the coefficient of $x$ inside the cosine:

$$
\begin{align*}
f(t)=\int_{-\infty}^{\infty}\frac{\cos(tx)}{x^2+1}\dd{x}
\end{align*}
$$

We then evaluate the derivative of the function using Leibniz's Rule:

$$
\begin{align*}
f'(t)&=\dv{t}\int_{-\infty}^{\infty}\frac{\cos(tx)}{x^2+1}\dd{x}\\
&=\int_{-\infty}^{\infty}\pdv{t}(\frac{\cos(tx)}{x^2+1}) \dd{x}\\
&=\int_{-\infty}^{\infty}\frac{-x\sin(tx)}{x^2+1}\dd{x}\\
&=-\int_{-\infty}^{\infty}\frac{x^2\sin(tx)}{x(x^2+1)}\dd{x}\\
&=-\int_{-\infty}^{\infty}\frac{(x^2+1-1)\sin(tx)}{x(x^2+1)}\dd{x}\\
&=-\int_{-\infty}^{\infty}\frac{(x^2+1)\sin(tx)}{x(x^2+1)}\dd{x}+\int_{-\infty}^{\infty}\frac{\sin(tx)}{x(x^2+1)}\dd{x}\\
&=-\int_{-\infty}^{\infty}\frac{\sin(tx)}{x}\dd{x}+\int_{-\infty}^{\infty}\frac{\sin(tx)}{x(x^2+1)}\dd{x}\\
\end{align*}
$$

We now use the general result of the Dirichlet integral and the fact that $\frac{\sin(x)}{x}$ is even (we will prove a version of this in example 3):

$$
\int_{0}^{\infty}\frac{\sin(tx)}{x}\dd{x}=\frac{\pi}{2} 
$$

$$
\Rightarrow \int_{-\infty}^{\infty}\frac{\sin(tx)}{x}\dd{x}=\pi 
$$

So therefore, we now have:

$$
\begin{align*}
f'(t)=-\pi+\int_{-\infty}^{\infty}\frac{\sin(tx)}{x(x^2+1)}\dd{x}
\end{align*}
$$

Now we have to differentiate again to obtain $f''(t)$:

$$
\begin{align*}
f''(t)&=\dv{t}(-\pi+\int_{-\infty}^{\infty}\frac{\sin(tx)}{x(x^2+1)}\dd{x})\\
&=\int_{-\infty}^{\infty}\pdv{t}(\frac{\sin(tx)}{x(x^2+1)})\dd{x}\\
&=\int_{-\infty}^{\infty}\frac{x\cos(tx)}{x(x^2+1)}\dd{x}\\
&=\int_{-\infty}^{\infty}\frac{\cos(tx)}{x^2+1}\dd{x}\\
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
f(0)=\int_{-\infty}^{\infty}\frac{\cos(0)}{x^2+1}\dd{x}=\int_{-\infty}^{\infty}\frac{1}{x^2+1}\dd{x}=\left[\arctan{x}\right]_{-\infty}^{\infty}=\frac{\pi}{2}-\left( -\frac{\pi}{2}\right) =\pi
$$

$$
f'(0)=-\pi+\int_{-\infty}^{\infty}\frac{\sin(0)}{x(x^2+1)}\dd{x} =-\pi+\int_{-\infty}^{\infty}0\dd{x}=-\pi
$$

Now using the conditions $f(0)=\pi$ and $f'(0)=-\pi$, we can find $c_1$ and $c_2$

$$
f(0)=\pi \Rightarrow c_1+c_2=\pi
$$

$$
f'(0)=-\pi \Rightarrow c_1-c_2=-\pi
$$

Simulteneously solving these two equations for $c_1$ and $c_2$, we obtain $c_1=0$ and $c_2=\pi$

Therefore, 

$$
f(t)=\pi e^{-t}=\int_{-\infty}^{\infty}\frac{\cos(tx)}{x^2+1}\dd{x}
$$

Notice how similar to example 1, we have now obtained a general expression for the value of the improper definite integral for any coefficient $t$ inside the cosine. In this particular question, the value was $t=1$, so therefore we can get our answer

$$
f(1)=\int_{-\infty}^{\infty}\frac{\cos(x)}{x^2+1}\dd{x}=\pi e^{-1}=\frac{\pi}{e}
$$

**Example 3**: Consider

$$
\int_{0}^{\infty}\frac{\sin{x}}{x}\dd{x}
$$

We define a new function as below:

$$
\begin{align*}
f(t)=\int_{0}^{\infty}\frac{\sin{x}}{x}e^{-tx}\dd{x}, \quad t\geq0
\end{align*}
$$

Now, we differentiate $f(t)$ with respect to t using Leibniz's rule:

$$
\begin{align*}
f'(t)&=\dv{t}\int_{0}^{\infty}\frac{\sin{x}}{x}e^{-tx}\dd{x}\\
&=\int_{0}^{\infty}\pdv{t}(\frac{\sin{x}}{x}e^{-tx}) \dd{x}\\
&=\int_{0}^{\infty}-\frac{\sin{x}}{x}xe^{-tx}\dd{x}\\
&=\int_{0}^{\infty}-e^{-tx}\sin{x}\dd{x}\\
&=\int_{0}^{\infty}-e^{-tx}\operatorname{Im}(e^{ix})\dd{x}\\
&=-\int_{0}^{\infty}\operatorname{Im}e^{(-t+i)x}\dd{x}\\
&=-\left[\operatorname{Im} \left( \frac{e^{(-t+i)x}}{-t+i}\right)  \right]_{0}^{\infty}\\
&= -\left[\operatorname{Im} \left(  (-t-i)\frac{e^{(-t+i)x}}{t^2+1}\right)  \right]_{0}^{\infty}\\
&= -\left[\operatorname{Im}\left(  (-t-i)\frac{e^{-tx}e^{ix}}{t^2+1}\right)  \right]_{0}^{\infty}\\
&= -\left[\frac{e^{-tx}}{t^2+1}\operatorname{Im}\left( (-t-i)e^{ix}\right) \right]_{0}^{\infty}\\
&=-\left[\frac{e^{-tx}}{t^2+1}\operatorname{Im}\left( (-t-i)(\cos{x}+i\sin{x})\right) \right]_{0}^{\infty}\\
&=-\left[\frac{e^{-tx}}{t^2+1}\operatorname{Im}\left( -t\cos{x}-it\sin{x}-i\cos{x}+\sin{x} \right) \right]_{0}^{\infty}\\
&=-\left[\frac{e^{-tx}}{t^2+1}(-t\sin{x}-\cos{x}) \right]_{0}^{\infty}\\
&=\left[\frac{e^{-tx}}{t^2+1}(t\sin{x}+\cos{x}) \right]_{0}^{\infty}\\
&=0-\frac{e^0}{t^2+1}(t\sin{0}+\cos{0})\\
&=-\frac{1}{t^2+1}
\end{align*}
$$

Now we can antidifferentiate $f'(t)$ to obtain an expression for $f(t)$:

$$
f'(t)=-\frac{1}{t^2+1}\Rightarrow f(t)=\int-\frac{1}{t^2+1}\dd{t}=-\arctan{t}+c
$$

Now, to obtain the value of the constant of integration $c$, we find a condition using (4). Consider the limit

$$
\lim_{t\to\infty}f(t)=\lim_{t\to\infty}\int_{0}^{\infty}\frac{\sin{x}}{x}e^{-tx}\dd{x}=\int_{0}^{\infty}0\dd{x}=0
$$

Thus, we can apply this to find $c$:

$$
\lim_{t\to\infty}(-\arctan{t}+c)=0 \Rightarrow -\frac{\pi}{2}+c=0 \Rightarrow c=\frac{\pi}{2}
$$

Therefore we arrive at the conclusion that:

$$
f(t)=\int_{0}^{\infty}\frac{\sin{x}}{x}e^{-tx}\dd{x}=-\arctan{t}+\frac{\pi}{2}
$$

Once again, like both of the previous examples, we have an expression for the value of the improper definite integral for any value of $t$. However, in this particular example, $t=0$. Thus, we have our answer

$$
f(0)=\int_{0}^{\infty}\frac{\sin{x}}{x}e^{0}\dd{x}=\int_{0}^{\infty}\frac{\sin{x}}{x}\dd{x}=-\arctan{0}+\frac{\pi}{2}=\frac{\pi}{2}
$$

**Example 4**: Consider

$$
\int_{0}^{\infty}e^{-x^2}\cos{(5x)}\dd{x}
$$

We define a new function with a variable $t$
$$
\begin{align*}
f(t)=\int_{0}^{\infty}e^{-x^2}\cos{(tx)}\dd{x}
\end{align*}
$$

Then, we compute the derivative of this newly defined function with respect to t using Leibniz's rule, which we notice that we can integrate by parts with

$$
\begin{align*}
f'(t)&=\dv{t}\int_{0}^{\infty}e^{-x^2}\cos{(tx)}\dd{x}\\
&=\int_{0}^{\infty}\pdv{t}(e^{-x^2}\cos{(tx)})\dd{x}\\
&=\int_{0}^{\infty}-xe^{-x^2}\sin{(tx)}\dd{x}\\
&=\int_{0}^{\infty}\dv{x}(\frac{1}{2}e^{-x^2}) \sin{(tx)}\dd{x}\\
&=\left[ \frac{1}{2}e^{-x^2}\sin{(tx)} \right]_{0}^{\infty} - \int_{0}^{\infty}\frac{1}{2}e^{-x^2}\frac{d}{dx}(\sin{(tx)})\dd{x}\\
&=\left[ \frac{1}{2}e^{-x^2}\sin{(tx)} \right]_{0}^{\infty} - \int_{0}^{\infty}\frac{1}{2}te^{-x^2}\cos{(tx)}\dd{x}\\
&=0-\frac{1}{2}\sin(0)-\frac{t}{2}\int_{0}^{\infty}e^{-x^2}\cos{(tx)}\dd{x}\\
&=-\frac{t}{2}f(t)
\end{align*}
$$

Therefore, we arrive at the differential equation below, which is seperable:

$$
\begin{align*}
f'(t)&=-\frac{t}{2}f(t)\\
\dv{f}{t}&=-\frac{t}{2}f\\
\frac{1}{f}\dv{f}{t}&=-\frac{t}{2}\\
\int\frac{1}{f}\dd{f}&=-\int \frac{t}{2}\dd{t}\\
\ln{|f|}&=-\frac{t^2}{4}+c\\
|f|&=e^{-\frac{t^2}{4}+c}\\
f&=c_1e^{-\frac{t^2}{4}}\\
\end{align*}
$$

Now, we search for an initial condition using (5) in order to find $c_1$

$$
f(0)=\int_{0}^{\infty}e^{-x^2}\cos{0}\dd{x}=\int_{0}^{\infty}e^{-x^2}\dd{x}=\frac{\sqrt{\pi}}{2}
$$

where we used the standard result of the Gaussian integral: 

$$ \int_{0}^{\infty}e^{-x^2}\dd{x}=\frac{\sqrt{\pi}}{2}         
$$

Therefore, we find the initial condition $f(0)=\frac{\sqrt{\pi}}{2}$, which we use to find the value of $c_1$:

$$
\frac{\sqrt{\pi}}{2}=c_1e^0 \Rightarrow c_1=\frac{\sqrt{\pi}}{2}
$$

$$
\therefore f(t)=\frac{\sqrt{\pi}}{2}e^{-\frac{t^2}{4}}=\int_{0}^{\infty}e^{-x^2}\cos{(tx)}\dd{x}
$$

As always, we found an expression for the value of the improper definite integral for any value of t in the integrand. In this particular example, $t=5$, therefore we have our answer

$$
f(5)=\int_{0}^{\infty}e^{-x^2}\cos{(5x)}\dd{x}=\frac{\sqrt{\pi}}{2}e^{-\frac{5^2}{4}}=\frac{\sqrt{\pi}}{2}e^{-\frac{25}{4}}
$$

