---
title: Note on Complex Analysis
published: 2025-10-16
description: 'Very good notes on introductory complex analysis.'
image: ''
tags: [Mathematic,Complex]
category: 'Mathematic'
draft: false 
lang: ''
pinned: true
---

## Preface
This article requires knowledge of differentiation. If you don't know how to differentiate, you can refer to [this article](https://www.luogu.com.cn/article/leem697k) (Permission has been obtained from the author of that article).  
This article also requires knowledge of integration. If you don't know integration, you can refer to... I haven't found any quick-start articles; you'll have to go study calculus!

This article was originally intended to prove Euler's formula, but after writing it, the author discovered a more concise method that doesn't require Taylor series. But I had already written 5kb on Taylor series for real functions!! So, I separated that part into a standalone [Taylor Series article](https://www.luogu.com.cn/article/9z2t5m66) and changed the topic of this article to Complex Analysis, ~~thus managing to produce two articles!~~

Oh no, that Taylor series article didn't pass review. Oh well, it is what it is.

After a series of formatting changes, **the proof of Euler's formula has been placed in the Introduction - Exponential Functions section.**

## Introduction
Considering that the treatment of complex numbers in the compulsory high school curriculum is too rudimentary, we reintroduce the concept of complex numbers here.  

### Basic Concepts and Operations
We define a complex number as an ordered pair $(x,y),(x,y\in\mathbb{R})$. Two complex numbers $(x_1,y_1),(x_2,y_2)$ are said to be equal if and only if $x_1=x_2$ and $y_1=y_2$. We usually use $z$ to represent a complex number.  
Next, we define two operations for complex numbers.  
- Addition: $(x_1,y_1)+(x_2,y_2)=(x_1+x_2,y_1+y_2)$.
- Multiplication: $(x_1,y_1)\times(x_2,y_2)=(x_1x_2-y_1y_2,x_1y_2+x_2y_1)$.

It can be easily proven that the complex numbers form a field with respect to these two operations. We call this field the Complex Number Field and denote it as $\mathbb{C}$.  
Based on these operations, we define two elements: $1=(1,0),i=(0,1)$. Then we can express any complex number as:
$$
z=(x,y)=x\cdot 1+y\cdot i
$$
We call $x$ the real part of $z$ and $y$ the imaginary part of $z$, denoted as:
$$
Re(z)=x,Im(z)=y
$$
Usually, we omit the $1$, just like in the real number field, giving complex numbers the form seen in the compulsory curriculum, and we can also obtain:
$$
i\times i=-1
$$
Note that $1,i$ are linearly independent. Therefore, we can use these two vectors as basis vectors to form a two-dimensional space, called the Complex Plane, as shown in the figure below:

![](https://cdn.luogu.com.cn/upload/image_hosting/nn9u634m.png)

As shown, each complex number corresponds to a vector in the complex plane. The modulus of a complex number is defined as the magnitude of the corresponding vector, denoted as:
$$
|z|=\sqrt{a^2+b^2}
$$
Its argument is defined as the angle of the corresponding vector, denoted as:
$$
\arg(z)=\arctan\frac yx
$$
A vector has a trigonometric representation, so the corresponding complex number also has a trigonometric representation. Let $r=|z|,\theta=\arg(z)$, then
$$
z=r\cos\theta+i\cdot r\sin\theta
$$
Complex numbers have more relations than vectors. For example, we say two complex numbers $z_1=(x_1,y_1),z_2=(x_2,y_2)$ are
- conjugates if $x_1=x_2,y_1=-y_2$, denoted as $z_1=\overline{z_2}$.

It is easy to see that the Completeness Axiom does not hold in the complex number field; that is, the complex numbers are not an ordered field. We can map points on the complex plane to a sphere (Riemann sphere), but I'm too lazy to write about that. If you want to learn more, you can read Shabat's ["Introduction to Complex Analysis"](https://academic.hep.com.cn/engi/CN/book/978-7-04-030578-4).

A complex function $w:\mathbb{C}\to\mathbb{C}$ is a rule defined on the complex field that maps to the complex plane. Generally, a complex function can be split into two real functions defined on the complex field, like:
$$
w(x,y)=u(x,y)+i\cdot v(x,y)
$$
where $x,y,u(x,y),v(x,y)\in\mathbb{R}$.

### Exponential Function
We consider defining it similarly to the real number field:
$$
e^z=\lim_{n\to\infty} \left(1+\frac zn\right)^n
$$
Then we consider whether this limit exists.  
We note that:
$$
|e^z|=\lim_{n\to\infty}
\left|\left(1+\frac zn\right)^n\right|=\lim_{n\to\infty}\left(1+\frac{2x}n+\frac{x^2+y^2}{n^2}\right)^\frac n2=e^x
$$
$$
\arg(e^z)=\lim_{n\to\infty}\arg\left(1+\frac zn\right)^n=\lim_{n\to\infty}n\arctan\left(\frac{\frac yn}{1+\frac xn}\right)=y
$$
Thus, this limit exists, and we have:
$$
e^z=e^x(\cos y+i\sin y)
$$
Setting $x=0$, we obtain Euler's formula. From now on, I will treat it as a known result in the subsequent sections.

### Power Function
With Euler's formula, a complex number can be represented as:
$$
z=|z|e^{i\arg(z)}
$$
This is a more concise form. This form is beneficial as it makes the power function more intuitive.
Consider $z=r e^{i\theta}$, then
$$
z^n=\left(re^{i\theta}\right)^n=r^ne^{i(n\theta)}
$$
This means the argument is multiplied by $n$, and the modulus is raised to the $n$th power, making the geometric interpretation more intuitive.

### Trigonometric Functions, Hyperbolic Functions
With Euler's formula, trigonometric functions can also be expressed using it:
$$
\sin(z)=\frac{e^{iz}-e^{-iz}}{2i}\\
\cos(z)=\frac{e^{iz}+e^{-iz}}2
$$
Notice how this looks just like the hyperbolic functions? So we can get the following expressions:
$$
\begin{aligned}
\sin(z)&=-i\sinh(iz)\\
\cos(z)&=\cosh(iz)
\end{aligned}
$$
Then we can define the remaining functions using $\sin,\cos,\sinh,\cosh$.

### Derivative
In the pure real number field, the derivative is usually represented as a rate of change. But does this hold in the complex field? In other words, do derivatives exist in the complex field? If they do, what are the conditions for existence?  

We define the derivative of a complex function similarly to the real case:
$$
w'(z_0)=\lim_{z\to z_0}\frac{w(z)-w{(z_0)}}{z-z_0}
$$
It seems the same as the real case! But a problem arises here: from which direction should $z$ approach $z_0$?  

Here we give the Cauchy-Riemann conditions: This function is differentiable (complex differentiable) if and only if:
$$
\frac{\partial u}{\partial x}=\frac{\partial v}{\partial y},\frac{\partial u}{\partial y}=-\frac{\partial v}{\partial x}
$$
Then, at that point, $w'=\frac{\partial u}{\partial x}+i\frac{\partial v}{\partial x}$. The proof is straightforward.  
If a function is differentiable at every point in its domain, it is called a holomorphic function. From now on, the functions we discuss will be holomorphic functions.

### Integral
In the complex field, integration is defined along paths, generally called line integrals or contour integrals.

Let a path be defined by $\gamma=\gamma(t)=x(t)+i\cdot y(t),t\in[a,b]$. Then the integral is defined as:
$$
\int_\gamma f(z)\,dz=\int_a^b f(\gamma(t))\gamma'(t)\,dt
$$
Based on this definition, we can derive the following simple properties:
- **Path Additivity**: If $\gamma=\gamma_1+\gamma_2$, then:
  $$\int_\gamma f(z)\,dz=\int_{\gamma_1} f(z)\,dz+\int_{\gamma_2} f(z)\,dz$$
- **Reverse Path**: For any path, we have:
  $$\int_{-\gamma} f(z)\,dz=-\int_\gamma f(z)\,dz$$

### Cauchy's Theorem
**Simply Connected Region**: In Shabat's Introduction to Complex Analysis, homotopy theory of paths is used to rigorously define a simply connected region. However, the author's language skills are poor and unable to articulate a rigorous definition clearly, coupled with the inherently high difficulty of understanding, so we define a simply connected region in an easy-to-understand way here.

If a region has no "holes" in it, it is called a simply connected region. Otherwise, it is called a multiply connected region.  

Do simply connected regions have any magical properties? Certainly, otherwise I wouldn't have mentioned them specifically.

**Theorem 1**: If $f(z)$ is holomorphic in a simply connected region $D$, then for any closed curve $\gamma\subset D$, we always have:
$$
\oint_\gamma f(z)\,dz=0
$$
(The circle on the integral sign indicates integration over a closed curve).  
This theorem essentially tells us that for integrals in a simply connected region, the value of the integral depends only on the start and end points, and is independent of the path. This is a very strong conclusion. It directly tells us that within a simply connected region, we only need to consider the start and end points, greatly simplifying the complexity of calculation. For example, we can transform a bizarre integration path into a straight line segment, and the integral over a line segment is just an ordinary integral~

**Theorem 2**: If $z_0$ is inside the closed curve $\gamma$, then:
$$
f(z_0)=\frac1{2\pi i}\oint_\gamma\frac{f(z)}{z-z_0}\,dz
$$
This is an extremely important theorem. It allows us to convert many integrals into function values, and function values into contour integrals.

### Relationship Between Higher-Order Derivatives and Integrals
This is a particularly important part, so I've dedicated a separate section to explain it.

There exists the following relationship between the higher-order derivatives of a function and integrals:
$$
\boxed{f^{(n)}(z_0)=\frac{n!}{2\pi i}\oint_\gamma\frac{f(z)}{(z-z_0)^{n+1}}\,dz}
$$
We prove this using mathematical induction.

**Proof**

When $n=0$, it reduces to Cauchy's Integral Formula (Theorem 2), so the proposition holds.
If the proposition holds for $n=k$, then:
$$
f^{(k)}(z_0)=\frac{k!}{2\pi i}\oint_\gamma\frac{f(z)}{(z-z_0)^{k+1}}\,dz
$$
We differentiate this with respect to $z_0$:
$$
\begin{aligned}
f^{(k+1)}(z_0)&=\frac{k!}{2\pi i}\oint_\gamma f(z)\frac{\partial}{\partial z_0}\frac{1}{(z-z_0)^{k+1}}\,dz\\
&=\frac{(k+1)!}{2\pi i}\oint_\gamma\frac{f(z)}{(z-z_0)^{k+2}}\,dz
\end{aligned}
$$
Therefore, the proposition holds for $\forall n\in\mathbb{N}$.

We will use this in the Taylor expansion in the complex domain.
## Expansion of Complex Functions
### Taylor Series
Let's recall the Cauchy Integral Formula derived earlier:
$$
f(z)=\frac1{2\pi i}\oint_\gamma\frac{f(\zeta)}{\zeta-z}\,d\zeta
$$
We consider expanding its kernel. Using a known result (geometric series), we get:
$$
\frac{1}{\zeta-z}=\frac{1}{(\zeta-z_0)-(z-z_0)}=\frac{1}{\zeta-z_0} \sum_{n=0}^{\infty} \left( \frac{z-z_0}{\zeta-z_0}\right)^n
$$
Substituting back into the original formula, we get:
$$
f(z) = \frac{1}{2\pi i} \oint_{C_r} f(\zeta) \sum_{n=0}^{\infty} \frac{(z-z_0)^n}{(\zeta-z_0)^{n+1}}  \,d\zeta = \sum_{n=0}^{\infty} (z-z_0)^n \left[ \frac{1}{2\pi i} \oint_{C_r} \frac{f(\zeta)}{(\zeta-z_0)^{n+1}}  \,d\zeta \right]
$$
Does the latter part look familiar? This is the higher-order derivative formula we just derived. Substituting it in, we obtain:
$$
f(z)=\sum_{n=0}^\infty\frac{f^{(n)}(z_0)}{n!}(z-z_0)^n
$$
This is the same result we obtained in the pure real number domain! But it's not over yet; we still need to discuss the convergence conditions for the Taylor series.

Obviously, the methods we used for expanding real functions are no longer applicable here. So we present a better method here.
### Cauchy–Hadamard Theorem
This is a superior method for determining convergence, giving a radius of convergence.

**Cauchy–Hadamard Theorem**: For the series $\displaystyle\sum_{n=0}^\infty c_n(z-z_0)^n$, its radius of convergence $R$ satisfies the following relation:
$$
\frac1R=\varlimsup_{n\to\infty}\sqrt[n]{|c_n|}
$$
Specifically, we define:
- $R=\infty$ when $\frac1R=0$.
- $R=0$ when $\frac1R=\infty$.

**Proof**

Here we only prove the case for $z_0=0$, as other cases can be obtained by substitution.  
Let $L=\displaystyle\varlimsup_{n\to\infty}\sqrt[n]{|c_n|}$. Consider calculating:
$$
\varlimsup_{n\to\infty}\sqrt[n]{|c_n|z^n}=|z|\cdot L
$$
Let's discuss case by case:  

1. $|z|\cdot L=0$, then clearly, for any $z$ in the complex plane, the series converges.
2. $|z|\cdot L\in(0,1)$ i.e. $|z|<\frac1L$, then the series converges absolutely.
3. $|z|\cdot L=1$ the test is inconclusive.
4. $|z|\cdot L\in(1,\infty)$, i.e. $|z|>\frac1L$, then the series diverges, because $|c_nz^n|>1$ for infinitely many $n$.
5. $|z|\cdot L=\infty$ then the series converges only for $z=0$.

In summary, except for the boundary case, the proposition holds.

### Laurent Series
Starting from here, we will discuss functions that are not holomorphic everywhere due to the presence of singularities.  

Assume the function $f(z)$ is holomorphic on the annulus $r\le|z-z_0|\le R$. Then there exists a series:
$$
f(z)=\sum_{n=-\infty}^{\infty}c_n (z-z_0)^n
$$
where
$$
c_n=\int_{|z-z_0|=\rho}\frac{f(z)\,dz}{(z-z_0)^{n+1}}
$$
and where $r\le\rho\le R$. We call this series the Laurent series.

We find that when $0\le n$, the coefficients of the series are the same as those in the Taylor series, but they cannot be written in the form $c_n=\frac{f^{(n)}(z_0)}{n!}$ if $f$ is not analytic at $z_0$.

Its convergence can also be determined using the Cauchy–Hadamard theorem. Furthermore, its coefficients satisfy Cauchy's inequality:
$$
|c_n|\le\frac M{\rho^n}
$$
where $M\ge\sup(f)$.
### Fourier Series
Recall the definition of the Fourier series in the real number domain:
$$
f(x)=\frac{A_0}2+\sum_{n=0}^\infty{A_n\cos{nx}+B_n\sin{nx}}
$$
where:
$$
A_n=\frac1\pi\int_0^{2\pi}f(t)\cos nt\,dt\\
B_n=\frac1\pi\int_0^{2\pi}f(t)\sin nt\,dt
$$
Applying Euler's formula mentioned earlier and defining new coefficients, we can write:
$$
f(x)=\sum_{n=-\infty}^\infty{c_ne^{int}}
$$
A simple derivation yields:
$$
c_n=\frac1{2\pi}\int_0^{2\pi}f(t)e^{-int}\,dt
$$
Note that if we let $z=e^{int}$ we get:
$$
f(z)=\sum_{n=-\infty}^\infty c_nz^n
$$
and
$$
c_n=\frac1{2\pi}\int_{|z|=1}\frac{f(z)}{z^n}\,dz
$$
This is the Laurent series on the unit circle. Conversely, the Laurent series of a function on the unit circle can be transformed into a Fourier series by substitution.
### Isolated Singularities
We define a point $z_0$ as an isolated singularity of the function $f$ if $f$ is holomorphic in the punctured disk $0<|z-z_0|<r$ for some $r>0$.

We say the isolated singularity $z_0$ is:
- A removable singularity if the limit $\displaystyle\lim_{z\to z_0} f(z)=A$ exists (and is finite).
- A pole if the limit $\displaystyle\lim_{z\to z_0}f(z)=\infty$.
- An essential singularity if the limit $\displaystyle\lim_{z\to z_0}f(z)$ does not exist (in the extended complex plane).

This passage probably has the distinctive inverted flavor of foreign textbooks. Would it sound more like it if the top part was written as: "Regarding an isolated singularity $z_0$, we call it..."?

Here are two examples. For the functions:
$$
f_1(z)=\frac{\sin z}{z},f_2(z)=e^\frac1z
$$
Clearly $z_0=0$ is a removable singularity for $f_1$ and an essential singularity for $f_2$.

**Theorem 3**: $z_0$ is a removable singularity of the function $f$ if and only if the coefficients $c_n$ in the Laurent series of $f$ about $z_0$ satisfy:
$$
c_n\equiv 0,\forall n<0
$$
The reader is invited to prove this themselves; you can try using Cauchy's inequality.

**Theorem 4**: $z_0$ is a pole of the function $f$ if and only if the coefficients $c_n$ in the Laurent series of $f$ about $z_0$ satisfy:
There exists an integer $N<0$ such that $c_n=0$ for all $n\le N$.
The reader is invited to prove this again.

**Theorem 4'**: $z_0$ is a pole of the function $f$ if and only if the function $\varphi=\frac1f$ is holomorphic in a neighborhood of $z_0$ and has $\varphi(z_0)=0$.

**Theorem 5**: $z_0$ is an essential singularity of the function $f$ if and only if the coefficients $c_n$ in the Laurent series of $f$ about $z_0$ satisfy: There are infinitely many negative indices $n$ for which $c_n\ne0$.

From Theorems $3$ to $5$, we can see the relationship between isolated singularities and the Laurent series.
### Residue Theorem
We now start considering points where a holomorphic function is no longer holomorphic.

Assume the function $f$ is holomorphic everywhere in a region $D$ except at a countable set of singular points. Let region $G\subseteq D$, and let $a_1,\cdots,a_n$ be the singularities inside $G$. Let $\gamma_\nu=\{|z-a_\nu|=r\}$, where $r$ is sufficiently small such that the disks around the singularities do not intersect. Let $\gamma_\nu$ be oriented counterclockwise. Define $G_r=G\setminus \bigcup _{\nu=1}^n \text{interior of } \gamma_\nu$.

![](https://cdn.luogu.com.cn/upload/image_hosting/5f3cs8ex.png)

The diagrams in complex analysis are great.

Then we clearly have (by Cauchy's Theorem for multiply connected domains, applying it to $G_r$):
$$
\int_{\partial G_r}f(z)\,dz=\sum_{\nu=1}^n\int_{\gamma_\nu}f(z)\,dz=0
$$
We define $\mathrm{res}_\nu f=\displaystyle\frac{1}{2\pi i}\int_{\gamma_\nu}f(z)\,dz$, called the residue of $f$ at the singularity $a_ν$. Then the original equation becomes:
$$
\int_{\partial G}f(z)\,dz=2\pi i\sum_{\nu=1}^n\mathrm{res}_\nu f
$$

Then the **Residue Theorem** states: The residue of a function $f$ at an isolated singularity $a\in D$ is the coefficient $c_{-1}$ in the Laurent series expansion of $f$ about $a$, i.e.:
$$
\mathrm{res}_af=c_{-1}
$$
The proof is overly obvious. ~~The reader can easily prove it themselves.~~

Here is a classic example of using residues to compute an integral. Consider computing the Laplace integral:
$$
\int_{-\infty}^\infty\frac{\cos{ax}}{b^2+x^2}\,dx
$$
First, construct a closed contour representing a semicircle of radius $R>b$, denoted $\gamma$, like this:

![](https://cdn.luogu.com.cn/upload/image_hosting/2x4b34kl.png)

Considering the integral along this path:
$$
I_R=\oint_\gamma\frac{e^{i\cdot az}}{b^2+z^2}\,dz
$$
There is a first-order pole (simple pole) at $z=ib$ (in the upper half-plane). Applying the residue theorem, we get:
$$
\mathrm{res}_{ib}\left(\frac{e^{iaz}}{b^2+z^2}\right)=\frac{e^{-ab}}{2ib}
$$
Thus, by the residue theorem:
$$
I_R = 2\pi i \cdot \frac{e^{-ab}}{2ib} = \frac{\pi }{b}e^{-ab}
$$

According to the preceding properties, we split it into two parts:
$$
I_R=\int_{-R}^R\frac{e^{i\cdot ax}}{b^2+x^2}\,dx+\int_0^\pi \frac{e^{ia\cdot Re^{i\theta}}}{b^2+R^2e^{i2\theta}}iRe^{i\theta}\,d\theta
$$
Now we let $R\to\infty$. The first part becomes the Laplace integral. For the second part, we have:
$$
\lim_{R\to\infty}\left|\int_0^\pi \frac{e^{ia\cdot Re^{i\theta}}}{b^2+R^2e^{i2\theta}}iRe^{i\theta}\,d\theta\right|\le\lim_{R\to\infty}\frac{\pi R}{R^2-b^2}=0
$$
But this only holds for $a > 0$. So when $a < 0$, we take the lower semicircle as the contour integral. Using the same method, we eventually get:
$$
I = \frac\pi b e^{a b} 
$$
Combining the two results, we get:
$$
\int_{-\infty}^\infty\frac{\cos{ax}}{b^2+x^2}\,dx=\frac\pi b e^{-|a b|} 
$$
## Analytic Continuation
Now that we have the complex number field, we naturally have the idea of extending real functions to the complex field. This process is called analytic continuation.  

More rigorously, if a holomorphic function $f_0$ is defined on a domain $M$, and there exists another holomorphic function $f$ defined on a domain $D\supset M$ such that:
$$
f|_{M}=f_0
$$
Then $f$ is the result of the analytic continuation of $f_0$. 

Analytic continuation has some commonly used methods, one of which is the Taylor series, which we have prepared extensively for earlier.

For general functions, they are not defined in the complex domain, but their Taylor series converge in the complex domain. Therefore, we can use their Taylor series to replace the original function, achieving the effect of analytic continuation.

The rest will be introduced in a separate article later.

## Some Casual Remarks
This article was written by the author while slacking off during training at ZR (likely a training camp). You can completely treat the rest of this text as a travelogue.  

Sshwy spent two hours during evening self-study ranting about how terrible C++ is, criticizing C++ from start to finish. "WTF is `using namespace std`?", showing that Sshwy holds C++ in high esteem. Here is the [article](https://notes.sshwy.name/Programming-Languages/).

Ayanami Rei is awesome, using Ayanami Rei as a wallpaper.

Met grass8cow (hereinafter referred to as c8n), who talked about DP optimization. However, it was incomprehensible, so in the afternoon, I read the slides word for word and still didn't understand, completely losing my language ability. c8n publicly demonstrated using the Luogu submission interface to solve problems, solved one blue and one purple, receiving worship from the whole class. However, when trying to solve [P3791 Ordinary Math Problem](https://www.luogu.com.cn/problem/P3791), he got TLE, but passed easily after adding memoization. Then he briefly talked about his CF alt account, mourning his banned account. Questioned by classmates about his poor English skills, he brought up his WC2025 (likely Winter Camp) defense incident. Basically, he was ranked 8th, thought he couldn't make the top 6, so he didn't prepare the defense. But on the last day, there was a reversal, and he was exactly 6th. He wanted to give the defense opportunity to someone lower ranked, but it turned out there was a precedent for this??? He was refused, so he stayed up late finishing his paper. However, the defense required an English self-introduction. So c8n spent half an hour cobbling together a self-introduction and wanted to spend an hour memorizing it. Ultimately, he didn't succeed and used sheer audacity to get through the self-introduction. Later learned that the precedent was dzd.

Very quickly, the training camp entered the stage of "deep understanding, complete belief" – it was really agonizing!!! Bought headphones, henceforth cut off from the world. Became obsessed with the band Cao Dong, listened to them every day, until one day checking the play duration:

"Wow, 18 out of the top 20 most played songs this month are by Cao Dong??? ['但' (But)](https://baike.baidu.com/item/%E4%BD%86/62894180) was played 140 times, expressing the author's desire not to be here (at ZR)."

However, ZR actually had a concert?? Signed up for '但' as soon as the announcement was posted, ~~suspected of spreading cult behavior~~, met Du Yuhao. Eh?! Someone sang '冬の花', although a large section wasn't sung, still good!! Sshwy sang ['Night Voyage' (夜航星)](https://baike.baidu.com/item/%E5%A4%9C%E8%88%AA%E6%98%9F/24969208), so awesome!! Surprised to hear someone sing ['Sakura Nagashi' (桜流し)](https://evangelion.fandom.com/wiki/Sakura_Nagashi) at ZR, EVA gets praise, although I wanted to suddenly stand up, clap and shout "おめでとう! (Congratulations!)", recreating the classic scene, but didn't dare, felt a bit awkward.

At the concert, finished watching [Cardcaptor Sakura](https://en.wikipedia.org/wiki/Cardcaptor_Sakura), Syaoran Li's confession was too difficult.

Went back at night, played a bit of [Honkai: Star Rail](https://en.wikipedia.org/wiki/Honkai:_Star_Rail), then continued updating the article. Had ACM the next day, but still stayed up until morning before sleeping.

Formed an abstract team. From team formation to the end of the competition, there were only 5 messages in the group chat, ~~four of which were sent by me~~, a bit quiet. The first blood balloon was a Nailoong , kinda funny. 18 people in the class claimed to be Nailong, but 9 of them were from GDSY , GDSY is too abstract, leaving no blade of grass standing wherever they go. Within the first half hour of the competition, I had already contributed 8 penalty tries, so I didn't dare to code anymore, switched with a teammate who went on to solve 4 problems furiously, felt inferior. Finally got 7 problems within three hours, then spent an hour reading problem H without understanding the meaning of the problem , demonstrating the junior high school level Chinese proficiency, started slacking off, gave the computer to the female classmate in the team, started watching anime. In the last half hour, stabilized at rank 29 (official contestants rank 24). The first place among official contestants was actually an eighth grader from Tieyi Middle School named lkr, and he was alone, felt inferior again. Ordered milk tea, thinking to pick it up after the competition.

During dinner, realized I had selected "pick up in store", I am Nailong, reordered, but it started pouring rain, couldn't go get the takeout, left it for two hours, when I got it, the sundae had turned into soup.

After many days of training, finally slacked off, chose not to attend evening self-study. Freed up a lot of time, but most of it was spent playing table tennis and playing [ADOFAI](https://store.steampowered.com/app/977950/A_Dance_of_Fire_and_Ice/), and also managed to pass [It Go](https://store.steampowered.com/app/977950/A_Dance_of_Fire_and_Ice/?) (likely a specific ADOFAI level) in one go. Then went to grind the game event. A classmate bought Alice's skin, but got a different one, lol. Learned how to play Strange Companion (?), grinding monsters became like farming in [Genshin Impact] opening treasure chests, played with classmates for half an hour felt boring, went back to the event. Fairy's auto-fishing took too long, but didn't want to harvest early, so didn't fish. Played [Stardew Valley](https://en.wikipedia.org/wiki/Stardew_Valley) and finally understood that fishing can really make you red with anger (frustrating).

Participated in a ZR contest, **"Blind faith in the teacher is worse than having no teacher"**, it was c8n's contest. Where are the humans? At first glance, 99 points thought it was the score for T1, but it was the total score, and this was the 20th place result. IOI contestants are just different.

Yamada Ryo (from Bocchi the Rock) is awesome, using Yamada Ryo as wallpaper.

MC (Minecraft) is fun, recommended server `hmsj.online`. My deskmate got red-faced angry due to 360 (antivirus software), started uninstalling 360, opened the main folder, searched for "360" in the search bar, found nothing, then went to the browser to search "how to uninstall 360 security guard". One article said to find the 360 process in the task manager, go to the 360 folder, and use the built-in uninstaller. So she opened the task manager and started frantically ending processes, found it useless, then read that article word for word, finally opened the 360 folder, and deleted the 360 shortcut. Found it hilarious, helped her uninstall 360 properly.

Now it's the last day at ZR, total of 10 Kb written, been updating for two weeks and still not finished, I am the king of procrastination.

Now it's the first day of school, been updating for a month. Transferred to a new school, became an OIer in a strong-province-weak-school situation, played CF for a month, rating increased quite quickly.

I FINALLY FINISHED WRITING!!!!
During the writing period, finished 13 anime series, also a godly feat.

No more casual remarks, afraid if I write more it won't pass review.
Didn't find a category, not submitting for review.
## References
Shabat B. V. Introduction to Complex Analysis. Too weak, can't understand English literature.

Is it over?
