---
layout: post
title: Residue theorem&#58; An awesome tool for integration
---


<div style="display:none">
  $
    \newcommand{\res}[2]{\underset{#1}{\Res}\left\lbrace #2 \right\rbrace }
    \DeclareMathOperator{\sgn}{sgn}
    \newcommand{\abs}[1]{\left| {#1} \right|}
  $
</div>

In these post, we will demonstrate the usefulness of the residue theorem when it comes to evaluating quite complicated integrals. Consider the following integral:

$$
I = \int_{0}^{\infty}\frac{\cos{(kx)}}{x^4+b} \dd{x}
$$

where $b>0$ and $k \in \mathbb{R} \setminus \left\lbrace 0 \right\rbrace $.


Firstly, we rewrite the integral as follows: 

$$
\begin{align*}
I &= \int_{0}^{\infty}\frac{\cos{(kx)}}{x^4+b} \dd{x} \\
&= \frac{1}{2}  \int_{0}^{\infty}\frac{e^{ikx}+e^{-ikx}}{x^4+b} \dd{x} \\
&= \frac{1}{2}  \int_{0}^{\infty}\frac{e^{ikx}}{x^4+b} \dd{x} + \frac{1}{2}  \int_{0}^{\infty}\frac{e^{-ikx}}{x^4+b} \dd{x} \\
&= \frac{1}{2}  \int_{0}^{\infty}\frac{e^{ikx}}{x^4+b} \dd{x} + \frac{1}{2}  \int_{0}^{\infty}\frac{e^{ik(-x)}}{(-x)^4+b} \dd{x} \\
&= \frac{1}{2}  \int_{0}^{\infty}\frac{e^{ikx}}{x^4+b} \dd{x} + \frac{1}{2}  \int_{0}^{-\infty}\frac{e^{ikx}}{x^4+b} (-\dd{x})
\end{align*}
$$

where we substituted $ (-x) \rightarrow x$ in the second integral. Thus, we have:

$$
\begin{align*}
I &= \frac{1}{2}  \int_{0}^{\infty}\frac{e^{ikx}}{x^4+b} \dd{x} + \frac{1}{2}  \int_{-\infty}^{0}\frac{e^{ikx}}{x^4+b} \dd{x} \\
&= \frac{1}{2}  \int_{-\infty}^{\infty}\frac{e^{ikx}}{x^4+b} \dd{x}
\end{align*}
$$

We now make the substitution $x \rightarrow \sgn(k)x$, where $\sgn(k)$ is defined as:

$$
\sgn(k) =  \begin{cases} -1 & k<0 \\ 1 & k>0 \end{cases} 
$$

Thus, we have:

$$
\begin{align*}
I &= \frac{1}{2}  \int_{-\sgn(k)\infty}^{\sgn(k)\infty}\frac{e^{ik\sgn(k)x}}{(\sgn(k)x)^4+b} (\sgn(k)\dd{x}) \\
&= \frac{1}{2}  \int_{-\infty}^{\infty}\frac{e^{i|k|x}}{x^4+b} \dd{x}
\end{align*}
$$

since we have that 

$$
k\sgn(k)=|k|
$$

Also, the $\sgn(k)$ factor takes into account the cases where $k>0$ and $k<0$ (i.e. the resultant negative sign flips back the terminals so they always go from $-\infty$ to $\infty$ for both cases of $k$).

Now we have the integral in the form where we start to apply the residue theorem. Firstly, we identify that the limits from $-\infty$ to $\infty$ really means:

$$
\begin{align}
I = \lim_{R \to \infty} \int_{-R}^{R} \frac{1}{2} \frac{e^{i|k|x}}{x^4+b} \dd{x}
\end{align}
$$

Now, consider the following contour:
<p align="center">
  <img src="https://github.com/aphelly/aphelly.github.io/blob/master/images/res1.PNG?raw=true" />
</p>

The semicircular contour is parameterized as:

$$
S_{R}: \quad \zeta(t) = Re^{it},\quad t \in [0, \pi]
$$

The straight line contour is parameterized as:

$$
L_{R}: \quad \zeta(t) = t, \quad t \in [-R,R]
$$

We also define the whole contour as $C_{R} = S_{R} \cup L_{R}$. Next, we find the poles of the integrand in (1). This occurs when the denominator is 0. Thus,

$$
\begin{align*}
	z^4+b&=0\\
	z^4&=-b\\
	\Rightarrow z&= b^{\frac{1}{4}}e^{i\frac{\pi}{4}}, b^{\frac{1}{4}}e^{i\frac{3\pi}{4}}, b^{\frac{1}{4}}e^{-i\frac{\pi}{4}}, b^{\frac{1}{4}}e^{-i\frac{3\pi}{4}}
\end{align*}
$$

The two relevant poles for our contour closed in the upper half plane are $b^{\frac{1}{4}}e^{i\frac{\pi}{4}}$ and $b^{\frac{1}{4}}e^{i\frac{3\pi}{4}}$. Both poles are enclosed by the contour $C_R$ as long as $R>b^{\frac{1}{4}}$. Now, we wish to have that:

$$
\begin{align}
I = \lim_{R \to \infty} \int_{-R}^{R} \frac{1}{2} \frac{e^{i|k|x}}{x^4+b} \dd{x} = \lim_{R \to \infty} \oint\limits_{C_{R}} \frac{1}{2} \frac{e^{i|k|z}}{z^4+b} \dd{z}
\end{align}
$$

In order for this equality to hold, we must show that

$$
\begin{align}
\lim_{R \to \infty} \left| \int\limits_{S_{R}} \frac{1}{2} \frac{e^{i|k|z}}{z^4+b} \dd{z}\right| =0
\end{align}
$$

i.e., in the limit as $R \to \infty$, the contribution to the contour integral from the semicircular arc vanishes, thus leaving behind just the integral along the straight line contour $L_R$ (which, in the limit $R \to \infty$, is our integral in (1)).


To show (3), we can apply the ML-bound. The ML inequality states that for a complex-valued function $f(z)$ which is continuous on a contour $\Gamma$, if $|f(z)|$ is bounded by a constant $M$ for all $z$ on $\Gamma$, then:

$$
\left| \int\limits_{\Gamma} f(z) \dd{z} \right|  \leq ML
$$

where $L$ is the length of the contour $\Gamma$.\\
In our case, the length of the semicircular contour is $L=\pi R$, and the integrand is bounded by:

$$
\begin{align*}
	\left| \frac{1}{2} \frac{e^{i|k|z}}{z^4+b} \right| &= \frac{1}{2} \frac{|e^{i|k|z}|}{|z^4+b|} \\
	&= \frac{1}{2} \frac{|e^{i|k|(\Re(z)+i\Im(z))}|}{|z^4+b|} \\
	&= \frac{1}{2} \frac{|e^{i|k|\Re(z)}e^{-|k|\Im(z)}|}{|z^4+b|} \\
	&= \frac{1}{2} \frac{e^{-|k|\Im(z)}}{|z^4+b|} \\
\end{align*}
$$

since $\abs{e^{i\abs{k}\Re(z)}}=1$. Since the contour is in the upper half plane, this means $\Im(z) \geq 0$. Hence, the numerator is bounded by 1 (i.e. $e^{-\abs{k}\Im(z)}\leq 1$). Furthermore, we can apply the reverse triangle inequality to the denominator:

$$
	|z^4+b| \geq |z|^4 - |b| = R^4 -b
$$

since $\abs{z}=R$ on $S_{R}$. Thus, we now have that:

$$
\begin{align*}
	\abs{\frac{1}{2} \frac{e^{i\abs{k}z}}{z^4+b}}  &= \frac{1}{2} \frac{e^{-\abs{k}\Im(z)}}{\abs{z^4+b}} \\
	&\leq \frac{1}{2} \frac{1}{R^4-b} = M
\end{align*}
$$

Therefore, by the ML inequality, we have that:

$$
 \abs{\int\limits_{S_{R}} \frac{1}{2} \frac{e^{i|k|z}}{z^4+b} \dd{z}} \leq \frac{1}{2} \frac{\pi R}{R^4-b} \xrightarrow{R\to\infty} 0
$$

Thus, (3) is indeed true and so we can use the equality (2) to evaluate $I$:

$$
I =  \lim_{R \to \infty} \oint\limits_{C_{R}} \frac{1}{2} \frac{e^{i|k|z}}{z^4+b} \dd{z}
$$

To evaluate this integral, we use the residue theorem. The residue theorem states that for a simple, closed contour $C$ with an interior domain $\Omega$, if a complex-valued function $f(z)$ is holomorphic in $\Omega$ except at finitely many isolated singularities $z_k$  $(1 \leq k \leq n)$ and that $f(z)$ is continuous on the closed set $\Omega \cup C$ except at these enclosed isolated singularities, then:

$$
\oint\limits_{C} f(z) \dd{z} = 2\pi i \sum_{k=1}^{n} \res{z=z_{k}}{f(z)}
$$

In our case, the two singularities enclosed by $C_{R}$ are at $z=b^{\frac{1}{4}}e^{i\frac{\pi}{4}}$ and $z=b^{\frac{1}{4}}e^{i\frac{3\pi}{4}}$. Hence, we have that:

$$
\begin{align}
 \oint\limits_{C_{R}} \frac{1}{2} \frac{e^{i|k|z}}{z^4+b} \dd{z}= 2\pi i\left[ \res{z=b^{\frac{1}{4}}e^{i\frac{\pi}{4}}}{\frac{1}{2} \frac{e^{i|k|z}}{z^4+b}} +\res{z=b^{\frac{1}{4}}e^{i\frac{3\pi}{4}}}{\frac{1}{2} \frac{e^{i|k|z}}{z^4+b}} \right] 
\end{align}
$$

These two singularities are simple poles since they are both zeroes of order $1$ of the denominator $z^4+b$. \\
In general, the residue of $f(z)$ at an isolated simple pole at $z=c$ is given by:

$$
\res{z=c}{f(z)} = \lim_{z\to c}[(z-c)f(z)]
$$

Hence, we have:

$$
\begin{align*}
	\res{z=b^{\frac{1}{4}}e^{i\frac{\pi}{4}}}{\frac{1}{2} \frac{e^{i|k|z}}{z^4+b}}&= \lim_{z\to b^{\frac{1}{4}}e^{i\frac{\pi}{4}}}\left[(z-b^{\frac{1}{4}}e^{i\frac{\pi}{4}})\frac{1}{2} \frac{e^{i|k|z}}{z^4+b}\right]\\
	&= \frac{1}{2} \lim_{z\to b^{\frac{1}{4}}e^{i\frac{\pi}{4}}}\left[\frac{e^{i|k|z}}{(z-b^{\frac{1}{4}}e^{i\frac{3\pi}{4}})(z-b^{\frac{1}{4}}e^{-i\frac{\pi}{4}})(z-b^{\frac{1}{4}}e^{-i\frac{3\pi}{4}})}\right] \\
	&= \frac{1}{2} \left[\frac{e^{i|k|b^{\frac{1}{4}}e^{i\frac{\pi}{4}}}}{(b^{\frac{1}{4}}e^{i\frac{\pi}{4}}-b^{\frac{1}{4}}e^{i\frac{3\pi}{4}})(b^{\frac{1}{4}}e^{i\frac{\pi}{4}}-b^{\frac{1}{4}}e^{-i\frac{\pi}{4}})(b^{\frac{1}{4}}e^{i\frac{\pi}{4}}-b^{\frac{1}{4}}e^{-i\frac{3\pi}{4}})}\right] \\
	&= \frac{1}{2b^{\frac{3}{4}}} \left[\frac{e^{i|k|b^{\frac{1}{4}}e^{i\frac{\pi}{4}}}}{(e^{i\frac{\pi}{4}}-e^{i\frac{3\pi}{4}})(e^{i\frac{\pi}{4}}-e^{-i\frac{\pi}{4}})(e^{i\frac{\pi}{4}}-e^{-i\frac{3\pi}{4}})} \right] \\
	&= \frac{1}{2b^{\frac{3}{4}}e^{i\frac{3\pi}{4}}} \left[\frac{e^{i|k|b^{\frac{1}{4}}e^{i\frac{\pi}{4}}}}{(1-e^{i\frac{\pi}{2}})(1-e^{-i\frac{\pi}{2}})(1-e^{-i\pi})} \right] \\
	&= \frac{1}{2b^{\frac{3}{4}}e^{i\frac{3\pi}{4}}} \left[\frac{e^{i|k|b^{\frac{1}{4}}e^{i\frac{\pi}{4}}}}{(1-i)(1+i)(1-(-1))} \right] \\
	&= \frac{1}{2b^{\frac{3}{4}}e^{i\frac{3\pi}{4}}} \left[\frac{e^{i|k|b^{\frac{1}{4}}e^{i\frac{\pi}{4}}}}{2 \times 2} \right] \\
	&= \frac{1}{8b^{\frac{3}{4}}e^{i\frac{3\pi}{4}}} e^{i|k|b^{\frac{1}{4}}e^{i\frac{\pi}{4}}}
\end{align*}
$$


Similarly for the other pole, we have:

$$
\begin{align*}
	\res{z=b^{\frac{1}{4}}e^{i\frac{3\pi}{4}}}{\frac{1}{2} \frac{e^{i|k|z}}{z^4+b}}&= \lim_{z\to b^{\frac{1}{4}}e^{i\frac{3\pi}{4}}}\left[(z-b^{\frac{1}{4}}e^{i\frac{3\pi}{4}})\frac{1}{2} \frac{e^{i|k|z}}{z^4+b}\right]\\
	&= \frac{1}{2} \lim_{z\to b^{\frac{1}{4}}e^{i\frac{3\pi}{4}}}\left[\frac{e^{i|k|z}}{(z-b^{\frac{1}{4}}e^{i\frac{\pi}{4}})(z-b^{\frac{1}{4}}e^{-i\frac{\pi}{4}})(z-b^{\frac{1}{4}}e^{-i\frac{3\pi}{4}})}\right] \\
	&= \frac{1}{2} \left[\frac{e^{i|k|b^{\frac{1}{4}}e^{i\frac{3\pi}{4}}}}{(b^{\frac{1}{4}}e^{i\frac{3\pi}{4}}-b^{\frac{1}{4}}e^{i\frac{\pi}{4}})(b^{\frac{1}{4}}e^{i\frac{3\pi}{4}}-b^{\frac{1}{4}}e^{-i\frac{\pi}{4}})(b^{\frac{1}{4}}e^{i\frac{3\pi}{4}}-b^{\frac{1}{4}}e^{-i\frac{3\pi}{4}})}\right] \\
	&= \frac{1}{2b^{\frac{3}{4}}} \left[\frac{e^{i|k|b^{\frac{1}{4}}e^{i\frac{3\pi}{4}}}}{(e^{i\frac{3\pi}{4}}-e^{i\frac{\pi}{4}})(e^{i\frac{3\pi}{4}}-e^{-i\frac{\pi}{4}})(e^{i\frac{3\pi}{4}}-e^{-i\frac{3\pi}{4}})} \right] \\
	&= \frac{1}{2b^{\frac{3}{4}}e^{i\frac{9\pi}{4}}} \left[\frac{e^{i|k|b^{\frac{1}{4}}e^{i\frac{3\pi}{4}}}}{(1-e^{-i\frac{\pi}{2}})(1-e^{-i\pi})(1-e^{-i\frac{3\pi}{2}})} \right] \\
	&= \frac{1}{2b^{\frac{3}{4}}e^{i\frac{9\pi}{4}}} \left[\frac{e^{i|k|b^{\frac{1}{4}}e^{i\frac{3\pi}{4}}}}{(1+i)(1-(-1))(1-i)} \right] \\
	&= \frac{1}{2b^{\frac{3}{4}}e^{i\frac{9\pi}{4}}} \left[\frac{e^{i|k|b^{\frac{1}{4}}e^{i\frac{3\pi}{4}}}}{2 \times 2} \right] \\
	&= \frac{1}{8b^{\frac{3}{4}}e^{i\frac{9\pi}{4}}} e^{i|k|b^{\frac{1}{4}}e^{i\frac{3\pi}{4}}}
\end{align*}
$$

Thus, from (4) we have that:

$$
\begin{align*}
	\oint\limits_{C_{R}} \frac{1}{2} \frac{e^{i|k|z}}{z^4+b} \dd{z}
	&= 2\pi i\left[ \frac{1}{8b^{\frac{3}{4}}e^{i\frac{3\pi}{4}}} e^{i|k|b^{\frac{1}{4}}e^{i\frac{\pi}{4}}} +\frac{1}{8b^{\frac{3}{4}}e^{i\frac{9\pi}{4}}} e^{i|k|b^{\frac{1}{4}}e^{i\frac{3\pi}{4}}} \right] \\
	&= \frac{\pi i}{4b^{\frac{3}{4}}} \left[ \frac{1}{e^{i\frac{3\pi}{4}}} e^{i|k|b^{\frac{1}{4}}e^{i\frac{\pi}{4}}} +\frac{1}{e^{i\frac{9\pi}{4}}} e^{i|k|b^{\frac{1}{4}}e^{i\frac{3\pi}{4}}} \right] \\
	&= \frac{\pi i}{4b^{\frac{3}{4}}} \left[ \frac{1}{-\frac{1}{\sqrt{2}}+\frac{1}{\sqrt{2}}i} e^{i|k|b^{\frac{1}{4}}\left(\frac{1}{\sqrt{2}}+\frac{1}{\sqrt{2}}i\right)} +\frac{1}{\frac{1}{\sqrt{2}}+\frac{1}{\sqrt{2}}i} e^{i|k|b^{\frac{1}{4}}\left(-\frac{1}{\sqrt{2}}+\frac{1}{\sqrt{2}}i \right) } \right] \\
	&= \frac{\pi i}{4b^{\frac{3}{4}}\left( \frac{1}{\sqrt{2}}\right) } \left[ \frac{1}{-1+i} e^{\frac{i|k|b^{\frac{1}{4}}}{\sqrt{2}}}e^{-\frac{|k|b^{\frac{1}{4}}}{\sqrt{2}}} +\frac{1}{1+i} e^{-\frac{i|k|b^{\frac{1}{4}}}{\sqrt{2}}}e^{-\frac{|k|b^{\frac{1}{4}}}{\sqrt{2}}} \right] \\
	&= \frac{\pi i}{2\sqrt{2}b^{\frac{3}{4}}} e^{-\frac{|k|b^{\frac{1}{4}}}{\sqrt{2}}} \left[\frac{(1+i)e^{\frac{i|k|b^{\frac{1}{4}}}{\sqrt{2}}}+(-1+i)e^{-\frac{i|k|b^{\frac{1}{4}}}{\sqrt{2}}}}{(-1+i)(1+i)} \right] \\
	&= -\frac{\pi i}{2\sqrt{2}b^{\frac{3}{4}}} e^{-\frac{|k|b^{\frac{1}{4}}}{\sqrt{2}}} \left[ \frac{(1+i)e^{\frac{i|k|b^{\frac{1}{4}}}{\sqrt{2}}}+(-1+i)e^{-\frac{i|k|b^{\frac{1}{4}}}{\sqrt{2}}}}{2} \right] \\
	&= -\frac{\pi i}{2\sqrt{2}b^{\frac{3}{4}}} e^{-\frac{|k|b^{\frac{1}{4}}}{\sqrt{2}}} \left[ \frac{e^{\frac{i|k|b^{\frac{1}{4}}}{\sqrt{2}}}- e^{-\frac{i|k|b^{\frac{1}{4}}}{\sqrt{2}}}+ ie^{\frac{i|k|b^{\frac{1}{4}}}{\sqrt{2}}} + ie^{\frac{-i|k|b^{\frac{1}{4}}}{\sqrt{2}}}}{2} \right] \\
	&= -\frac{\pi i}{2\sqrt{2}b^{\frac{3}{4}}} e^{-\frac{|k|b^{\frac{1}{4}}}{\sqrt{2}}} \left[ \frac{e^{\frac{i|k|b^{\frac{1}{4}}}{\sqrt{2}}}- e^{-\frac{i|k|b^{\frac{1}{4}}}{\sqrt{2}}}}{2}+i\frac{ e^{\frac{i|k|b^{\frac{1}{4}}}{\sqrt{2}}} + e^{\frac{-i|k|b^{\frac{1}{4}}}{\sqrt{2}}}}{2} \right] \\
	&= -\frac{\pi i}{2\sqrt{2}b^{\frac{3}{4}}} e^{-\frac{|k|b^{\frac{1}{4}}}{\sqrt{2}}} \left[ i\sin(\frac{|k|b^{\frac{1}{4}}}{\sqrt{2}})+i\cos(\frac{|k|b^{\frac{1}{4}}}{\sqrt{2}}) \right] \\
	&=\frac{\pi}{2\sqrt{2}b^{\frac{3}{4}}} e^{-\frac{|k|b^{\frac{1}{4}}}{\sqrt{2}}} \left[ \sin(\frac{|k|b^{\frac{1}{4}}}{\sqrt{2}})+\cos(\frac{|k|b^{\frac{1}{4}}}{\sqrt{2}}) \right] \\
\end{align*}
$$

Therefore, we finally have the result:

$$
\begin{align*}
	I &= \int_{0}^{\infty}\frac{\cos{(kx)}}{x^4+b} \dd{x} \\
	&= \lim_{R \to \infty} \oint\limits_{C_{R}} \frac{1}{2} \frac{e^{i|k|z}}{z^4+b} \dd{z} \\
	&= \lim_{R \to \infty} \left[\frac{\pi}{2\sqrt{2}b^{\frac{3}{4}}} e^{-\frac{|k|b^{\frac{1}{4}}}{\sqrt{2}}}  \left( \sin(\frac{|k|b^{\frac{1}{4}}}{\sqrt{2}})+\cos(\frac{|k|b^{\frac{1}{4}}}{\sqrt{2}}) \right) \right] \\
	&= \frac{\pi}{2\sqrt{2}b^{\frac{3}{4}}} e^{-\frac{|k|b^{\frac{1}{4}}}{\sqrt{2}}} \left[ \sin(\frac{|k|b^{\frac{1}{4}}}{\sqrt{2}})+\cos(\frac{|k|b^{\frac{1}{4}}}{\sqrt{2}}) \right] \qed
\end{align*}
$$
