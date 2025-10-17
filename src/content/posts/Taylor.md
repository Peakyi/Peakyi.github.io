---
title: Taylor Series
published: 2025-10-16
description: 'I HAD ALREADY WRITTEN 5KB ON TAYLOR SERIES!!!'
image: ''
tags: [Mathematic]
category: 'Mathematic'
draft: false 
lang: ''
---

## Taylor's Formula
Let's consider a polynomial:
$$
p=p(x)=a_0+a_1x+a_2x^2+\dots+a_nx^n
$$
Using high school differentiation rules, we can easily obtain the following results:
$$
\begin{aligned}
p'&=a_1+2a_2x+3a_3x^2+\dots+na_nx^{n-1},\\
p''&=2a_2+3\cdot 2a_3x+\dots+n\cdot (n-1)a_nx^{n-2},\\
&\dots\\
p^{(n)}&=n\cdot(n-1)\cdot(n-2)\dots2\cdot a_n
\end{aligned}
$$
Now, let $x=0$, then we have:
$$
p^{(i)}(0)=a_i\cdot i!\\
\Rightarrow a_i=\frac{p^{(i)}(0)}{i!}
$$
Substituting back into the original expression, we get:
$$
p(x)=p(0)+\frac{p'(0)}{1!}x+\frac{p''(0)}{2!}x^2+\dots+\frac{p^{(n)}(0)}{n!}x^n
$$
If we had initially let $x=(x-x_0)$, then at this step, we would obtain:
$$
p(x)=p(x_0)+\frac{p'(x_0)}{1!}(x-x_0)+\frac{p''(x_0)}{2!}(x-x_0)^2+\dots+\frac{p^{(n)}(x_0)}{n!}(x-x_0)^n
$$
This is the well-known Taylor's formula.
## Expansion of Arbitrary Functions
If a function $f(x)$ is $n$-times differentiable at $x_0$ on the interval $[a,b]$, then we can construct the polynomial
$$
p_n(x)=f(x_0)+\frac{f'(x_0)}{1!}(x-x_0)+\frac{f''(x_0)}{2!}(x-x_0)^2+\dots+\frac{f^{(n)}(x_0)}{n!}(x-x_0)^n
$$
However, at this point, $f(x)=p_n(x)$ does not necessarily hold true. The $p(x)$ we obtained can only be regarded as an approximation of the function $f(x)$.  
We denote their error as $r_n(x)=f(x)-p_n(x)$.  
We find that when $x\rightarrow x_0$, $r_n(x)=o((x-x_0)^n)$.

**Proof**

Consider its equivalent proposition:
$$
r_n(x_0)=r_n'(x_0)=\dots=r_n^{(m)}(x_0)=0
$$ 
We use mathematical induction for the proof.  
When $m=0,1$, clearly:
$$
r_n(x_0)=r_n'(x_0)=0
$$
Assume it holds for $1\le m=k$. To prove it also holds for $m=k+1$, i.e.,
$$
r_n(x_0)=r_n'(x_0)=\dots=r_n^{(k+1)}(x_0)=0
$$
then 
$$
r_n(x)=o((x-x_0)^{k+1})
$$
Thus,
$$
r_n'(x)=o((x-x_0)^k)
$$
[But](https://baike.baidu.com/item/%E4%BD%86/62894180) (A chinese meme) by Lagrange's Mean Value Theorem, there must exist $\exists x_t\in[x,x_0]$ such that
$$
r_n'(x_t)(x-x_0)=r_n(x)-r_n(x_0)\\
\Rightarrow r_n'(x_t)=o((x-x_0)^k)\\
$$

Then we very easily obtain:
$$
f(x)=\sum^n_{i=0}{\frac{f^{(i)}(x_0)}{i!}(x-x_0)^i}+o((x-x_0)^n)
$$
This is called the **Taylor's formula with Peano remainder**.  
Next, we prove its uniqueness.

**Proof of Uniqueness**

Suppose we simultaneously have:
$$
f(x)=\sum^n_{i=0}{A_i(x-x_0)^i}+o((x-x_0)^n)
$$
and
$$
f(x)=\sum^n_{i=0}{A'_i(x-x_0)^i}+o((x-x_0)^n)
$$
Letting $x\to x_0$, we get $A_0=A'_0$. Subtract the two equations, then divide by $(x-x_0)$, to get $A_1=A'_1$. Continuing this process, we obtain:
$$
A_i=A'_i(\forall i\in[1,n]\cap\mathbb{N})
$$
Thus, it's unique!

Substituting $x_0=0$, we get a more concise expression called the **Maclaurin expansion**. Giving it a new name?! Actually quite ironic.  
Below are the Maclaurin expansions of some basic elementary functions.
$$
\begin{aligned}
e^x&=\sum_{i=0}^n\frac{x^i}{i!}+o(x^n)\\
\sin(x)&=\sum_{i=0}^n(-1)^{i+1}\frac{x^{2i-1}}{(2i-1)!}+o(x^{2n})\\
\cos(x)&=\sum_{i=0}^n(-1)^i\frac{x^{2i}}{(2i)!}+o(x^{2n+1})\\
\end{aligned}
$$
## Taylor Series
In the previous Taylor's formula, note that $n$ can take any value, so naturally, we consider letting it tend to infinity.  
Thus, the Taylor series refers to the Taylor formula when $n\to\infty$~  
Formally, the Taylor series has the following form:
$$
f(x)=\sum^\infty_{i=0}{A_i(x-x_0)^i}
$$
where
$$
A_n=\frac{f^{(i)}(x_0)}{i!}
$$
are called the Taylor coefficients.  
Although this seems very simple, it raises many problems. The most direct one is: Does that series converge? And will it still equal the original function? This is a very tricky problem.

$f(x)$ can equal that summation if and only if the remainder term $r_n(x)$ satisfies:
$$\lim_{n\to\infty}r_n(x)=0$$
The proof is obvious.  
But to prove this equality holds, we might need to study other forms of the remainder term. Below, I will discuss the case for $x_0=0$; other cases are left for the reader to explore.  
- Lagrange form: $r_n(x)=\frac{f^{(n+1)}(\theta x)}{(n+1)!}x^{n+1}$
- Cauchy form: $r_n(x)=\frac{f^{(n+1)}(\theta x)}{n!}(1-\theta)x^{n+1}$

where $\theta\in[0,1]$.  
Proof? The Lagrange form is proved using Lagrange's Mean Value Theorem, and the Cauchy form is proved using Cauchy's Mean Value Theorem.

Here are the specific Taylor expansions of some functions.
### Taylor Expansions of Exponential and Basic Trigonometric Functions
If a function $f(x)$ has derivatives of all orders on the interval $[0,H]$ or $[-H,0](H>0)$, and when $x$ varies within the given interval, the absolute values of all these derivatives are bounded by the same number:
$$|f^{(n)}(x)|\le L$$
Then this function can be expanded as a Taylor series.

**Proof**

We take the remainder in the Lagrange form, then we easily get:
$$|r_n(x)|=\frac{|f^{(n+1)}(\theta x)|}{(n+1)!}|x|^{n+1}\le L\cdot\frac{H^{n+1}}{(n+1)!}$$
Let's prove a stronger conclusion. Summing both sides, we get:
$$
\sum_{n=0}^\infty|r_n(x)|\le L\cdot\sum_{n=0}^\infty \frac{H^{n+1}}{(n+1)!}
$$
The right-hand side clearly converges, thus we can deduce $r_n(x)\to 0$!

When $f(x)=e^x,\sin(x),\cos(x)$, the conditions are clearly satisfied, so we can write their expansions:
$$
\begin{aligned}
e^x&=\sum_{i=0}^\infty\frac{x^i}{i!}\\
\sin(x)&=\sum_{i=1}^\infty(-1)^{i+1}\frac{x^{2i-1}}{(2i-1)!}\\
\cos(x)&=\sum_{i=0}^\infty(-1)^i\frac{x^{2i}}{(2i)!}\\
\arctan(x)&=\sum_{i=1}^\infty(-1)^{i+1}\frac{x^{2i-1}}{2i-1}
\end{aligned}
$$
Here, for the arctangent expansion, substituting $x=1$, we get:
$$
\frac\pi4=1-\frac13+\frac15-\cdots
$$
which is the classic Leibniz formula.
### Logarithmic Function

Consider expanding $f(x)=\ln(1+x)$. The reason we expand $\ln(1+x)$ is that it's convenient for calculation.  
First, write its Taylor series:
$$
\ln(1+x)=\sum_{n=1}^\infty(-1)^{n+1}\frac{x^n}{n}
$$
We use the Lagrange form of the remainder to consider its convergence.
$$
\lim_{n\to\infty}r_n(x)=\frac{(-1)^n}{n+1}\cdot(\frac x{\theta x+1})^{n+1}=0
$$
But unfortunately, the above only holds when $x\in(-1,1]$, meaning its expansion converges only in this interval.
### Stirling's Formula
Most applications of Taylor series involve estimation. Here is a classic example of estimation.  
Consider the Taylor expansion of $\ln(1+x)$ we obtained earlier. We can easily get:
$$
\ln\frac{1+x}{1-x}=\ln(1+x)-\ln(1+(-x))=2x\cdot(1+\frac{x^2}{3}+\frac{x^4}5+\dots)
$$
Let $x=\frac1{2n+1}$, then we can obtain:
$$
\ln\frac{n+1}{n}=\frac2{2n+1}\cdot[1+\frac13\cdot\frac1{(2n+1)^2}+\dots]
$$
Rearranging terms, we get:
$$
\begin{aligned}
1<(n+\frac12)\ln(1+\frac1n)&=1+\frac13\cdot\frac1{(2n+1)^2}+\dots\\
&<1+\frac13\cdot[\frac1{(2n+1)^2}+\frac1{(2n+1)^4}+\dots]\\
&=1+\frac1{12n(n+1)}
\end{aligned}
$$
Taking the natural exponential on both sides:
$$
1<\frac{(1+\frac1n)^{n+\frac12}}{e}<e^\frac1{12n(n+1)}
$$
Here introduces a genius idea. Let $a_n=\frac{n!e^n}{n^{n+\frac12}}$, then we can get:
$$
1<\frac{a_n}{a_{n+1}}=\frac{(1+\frac1n)^{n+\frac12}}{e}<e^\frac1{12n(n+1)}=\frac{e^\frac1{12n}}{e^\frac1{12(n+1)}}\\
\Rightarrow a_n e^{-\frac1{12n}}<a_{n+1}e^{-\frac1{12(n+1)}}
$$
Note that clearly $\exists a$ such that $a_n e^{-\frac1{12n}}<a<a_n$ holds. Let
$$
a=a_ne^{-\frac\theta{12n}}
$$
Substituting the definition of $a_n$, we can obtain:
$$
n! =a\sqrt n(\frac ne)^n\cdot e^\frac\theta{12n}
$$
Now consider how to solve for $a$.  
Note that:
$$
\frac\pi2=\lim_{n\to\infty}\frac1{2n+1}\cdot\left[\frac{(2n)!!}{(2n-1)!!}\right]^2
$$
Let's transform this double factorial:
$$
\frac{(2n)!!}{(2n-1)!!}=\frac{2^{2n}(n!)^2}{(2n)!}
$$
Replace $n!$ and $(2n)!$ with the results we derived earlier:
$$
\frac{(2n)!!}{(2n-1)!!}=a\sqrt\frac n2\cdot e^\frac{4\theta-\theta'}{24n}
$$
Substitute back into the original limit:
$$
\frac\pi2=\lim_{n\to\infty}\frac1{2n+1}a^2\cdot\frac n2\cdot e^\frac{4\theta-\theta'}{12n}
=\frac{a^2}4\\
\Rightarrow a=\sqrt{2\pi}
$$
Substitute back into the initial equation, and we finally obtain Stirling's formula:
$$
n! =\sqrt{2\pi n}\cdot(\frac ne)^n\cdot e^\frac\theta{12n}
$$
This can be used for estimation when $n$ is very large.
