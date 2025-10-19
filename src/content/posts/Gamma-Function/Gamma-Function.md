---
title: Gamma Function
published: 2025-10-19
description: 'Introduction on Gamma Function (polygamma)'
image: './bg.jpg'
tags: [Complex,Mathematic]
category: 'Mathematic'
draft: false 
lang: ''
---
## Casual Remarks (Chinese)
河溢危，禾已萎，鹤依偎。禾异味，鹤已畏，合一，谓何？"异味？"何矣，味何？以萎。何异胃颌已危，何医为？河易为河医。为何？医喂荷以维何一胃。何已维。"颌医未。"何矣，胃颌易维，合一位，荷医为颌，医危颌，"已伟！"何意为贺医位。（好文当赏！）    
## Some Definitions
We define the following two functions:
$$
\Gamma(s)=\int_0^\infty t^{s-1}e^{-t}\,\mathrm{d}t\\
\psi^{(n)}(s)=\frac{\mathrm{d}^{n+1}}{\mathrm{d}s^{n+1}}\ln\Gamma(s)
$$
The first is the well-known $\text{Gamma}$ function, and the second is the $\text{polygamma}$ function (hereinafter abbreviated as $\text{psi}$ function for convenience, let $\psi=\psi^{(0)}$).  
Also, some constants that will be used later:
$$
\begin{aligned}
&\gamma=\lim_{n\to\infty}\left(\sum_{i=1}^n\frac1i-\ln n\right)\\
&e^x=\lim_{n\to\infty}\left(1+\frac xn\right)^n
\end{aligned}
$$
## $\Gamma$ Function
Usually, the $\Gamma$ function can be written in product form, such as:
$$
\Gamma(s)=\lim_{n\to\infty}\frac{n!n^s}{s(s+1)\cdots(s+n)}
$$
Then obviously:
$$
\Gamma(s+1)=s\Gamma(s)=s!
$$
This definition is very convenient. We use it to derive some properties of the $\Gamma$ function.  
First, let's write another product form of the $\Gamma$ function.
$$
\begin{aligned}
\frac1s\prod_{n=1}^\infty\frac{\left(1+\frac1n\right)^s}{1+\frac sn}&=\lim_{n\to\infty}\frac{n!n^s}{s(s+1)\cdots(s+n)}\\
&=\Gamma(s)
\end{aligned}
$$
Also, note that:
$$
\sin x=x\prod_{n=1}^\infty\left(1-\frac{x^2}{n^2\pi^2}\right)
$$
Let $s=\pi x$, then:
$$
\sin s\pi=s\pi\prod_{n=1}^\infty\left(1-\frac{s^2}{n^2}\right)
$$
Thus we have:
$$
\boxed{\Gamma(s)\Gamma(1-s)=\frac\pi{\sin s\pi}}
$$
Also, we can derive the expansion:
$$
e^{\gamma x}\Gamma(x+1)=\prod_{n=1}^\infty\frac{e^\frac xn}{1+\frac xn}
$$
This is the famous Weierstrass formula.  
Additionally, there is a multiplication theorem:
$$
\Gamma(s)\Gamma\left(s+\frac1n\right)\cdots\Gamma\left(s+\frac{n-1}n\right)=\frac{(2\pi)^{\frac{n-1}2}}{n^{ns-\frac12}}\Gamma(ns)
$$
where $n\in\mathbb{N}$. I personally think this is really ugly.
## $\psi$ Function
Now for the main content.

**Theorem 1** 
$$
-\psi(z)=\frac1z+\gamma+\sum_{n=1}^\infty\left(\frac1n-\frac1{n+z}\right)
$$
The proof is very simple, just take the logarithm of both sides of the Weierstrass formula mentioned above; it is left as an exercise.  
Based on **Theorem 1**, two corollaries can be easily obtained.
- **Corollary 1.1** $\psi(z+n)-\psi(z)=\displaystyle\sum_{k=0}^{n-1}\frac1{z+k}$
- **Corollary 1.2** $\psi^{(m)}(z+n)-\psi^{(m)}(z)=m!(-1)^{m+1}\displaystyle\sum_{k=0}^{n-1}\frac1{(z+k)^{m+1}}$

These two conclusions are easily derived from **Theorem 1**, so the proofs are omitted here.  
Then there is the reflection formula:
$$
\psi(1-z)-\psi(z)=\pi\cot \pi z
$$
This is obtained by taking the logarithm of the $\Gamma$ function reflection formula and then differentiating.  
Let's find some special values:

- When $z=1$, we have
$$
\psi^{(n)}(1)=
\begin{cases}
 -\gamma & \text{ if } n=0. \\
 n!(-1)^{n+1}\zeta(n+1) & \text{Otherwise.}
\end{cases}
$$
- When $z=\frac12$, we have
$$
\psi^{(n)}\left(\frac12\right)= 
\begin{cases}
 -\gamma-2\ln2 & \text{ if } n=0. \\
 n!(-1)^{n+1}\left(2^{n+1}-1\right)\zeta(n+1) & \text{Otherwise.}
