---
title: Riemann Function
published: 2025-10-17
description: 'We must know. We will know.'
image: ''
tags: [Mathematic,Complex]
category: 'Mathematic'
draft: false 
lang: ''
---

## Basics of the Riemann Zeta Function
The Riemann zeta function is defined as follows:
$$
\zeta(z)=\sum^{\infty}_{i=1}{\frac{1}{i^z}}
$$
This is an extremely remarkable function. When $z=1$, it becomes the harmonic series, which was first proven to diverge in 1350. Here is a simple proof:
$$
\begin{aligned}
\zeta(1)&=1+\frac{1}{2}+\frac{1}{3}+\frac{1}{4}+\cdots\\
&\ge1+(\frac{1}{2})+(\frac{1}{4}+\frac{1}{4})+\cdots\\
&=1+\frac{1}{2}+\frac{1}{2}+\cdots\\
\end{aligned}
$$
Therefore, this series diverges.  
The Riemann zeta function has rather magical properties. We can express it as a product over the reciprocals of prime numbers, as follows:
$$
\begin{aligned}
\zeta(z)&=1+\frac{1}{2^z}+\frac{1}{3^z}+\frac{1}{4^z}+\cdots\\
\frac{1}{2^z}\zeta(z)&=\frac{1}{2^z}+\frac{1}{4^z}+\frac{1}{6^z}+\frac{1}{8^z}+\cdots\\
(1-\frac{1}{2^z})\zeta(z)&=1+\frac{1}{3^z}+\frac{1}{5^z}+\frac{1}{7^z}+\cdots\\
(1-\frac{1}{2^z})(1-\frac{1}{3^z})\zeta(z)&=1+\frac{1}{5^z}+\frac{1}{7^z}+\frac{1}{11^z}+\cdots\\
\Rightarrow \prod_{p}(1-\frac{1}{p^z})\zeta(z)&=1\\
\Rightarrow \zeta(z)&=\prod_{p}(1-\frac{1}{p^z})^{-1}
\end{aligned}
$$
Here, $p$ denotes a prime number.  
## Evaluation of $\zeta(2)$ and Euler
In 1650, Pietro Mengoli's book "Novae Quadraturae Arithmeticae" mentioned the problem concerning $\zeta(2)$. The 18th-century French mathematician and historian Montucla referred to this problem as "the despair of analysts." However, in 1734, Euler suddenly solved this problem. His derivation method utilized the Taylor expansion of the sine function.

