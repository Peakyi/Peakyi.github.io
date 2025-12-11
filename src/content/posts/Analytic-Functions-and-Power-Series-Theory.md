---
title: Analytic Functions and Power Series Theory
published: 2025-12-10
description: 'Found that someone has already written about this, so no further organization is needed.'
image: ''
tags: [Mathematic]
category: 'Mathematic'
draft: false 
lang: ''
---

# Preparatory Work

## Complex Derivative

Let $U\subset\mathbb C$, $f:U\to\mathbb C$, $z\in U$. If there exists a $\mathbb C$-linear function $df|_z\in\operatorname{Hom}_{\mathbb C}(\mathbb C,\mathbb C)$ such that for any $h\in\mathbb C$, as $|h|\to 0$, $|f(z+h)-f(z)-df|_z(h)|=o(|h|)$, then $f$ is said to be complex differentiable at point $z$, and $df|_z(1)$ is called its complex derivative, denoted by $f'(z)$. Note that the complex derivative exists if and only if there exists $df|_z\in\operatorname{Hom}_{\mathbb C}(\mathbb C,\mathbb C)$ such that
$$
\lim_{|h|\to 0}\left|\frac{f(z+h)-f(z)-df|_z(h)}{h}\right|=0,
$$
i.e.,
$$
\lim_{h\to 0}\frac{f(z+h)-f(z)-df|_z(h)}{h}=0,
$$
or
$$
\lim_{h\to 0}\frac{f(z+h)-f(z)}{h}=\lim_{h\to 0}\frac{df|_z(h)}{h}.
$$
Since $\dim_{\mathbb C}\mathbb C=1$, $df|_z(h)=f'(z)h$, hence
$$
f'(z)=\lim_{h\to 0}\frac{f(z+h)-f(z)}{h}.
$$
Let $f(z)=u(\operatorname{Re}z,\operatorname{Im}z)+iv(\operatorname{Re}z,\operatorname{Im}z)$. Set $z=x+iy$, denote $\widetilde f(x,y):=f(x+iy)$. Below we will not distinguish $\widetilde f$ and $f$. If $h$ approaches $z$ from the real direction, then
$$
f'(z)=\frac{\partial f}{\partial x}=\frac{\partial u}{\partial x}+i\frac{\partial v}{\partial x},
$$
if $h$ approaches $z$ from the purely imaginary direction, then
$$
f'(z)=\lim_{s\to 0}\frac{f(z+is)-f(z)}{is}=\frac{\partial u}{i\partial y}+i\frac{\partial v}{i\partial y}=-i\frac{\partial u}{\partial y}+\frac{\partial v}{\partial y}.
$$
The equality of these two expressions gives a necessary condition for complex differentiability.

For $p=x+iy\in\mathbb C$, formally define
$$
\frac{\partial f}{\partial z}\bigg|_{p}=\frac{1}{2}\left(\frac{\partial f}{\partial x}\bigg|_{(x,y)}-i\frac{\partial f}{\partial y}\bigg|_{(x,y)}\right),\qquad\frac{\partial f}{\partial\overline z}\bigg|_{p}=\frac{1}{2}\left(\frac{\partial f}{\partial x}\bigg|_{(x,y)}+i\frac{\partial f}{\partial y}\bigg|_{(x,y)}\right),
$$
and define $dz=dx+i\,dy,\,d\overline z=dx-i\,dy$, then
$$
\begin{aligned}
\frac{\partial f}{\partial z}\,dz+\frac{\partial f}{\partial\overline z}\,d\overline z&=\frac{1}{2}\left(\frac{\partial f}{\partial x}-i\frac{\partial f}{\partial y}\right)(dx+i\,dy)+\frac{1}{2}\left(\frac{\partial f}{\partial x}+i\frac{\partial f}{\partial y}\right)(dx-i\,dy)\\
&=\frac{\partial f}{\partial x}\,dx+\frac{\partial f}{\partial y}\,dy=df.
\end{aligned}
$$

**Theorem 1.1** $\quad$ Let $U\subset\mathbb C$ be an open set, $z\in U$, then $f:U\to\mathbb C$ is differentiable at $z$ if and only if $\widetilde f$ is differentiable and
$$
\frac{\partial f}{\partial\overline z}=0
$$
i.e.,
$$
\frac{\partial f}{\partial x}=-i\frac{\partial f}{\partial y}
$$
i.e.,
$$
\frac{\partial u}{\partial x}=\frac{\partial v}{\partial y},\qquad\frac{\partial u}{\partial y}=-\frac{\partial v}{\partial x}.
$$

**Proof** $\quad$ Obviously if $f$ is complex differentiable at $z$ then $\widetilde{f}$ is real differentiable at that point, hence the necessity has been shown above.

Conversely, assume $\widetilde f$ is real differentiable and satisfies the Cauchy-Riemann equations. Then for $h\in\mathbb R^2$, if $|h|\to 0$, then $\widetilde f(z+h)-\widetilde{f}=A(h)+o(|h|)$, where
$$
A=\begin{pmatrix}
\frac{\partial u}{\partial x}\big|_{z}&\frac{\partial u}{\partial y}\big|_{z}\\
\frac{\partial v}{\partial x}\big|_{z}&\frac{\partial v}{\partial y}\big|_{z}
\end{pmatrix}.
$$
Now we require $A(\cdot)$ to be $\mathbb C$-linear. Note that the Cauchy-Riemann equations guarantee that $A$ is of the form $\begin{pmatrix}
a&-b\\b&a
\end{pmatrix}$, so $A(\cdot)$ is exactly $(\frac{\partial u}{\partial x}+i\frac{\partial v}{\partial x})(\cdot)$, thus $f$ is complex differentiable at $z$. $\square$

A complex function is holomorphic if it is complex differentiable at every point of the entire $U$.

## Power Series

**Theorem 1.2** $\quad$ For every power series $\sum_{n=0}^{\infty}a_nz^n$, there exists $R\in[0,\infty]$, called the radius of convergence, such that
1. The series converges absolutely on $B(0,R)$;
2. The series converges uniformly on compact subsets of $B(0,R)$;
3. The series diverges on $\mathbb C\setminus\overline{B(0,R)}$, and its terms are unbounded;
d. On $B(0,R)$, the sum of the series is analytic, its derivative is $\sum_{n=1}^{\infty}na_nz^{n-1}$, and they have the same radius of convergence;
5. $1/R=\lim\limits_{n\to\infty}\sup\sqrt[n]{|a_n|}$.

**Proof** $\quad$ If $|z|<R$, then there exists $\rho\in(|z|,R)$, so $\rho^{-1}>R^{-1}$, hence $\exists N\in\mathbb N$ such that $\forall n\geq N$, $|a_n|^{1/n}<\rho^{-1}$, so $|a_n|<\rho^{-n}$, hence $|a_nz^n|<(|z|/\rho)^n$. Therefore
$$
\sum_{n=N}^{\infty}\left|a_n\right||z^n|<\sum_{n=N}^{\infty}\left(\frac{|z|}{\rho}\right)^n<\infty,
$$
so the power series converges absolutely at $z$. For a given $\rho<R$, choose $\rho_0\in(\rho,R)$, there exists $N\in\mathbb N$ such that $\forall n\geq N$, $|a_n|^{1/n}<\rho_0^{-1}$, then similarly, for any $|z|\leq\rho$, for any $\epsilon>0$, there exists $\mathbb N'\geq N$ such that $\forall n,m\geq N'$, we have
$$
\sum_{j=n}^{m}\left|a_j\right||z^j|<\sum_{j=n}^{m}\left(\frac{\rho}{\rho_0}\right)^j<\epsilon,
$$
so the power series converges uniformly on $\overline{B(0,\rho)}$, hence it converges uniformly on compact subsets of $B(0,R)$. If $|z|>R$, then we can find $\rho\in(R,|z|)$, so $\rho^{-1}<R^{-1}$, then for any $N\in\mathbb N$ there exists $n>N$ such that $|a_n|>\rho^{-n}$, so for infinitely many $n$, $|a_nz^n|>(|z|/\rho)^n$, thus the terms of the series are unbounded, and the series diverges.

Since $\sqrt[n]{n}\to 1$, $\sum_{n=1}^{\infty}na_nz^{n-1}$ has the same radius of convergence. Finally, for $|z|<R$, set
$$
\begin{aligned}
f(z)&=\sum_{n=0}^{\infty}a_nz^n=:s_n(z)+R_n(z),\\
s_n(z)&:=a_0+a_1z+\cdots+a_{n-1}z^{n-1},\qquad R_n(z):=\sum_{j=n}^{\infty}a_jz^j,\\
f_1(z)&:=\sum_{n=1}^{\infty}na_nz^{n-1}=\lim_{n\to\infty}s_n'(z).
\end{aligned}
$$
Now we prove $f'=f_1$. For any $z_0\in B(0,R)$, consider the identity
$$
\begin{aligned}
\frac{f(z)-f(z_0)}{z-z_0}-f_1(z_0)=\left(\frac{s_n(z)-s_n(z_0)}{z-z_0}-s_n'(z_0)\right)+(s_n'(z_0)-f_1(z_0))+\frac{R_n(z)-R_n(z_0)}{z-z_0},
\end{aligned}
$$
where $z\neq z_0$ and $|z|,|z_0|<\rho<R$. Note that
$$
\begin{aligned}
\frac{R_n(z)-R_n(z_0)}{z-z_0}&=\frac{1}{z-z_0}\sum_{j=n}^{\infty}(a_jz^j-a_jz_0^j)\\
&=\frac{1}{z-z_0}\sum_{j=n}^{\infty}(z-z_0)a_j(z^{j-1}+z^{j-2}z_0+\cdots+zz_0^{j-2}+z_0^{j-1})\\
&=\sum_{j=n}^{\infty}a_j(z^{j-1}+z^{j-2}z_0+\cdots+zz_0^{j-2}+z_0^{j-1}),
\end{aligned}
$$
thus as $n\to\infty$
$$
\left|\frac{R_n(z)-R_n(z_0)}{z-z_0}\right|\leq\sum_{j=n}^{\infty}j|a_j|\rho^{j-1}\to 0.
$$
On the other hand, $|s_n'(z_0)-f_1(z_0)|\to 0$, so there exists $N\in\mathbb N$ such that for $n\geq N$, each of the above two terms is less than $\epsilon/3$. For any such $n$, by the definition of derivative, there exists $\delta>0$ such that $\forall z\in B(z_0,\delta)$ we have
$$
\left|\frac{s_n(z)-s_n(z_0)}{z-z_0}-s_n'(z_0)\right|<\frac{\epsilon}{3}.
$$
Combining these we get
$$
\left|\frac{f(z)-f(z_0)}{z-z_0}-f_1(z_0)\right|<\epsilon,
$$
so $f_1(z_0)=f'(z_0)$. $\square$