\end{cases}
$$
### Taylor Expansion of the $\psi$ Function
Now, let's Taylor expand the $\psi$ function around $1$:
$$
\psi(x)+\gamma=\sum_{n=1}^\infty\frac{\psi^{(n)}(1)}{n!}(x-1)^n
$$
Substituting the expression from above:
$$
\sum_{n=1}^\infty x^n\zeta(n+1)=-\psi(1-x)-\gamma
$$
Then, you can mass-produce series.
## Gauss Digamma Theorem
This theorem states:
$$
\psi\left(\frac pq\right)=-\gamma-\frac\pi2\cot\frac{\pi p}q-\ln q+\sum_{n=1}^{q-1}\cos\frac{2\pi np}q\ln\left(2\sin\frac{\pi n}{q}\right)
$$
**Proof:**  
Recall **Theorem 1** for the $\psi$ function:
$$
-\psi(z)=\frac1z+\gamma+\sum_{n=1}^\infty\left(\frac1n-\frac1{n+z}\right)
$$
Let $z=\frac pq,(0<p<q,p,q\in\mathbb{N})$, using Abel's limit theorem, then:
$$
\psi\left(\frac pq\right)+\gamma=\lim_{t\to1^-}\sum_{n=0}^\infty\left(\frac1{n+1}-\frac{q}{p+nq}\right)t^{p+nq}
$$
Further,
$$
\begin{aligned}
\sum_{n=0}^{\infty} \left( \frac{1}{n+1} - \frac{q}{p+nq} \right) t^{p+nq} &= \sum_{n=0}^{\infty} \frac{t^{p+nq}}{n+1} - \sum_{n=0}^{\infty} \frac{qt^{p+nq}}{p+nq}\\

&= t^{p-q} \sum_{n=0}^{\infty} \frac{t^{(n+1)q}}{n+1} - q \sum_{n=0}^{\infty} \frac{t^{p+nq}}{p+nq}\\

&= -t^{p-q} \ln (1-t^q) + \sum_{n=0}^{q-1} \omega^{-np} \ln (1-\omega^n t)\\

&= -t^{p-q} \ln \frac{1-t^q}{1-t} - (t^{p-q}-1) \ln (1-t) + \sum_{n=1}^{q-1} \omega^{-np} \ln (1-\omega^n t)\\
\end{aligned}
$$
where $\omega = e^{\frac{2\pi i}{q}}$. Letting $t \to 1^-$ yields:
$$
\psi \left( \frac{p}{q} \right) = -\gamma - \ln q + \sum_{n=1}^{q-1} \omega^{-np} \ln (1-\omega^n)
$$
From this we easily get:
$$
\psi \left( \frac{p}{q} \right) + \psi \left( \frac{q-p}{q} \right) = -2\gamma - 2 \ln q + 2 \sum_{n=1}^{q-1} \cos \left( \frac{2\pi np}{q} \right) \ln (1-\omega^n)\tag{1}
$$
The left side of the above equation is real, so the right side must take the real part, and
$$
\begin{aligned}
\Re(\ln(1-\omega^n)) &= \ln|1-\omega^n|\\
&= \ln\left| \left( 1 - \cos\frac{2\pi n}{q} \right)^2 + \sin^2\frac{2\pi n}{q} \right|^{\frac12}\\
&= \frac{1}{2}\ln\left( 2-2\cos\frac{2\pi n}{q} \right)\\
&= \ln\left( 2\sin\frac{\pi n}{q} \right)
\end{aligned}
$$
From the reflection formula
$$
\Gamma(s)\Gamma(1-s) = \frac{\pi}{\sin \pi s}
$$
Taking the logarithmic derivative with respect to $s$, we get
$$
\psi(s) - \psi(1-s) = \frac{d}{ds}\ln(\Gamma(s)\Gamma(1-s)) = -\pi\cot \pi s
$$
Thus
$$
\psi\left(\frac{p}{q}\right) - \psi\left(\frac{q-p}{q}\right) = -\pi\cot\frac{\pi p}{q}\tag{2}
$$
Finally, adding $(1)$ and $(2)$, we get:
$$
\psi\left(\frac pq\right)=-\gamma-\frac\pi2\cot\frac{\pi p}q-\ln q+\sum_{n=1}^{q-1}\cos\frac{2\pi np}q\ln\left(2\sin\frac{\pi n}{q}\right)
$$
This is absolutely the messiest $\KaTeX$ typesetting I have ever written. It can't be helped; the $\KaTeX$ version supported by markdown is ridiculously low.
## Some Conclusions
$$
\gamma=\int_0^\infty e^{-t}\left(\frac1{1-e^{-t}}-\frac1t\right)\,\mathrm{d}t
$$
Proof:
$$
\text{To be continued.}
$$

## References
- [Proof of Gauss's Digamma Theorem](https://www.cnblogs.com/pengdaoyi/p/7262478.html)