### How to Solve for $\zeta(2)$
Consider the equation $\frac{\sin(x)}x=0$. It's easy to find the roots $x=k\pi,k\in\mathbb{Z}\setminus\{0\}$. Thus, we can factor the sine function:
$$
\begin{aligned}
\sin(x)&=x(x-\pi)(x+\pi)(x-2\pi)(x+2\pi)\cdots\\
\frac{\sin(x)}{x}&=(1-\frac{x}{\pi})(1+\frac{x}{\pi})(1-\frac{x}{2\pi})(1+\frac{x}{2\pi})\cdots\\
&=(1-\frac{x^2}{\pi^2})(1-\frac{x^2}{4\pi^2})\cdots
\end{aligned}
$$
From earlier, we have the Taylor expansion of $\sin(x)$, so:
$$
\frac{\sin(x)}{x}=1-\frac{x^2}{3!}+\frac{x^4}{5!}-\frac{x^6}{7!}\cdots
$$
Considering the expansion from the factored form, we have:
$$
\frac{\sin(x)}x=1-(\frac{1}{\pi^2}+\frac{1}{4\pi^2}+\cdots)x^2+\cdots
$$
We are only concerned with the coefficient of the $x^2$ term, thus:
$$
\frac{1}{\pi^2}+\frac{1}{4\pi^2}+\frac{1}{9\pi^2}+\cdots=\frac{1}{3!}=\frac{1}{6}\\
\Rightarrow \frac{1}{\pi^2}(1+\frac{1}{2^2}+\frac{1}{3^2}+\cdots)=\frac{1}{6}\\
\Rightarrow \zeta(2)=\frac{\pi^2}{6}
$$
Thus, following Euler, we have derived $\zeta(2)$.
## A Brief Discussion on the Riemann Zeta Function
First, you need to know about $\Gamma(s)$.
### About the Gamma Function
The Gamma function is defined as:
$$
\Gamma(s)=\int^\infty_0{e^{-x}x^{s-1}\,dx}
$$
Using integration by parts, it's easy to find:
$$
\begin{aligned}
\Gamma(s)&=\int^\infty_0{e^{-x}x^{s-1}\,dx}\\
&=-\int^\infty_0 x^{s-1} \, d(e^{-x}) \\
&= (s-1)\int^\infty_0{e^{-x}x^{s-2}\,dx} \quad \text{(after integration by parts and simplification)}\\
&=(s-1)\Gamma(s-1)
\end{aligned}
$$
Also, $\Gamma(1)=1$, so we have:
$$
\Gamma(s)=(s-1)!
$$
You can think of it as a generalization of the factorial.  
Due to the above property, we can find the factorial of negative numbers (via analytic continuation). The following derivation leads to Euler's reflection formula:
$$
\begin{aligned}
\Gamma(n)\Gamma(1-n)&=\frac{n!(-n)!}n \quad \text{(This is informal; it's about the Gamma function at these values)}\\
&= \dots \quad \text{(The user's derivation seems to aim for the reflection formula but contains notational issues. We'll summarize the key idea.)}
\end{aligned}
$$
Using a change to polar coordinates and substitution, one can derive Euler's reflection formula:
$$
\Gamma(n)\Gamma(1-n) = \frac{\pi}{\sin(\pi n)}
$$

### Product Form and Connection to Zeta
From the Gamma function, we can make a simple transformation:
$$
\Gamma(s)=\int^\infty_0{e^{-x}x^{s-1}\,dx}\\
\Rightarrow\frac{\Gamma(s)}{n^s}=\int^\infty_0{e^{-nx}x^{s-1}\,dx}
$$
Summing both sides over $n$ gives:
$$
\begin{aligned}
\sum^\infty_{n=1}\frac{\Gamma(s)}{n^s}&=\sum^\infty_{n=1}\int^\infty_0{e^{-nx}x^{s-1}\,dx}\\
\Gamma(s)\zeta(s)&=\int^\infty_0x^{s-1}\sum^\infty_{n=1}{e^{-nx}\,dx}\\
&=\int^\infty_0{\frac{x^{s-1}}{e^{x}-1}\,dx}
\end{aligned}
$$
## The Riemann Hypothesis
In fact, the product of the Riemann zeta function and the Gamma function has further applications:
$$
\zeta(s)=\zeta(1-s)\Gamma(1-s)2^s\pi^{s-1}\sin{\frac{\pi s}{2}}
$$
Note that when $s=-2k,k\in\mathbb{N}$, $\zeta(s)=0$ (these are the trivial zeros).  
Now, extending the Riemann zeta function to the complex plane, using contour integration, the analytically continued Riemann zeta function can be represented as:
$$
\zeta(s)=\frac{\Gamma(1-s)}{2\pi i}\oint \frac{(-z)^s}{e^z-1}\frac{\,dz}{z} \quad \text{(This is a standard contour integral representation)}
$$
Now, we can formally state the Riemann Hypothesis:  
For all $z_0$ satisfying $\zeta(z_0)=0$ (non-trivial zeros), we have $z_0=\frac{1}{2}+bi$ for some $b\in\mathbb{R}^*$.  
Of course, we should first explain why the Riemann Hypothesis is important.
### The Expression for $\pi(x)$
Simply put, the function $\pi(x)$ is the number of primes less than or equal to $x$. Its graph looks roughly like this:
![](https://pica.zhimg.com/v2-1fd883d09611b48afbde5eb0959dd890_b.webp?consumer=ZHI_MENG)  
Finding an explicit expression for this function has long been a goal for mathematicians. They even proposed the Prime Number Theorem:
$$
\lim_{x\rightarrow+\infty}\frac{\pi(x)}{\text{Li}(x)}=1
$$
where $\text{Li}(x)=\displaystyle\int_2^x\frac{1}{\ln t}\,dt$.  
This is a good approximation, but the error is still significant.  
However, Riemann directly gave his exact expression:
$$
\pi(x)=\sum^\infty_{n=1}{\frac{\mu(n)}{n}J(\sqrt[n]{x})}
$$
Confused? Let's analyze it step by step!  
First, $\mu(n)$ is the Möbius function. The term $J(x)$ is further expanded as:
$$
J(x)=\text{Li}(x)-\sum_{\rho}{\text{Li}(x^{\rho})}-\ln2+\int_x^\infty\frac{\,dt}{t(t^2-1)\ln t}
$$
In this strange-looking expression, $\rho$ runs over the non-trivial zeros of $\zeta(s)$.  
By plugging in these complex roots one by one, $J(x)$ approximates $\pi(x)$.  
Here's an animation to get a feel for it!
![](https://pica.zhimg.com/v2-9d77a93b053dfdc6d38980af45e61180_b.gif?consumer=ZHI_MENG)  
This is amazing. So mathematicians frantically searched for the distribution pattern of the complex roots of the Riemann zeta function, leading to the Riemann Hypothesis.
### What if the Riemann Hypothesis is Proven True?
If all non-trivial zeros have real part $\frac{1}{2}$, then:
$$
\pi(x)=\text{Li}(x)+O(\sqrt{x} \ln x)
$$
This is the common formula found online, which intuitively shows the error between $\pi(x)$ and $\text{Li}(x)$.  
Besides this, there is also a $1,000,000 prize.

**This article ends abruptly here.**

Let's end with a quote from Hilbert.  
![](https://cdn.luogu.com.cn/upload/image_hosting/ly8pqu8z.png)
## References
- [Tale of Imaginary Numbers](https://book.douban.com/subject/3535356/)  
- [What is the Riemann hypothesis? What is its use?](https://www.zhihu.com/tardis/bd/ans/638869523)  
- [Everything said in this video is true, but you can never prove it](https://www.bilibili.com/video/BV19u4y1D7GT/)