---
title: Some Useful Transform
published: 2025-10-22
description: 'Here are some useful transform (classic), these notes should be useful in solving integral problem.'
image: 'bg.png'
tags: [Mathematic,Complex]
category: 'Mathematic'
draft: false
lang: ''
---

This article serves primarily as a summary and groundwork.
When solving physics problems, we often need to solve complex differential equations (a pain in the ass). However, applying certain transforms to these equations can often turn them into linear equations, which is good. Therefore, it is important to specifically study some transforms.

## Some Notations
$$
f*g=\int_0^\infty f(t)g\left(\frac xt\right)\frac{\mathrm dt}{t} \\
\mathrm{} \\
f\circ g=\int_0^\infty f(xt)g(t)\,\mathrm dt \\
\mathrm{} \\
{x\to x_0\pm0}\Leftrightarrow x\to x_0^\pm \\
\mathrm{} \\
\int^\infty\Leftrightarrow\int^{+\infty} \\
\mathrm{} \\
\mathcal{Transform}\{f\}\Leftrightarrow\mathcal{Transform}\{f(t)\}(s)
$$

## Fourier Transform
The Fourier transform is, of course, a very common transform. Its main purpose is to convert a function into a frequency spectrum of sines and cosines. This spectrum is quite common; open a sound recorder app, make some random noises, and the moving bars you see are the frequency spectrum.

