---
title: Ramanujan Master Theorem
published: 2025-10-23
description: 'A really well article about Ramanujan Master Theorem and DHL integral'
image: './bg.jpg'
tags: [Mathematic,Complex]
category: 'Mathematic'
draft: false 
lang: ''
---
:::note[Prerequisites]  
This article requires knowledge of **complex numbers** and **some transforms**.  
- If you don't know **complex numbers**, you can refer to [this article](https://peakyi.github.io/posts/note/).
- If you don't know **transforms**, you can refer to [this article](https://peakyi.github.io/posts/transform/transform/).  

:::  
## Shift Operator
We define: $D\equiv \frac{\mathrm d}{\mathrm dx}$. Consider
$$
e^D=\sum_{n=0}^\infty\frac{D^n}{n!}
$$
Acting on a function $f(x)$, we have:
$$
e^Df=\sum_{n=0}^\infty\frac{D^n}{n!}f(x)=\sum_{n=0}^\infty\frac{f^{(n)}(x)}{n!}1^n
$$
Noting that this is the Taylor expansion of the function $f(x)$ at $x$, we clearly have:
$$
\boxed{e^Df=f(x+1)}
$$
Similarly:
$$
e^{tD}f=\sum_{n=0}^\infty\frac{f^{(n)}(x)}{n!}t^n=f(x+t)
$$

Consider computing:
$$
\begin{aligned}
e^{aD}\cdot e^{bD}&=\sum_{n=0}^\infty\frac{a^nD^n}{n!}\cdot\sum_{n=0}^\infty\frac{b^nD^n}{n!}\\
&=\sum_{n=0}^\infty D^n\sum_{k=0}^n\frac{a^k b^{n-k}}{k!(n-k)!}\\
&=\sum_{n=0}^\infty\frac{D^n}{n!}\underbrace{\sum_{k=0}^n\binom{n}{k}a^kb^{n-k}}_{(a+b)^n}\\
&=\sum_{n=0}^\infty\frac{D^n}{n!}(a+b)^n\\
&=e^{(a+b)D}
\end{aligned}
$$

Thus the shift operator satisfies exponential operations.  
### Difference and Shift
Define the difference operator $\Delta$ as:
$$
\Delta f(x)=f(x+1)-f(x)=e^Df(x)-f(x)=(e^D-1)f(x)
$$
Thus:
$$
\Delta=e^D-1
$$
Taking the inverse on both sides, we have:
$$
\Delta^{-1}=\frac1{e^D-1}=\frac1D\frac D{e^D-1}
$$
The latter part is exactly the generating function of Bernoulli numbers, so expanding gives:
$$
\Delta^{-1}=\frac1D\sum_{n=0}^\infty\frac{B_n}{n!}D^n
$$
Note that:
$$
\sum=\Delta^{-1},\int=D^{-1}
$$
Substituting into the above equation, we get:
$$
\begin{aligned}
\sum&=\int\sum_{n=0}^\infty\frac{B_n}{n!}D^n\\
&=\int+\sum_{n=1}^\infty\frac{B_n}{n!}\int D^n\\
&=\int+\sum_{n=1}^\infty\frac{B_n}{n!}D^{n-1}\\
\end{aligned}
$$
Noting that the odd-indexed Bernoulli numbers (except the first term) are all $0$, we have:
$$
\sum=\int-\frac12+\sum_{n=1}^\infty\frac{B_{2n}}{(2n)!}D^{2n-1}
$$
Applying this formula from $a$ to $b$ to the function $f(x)$, we obtain:
$$
\sum_{a\le n\le b}f(n)=\int_a^bf(x)\mathrm dx-\frac{f(b)-f(a)}2+\sum_{n=1}^\infty\frac{B_{2n}}{(2n)!}\left[f^{(2n-1)}(b)-f^{(2n-1)}(a)\right]
$$
Thus simply deriving the **Euler-Maclaurin summation formula**.
## Ramanujan Master Theorem
Consider the Laplace transform:
$$
\mathcal L\{x^{s-1}\}(e^D)=\int_0^\infty x^{s-1}e^{-xe^D}\,\mathrm dx=\Gamma(s)e^{-sD}
$$
We substitute
$$
e^{-xe^D}=\sum_{n=0}^\infty\frac{e^{nD}}{n!}(-x)^n
$$
and let it act on the function $\phi(0)$, yielding:
$$
\int_0^\infty x^{s-1}\sum_{n=0}^\infty\frac{e^{nD}}{n!}(-x)^n\phi(0)\,\mathrm dx=\Gamma(s)\underbrace{e^{-sD}\cdot\phi(0)}_{\phi(-s)}
$$
Let
$$
\begin{aligned}
f(x)&=\sum_{n=0}^\infty\frac{e^{nD}\phi(0)}{n!}(-x)^n\\
&=\sum_{n=0}^\infty\frac{\phi(n)}{n!}(-x)^n
\end{aligned}
$$
Then:
$$
\int_0^\infty x^{s-1}f(x)\,\mathrm dx=\Gamma(s)\phi(-s)
$$
This is the **Ramanujan Master Theorem** ($\textcolor{FF8C00}{\text{Ramanujan CF2100}}$ Theorem). We formally state its proposition:  

