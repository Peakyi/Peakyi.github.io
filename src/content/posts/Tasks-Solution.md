---
title: A Collection of Integral Problem Solutions
published: 2025-10-17
description: 'Dive into these step-by-step solutions that break down complex problems into manageable steps. Learn essential techniques and tricks to master integration and boost your calculus skills!'
image: ''
tags: [Mathematic,Complex,Solutions]
category: 'Mathematic'
draft: false 
lang: ''
---
**This is a collection of solutions to calculus training problems for the team Andy AK IOI.**  
Portal: [Andy AK Calculus Training Problems](https://www.luogu.com.cn/training/855627).

### [T669506 Training Problem (Math 1)](https://www.luogu.com.cn/problem/T669506)
$$
\begin{aligned}
\mathrm{I}&=\int_0^\frac\pi2\ln\sin x\,dx\\
&=\frac12\int_0^\frac\pi2\ln\sin x+\ln\cos x\,dx\\
&=\frac12\int_0^\frac\pi2\ln\sin 2t\,dx
\end{aligned}
$$
Then use substitution method to quickly solve this problem.

### [T669552 Training Problem (Math 2)](https://www.luogu.com.cn/problem/T669552)
$$
\mathrm{I}=\int_0^\infty \frac{\sin x}x\,dx
$$
This is a classic improper integral. We consider using the generalized integral method:
$$
\begin{aligned}
\mathrm{I}(t)&=\int_0^\infty e^{-tx}\frac{\sin x}x\,dx\\
\mathrm{I}'(t)&=\int_0^\infty\frac\partial{\partial  t}e^{-tx}\frac{\sin x}x\,dx\\
&=-\int_0^\infty e^{-tx}\sin x\,dx\\
\end{aligned}
$$
This is an elementary integral. After solving it using elementary integration methods, integrate back. Now let's discuss the validity of applying Leibniz's rule to this integral.  
Note the following inequality:
$$
0\le |\mathrm{I}(t)| \le \int_0^\infty e^{-tx}\left|\frac{\sin x}x\right|\,dx\le\int_0^\infty e^{-tx}\,dx=\frac1t
$$
Thus,
$$
\lim_{t\to\infty}\mathrm{I}(t)=0
$$
Therefore, the order of integration can be exchanged, and the original method is valid.

### [T669555 Training Problem (Math 3)](https://www.luogu.com.cn/problem/T669555)
Given:
$$
\Gamma(s)=\int_0^\infty t^{s-1}e^{-t}\,dt
$$
Based on this integral, we can derive the following properties:
- $\Gamma(s)=(s-1)\Gamma(s-1)$
- $\Gamma(s)=\displaystyle\lim_{n\to\infty}\frac{n!n^s}{s(s+1)\cdots(s+n)}$
- $\Gamma(s)\Gamma(1-s)=\frac\pi{\sin s\pi}$

Now, you are asked to find the specific value of $\Gamma''(1)$, accurate to 12 decimal places.  

This is an important integral. To find $\Gamma''(1)$, we need to use logarithmic differentiation.
$$
\frac{\mathrm{d}}{\mathrm{d}s}\ln\Gamma(s)=\frac{\Gamma'(s)}{\Gamma(s)}=\sum_{n=0}^\infty\left(\frac{1}{n+1}-\frac{1}{s+n}\right)-\gamma
$$
Since the $\ln$ function has the nice property of converting products into sums, using logarithmic differentiation here is very convenient.  
Differentiating further:
$$
\frac{\mathrm{d}^2}{\mathrm{d}s^2}\ln\Gamma(s)=\frac{\Gamma''(s)\Gamma(s)-\Gamma'^2(s)}{\Gamma^2(s)}=\sum_{n=0}^\infty\frac{1}{(s+n)^2}
$$
Substitute $s=1$ to get the answer.  
You surely know how to solve the Basel problem, right? Right!

### [T670827 Training Problem (Math 4)](https://www.luogu.com.cn/problem/T670827)
Daily life is really beautiful, though small town daily life pales in comparison.
$$
\begin{aligned}
\mathrm{Nano}&=\int_0^1\left \{ \frac{1}{1-x} \right \}\,dx\\
&=\lim_{n\to\infty}\int_{\frac1n}^1\frac{1}{x}-\left\lfloor\frac1x\right\rfloor\,dx\\
&=\lim_{n\to\infty}\left(\ln1-\ln\frac1n-\int_{\frac1n}^1\sum_i\left\lfloor\frac1x\right\rfloor\ge i\right)\\
&=\lim_{n\to\infty}\left(\ln\frac1n-\mathrm{H}(n)+1\right)\\
&=1-\gamma
\end{aligned}
$$
The easiest problem.

### [T671620 Training Problem (Math 5)](https://www.luogu.com.cn/problem/T671620)
$$
\mathrm{Nano}=\prod_{n=1}^\infty\frac{\sqrt[n]e}{1+n^{-1}}
$$
As the simple version, we'll use a special method to solve this problem.
$$
\begin{aligned}
\mathrm{Nano}&=\prod_{n=1}^\infty e^\frac1n\frac{n}{n+1}\\
&=\lim_{n\to\infty}\frac{e^{\mathrm{H}(n)}}n\\
&=e^\gamma
\end{aligned}
$$

### [T671869 Training Problem (Math 5+) Enhanced Version](https://www.luogu.com.cn/problem/T671869)
As the enhanced version, this problem can still be solved using a special method, requiring the use of Wallis' formula, which won't be elaborated here.
Consider writing the $\Gamma$ function and $e^{\gamma x}$ in product form:
$$
\begin{aligned}
\Gamma(1+s)&=\prod_{n=1}^\infty\frac{\left(1+\frac 1n\right)^s}{1+\frac sn}\\
e^{\gamma s}&=\prod_{n=1}^\infty\frac{e^{\frac sn}}{\left(1+\frac 1n\right)^s}
\end{aligned}
$$
Multiplying the two expressions:
$$
e^{\gamma s}\Gamma(1+s)=\prod_{n=1}^\infty\frac{e^{\frac sn}}{1+\frac sn}
$$
For the first problem, substitute $s=1$; for the enhanced version, substitute $s=-\frac12$.

### [T678333 Anby loves gamma constant I](https://www.luogu.com.cn/problem/T678333)
This is a good problem. I found a generalization of this integral online and worked out this particular solution on scratch paper, but the process is too cumbersome and not an elegant one, so it won't be shown here.

**Lemmas**
- $e^{i\theta}=\cos\theta+i\sin\theta$
- $\displaystyle\int_0^\infty t^{z-1}e^{-pt}\,dt=p^{-z}\Gamma(z)$

If you don't know how to prove the first lemma, please refer to [Note on Complex Analysis](https://peakyi.github.io/posts/note/).

**Definition**
$$
I(s,\omega)=\int_0^\infty\frac{\ln x}x\sin(\omega x)e^{-sx}\,dx
$$
Differentiate with respect to the parameter (omitting the proof of validity):
$$
\begin{aligned}
\frac{\partial}{\partial s}I(s,\omega)&=-\int_0^\infty\ln x\sin(\omega x)e^{-sx}\,dx\\
&=-\mathrm{Im}\left[\int_0^\infty e^{(i\omega-s)x}\ln x\,dx\right]\\
&=-\mathrm{Im}\left[\frac\partial{\partial z}(s-i\omega)^{-z}\Gamma(z)|_{z=1}\right]_{}\\
&=\frac1{s^2+\omega^2}\mathrm{Im}\left[(\gamma+\ln(s-i\omega))(s+i\omega)\right]
\end{aligned}
$$
Since we have:
$$
\ln(s-i\omega)=\frac12\ln(s^2+\omega^2)-i\arctan\frac\omega s
$$
Thus, we get:
$$
\frac{\partial}{\partial s}I(s,\omega)=\frac1{s^2+\omega^2}\left(\gamma\omega-s\arctan\frac\omega s+\frac12\omega\ln\left(s^2+\omega^2\right)\right)
$$
Finally, integrate both sides with respect to $s$:
$$
I(s,\omega)=\int\frac{\gamma\omega}{s^2+\omega^2}\,ds-\int\frac{s\arctan\frac\omega s}{s^2+\omega^2}\,ds+\frac12\int\frac{\omega\ln\left(s^2+\omega^2\right)}{s^2+\omega^2}\,ds
$$
It's easy to see that the second and third integrals are messy, so consider eliminating them. Obviously, we can use integration by parts to eliminate them:
$$
\int\frac{s\arctan\frac\omega s}{s^2+\omega^2}\,ds=\frac12\ln(s^2+\omega^2)\arctan\left(\frac\omega s\right)+\text{third integral}
$$
Substituting:
$$
I(s,\omega)=\gamma\arctan\left(\frac s\omega\right)-\frac12\ln(s^2+\omega^2)\arctan\left(\frac\omega s\right)+C
$$
Almost forgot the constant, but it's important here.
$$
\begin{aligned}
&\because\lim_{\omega\to0}I(s,\omega)=0\\\\
&\therefore C=-\frac{\gamma\pi}2
\end{aligned}
$$
Thus, the original expression becomes:
$$
I(s,\omega)=-\arctan\left(\frac\omega s\right)\left(\gamma+\frac12\ln(s^2+\omega^2)\right)
$$
Letting $s\to 0$, $\omega=0$ gives:
$$
\color{red}{\boxed{\int_0^\infty\frac{\ln x}x\sin x\,dx=-\frac{\gamma\pi}2}}
$$

### [T679431 Anby loves gamma constant II](https://www.luogu.com.cn/problem/T679431)
This problem was my mistake. Originally, I intended to use the Taylor expansion of the $\psi$ function, so it was initially rated as a blue.  
However, this problem can be solved directly, so the difficulty was reduced to orange. Here, I'll show the Taylor expansion of the $\psi$ function.

**$\psi$ function**
I'll dedicate a separate topic to this; here I'll only cover some basic aspects.

$$
\begin{aligned}
&\psi^{(0)}(x)=\frac{\mathrm{d}}{\mathrm{d}x}\ln\Gamma(x)\\
&\psi^{(n)}(x)=\frac{\mathrm{d}^n}{\mathrm{d}x^n}\psi^{(0)}(x)
\end{aligned}
$$
Using the expansion of the $\Gamma$ function from earlier, we get:
$$
-\psi^{(0)}(x)=\frac1x+\gamma-\sum_{n=1}^\infty\frac1n-\frac1{n+x}
$$
Differentiating $n$ times:

$$
\psi^{(n)}(1)=
\begin{cases}
 -\gamma & \text{ if } n=0. \\
 n!(-1)^{n+1}\zeta(n+1) & \text{Otherwise.}
\end{cases}
$$

Good $\LaTeX$ skills will take you far.

Now, let's Taylor expand the $\psi$ function around $1$:
$$
\psi^{(0)}(x)+\gamma=\sum_{n=1}^\infty\frac{\psi^{(n)}(1)}{n!}(x-1)^n
$$
Substituting the above expression:
$$
\sum_{n=1}^\infty x^n\zeta(n+1)=-\psi^{(0)}(1-x)-\gamma
$$
Integrating both sides and determining the constant:
$$
\sum_{n=1}^\infty\frac{x^{n+1}}{n+1}\zeta(n+1)=-\ln\Gamma(1-x)-\gamma x
$$
Substitute $x=-1$ to get the desired result.