But why sines and cosines? The primary reason is that the Fourier transform was initially developed to analyze heat conduction, and temperature is easiest to calculate when it follows a sine or cosine pattern—the amplitude simply decays over time (I guess, I haven't studied thermodynamics). But heat is additive, so decomposing the heat function $f(x)$ into a superposition of sines and cosines greatly simplifies our analysis.

So how is the Fourier transform achieved? Let's start with real numbers. Taking sine as an example, we have:
$$
\begin{aligned}
&\int_{-\pi}^\pi \sin nx\sin mx\,\mathrm{d}x=
\begin{cases}
\frac12,&n=m,\\
0,&\text{otherwise.}
\end{cases}\\
&\int_{-\pi}^\pi \cos nx\cos mx\,\mathrm{d}x=
\begin{cases}
\frac12,&n=m,\\
0,&\text{otherwise.}
\end{cases}\\
&\int_{-\pi}^\pi \sin nx\cos mx\,\mathrm{d}x=0\\
\end{aligned}
$$
where $n,m\in\mathbb{Z}$. Then we call $\left\{\sin x,\cos x,\sin 2x,\cos2x,\cdots\right\}$ an orthogonal system.

Based on the orthogonality of sines and cosines, we can perform a Fourier series expansion (not the transform at this point) for any function composed of a superposition of sines and cosines (or other orthogonal systems):
$$
f(x)\sim\sum_{k=0}^{\infty}A_k\cos kx+B_k\sin kx
$$
Note: Since we obtain a function defined only on $[-\pi,\pi]$, we use $\sim$ instead of $=$.
Consider finding the coefficients $A_n,B_n$. We multiply both sides by $\sin nx$, then integrate $\displaystyle\int_{-\pi}^\pi$, yielding:
$$
\begin{aligned}
\int_{-\pi}^\pi f(x)\sin nx\,\mathrm{d}x&=\int_{-\pi}^\pi\sum_{k=0}^{\infty}A_k\cos kx\sin nx+B_k\sin kx\sin nx\,\mathrm{d}x\\
&=\int_{-\pi}^\pi B_n\sin nx \sin nx\,\mathrm{d}x\\
&=\pi B_n
\end{aligned}
$$
Thus,
$$
B_n=\frac1\pi\int_{-\pi}^\pi f(x)\sin nx\,\mathrm{d}x
$$
Using the same method, we can derive $A_n$, but there's a minor issue: there is a special case for $n=1$. Let's calculate it separately:
$$
\int_{-\pi}^\pi f(x)\,\mathrm{d}x=2\pi A_0\\
\Rightarrow A_0=\frac1{2\pi}\int_{-\pi}^\pi f(x)\,\mathrm{d}x
$$
To unify, we write:
$$
f(x)\sim\frac {A_0}2+\sum_{n=1}^\infty A_n\cos nx+B_n\sin nx
$$

Similarly, for a function $f(x)$ with period $T=\frac{2\pi}\omega$, defined on $[-T,T]$, we have:
$$
f(x)\sim\frac {A_0}2+\sum_{n=1}^\infty A_n\cos n\omega x+B_n\sin n\omega x
$$
where:
$$
A_n=\frac2T\int_{-T}^Tf(x)\cos n\omega x\,\mathrm{d}x\\
\mathrm{}\\
B_n=\frac2T\int_{-T}^Tf(x)\sin n\omega x\,\mathrm{d}x\\
$$
There are many unresolved issues regarding Fourier series, such as integrability, uniqueness, etc., but these more detailed topics are somewhat more difficult. As study notes, this serves only as a record, so we will not discuss them further here.

Let's try to unify the coefficients using Euler's formula:
$$
e^{i\theta}=\cos\theta+i\sin\theta
$$
Thus:
$$
f(x)\sim\frac{A_0}2+\sum_{n=1}^\infty\left[\frac{A_n+B_n}2e^{in\omega }+\frac{A_n-B_n}2e^{-in\omega}\right]
$$
Define new coefficients:
$$
\begin{aligned}
C_n&=\frac{A_n+B_n}{2}\\
&=\frac1T\int_{-T}^Tf(x)e^{-in\omega x}\,\mathrm{d}x
\end{aligned}
$$
Simultaneously, splitting and recombining the series gives:
$$
f(x)=\sum_{n=-\infty}^{\infty}C_n e^{in\omega}
$$
Here we switch to $=$ for convenience in explaining the Fourier transform.

The preceding was about Fourier series, which primarily involves discrete orthogonal systems.
Consider the case where the period $T\to\infty$. Then $\omega\to0$, and considering at least $n\mathrm{d}\omega\to\omega$, we rewrite the coefficient $C_n$ as a function of $\omega$, $C(\omega)$:
$$
C(\omega)=\frac{1}{2\pi}\int_{-\infty}^\infty f(t)e^{-i\omega t}\,\mathrm{d}{t}
$$
Note that in this case, the previous expression takes the form of a Riemann sum, thus:
$$
f(x)=\int_{-\infty}^\infty C(\omega)e^{i\omega t}\,\mathrm{d}\omega
$$
We define the Fourier transform:
$$
\mathcal{F}(\omega)=2\pi C(\omega)
$$
Thus we have:
$$
f(x)=\frac1{2\pi}\int_{-\infty}^\infty \mathcal{F}(\omega)e^{i\omega t}\,\mathrm{d}\omega\\
\mathrm{}\\
\mathcal{F}(\omega)=\int_{-\infty}^\infty f(t)e^{-i\omega t}\,\mathrm{d}{t}
$$
The Fourier transformed function has many properties, but since the more general Laplace transform possesses these properties as well, we will place the discussion of these properties under the Laplace transform section.

## Laplace Transform
The Fourier transform greatly simplifies many calculations, but in certain specific scenarios, it might fail, such as with the Dirac delta function, or high-order exponential power functions where the integral diverges. Introducing a convergence factor is effective here. We redefine the transform:
$$
\mathcal{L}\{f(t)\}(\sigma,\omega)=\int_{-0}^\infty f(t)e^{-\sigma t}e^{-i\omega t}\,\mathrm{d}t
$$
But note that $\sigma+i\omega$ is precisely a complex number, so let $s=\sigma+i\omega$, yielding:
$$
\mathcal{L}\{f(t)\}(s)=\int_{-0}^\infty f(t)e^{-st}\,\mathrm dt
$$
And the inverse transform:
$$
f(t)=\frac1{2\pi i}\int_{\sigma-i\infty}^{\sigma+i\infty} \mathcal{L}(s)e^{st}\,\mathrm dt
$$
The Laplace transform has many nice properties, such as:
$$
\begin{aligned}
\large\text{1. } &\mathcal L\{af(t)+bg(t)\}=a\mathcal L\{f(t)\}+b\mathcal L\{g(t)\}\\
\large\text{2. } &\mathcal L\left\{f^{(n)}(t)\right\}=s^n\mathcal L\{f(t)\}-s^{n-1}f(0)-s^{n-2}f'(0)-\cdots-f^{(n-1)}(0)\\
\large\text{3. } &\mathcal L\left\{\underbrace{\int_0^t\,\mathrm dt\int_0^t\,\mathrm dt\cdots\int_0^t f(t)\,\mathrm dt}_{\text{nth integral}}\right\}=\frac1{s^n}\mathcal L\{f(t)\}\\
\large\text{4. } &\mathcal L\{f*g\}=\mathcal L\{f(t)\}\cdot\mathcal L\{g(t)\}\\\\
&\text{blah blah ...}
\end{aligned}
$$

## Mellin Transform
This is also derived from the Fourier transform.
$$
\mathcal M\{f(x)\}(s)=\int_0^\infty x^{s-1}f(x)\,\mathrm dx\\
\mathrm{}\\
f(x)=\frac1{2\pi i}\int_{\sigma-i\infty}^{\sigma+i\infty}x^{-s}\mathcal M(s)\,\mathrm ds
$$
The connection to the Fourier transform:
$$
\mathcal M\{f(x)\}(s)=\mathcal F\{f(e^{-x})\}(-is)
$$
The Mellin Transform laid the foundation for Ramanujan's Master Theorem (digging a pit). Here are some properties:
$$
\begin{aligned}
\large\text{1. } &\mathcal M\{f*g\}=\mathcal M\{f(x)\}\cdot\mathcal M\{g(x)\}\\
\large\text{2. } &\mathcal M\{f\circ g\}=\mathcal M\{f(x)\}\cdot\mathcal M\{g(x)\}(1-s)\\
\large\text{3. } &\mathcal M\{f\cdot g\}=\mathcal M^{-1}\{\mathcal M\{f\}(x)\cdot\mathcal M\{g\}(s-x)\}(1)\\
&\text{blah blah ...}
\end{aligned}
$$

## Appendix
Laplace Transform Table.
| $f(t)$ | $\mathcal L\{f(t)\}(s)$ |
|:---:|:---:|
| $\delta(t)$ | $1$ |
| $1$ | $\frac 1s$ |
| $e^{at}$ | $\frac1{s-a}$ |
| $e^{at}t^n$ | $\frac{\Gamma(n+1)}{(s-a)^{n+1}}$ |
| $\sin at$ | $\frac a{s^2+a^2}$ |
| $\cos at$ | $\frac s{s^2+a^2}$ |
| $\sinh at$ | $\frac a{s^2-a^2}$ |
| $\cosh at$ | $\frac s{s^2-a^2}$ |