:::note[Ramanujan Master Theorem]  
For a function $f(x)$, its Mellin Transform satisfies:
$$
\mathcal M\{f(x)\}(s)=\int_0^\infty x^{s-1}f(x)\,\mathrm dx=\Gamma(s)\phi(-s)
$$
if and only if the function $f(x)$ satisfies:
$$
f(x)=\sum_{n=0}^\infty\frac{\phi(n)}{n!}(-x)^n
$$
:::  
This theorem describes the general property of the Mellin transform for entire functions.

## Applications
### DHL Integral
First, I will prove the DHL integral mentioned in my blog introduction.  
Consider the integral:
$$
I=\int_0^\infty\sin x^n\,\mathrm dx
$$
Let $t=x^n,s=\frac1n$, then:
$$
\begin{aligned}
I&=s\int_0^\infty t^{s-1}\sin t\,\mathrm dt\\
&=s\mathfrak I\int_0^\infty t^{s-1}e^{it}\,\mathrm dt
\end{aligned}
$$
Consider Taylor expanding $e^{it}$ (I proved in [a previous article](https://peakyi.github.io/posts/note/#expansion-of-complex-functions) that this is feasible):
$$
\begin{aligned}
e^{it}&=\sum_{n=0}^\infty\frac{(it)^n}{n!}\\
&=\sum_{n=0}^\infty\frac{(-t)^n}{n!}\underbrace{e^{-i\frac{n\pi}2}}_{\phi(n)}
\end{aligned}
$$
Applying the Ramanujan Master Theorem, we get:
$$
I=\mathfrak I[\,s\Gamma(s)e^{i\frac{s\pi}2}]=\frac1n\Gamma\left(\frac1n\right)\sin\left(\frac\pi{2n}\right)
$$
Similarly:
$$
\int_0^\infty\cos x^n\,\mathrm dx=\frac1n\Gamma\left(\frac1n\right)\cos\left(\frac\pi{2n}\right)
$$
### An Anomalous Integral
Consider the integral:
$$
I=\int_0^\infty\frac{\mathrm dx}{1+x^n}
$$
Let $t=x^n,s=\frac1n$, then we have:
$$
\int_0^\infty\frac{\mathrm dx}{1+x^n}=s\int_0^\infty\frac{t^{s-1}}{1+t}\,\mathrm dt
$$
Note that:
$$
\frac1{1+t}=\sum_{n=0}^\infty(-t)^n=\sum_{n=0}^\infty\frac{(-t)^n}{n!}\underbrace{\Gamma(1+n)}_{\phi(n)}
$$
Applying the Ramanujan Master Theorem, we get:
$$
I=s\Gamma(s)\Gamma(1-s)=\frac{\pi}{n\sin\frac\pi n}
$$
### Logarithm-related improper integral
First, recall the series expansion form of the $\psi$ function:
$$
\psi(n)=-\gamma+\sum_{k=0}^\infty\left(\frac1{k+1}-\frac1{k+n}\right)
$$
Rearranging gives:
$$
H_n=\psi(1+n)+\gamma
$$
Consider the integral:
$$
I=\int_0^\infty\frac{x^{s-1}\ln(1+x)}{1+x}\,\mathrm dx,\mathfrak{R}(s)\in(0,1)
$$
Note that:
$$
\ln(1+x)=-\sum_{n=0}^\infty\frac{(-x)^{n+1}}{n+1},\frac1{1+x}=\sum_{n=0}^\infty(-x)^n
$$
Then:
$$
\begin{aligned}
\frac{\ln(1+x)}{1+x}&=-\sum_{n=0}^\infty\frac{x^{n+1}}{n+1}\cdot\sum_{n=0}^\infty(-x)^n\\
&=-\sum_{n=0}^\infty(-x)^n\sum_{k=1}^n\frac{1}k\\
&=-\sum_{n=0}^\infty H_n(-x)^n\\
&=-\sum_{n=0}^\infty \left[\psi(1+n)+\gamma\right](-x)^n
\end{aligned}
$$
Using the same technique as the previous problem, we obtain:
$$
I=-\frac\pi{\sin \pi s}\left[\psi(1-s)+\gamma\right]
$$
### Zeta Function 
Finally, we give the connection between the Riemann Zeta function and Bernoulli numbers.  
First:
$$
\zeta(s)\Gamma(s)=\int_0^\infty\frac{x^{s-1}}{e^x-1}\,\mathrm dx
$$
Note that the right side is a Mellin Transform. According to the Ramanujan Master Theorem:
$$
\frac1{e^x-1}=\sum_{n=0}^\infty\frac{\zeta(-n)}{n!}(-x)^n
$$
Note that this is very similar to the generating function of Bernoulli numbers, so:
$$
\sum_{n=0}^\infty\textcolor{red}{B_n}\frac{x^n}{n!}=\sum_{n=0}^\infty (-1)^n\frac{\zeta(-n)}{n!}x^{n+1}
$$
Consider unifying the powers. Note that $\displaystyle\lim_{n\to\infty}\frac{n}{n!}=0$, so:
$$
\sum_{n=0}^\infty (-1)^n\frac{\zeta(-n)}{n!}x^{n+1}=\sum_{n=0}^\infty\textcolor{red}{(-1)^{n+1}n\zeta(1-n)}\frac{x^n}{n!}
$$
Comparing coefficients, we get:
$$
\zeta(1-n)=(-1)^{n+1}\frac{B_n}{n}
$$
Noting that the odd-indexed Bernoulli numbers (except the first term) are all $0$, the formula can be rewritten as:
$$
\boxed{\zeta(1-2n)=-\frac{B_{2n}}{2n},n\in\mathbb Z}
$$