# Cauchy Integral Theorem

## Line Integrals

Let the equation of $\gamma:[a,b]\to\mathbb C$ be $z(t)$. Define
$$
\int_{\gamma}f\,dz:=\int_a^bf(z(t))z'(t)\,dt
$$
and
$$
\int_{\gamma}f\,d\overline{z}:=\overline{\int_{\gamma}\overline f\,dz}=\int_a^bf(z(t))\overline{z'(t)}\,dt.
$$
For $dx=\frac{1}{2}(dz+d\overline{z}),\,dy=\frac{1}{2i}(dz-d\overline{z})$, define
$$
\begin{aligned}
\int_{\gamma}f\,dx:=\frac{1}{2}\left(\int_{\gamma}f\,dz+\int_{\gamma}f\,d\overline{z}\right),\\
\int_{\gamma}f\,dy:=\frac{1}{2i}\left(\int_{\gamma}f\,dz-\int_{\gamma}f\,d\overline{z}\right),
\end{aligned}
$$
then
$$
\begin{aligned}
\int_{\gamma}f\,dz=\int_{\gamma}f\,dx+i\int_{\gamma}f\,dy,\qquad\int_{\gamma}f\,d\overline z=\int_{\gamma}f\,dx-i\int_{\gamma}f\,dy.
\end{aligned}
$$
Set $x:=\operatorname{Re}z,\,y:=\operatorname{Im}z,\,u:=\operatorname{Re}f,\,v:=\operatorname{Im}f$, then
$$
\begin{aligned}
\begin{aligned}
\int f\,dx&=\int_a^bf(z(t))x'(t)\,dt=\int_{\gamma}u\,dx+i\int_{\gamma}v\,dx,\\
\int f\,dy&=\int_a^bf(z(t))y'(t)\,dt=\int_{\gamma}u\,dy+i\int_{\gamma}v\,dy,\\
\int f\,dz&=\int_{\gamma}(u\,dx-v\,dy)+i\int_{\gamma}(v\,dx+u\,dy),\\
\int f\,d\overline z&=\int_{\gamma}(u\,dx+v\,dy)+i\int_{\gamma}(v\,dx-u\,dy).\\
\end{aligned}
\end{aligned}
$$

Define the integral with respect to arc length as
$$
\int_{\gamma}f\,ds=\int_{\gamma}f\,|dz|:=\int_a^bf(z(t))|z'(t)|\,dt.
$$

## Rectifiable Arcs

The length of an arc is defined as
$$
l(\gamma):=\sup_{n,a=t_0<\cdots<t_n=b}\sum_{1}^n|z(t_j)-z(t_{j-1})|.
$$
If $l(\gamma)<\infty$, $\gamma$ is said to be rectifiable.

**Theorem 2.3** $\quad$ An arc $\gamma:z=z(t)$ is rectifiable if and only if its real and imaginary parts are of bounded variation.

**Proof** $\quad$ Note that $|x(t_j)-x(t_{j-1})|\leq|z(t_j)-z(t_{j-1})|$ and $|y(t_j)-y(t_{j-1})|\leq|z(t_j)-z(t_{j-1})|$, while $|z(t_j)-z(t_{j-1})|\leq|x(t_j)-x(t_{j-1})|+|y(t_j)-y(t_{j-1})|$,
thus if $x(t),y(t)$ are of bounded variation then $l(\gamma)<\infty$, conversely, if $l(\gamma)<\infty$ then $x(t),y(t)$ are both of bounded variation. $\square$

**Theorem 2.4** $\quad$ If $\gamma:[a,b]\to\mathbb C\xrightarrow{\sim}\mathbb R^2$ is $C^1$, then $\gamma$ is rectifiable, and $l(\gamma)=\int_{\gamma}\,ds=\int_a^b|z'(t)|\,dt$.

**Proof** $\quad$ Let $P$ be a partition of $[a,b]$, then $|z(t_{j+1})-z(t_j)|=\left|\int_{t_j}^{t_{j+1}}z'(t)\,dt\right|\leq\int_{t_j}^{t_{j+1}}|z'(t)|\,dt$, so
$$
l_{P}(\gamma)=\sum_{j=0}^{n-1}|z(t_{j+1})-z(t_j)|\leq\sum_{j=0}^{n-1}\int_{t_j}^{t_{j+1}}|z'(t)|\,dt=\int_{a}^{b}|z'(t)|\,dt<\infty,
$$
hence $l(\gamma)<\infty$, $\gamma$ is rectifiable. Since $z'(t)$ is continuous on $[a,b]$, it is uniformly continuous, so for any $\epsilon>0$, there exists $\delta>0$ such that $\forall s,t\in[a,b],\,|t-s|<\delta$, we have $|z'(t)-z'(s)|<\epsilon$. Take a partition $P$ such that $\forall j,\,|t_j-t_{j-1}|<\delta$. Then for any $t\in[t_j,t_{j+1}]$, $|z'(t)-z'(t_{j})|<\epsilon$. Thus
$$
\begin{aligned}
\int_{t_j}^{t_{j+1}}|z'(t)|\,dt&\leq\int_{t_j}^{t_{j+1}}|z'(t_j)|\,dt+\int_{t_j}^{t_{j+1}}|z'(t)-z'(t_j)|\,dt\\
&<\left|\int_{t_j}^{t_{j+1}}z'(t_j)\,dt\right|+(t_{j+1}-t_j)\epsilon\\
&\leq\left|\int_{t_j}^{t_{j+1}}z'(t)\,dt\right|+\left|\int_{t_j}^{t_{j+1}}(z'(t_j)-z'(t))\,dt\right|+(t_{j+1}-t_j)\epsilon\\
&<\left|\int_{t_j}^{t_{j+1}}z'(t)\,dt\right|+2(t_{j+1}-t_j)\epsilon\\
&=|z(t_{j+1})-z(t_j)|+2(t_{j+1}-t_j)\epsilon.
\end{aligned}
$$
Therefore
$$
\begin{aligned}
\int_{a}^{b}|z'(t)|\,dt&=\sum_{j=0}^{n-1}\int_{t_j}^{t_{j+1}}|z'(t)|\,dt\\
&<\sum_{j=0}^{n-1}\big(|z(t_{j+1})-z(t_j)|+2(t_{j+1}-t_j)\epsilon\big)\\
&=l_P(\gamma)+2(b-a)\epsilon<l(\gamma)+2(b-a)\epsilon.
\end{aligned}
$$
Since $\epsilon$ is arbitrary, letting $\epsilon\to 0$ yields $l(\gamma)=\int_{\gamma}\,ds=\int_a^b|z'(t)|\,dt$. $\square$

If $\gamma$ is $C^1$ and $f(z)$ is continuous on $\gamma$, then $f(z(t))|z'(t)|$ is uniformly continuous.

## Cauchy Integral Theorem

After decomposing mappings into real and imaginary parts, theorems concerning exact forms, closed forms, and curve integrals can be directly applied. If $p,q$ are respectively the partial derivatives of some complex function $U$ with respect to $x$ and $y$, then the integral $\int_{\gamma}(p\,dx+q\,dy)$ depends only on the endpoints. Indeed, let $p=a+ib,q=c+id$, then
$$
p\,dx+q\,dy=(a+ib)\,dx+(c+id)\,dy=(a\,dx+c\,dy)+i(b\,dx+d\,dy),
$$
if we can find $V,W$ such that $dV=a\,dx+c\,dy,dW=b\,dx+d\,dy$, then $U:=V+iW$ satisfies $dU=p\,dx+q\,dy$. Conversely, if there exists a complex-valued function $U$ such that $dU=p\,dx+q\,dy$, then set $U=V+iW$, we have
$$
\frac{\partial U}{\partial x}=a\,dx+ib\,dx=\frac{\partial V}{\partial x}+i\frac{\partial W}{\partial x},
$$
giving $\partial V/\partial x=a,\,\partial W/\partial x=b$, similarly, $\partial V/\partial y=c,\,\partial W/\partial y=c$, so $a\,dx+c\,dy,\,b\,dx+d\,dy$ are each exact, hence the integral $\int_\gamma(p\,dx+q\,dy)$ is independent of the path.

If the integral $\int_{\gamma}f\,dz$ is independent of the specific path, i.e., $f\,dz$ is exact, then there exists $F(z)$ such that $dF=f\,dx+if\,dy$, so
$$
\frac{\partial F}{\partial x}=f,\qquad\frac{\partial F}{\partial y}=if,
$$
thus $F(z)$ satisfies the Cauchy-Riemann equations.

From the above discussions, it can already be concluded that since $dz$, $z\,dz$ are exact, or more generally, $z^n\,dz\,(n\geq 0)$ are all exact, as long as the integral is closed, we have
$$
\oint dz=\oint z\,dz=\oint z^n\,dz=0.
$$
Secondly, if the region is simply connected, $f$ is holomorphic and its partial derivatives are continuous, then $\oint f\,dz=0$. This is because by the Cauchy-Riemann equations, we have respectively
$$
\begin{aligned}
d(u\,dx-v\,dy)&=-\left(\frac{\partial u}{\partial y}+\frac{\partial v}{\partial x}\right)dx\wedge dy=0,\\
d(v\,dx+u\,dy)&=\left(\frac{\partial u}{\partial x}-\frac{\partial v}{\partial y}\right)dx\wedge dy=0,
\end{aligned}
$$
so $f\,dz$ is exact, yielding $\oint f\,dz=0$.

This is the proof initially given by Cauchy. In the corollary of Poincaré's lemma, if $U$ is simply connected, then closed is equivalent to exact on $U$, but the proof of Poincaré's lemma requires the partial derivatives of $f$ to be continuous. Later, Goursat found that the condition of continuous partial derivatives is unnecessary, thus giving the following first version of the Cauchy integral theorem.

**Theorem 2.5 (Goursat)** $\quad$ Let $R$ be a rectangle, $f$ holomorphic on $\overline{R}$, then
$$
\int_{\partial R}f\,dz=0.
$$

**Proof** $\quad$ For a region $H$, denote $\eta(H):=\int_{\partial H}f\,dz$. For $R$, divide it into four congruent rectangles $R_1^1,R_2^1,R_3^1,R_4^1$, then
$$
\eta(R)=\eta(R_1)+\eta(R_2)+\eta(R_3)+\eta(R_4).
$$
Thus at least one $R_{j_1}^1$ satisfies $|\eta(R_j^1)|\geq 4^{-1}|\eta(R)|$. Continue dividing this $R_{j_1}^1$, there exists $R_{j_2}^2$ satisfying $|\eta(R_{j_2}^2)|\geq 4^{-1}|\eta(R_{j_2}^2)|$. Continuing this way, we obtain a descending sequence of rectangles $\{R_{j_k}^k\}_{k=1}^{\infty}$, where $|\eta(R_{j_k}^k)|\geq 4^{-k}|\eta(R)|$. By the Cantor intersection theorem, $\bigcap_{k=1}^{\infty}R_{j_k}^k=z_0\in\mathbb R$. Since $R$ is complex differentiable at $z_0$, for any $\epsilon>0$, there exists $\delta>0$ such that
$$
|f(z)-f(z_0)-f'(z_0)(z-z_0)|<\epsilon|z-z_0|,\qquad\forall z\in B(z_0,\delta).
$$
Take $n$ sufficiently large such that $R_{j_n}^n\subset B(z_0,\delta)$, let $R_n:=R_{j_n}^n$. From previous discussions, we know that integrals of $dz$ and $z\,dz$ are zero, so
$$
\begin{aligned}
|\eta(R_n)|&=\left|\int_{\partial R_n}(f(z)-f(z_0)-f'(z_0)(z-z_0))\,dz\right|\\
&\leq\int_{\partial R_n}|f(z)-f(z_0)-f'(z_0)(z-z_0)|\,|dz|<\epsilon\int_{\partial R_n}|z-z_0|\,ds.
\end{aligned}
$$
Let the diagonal of the original rectangle be $d$, perimeter be $L$, then the diagonal of $R_n$ is $d_n=2^{-n}d$, perimeter $L_n=2^{-n}L$, so
$$
4^{-n}|\eta(R)|\leq|\eta(R_n)|<\epsilon\int_{\partial R_n}d_n\,ds=\epsilon d_nL_n=4^{-n}\epsilon dL,
$$
i.e., $|\eta(R)|<\epsilon dL$. Since $\epsilon$ is arbitrary, we get $\int_{\partial R}f\,dz=\eta(R)=0$. $\square$

**Theorem 2.6** $\quad$ Let $R$ be a rectangle, with finitely many points $\{\zeta_j\}_1^n$ in its interior, $f$ holomorphic on $\overline R\setminus\{\zeta_j\}$. If
$$
\lim_{z\to\zeta_j}(z-\zeta_j)f(z)=0,\qquad\forall j=1,2,\cdots,n,
$$
then
$$
\int_{\partial R}f\,dz=0.
$$

**Proof** $\quad$ Decompose $R$ into small rectangles so that each contains at most one $\zeta_j$. Thus the problem reduces to the case of a single point set $\{\zeta_j\}=\{\zeta\}$. In this case, divide $R$ into nine small rectangles, with only the central one $R_0$ containing $\zeta$. Apply the first version of Cauchy's integral theorem to the other eight rectangles, then sum all integrals to get
$$
\int_{\partial R}f\,dz=\int_{\partial R_0}f\,dz.
$$
For any $\epsilon$, by the theorem condition, we can choose $R_0$ sufficiently small such that on $\partial R$, $|f(z)|<\epsilon/|z-\zeta|$. Since such $R_0$ can be chosen arbitrarily, assume $R_0$ is a square with $\zeta$ at its center. Then
$$
\left|\int_{\partial R_0}f\,dz\right|\leq\epsilon\int\frac{|dz|}{|z-\zeta|}.
$$
Now estimate the integral on the right. The integral is symmetric, so we only need to compute one side. Suppose $R_0$ has side length $2s$, after translation $\zeta=0$, consider the top side of the rectangle, then $|dz|=dx$, $|z|\geq s$. So the integral on the top side is less than $\int_{-s}^s\frac{dx}{s}=2$, overall
$$
\int_{\partial R_0}\frac{|dz|}{|z-\zeta|}<8,\qquad \left|\int_{\partial R_0}f\,dz\right|<8\epsilon.
$$
Since $\epsilon$ is arbitrary, the proposition follows. $\square$

With the Cauchy integral theorem for rectangles, we can prove the Cauchy integral theorem for disks without requiring the partial derivatives of $f$ to be continuous.

**Theorem 2.7** $\quad$ Let $f$ be holomorphic on an open disk $D$, then for every closed curve $\gamma$ in $D$, we have
$$
\int_{\gamma}f\,dz=0.
$$

**Proof** $\quad$ Let the center be $x_0+iy_0$. For $x+iy\in D$, define $\sigma$ as the path from $x_0+iy_0$ horizontally to $x+iy_0$, then vertically to $x+iy$. By Goursat's theorem, if $\tau$ is the path first vertically then horizontally, then the integrals of $f$ along these two paths are equal. Set
$$
F(z)=\int_{\sigma}f\,dz=\int_{\tau}f\,dz,
$$
considering the integrals along $\tau$ and $\sigma$ with respect to partial $x$ and partial $y$ respectively, we find
$$
\frac{\partial F}{\partial x}\bigg|_{z}=f(z),\qquad\frac{\partial F}{\partial y}\bigg|_z=if(z),
$$
so $f\,dz$ is exact, hence the integral of $f$ over any closed curve is zero. $\square$

**Corollary 2.8** $\quad$ Let $D$ be an open disk with finitely many points $\{\zeta_j\}_1^n$ in its interior. Let $f$ be holomorphic on $D$, and
$$
\lim_{z\to\zeta_j}(z-\zeta_j)f(z)=0,\qquad\forall j=1,2,\cdots,n,
$$
then for every closed curve $\gamma$ in $D$, we have
$$
\int_{\gamma}f\,dz=0.
$$

**Proof** $\quad$ Replace the Goursat theorem used in the proof of the previous theorem with its version with punctured points. $\square$

# Winding Number

First consider the winding number on $S^1$. In 3.1 to 3.6, we assume curves are $C^1$.

**Definition 3.1** $\quad$ Let $S^1\subset\mathbb R^2$ be the unit circle and $c:I=[0,b]\to S^1,t\mapsto(x(t),y(t))$ a closed curve. Find $\varphi_0$ such that $\cos(\varphi_0)=x(0),\sin(\varphi_0)=y(0)$. Define
$$
\begin{aligned}
\varphi:I&\longrightarrow\mathbb R,\\
t&\longmapsto\varphi(t):=\varphi_0+\int_0^t(xy'-yx')\,d\tau,
\end{aligned}
$$
called the angle function of the closed curve $c$.

The geometric meaning of the angle function is given immediately by the following proposition:

**Lemma 3.2** $\quad$ Let $c:[0,b]\to S^1$ be a closed curve, $\varphi$ its angle function, then
$$
\begin{cases}
\cos(\varphi(t))=x(t),\\
\sin(\varphi(t))=y(t).
\end{cases}
$$

**Proof** $\quad$ Set $F(t):=(x(t)-\cos(\varphi(t)))^2+(y(t)-\sin(\varphi(t)))^2$, then
$$
\begin{aligned}
F&=(x-\cos\varphi)^2+(y-\sin\varphi)^2\\
&=x^2-2x\cos\varphi+\cos^2\varphi+y^2-2y\sin\varphi+\sin^2\varphi.
\end{aligned}
$$
Note that $\varphi'=xy'-yx'$, differentiating $F$ gives
$$
\begin{aligned}
F'&=2xx'-2(x'\cos\varphi-x\varphi'\sin\varphi)-2\varphi'\cos\varphi\sin\varphi\\
&\quad+2yy'-2(y'\sin\varphi+y\varphi'\cos\varphi)+2\varphi'\cos\varphi\sin\varphi\\
&=2(xx'+yy')+2(-x'-y\varphi')\cos\varphi+2(-y'+x\varphi')\sin\varphi.
\end{aligned}
$$
Since $x(t)^2+y(t)^2=1$, we have $2x(t)x'(t)+y(t)y'(t)=0$, i.e., $xx'+yy'=0$. $x,y$ or $x',y'$ obviously cannot be identically zero, the only possibility is that there exists $k(t)$ such that $x'=-ky,\,y'=kx$. Thus
$$
\varphi'(t)=xy'-yx'=k(x^2+y^2)=k(t),
$$
so $x'=-\varphi'y,\,y'=\varphi'x$. Substituting yields
$$
F'\equiv 0.
$$
This shows $F$ is constant. Note that at $t=0$
$$
F=F(0)=(x(0)-\cos(\varphi_0))^2+(y(0)-\sin(\varphi_0))^2=0,
$$
so $F$ is identically zero on $[0,b]$. This proves $\cos(\varphi(t))=x(t),\sin(\varphi(t))=y(t)$. $\square$

**Definition 3.3** $\quad$ Let $c:[0,b]\to S^1$ be a closed curve, $\varphi$ its angle function. Define
$$
n(c):=\frac{1}{2\pi}(\varphi(b)-\varphi(0)),
$$
called the winding number of $c$. Since $c$ is closed, by Lemma 3.2, $n(c)\in\mathbb Z$.

Now we extend the concept of winding number to general closed curves.

**Definition 3.4** $\quad$ Let $p\in\mathbb R^2$, $\gamma:[0,b]\to\mathbb R^2\setminus\{p\}$, set $d(t):=\gamma(t)-p,\,\rho(t):=|d(t)|,\,c(t):=d(t)/\rho(t)$, then $d,\rho,c\in C^1$, and $\gamma(t)=p+\rho(t)c(t)$. Define
$$
n(\gamma,p):=n(c)
$$
as the winding number of $\gamma$ about $p$.

**Proposition 3.5** $\quad$ Let $\gamma(t):=p+\rho(t)c(t)$ be a closed curve $[0,b]\to\mathbb R^2\setminus\{p\}$. Set $(x(t),y(t)):=\gamma(t)-p$, then
$$
n(\gamma,p)=\frac{1}{2\pi}\int_{\gamma}\omega_0,\qquad\omega_0:=-\frac{y}{x^2+y^2}\,dx+\frac{x}{x^2+y^2}\,dy.
$$

**Proof** $\quad$ Note that $c(t)=(x(t)/\rho(t),y(t)/\rho(t))$, thus
$$
\begin{aligned}
n(c)&=\frac{1}{2\pi}\int_0^b\left(\frac{x(t)}{\rho(t)}\left(\frac{y(t)}{\rho(t)}\right)'-\frac{y(t)}{\rho(t)}\left(\frac{x(t)}{\rho(t)}\right)'\right)\,dt\\
&=\frac{1}{2\pi}\int_0^b\left(\frac{x}{\rho}\frac{y'\rho-y\rho'}{\rho^2}-\frac{y}{\rho}\frac{x'\rho-x\rho'}{\rho^2}\right)\,dt=\frac{1}{2\pi}\int_0^{b}\frac{xy'-yx'}{\rho^2}\,dt.
\end{aligned}
$$
On the other hand
$$
\begin{aligned}
\frac{1}{2\pi}\int_{\gamma}\omega_0&=\frac{1}{2\pi}\int_{\gamma}\left(-\frac{y}{x^2+y^2}\,dx+\frac{x}{x^2+y^2}\,dy\right)\\
&=\frac{1}{2\pi}\int_0^b\left(-\frac{yx'}{x^2+y^2}+\frac{xy'}{x^2+y^2}\right)\,dt=\frac{1}{2\pi}\int_0^b\frac{xy'-yx'}{\rho^2}\,dt,\\
\end{aligned}
$$
so $n(\gamma,p)=n(c)=\frac{1}{2\pi}\int_{\gamma}\omega_0$. $\square$

**Theorem 3.6** $\quad$ Let $\gamma_0,\gamma_1:[0,b]\to\mathbb R^2\setminus\{p\}$ be two closed curves. Then $\gamma_0$ and $\gamma_1$ are freely homotopic if and only if $n(\gamma_0,p)=n(\gamma_1,p)$.

**Proof** $\quad$ Take the exterior derivative of the $1$-form $\omega_0$ in Proposition 3.5:
$$
\begin{aligned}
d\omega_0&=d\left(-\frac{y}{x^2+y^2}\,dx+\frac{x}{x^2+y^2}\,dy\right)\\
&=d\left(\frac{-y}{x^2+y^2}\right)\wedge dx+d\left(\frac{x}{x^2+y^2}\right)\wedge dy\\
&=\frac{-x^2+y^2}{(x^2+y^2)^2}\,dy\wedge dx+\frac{-x^2+y^2}{(x^2+y^2)^2}\,dx\wedge dy=0,
\end{aligned}
$$
so $\omega_0$ is closed. Integrals of closed forms along freely homotopic paths are always equal, so by Proposition 3.5, necessity is proven.

Sufficiency: Let $\gamma_j=p+\rho_jc_j$, let $\varphi_j$ be the angle function of $c_j$, set $\varphi(t,\tau):=(1-\tau)\varphi_0(t)+\tau\varphi_1(t)$, $H(t,\tau):=p+(\cos(\varphi(t,\tau)),\sin(\varphi(t,\tau)))$, and set $\widehat{\gamma}_j:=p+c_j$ and
$$
H_j(t,\tau):=p+\frac{\rho_j(t)}{(1-\tau)+\tau\rho_j(t)}c_j(t).
$$
Obviously $H_j$ is a free homotopy from $\gamma_j$ to $\widehat{\gamma}_j$. If $n(\gamma_0,p)=n(\gamma_1,p)$, then $\forall\tau\in[0,1]$ we have
$$
\begin{aligned}
\varphi(b,\tau)-\varphi(0,\tau)&=(1-\tau)\varphi_0(b)+\tau\varphi_1(b)-\big((1-\tau)\varphi_0(0)+\tau\varphi_1(0)\big)\\
&=(1-\tau)(\varphi_0(b)-\varphi_0(0))+\tau(\varphi_1(b)-\varphi_1(0))\\
&=(1-\tau)2\pi n(\gamma_0,p)+\tau 2\pi n(\gamma_1,p)=2\pi n(\gamma_0,p),
\end{aligned}
$$
so $H$ is a free homotopy from $\widehat{\gamma}_0$ to $\widehat{\gamma}_1$. In summary
$$
\gamma_0\simeq\widehat{\gamma}_0\simeq\widehat{\gamma}_1\simeq\gamma_1,
$$
proving sufficiency. $\square$

Generally, let $\gamma:[a,b]\to\mathbb C$ be a closed rectifiable curve, $w\notin\operatorname{im}(\gamma)$, define
$$
\begin{aligned}
u:[a,b]&\longrightarrow S^1=\partial\mathbb D\subset\mathbb C\\
t&\longmapsto\frac{\gamma(t)}{|\gamma(t)-w|},
\end{aligned}
$$
then by Theorem 3.6, if $\gamma$ is once differentiable then $n(\gamma,w)=n(u)$. Now we extend the winding number to rectifiable curves and express it using complex integrals.

**Lemma 3.7 (Special case of Lifting Lemma)** $\quad$ Let $\pi:\mathbb R\to S^1,s\mapsto e^{i2\pi s}$ be the universal cover. Then there exists a lift $\tilde u:[a,b]\to\mathbb R$ of $u$ such that $\pi\circ\tilde{u}=u$.

**Proof** $\quad$ If $u$ is once differentiable then $\tilde u$ can be taken as $\varphi(t)/2\pi$, which also proves existence for piecewise differentiable curves. Since rectifiable curves can be approximated by piecewise differentiable curves, the lemma follows. $\square$

**Definition 3.8** $\quad$ Let $\gamma:[a,b]\to\mathbb C$, $w\notin\operatorname{im}(\gamma)$, $u$ defined as above, $\tilde u$ its lift. Define the winding number of $\gamma$ about $w$ as $n(\gamma,w)=\tilde u(b)-\tilde u(a)$, an extension of Definition 3.3.

**Theorem 3.9** $\quad$ The winding number varies continuously under free homotopy, i.e., let $\gamma_j:[a,b]\to\mathbb C$, $w\notin\operatorname{im}(\gamma_j)$ rectifiable, $H(t,\tau)$ a free homotopy from $\gamma_1$ to $\gamma_2$, then $n(\tau):=n(H(\cdot,\tau),w)$ is continuous. In particular, if $\gamma_1,\gamma_2$ are freely homotopic, then $n(\gamma_1,w)=n(\gamma_2,w)$.

**Proof** $\quad$ Apply the lifting lemma to $H$ to get $\tilde H$, then $n(\tau)=\tilde H(b,\tau)-\tilde H(a,\tau)$. Since $\tilde H$ is continuous, $n(\tau)$ is naturally continuous. Since $n(\tau)$ always takes integer values, we have $n(\gamma_1,w)=n(0)=n(1)=n(\gamma_2,w)$. $\square$

**Theorem 3.10** $\quad$ Let $\gamma:[a,b]\to\mathbb C$ be a rectifiable curve, $w\notin\operatorname{im}(\gamma)$. Then
$$
n(\gamma,w)=\frac{1}{2\pi i}\int_{\gamma}\frac{1}{z-w}\,dz.
$$

**Remark** $\quad$ Rectifiable curves can be uniformly approximated by piecewise differentiable curves, so it suffices to prove the proposition for the $C^1$ case. Two proofs are given here.

**Proof 1** $\quad$ Let $\zeta(t):=\gamma(t)-w=x(t)+iy(t)$, then
$$
\begin{aligned}
\frac{d\zeta}{\zeta}&=\frac{dx+i\,dy}{x+iy}=\frac{(dx+i\,dy)(x-iy)}{(x+iy)(x-iy)}\\
&=\frac{x\,dx+y\,dy}{x^2+y^2}+i\left(\frac{x\,dy-y\,dx}{x^2+y^2}\right)\\
&=\frac{x\,dx+y\,dy}{x^2+y^2}+i\omega_0,
\end{aligned}
$$
hence
$$
\begin{aligned}
\frac{1}{2\pi i}\int_{\gamma}\frac{1}{z-w}\,dz&=\frac{1}{2\pi i}\int_{\gamma}\frac{d\zeta}{\zeta}\\
&=\frac{1}{2\pi i}\int_{\gamma}i\omega_0+\frac{1}{2\pi i}\int_{\gamma}\frac{x\,dx+y\,dy}{x^2+y^2}\\
&=n(\gamma,w)+\frac{1}{2\pi i}\int_{\gamma}\frac{x\,dx+y\,dy}{x^2+y^2}.
\end{aligned}
$$
Note that
$$
\frac{x\,dx+y\,dy}{x^2+y^2}=\frac{1}{2}\frac{d(x^2+y^2)}{x^2+y^2}=\frac{1}{2}d\log(x^2+y^2)
$$
is exact, so its integral around $\gamma$ is zero. Therefore
$$
n(\gamma,w)=\frac{1}{2\pi i}\int_{\gamma}\frac{1}{z-w}\,dz.
$$

**Proof 2** $\quad$ Set
$$
h(t):=\frac{1}{2\pi i}\int_a^t\frac{\gamma'(s)}{\gamma(s)-w}\,ds,\qquad g(t):=e^{-2\pi ih(t)}(\gamma(t)-w),
$$
then
$$
\begin{aligned}
h'(t)&=\frac{1}{2\pi i}\frac{\gamma'(t)}{\gamma(t)-w},\qquad g'(t)\equiv 0,
\end{aligned}
$$
so $g(t)$ is constant; further $g=g(a)=(\gamma(a)-w)$. Thus
$$
e^{2\pi ih(t)}=\frac{\gamma(t)-w}{\gamma(a)-w}.
$$
On the other hand
$$
e^{2\pi i\tilde u(t)}=\frac{\gamma(t)-w}{|\gamma(t)-w|},
$$
set $v(t):=\log|\gamma(t)-w|$, then $v(b)=v(a)$ and
$$
e^{2\pi i\tilde u(t)+v(t)}=\gamma(t)-w,
$$
so there exists a constant $\alpha\in\mathbb C$ such that
$$
2\pi ih(t)=2\pi i\tilde u(t)+v(t)+\alpha,
$$
hence
$$
n(\gamma,w)=\tilde u(b)-\tilde u(a)=h(b)-h(a)=\frac{1}{2\pi i}\int_{\gamma}\frac{1}{z-w}\,dz.
$$
$\square$

# Cauchy Integral Formula

This section proves that holomorphic functions are smooth, and along the way yields important theorems such as the Fundamental Theorem of Algebra.

## Basic Statement

Let $f(z)$ be holomorphic on an open disk, $\gamma$ a closed curve inside it. For a point $a\in\Delta$ outside $\gamma$, consider the function
$$
F(z):=\frac{f(z)-f(a)}{z-a},
$$
this function is holomorphic on $D\setminus\{a\}$, so as $z\to a$, $(z-a)F(z)=f(z)-f(a)\to 0$. Then applying the Cauchy integral theorem gives
$$
\int_{\gamma}\frac{f(z)-f(a)}{z-a}\,dz=0,
$$
i.e.,
$$
\int_{\gamma}\frac{f(z)}{z-a}\,dz=f(a)\int_{\gamma}\frac{dz}{z-a}.
$$
Note that the integral on the right is precisely $2\pi i\cdot n(\gamma,a)$. Generally, we have the following theorem.

**Theorem 4.1** $\quad$ Let $f$ be holomorphic on an open disk $D$, $\gamma$ a closed curve in $D$, $a\in\mathbb C\setminus\operatorname{im}(\gamma)$, then
$$
n(\gamma,a)f(a)=\frac{1}{2\pi i}\int_{\gamma}\frac{f(z)}{z-a}\,dz.
$$

**Proof** $\quad$ The case $a\in D$ has been argued above. If $a\notin D$, then the winding number $n(\gamma,a)$ and the integral on the right are also zero, so the formula still holds. $\square$

For a fixed closed curve $\gamma$, for those points $z$ with winding number $n(\gamma,z)=1$, we have
$$
f(z)=\frac{1}{2\pi i}\int_{\gamma}\frac{f(w)}{w-z}\,dw,\qquad n(\gamma,z)=1.
$$
This is the Cauchy integral formula. In particular, for an open disk $D\subset\mathbb C$, let $f:\overline{D}\to\mathbb C$ be holomorphic, then taking a slightly larger open disk on which $f$ is also holomorphic yields
$$
f(z)=\frac{1}{2\pi i}\int_{\partial D}\frac{f(w)}{w-z}\,dw.
$$

## Higher Order Derivatives

**Lemma 4.2** $\quad$ Let $\phi(w)$ be a continuous function on an arc $\gamma$, then the function
$$
\Phi_n(z):=\int_{\gamma}\frac{\phi(w)}{(w-z)^n}\,dw
$$
is analytic on $\mathbb C\setminus\operatorname{im}(\gamma)$, and $\Phi_n'(z)=n\Phi_{n+1}(z)$.

**Proof** $\quad$ First prove $\Phi_1$ is continuous. Let $z_0$ be a point not on $\gamma$, take $B(z_0,\delta)$ not intersecting $\gamma$, then for all $z\in B(z_0,\delta/2),\,w\in\gamma$, we have $|w-z|>\delta/2$. Thus from
$$
\frac{1}{w-z}-\frac{1}{w-z_0}=\frac{z-z_0}{(w-z)(w-z_0)}
$$
we get
$$
\begin{aligned}
|\Phi_1(z)-\Phi_1(z_0)|&=\left|(z-z_0)\int_{\gamma}\frac{\phi(w)\,dw}{(w-z)(w-z_0)}\right|\\
&<\left|z-z_0\right|\frac{4}{\delta^2}\int_{\gamma}|\phi(w)|\,|dw|=:C\left|z-z_0\right|,
\end{aligned}
$$
where $C$ is a constant. This proves $\Phi_1$ is continuous at any $z_0$ not on $\gamma$. Generally, from
$$
\frac{1}{(w-z)^n}-\frac{1}{(w-z_0)^n}=\frac{1}{(w-z)^{n-1}(w-z_0)}+\frac{(z-z_0)}{(w-z)^n(w-z_0)}-\frac{1}{(w-z_0)^n}
$$
we get
$$
\begin{aligned}
\Phi_n(z)-\Phi_n(z_0)&=\left[\int_{\gamma}\frac{\phi(w)\,dw}{(w-z)^{n-1}(w-z_0)}-\int_{\gamma}\frac{\phi(w)\,dw}{(w-z_0)^n}\right]\\
&\quad+(z-z_0)\int_{\gamma}\frac{\phi(w)\,dw}{(w-z)^n(w-z_0)}.
\end{aligned}
$$
Now prove by induction that $\Phi_n$ is continuous. Assume the proposition holds for $n-1$, then taking $\psi:=\phi(w)/(w-z_0)$ and applying the induction hypothesis shows the function
$$
\Psi_{n-1}(z_0;z):=\int_{\gamma}\frac{\phi(w)\,dw}{(w-z)^{n-1}(w-z_0)}
$$
is continuous, so as $z\to z_0$,
$$
\int_{\gamma}\frac{\phi(w)\,dw}{(w-z)^{n-1}(w-z_0)}-\int_{\gamma}\frac{\phi(w)\,dw}{(w-z_0)^n}\;\to\;\int_{\gamma}\frac{\phi(w)\,dw}{(w-z_0)^n}-\int_{\gamma}\frac{\phi(w)\,dw}{(w-z_0)^n}=0,
$$
and the remaining term can be shown to tend to zero as $z\to z_0$ by taking $\delta/2$ similarly. This proves $F_n$ is continuous.

For $n=1$, note that
$$
\frac{\Phi_1(z)-\Phi_1(z_0)}{z-z_0}=\int_{\gamma}\frac{\phi(w)\,dw}{(w-z)(w-z_0)},
$$
we have already shown the integral on the right is continuous in $z$, so as $z\to z_0$ we get
$$
\Phi_1'(z_0)=\int_{\gamma}\frac{\phi(w)\,dw}{(w-z_0)^2}=F_2(z_0),\qquad\forall z_0\notin\operatorname{im}(\gamma).
$$
Now prove by induction that $\Phi_n'(z)=n\Phi_{n+1}(z)$. Assume the proposition holds for $n-1$, then
$$
\begin{aligned}
\frac{\Phi_n(z)-\Phi_n(z_0)}{z-z_0}&=\frac{1}{z-z_0}\left[\int_{\gamma}\frac{\phi(w)\,dw}{(w-z)^{n-1}(w-z_0)}-\int_{\gamma}\frac{\phi(w)\,dw}{(w-z_0)^n}\right]\\
&\quad+\int_{\gamma}\frac{\phi(w)\,dw}{(w-z)^n(w-z_0)}\\
&=\frac{\Psi_{n-1}(z_0;z)-\Psi_{n-1}(z_0;z_0)}{z-z_0}+\int_{\gamma}\frac{\phi(w)\,dw}{(w-z)^n(w-z_0)},
\end{aligned}
$$
taking $z\to z_0$ and using the induction hypothesis gives
$$
\Phi_n'(z_0)=(n-1)\Psi_{n}(z_0;z_0)+\Phi_{n+1}(z_0).
$$
But $\Psi_k(z_0;z_0)=\Phi_{k+1}(z_0)$, so
$$
\Phi_n'(z_0)=n\Phi_{n+1}(z_0),\qquad\forall z_0\notin\operatorname{im}(\gamma).
$$
$\square$

**Proposition 4.3** $\quad$ Let $D\subset\mathbb C$ be an open disk, $f$ holomorphic on $\overline D$, then for any $z\in\mathbb D$, $f$ is $C^{\infty}$ at point $z$, and
$$
f^{(n)}(z)=\frac{n!}{2\pi i}\int_{\partial D}\frac{f(\zeta)\,d\zeta}{(\zeta-z)^{n+1}}.
$$

**Proof** $\quad$ Apply the Cauchy integral theorem. $\square$

# General Form of Cauchy Integral Theorem

**Definition 5.1 (Chain, Cycle)** $\quad$ Let $U\subset\mathbb C$ be an open set, $\mathcal R$ the set of all rectifiable curves on $U$, denote $C_0(U):=\mathbb Z^{\oplus U},C_1(U):=\mathbb Z^{\oplus\mathcal R}$, abbreviated as $C_0,C_1$. A 1-chain is a formal sum $\gamma=\sum_{j=1}^na_j\gamma_j\in C_1$. Denote $\operatorname{im}(\gamma):=\bigcup_1^n\operatorname{im}(\gamma_j)$. For any $f\in C(\operatorname{im}(\gamma))$, define
$$
\int_{\gamma}f\,dz:=\sum_{j=1}^na_j\int_{\gamma_j}f\,dz.
$$
Let $\iota:U\to C_0$ be the canonical inclusion map. Define
$$
\begin{aligned}
\partial:C_1&\longrightarrow C_0\\
\sum_1^na_j\gamma_j&\longmapsto\sum_1^na_j(\iota(\gamma_j(\beta_j))-\iota(\gamma_j(\alpha_j))),
\end{aligned}
$$
where $\gamma_j:[\alpha_j,\beta_j]\to\mathbb C$. Elements in $\ker(\partial)$ are called cycles. For a cycle $\gamma$ and $z\notin\operatorname{im}(\gamma)$, define
$$
n(\gamma,z):=\frac{1}{2\pi i}\int_{\gamma}\frac{dw}{w-z}.
$$

**Definition 5.2** $\quad$ Let $U\subset\mathbb C$ be an open set, $\gamma\in C_1(U)$ a cycle. $\gamma$ is said to be homologous to $0$ in $U$ if $\forall z\in\mathbb C\setminus U$, $n(\gamma,z)=0$.

In the following, we may assume the cycle $\gamma$ is a sum of closed curves.

**Lemma 5.3** $\quad$ Let $U\subset\mathbb C$ be a simply connected open set, then any cycle on $U$ is homologous to $0$.

**Proof** $\quad$ Each $\gamma_j$ is homotopic to a point, and homotopy preserves winding number. $\square$

**Theorem 5.4 (General Form of Cauchy Integral Theorem)** $\quad$ Let $U\subset\mathbb C$ be an open set, $\gamma$ a cycle on $U$ homologous to $0$. Let $f$ be a holomorphic function on $U$. Then
$$
\int_{\gamma}f\,dz=0.
$$

**Proof** $\quad$ First assume $U$ is bounded. For any $\delta>0$, take $n\in\mathbb Z$ such that $2^{-n}<\delta$, consider the family of closed squares $\mathcal Q_n$ of side length $2^{-n}$ in the complex plane. Let $\{Q_j\}_{j\in J}\subset\mathcal Q_n$ be those closed squares entirely contained in $U$, since $U$ is bounded, it is indeed a finite set. Choose $\delta$ sufficiently small so that $\{Q_j\}$ is nonempty. Consider the cycle
$$
\Gamma_{n}:=\sum_{j\in J}\partial Q_j.\\
$$
Set
$$
U_n:=\operatorname{int}\Bigl(\bigcup_{j\in J}Q_j\Bigr),\qquad\Gamma_n':=\partial U_n,\qquad V_n:=\bigcup_{j\in J}(\operatorname{int}Q_j).\\
$$
Let $\gamma$ be a cycle on $U$ homologous to $0$. Choose $\delta$ sufficiently small such that $\operatorname{im}(\gamma)\subset U_n$. Let $\xi\in U\setminus U_n$, then there exists $Q\in\mathcal Q\setminus\{Q_j\}$ such that $\xi\in Q$ and $Q\notin U$. Pick $\xi_0\in Q\setminus U$. Since $\gamma$ is homologous to $0$, $n(\gamma,\xi_0)=0$. We can connect $\xi$ and $\xi_0$ by a straight line $L\subset Q$ such that $L\cap U_{n}=\varnothing$, then $L\subset\mathbb C\setminus\operatorname{im}(\gamma)$, meaning $\xi_0,\xi$ are in the same connected component of $\mathbb C\setminus\operatorname{im}(\gamma)$. Since the winding number is continuous in the point, $n(\gamma,\xi)=n(\gamma,\xi_0)=0$. Since $\Gamma_n'\subset U\setminus U_n$, for any $\xi\in\Gamma_n'$, $n(\gamma,\xi)=0$.

Let $z\in V_n$, then there exists a unique $j_0\in J$ such that $z\in Q_{j_0}$. By the Cauchy integral formula for rectangles, we have
$$
\frac{1}{2\pi i}\int_{\Gamma_{n}}\frac{f(w)}{w-z}\,dw=\frac{1}{2\pi i}\int_{\partial Q_{j_0}}\frac{f(w)}{w-z}\,dw=f(z).\\
$$
It is easy to see that the integral along $\Gamma_{n}$ always equals the integral along $\Gamma_n'$, so
$$\frac{1}{2\pi i}\int_{\Gamma_n'}\frac{f(w)}{w-z}\,dw=f(z).\\
$$
The above equality holds on $V_n$. Since both sides are continuous, it holds for all $z\in U_n$. In particular, we have
$$
\int_{\gamma}f\,dz=\int_{\gamma}\left(\frac{1}{2\pi i}\int_{\Gamma_n}\frac{f(w)}{w-z}\,dw\right)\,dz.\\
$$
Since $\Gamma_n'\cap\gamma=\varnothing$, the integrand is continuous in both variables, so
$$
\begin{aligned}
\int_{\gamma}f\,dz&=\int_{\Gamma_n'}\left(\frac{1}{2\pi i}\int_{\gamma}\frac{f(w)}{w-z}\,dz\right)\,dw\\
&=\int_{\Gamma_{n}'}(-n(\gamma,w)f(w))\,dw=0.
\end{aligned}\\
$$
If $U$ is unbounded, take $R$ sufficiently large such that $\operatorname{im}(\gamma)\subset D(0,R)$ and set $U':=U\cap D(0,R)$.
$\square$

**Corollary 5.5** $\quad$ Let $U\subset\mathbb C$ be a simply connected open set, $\gamma$ a cycle in $U$, $f$ a holomorphic function on $U$. Then
$$
\int_{\gamma}f\,dz=0.\\
$$

**Theorem 5.6 (General Form of Cauchy Integral Formula)** $\quad$ Let $U\subset\mathbb C$ be an open set, $\gamma$ a cycle on $U$ homologous to $0$. Let $f$ be a holomorphic function on $U$, $a\in U\setminus\operatorname{im}(\gamma)$. Then
$$
\frac{1}{2\pi i}\int_{\gamma}\frac{f(z)}{z-a}\,dz=n(\gamma,a)f(a).\\
$$

**Proof** $\quad$ Set
$$
g(z):=\frac{f(z)-f(a)}{z-a},\\
$$
then $g$ is holomorphic on $U$, so $\int_{\gamma}g\,dz=0$. Hence
$$
\frac{1}{2\pi i}\int_{\gamma}\frac{f(z)}{z-a}\,dz=\frac{1}{2\pi i}\int_{\gamma}\frac{f(a)\,dz}{z-a}=n(\gamma,a)f(a).\\
$$
$\square$

# Analytic Functions

## Analyticity, Taylor Expansion

**Theorem 6.1** $\quad$ Let $\gamma$ be a rectifiable curve in $\mathbb C$, $\phi:\operatorname{im}(\gamma)\to\mathbb C$ a continuous function. For $z\in\mathbb C\setminus\operatorname{im}(\gamma)$, define
$$
f(z):=\int_{\gamma}\frac{\phi(w)}{w-z}\,dw,\\
$$
then for any $z_0\in\mathbb C\setminus\operatorname{im}(\gamma)$, set $r:=\operatorname{dist}(z_0,\operatorname{im}(\gamma))$, $f$ can be expanded as a power series in $B(z_0,r)$:
$$
f(z)=\sum_{n=0}^{\infty}\left(\int_{\gamma}\frac{\phi(w)\,dw}{(w-z_0)^{n+1}}\right)(z-z_0)^n.\\
$$

**Proof** $\quad$ Take $w\in\operatorname{im}(\gamma)$, note that
$$
\frac{\phi(w)}{w-z}=\frac{\phi(w)}{w-z_0}\frac{w-z_0}{w-z}=\frac{\phi(w)}{w-z_0}\frac{1}{1-(z-z_0)/(w-z_0)},\\
$$
thus for $\left|\frac{z-z_0}{w-z_0}\right|\leq 1$, in particular for $z\in B(z_0,r)$, we have
$$
\frac{\phi(w)}{w-z}=\sum_{n=0}^{\infty}\frac{\phi(w)}{(w-z_0)^{n+1}}(z-z_0)^n.\\
$$
Set $g_n(w):=\sum_{j=0}^{n}\phi(w)(w-z_0)^{-j-1}(z-z_0)^j$, we will show $g_n\to\phi(w)/(w-z)$ uniformly on $\operatorname{im}(\gamma)$. Indeed, let $M:=\|\phi\|_u$ and $r':=|z-z_0|<r$, then
$$
\begin{aligned}
\left|g_n(w)-\frac{\phi(w)}{w-z}\right|&=\left|\sum_{j=n}^{\infty}\frac{\phi(w)}{(w-z_0)^{j+1}}(z-z_0)^j\right|\\
&\leq M\sum_{j=n}^{\infty}\left|\frac{(z-z_0)^j}{(w-z_0)^{j+1}}\right|\leq M\sum_{j=n}^{\infty}\left(\frac{r'}{r}\right)^j\frac{1}{r}=\frac{M}{r-r'}\left(\frac{r'}{r}\right)^n,
\end{aligned}\\
$$
so $\|g_n-\phi/(w-z)\|_u\to 0$, proving uniform convergence. Hence
$$
\int_{\gamma}\frac{\phi(w)}{w-z}\,dw=\sum_{n=0}^{\infty}\left(\int_{\gamma}\frac{\phi(w)\,dw}{(w-z_0)^{n+1}}\right)(z-z_0)^n.\\
$$
$\square$

**Corollary 6.2 (Taylor Expansion)** $\quad$ Let $D:=D(z_0,r)\subset C$ be a disk, $f:\overline D\to\mathbb C$ holomorphic, then $f$ equals a power series on $D$, in particular
$$
f(z)=\frac{1}{2\pi i}\sum_{n=0}^{\infty}\left(\int_{\partial D}\frac{f(w)\,dw}{(w-z_0)^{n+1}}\right)(z-z_0)^n.\\
$$

Comparing the coefficients from Theorem 6.1 and the Cauchy integral formula with the Taylor series also yields the derivative formula
$$
f^{(n)}(z)=\frac{n!}{2\pi i}\int_{\partial D}\frac{f(\zeta)\,d\zeta}{(\zeta-z)^{n+1}},\\
$$
and this method is simpler than the one we used in Section 4.

**Theorem 6.3 (Morera)** $\quad$ Let $U\subset\mathbb C$ be an open set, $f:U\to\mathbb C$ continuous. If for every rectifiable closed curve $\gamma$ in $U$, $\int_{\gamma}f\,dz=0$, then $f$ is holomorphic.

**Proof** $\quad$ The condition implies $f\,dz$ is exact. $\square$

**Theorem 6.4** $\quad$ Let $U\subset\mathbb C$ be an open set, $\{f_n\}$ a sequence of holomorphic functions on $U$, converging uniformly to $f$ on every compact subset of $U$. Then $f$ is also a holomorphic function on $U$.

**Proof** $\quad$ For any $\overline D\subset U$, for $z\in D$, $f_n(z)=\frac{1}{2\pi i}\int_{\partial D}\frac{f_n(w)}{w-z}\,dw$, letting $n\to\infty$ gives $f(z)=\frac{1}{2\pi i}\int_{\partial D}\frac{f(w)}{w-z}\,dw$. By Theorem 6.1, $f$ is holomorphic on $D$. Thus $f$ is holomorphic on the entire $U$. $\square$

## Cauchy Estimates, Liouville's Theorem, Fundamental Theorem of Algebra

**Theorem 6.5 (Cauchy's estimate)** $\quad$ Let $D:=B(z_0,r)\subset\mathbb C$ be a disk, $f:\overline{D}\to\mathbb C$ holomorphic. Set $M:=\max_{z\in\partial D}|f(z)|$. Then
$$
|f^{(n)}(z_0)|\leq Mn!r^{-n}.\\
$$

**Proof** $\quad$
$$
\begin{aligned}
|f^{(n)}(z_0)|&=\left|\frac{n!}{2\pi i}\int_{\partial D}\frac{f(\zeta)\,d\zeta}{(\zeta-z)^{n+1}}\right|\leq\left|\int_{\partial D}Mr^{-n-1}\,ds\right|=Mn!r^{-n}.
\end{aligned}\\
$$
$\square$

**Theorem 6.6 (Liouville)** $\quad$ Let $f:\mathbb C\to\mathbb C$ be a bounded holomorphic function, then $f$ is constant.

**Proof** $\quad$ Suppose $|f|\leq M$, let $z_0\in\mathbb C$, for any $R\in\mathbb R$ apply Cauchy's estimate on $B(z_0,R)$ to get $|f'(z_0)|\leq MR^{-n}$, since $R$ is arbitrary, $f'(z_0)=0$, so $f'\equiv 0$. Hence $f$ is constant. $\square$

**Definition 6.7** $\quad$ If a function $f$ is holomorphic on the entire complex plane, it is called an entire function.

**Corollary 6.8** $\quad$ If the real or imaginary part of an entire function $f$ is bounded, then $f$ is constant.

**Proof** $\quad$ Let $f=u+iv$. Suppose $u$ is bounded. Consider $g:=\exp(f)$, then $|g|=|e^u|$. Since $u$ is bounded, so is $g$, thus by Liouville's theorem $g=\exp(f)$ is constant, so $f$ is constant. $\square$

**Theorem 6.9 (Fundamental Theorem of Algebra)** $\quad$ $\mathbb C$ is algebraically closed: Let $f\in\mathbb C[X]$, $\deg f\geq 1$. Then $f$ has at least one root in $\mathbb C$.

**Proof** $\quad$ Assume $f$ has no root in $\mathbb C$, then $1/f$ is holomorphic on all of $\mathbb C$. Since $\deg\geq 1$, as $|z|\to\infty$, $|f|\to\infty$, so $1/f\to 0$, hence $1/f$ is bounded. By Liouville's theorem, $1/f$ is constant, so $f$ is also constant, contradicting $\deg f\geq 1$. Therefore $f$ has at least one root in $\mathbb C$. $\square$

## Zeros and Uniqueness

**Lemma 6.10** $\quad$ Let $U\subset\mathbb C$ be a connected open set, $f$ a holomorphic function on $U$, $z_0\in U$. Suppose for all $n\geq 1$, $f^{(n)}(z_0)=0$. Then $f\equiv f(z_0)$ on $U$.

**Proof** $\quad$ Set
$$
V:=\{z\in U:f(z)=f(z_0),\,f^{(n)}(z)=0,\,\forall n\geq 1\}.\\
$$
Since $z_0\in V$, $V$ is nonempty. Clearly $V$ is closed. Let $z\in V$, then there exists $\overline{D(z,\epsilon)}\subset U$ such that $f$ is holomorphic on $\overline{D(z,\epsilon)}$, so $f$ can be expanded as a power series in $D$ and all coefficients of nonzero terms are zero, hence $f$ is identically $f(z_0)$ on $D$, so all derivatives of $f$ are zero on $D$, thus $D\subset V$. This shows $V$ is open. Since $U$ is connected, $V=U$. $\square$

**Lemma 6.11** $\quad$ Zeros of holomorphic functions are isolated: Let $U\subset\mathbb C$ be a connected open set, $f$ a non-constant holomorphic function on $U$, $z_0\in U$, then there exists $r>0$ such that $z_0$ is the unique zero of $f-f(z_0)$ in $D(z_0,r)$.

**Proof** $\quad$ By Lemma 6.10, there exist $r_0>0$ and $m\in\mathbb N_{\geq 1}$ such that on $D':=D(z_0,r_0)$
$$
f(z)=f(z_0)+a_m(z-z_0)^m+\cdots,\quad a_m\neq 0,\\
$$
then on $D'$, $f-f(z_0)=(z-z_0)^mg(z)$, where the holomorphic function $g$ satisfies $g(z_0)=a_m\geq 0$. Since $g$ is continuous, there exists $0<r<r_0$ such that on $D:=D(z_0,r)$, $g(z)\neq 0$. Thus $z_0$ is the unique zero of $f-f(z_0)$ on $D$. $\square$

**Corollary 6.12** $\quad$ Let $U\subset\mathbb C$ be a connected open set, $f,g$ holomorphic functions on $U$. If there exists a sequence of points $\{z_n\}$ such that $z_n\to z\in U$ and $f(z_j)=g(z_j),\quad\forall j\in\mathbb N$, then $f\equiv g$ on $U$.

**Proof** $\quad$ By continuity $f(z_0)=g(z_0)$, then apply Lemma 6.11. $\square$

## Logarithm and Taking Roots

**Theorem 6.13 (Logarithm)** $\quad$ Let $U\subset\mathbb C$ be a simply connected open set, $f$ a holomorphic function on $U$, with $f\neq 0$ pointwise. Then there exists a holomorphic function $g$ on $U$ such that $e^g=f$.

**Proof** $\quad$ $f'/f$ is holomorphic on $U$. For $a\in U$, choose $\alpha\in\mathbb C$ such that $e^{\alpha}=f(a)$. For any $z\in U$, let $\gamma$ be a rectifiable curve connecting $a$ and $z$, define
$$
g(z):=\alpha+\int_{\gamma}\frac{f'}{f}\,dz,\\
$$
then $g$ is independent of the choice of $\gamma$, so $g$ is holomorphic and $g'=f'/f$. Set $h:=\exp(-g)f$, then $h(a)=1$. Further
$$
h'(z)=-e^{-g(z)}g'(z)f(z)+f'(z)e^{-g(z)}=0,\qquad\forall z\in U.\\
$$
Thus $h\equiv 1$. Therefore $e^g=f$ on $U$. $\square$

**Theorem 6.14 (Taking Roots)** $\quad$ Let $U\subset\mathbb C$ be a simply connected open set, $f$ a holomorphic function on $U$, with $f\neq 0$ pointwise. Then there exists a holomorphic function $g$ on $U$ such that $g^n=f$.

**Proof** $\quad$ There exists a holomorphic function $h$ such that $e^h=f$. Set $g:=e^{h/n}$, then $g^n=f$. $\square$

## Open Mapping Theorem, Biholomorphic Mappings, Local Normal Form

**Definition 6.15 (Biholomorphic function)** $\quad$ Let $U,V$ be two open sets in $\mathbb C$. A holomorphic function $f:U\to V$ is called biholomorphic if $f$ is bijective and $f^{-1}V\to U$ is holomorphic.

By the inverse function theorem, if $f:U\to\mathbb C$ is holomorphic, $z_0\in U$, and $f'(z_0)\neq 0$, then $f$ is locally biholomorphic at $z_0$.

**Theorem 6.16 (Local Normal Form of Holomorphic Functions)** $\quad$ Let $f$ be holomorphic on an open set $U\subset\mathbb C$, $z_0\in U$, $f^{(m)}(z_0)\neq 0$ and $\forall j\leq m-1,\,f^{(j)}(z_0)=0$. Then there exist $D:=D(z_0,r)\subset U$ and a biholomorphic function $h$ on $D$ such that on $D$, $f-f(z_0)=h^m$.

**Proof** $\quad$ Locally on $D':=D'(z_0,r)$ we can write $f-f(z_0)=(z-z_0)^mg(z)$, where $g$ is holomorphic, $g(z_0)=a_m\neq 0$. Let $\tilde h$ be a holomorphic function on $D'$ satisfying $\tilde h^m=g$, $h:=(z-z_0)\tilde h$, then $h$ is holomorphic on $D'$ and $f-f(z_0)=h^m$. Note that $h'(z_0)=\tilde h(z_0)\neq 0$, so by the inverse function theorem, there exists $D\subset D'$ such that $h$ is biholomorphic on $D$. $\square$

**Lemma 6.17** $\quad$ $g_m(z):\mathbb C\to\mathbb C\,,z\mapsto z^m$ is a proper and open map; further, if $z\neq 0$, then $g_m^{-1}(z)$ contains exactly $m$ points.

**Proof** $\quad$ It is easy to see $g_m(z)$ is proper. Let $z=re^{i\theta}$, consider the equation $w^n=z$. Let $w=\rho e^{i\psi}$, then $\rho^m=r$, $m\psi=\theta+2k\pi$. The real number $\rho=r^{1/m}$ is unique, while $\phi$ has exactly $m$ solutions modulo $2\pi$. This proves $g_m^{-1}(z)$ has $m$ points. $\square$

**Theorem 6.18 (Open Mapping Theorem)** $\quad$ Let $f$ be a non-constant holomorphic function on a connected open set $U\subset\mathbb C$, then $f$ is an open map.

**Proof** $\quad$ It suffices to show that for any $z_0\in U$, there exists $r>0$ such that for any $r'<r$, $D'=D(z_0,r')$, $f(D')$ is open. Indeed, by Theorem 6.14, there exist $m\geq 1$, a biholomorphic function $h$, and a disk $D=:D(z_0,r)$ such that on $D$, $f-f(z_0)=h^m$. By Lemma 6.15, $z\mapsto z^m$ is open, so such $D$ is as desired. $\square$

**Theorem 6.19** $\quad$ Let $f$ be a holomorphic function on $\mathbb U$. If $f$ is injective, then $f:U\to f(U)$ is biholomorphic.

**Proof** $\quad$ It suffices to prove the proposition for each connected component of $U$. Below assume $U$ is connected. $f(U)$ is open. $\forall z_0\in U$, $f'(z_0)\neq 0$, otherwise by Theorem 6.14, $f$ is at least $m\,(m\geq 2)$-to-one around $z_0$, so by the inverse function theorem, $f^{-1}$ is locally holomorphic at $f(z_0)$. Since $z_0$ is arbitrary, $f$ is biholomorphic. $\square$

## Maximum Modulus Principle

**Theorem 6.20 (Maximum Modulus Principle)** $\quad$ Let $U\subset\mathbb C$ be a connected open set, $f$ a non-constant holomorphic function on $U$. Then there does not exist $z_0\in U$ such that $|f(z_0)|=\sup_{z\in U}|f(z)|$.

**Proof** $\quad$ This is because $f(U)$ is open. $\square$

Considering neighborhoods $U'\subset U$ for any $z_0\in U$ in the maximum modulus principle, it further follows that $f$ cannot attain a local maximum at any $z_0\in U$. Similarly, we have the dual "minimum modulus principle".

**Proposition 6.21** $\quad$ Let $U\subset\mathbb C$ be a connected open set, $f$ a non-constant holomorphic function on $U$, with $f\neq 0$ pointwise. Then there does not exist $z_0\in U$ such that $|f(z_0)|=\inf_{z\in U}|f(z)|$.

**Corollary 6.22** $\quad$ Let $U\subset\mathbb C$ be a bounded connected open set, $f$ a non-constant holomorphic function on $\overline U$. Then the maximum of $|f|$ on $\overline U$ is attained on $\partial U$. If further $f$ is nonvanishing pointwise, then the minimum of $|f|$ is attained on $\partial U$.

# Laurent Series

Let $z_0\in\mathbb C$. A Laurent series centered at $z_0$ is a series of the form:
$$
\sum_{n=1}^{\infty}b_n(z-z_0)^{-n}+\sum_{n=0}^{\infty}a_n(z-z_0)^n,
$$
where $a_n,b_n\in\mathbb C$. $\sum_{n=1}^{\infty}b_n(z-z_0)^{-n}$ is called the principal part, $\sum_{n=0}^{\infty}a_n(z-z_0)^n$ the regular part.

Let $f:=\sum_{n=1}^{\infty}b_n(z-z_0)^{-n}+\sum_{n=0}^{\infty}a_n(z-z_0)^n$, $R$ the radius of convergence of its regular part. For the principal part, we can also define a "radius of divergence" $r$. Indeed, set $S:=\sum_{j=0}^{\infty}b_jz^j$, consider the radius of convergence $R'$ of $S$, then the principal part converges if and only if $S\big((z-z_0)^{-1}\big)$ converges. Thus if $|(z-z_0)^{-1}|>R'$ i.e., $|z-z_0|<1/R'$, the principal part does not converge, conversely, if $|z-z_0|>1/R'$, the principal part converges. So we can set $r=1/R'$. Define the open annulus
$$
D(z_0,r,R):=\{z\in\mathbb C:r<|z-z_0|<R\},
$$
then $f$ converges uniformly on compact subsets of $D(z_0,r,R)$. Since each partial sum is holomorphic, $f$ is holomorphic on $D(z_0,r,R)$.

**Lemma 7.1** $\quad$ Let $g$ be a holomorphic function on $D(z_0,r,R)$, $r<r_1<r_2<R$. Then
$$
\int_{\partial D(z_0,r_1)}g(z)\,dz=\int_{\partial D(z_0,r_2)}g(z)\,dz.
$$

**Proof** $\quad$ Set $\gamma:=\partial D(z_0,r_1)-\partial D(z_0,r_2)$. Since $\partial D(z_0,r_j)$ are homotopic, $\gamma$ is homologous to $0$ in $D(z_0,r,R)$, so by the general form of Cauchy's integral theorem, $\int_{\gamma}g\,dz=0$, proving the lemma. $\square$

**Theorem 7.2** $\quad$ Let $f=\sum_{n=-\infty}^{\infty}a_n(z-z_0)^n$ be a Laurent series convergent on $D(z_0,r,R)$, $r<\rho<R$. Then
$$
a_n=\frac{1}{2\pi i}\int_{\partial D(z_0,\rho)}\frac{f(w)}{(w-z_0)^{n+1}}\,dw.
$$

**Proof** $\quad$ By uniform convergence,
$$
\int_{\partial D(z_0,\rho)}\frac{f(w)}{(w-z_0)^{n+1}}\,dw=\sum_{k=-\infty}^{\infty}\int_{\partial D(z_0,\rho)}\frac{a_k\,dw}{(w-z_0)^{n+1-k}}.
$$
If $k\neq n$ then $a_k(w-z_0)^{k-n-1}$ is exact, its integral is zero. So
$$
\begin{aligned}
\int_{\partial D(z_0,\rho)}\frac{f(w)}{(w-z_0)^{n+1}}\,dw=\int_{\partial D(z_0,\rho)}\frac{a_n\,dw}{w-z_0}=2\pi i\cdot a_n.
\end{aligned}
$$
$\square$

**Theorem 7.3 (Laurent Expansion)** $\quad$ Let $f$ be a holomorphic function on $D(z_0,r,R)$, then $f$ can be represented as a Laurent series centered at $z_0$ on $D(z_0,r,R)$.

**Proof** $\quad$ By Theorem 7.2, the coefficients of the Laurent series, if they exist, are unique. It suffices to show that $f$ can be expanded as a Laurent series on each $D(z_0,r',R'),\,r<r'<R'<R$. For each $z\in D(z_0,r',R')$, $n(\partial D(z_0,R')-\partial D(z_0,r'),z)\equiv 1$. Then by the general form of Cauchy's integral theorem,
$$
f(z)=\frac{1}{2\pi i}\int_{\partial D(z_0,R')}\frac{f(w)}{w-z}\,dw-\frac{1}{2\pi i}\int_{\partial D(z_0,r')}\frac{f(w)}{w-z}\,dw,
$$
for fixed $z\in D(z_0,r',R')$, consider the series
$$
\frac{w-z_0}{w-z}=\sum_{n=0}^{\infty}\left(\frac{z-z_0}{w-z_0}\right)^n,
$$
it converges for $w\in D(z_0,R')$, so
$$
\int_{\partial D(z_0,R')}\frac{f(w)}{w-z}\,dw=\sum_{n=0}^{\infty}\left(\int_{\partial D(z_0,R')}\frac{f(w)\,dw}{(w-z_0)^{n+1}}\right)(z-z_0)^n.
$$
For fixed $z\in D(z_0,r',R')$, consider the series
$$
\frac{z-z_0}{z-w}=\sum_{n=0}^{\infty}\left(\frac{w-z_0}{z-z_0}\right)^n,
$$
it converges for $w\in D(z_0,r')$, so
$$
\begin{aligned}
\int_{\partial D(z_0,r')}\frac{f(w)}{w-z}\,dw&=-\sum_{n=0}^{\infty}\left(\int_{\partial D(z_0,r')}(w-z_0)^nf(w)\,dw\right)(z-z_0)^{-n-1}\\
&=-\sum_{n=-1}^{-\infty}\left(\int_{\partial D(z_0,r')}\frac{f(w)\,dw}{(w-z_0)^{n+1}}\right)(z-z_0)^n.
\end{aligned}
$$
Combining these two parts proves the proposition. $\square$

From Theorem 7.2 and Theorem 7.3, if $f$ is holomorphic on $D(z_0,r,R)$, then $f$ can be expanded as
$$
f(z)=\frac{1}{2\pi i}\sum_{n=-\infty}^{\infty}\left(\int_{\partial D(z_0,\rho)}\frac{f(\zeta)\,d\zeta}{(\zeta-z_0)^{n+1}}\right)(z-z_0)^n.
$$
