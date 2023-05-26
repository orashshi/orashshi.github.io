---
title: Problems Solving
date: 2023-05-15 13:07:27 +0800
tags:
- Calculus
- mathematics
layout: post
--- 

<head>
    <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
    <script type="text/x-mathjax-config">
        MathJax.Hub.Config({
            tex2jax: {
            skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
            inlineMath: [['$','$']]
            }
        });
    </script>
</head>

刷的几道比较难的数学分析题。持续更新~

### Question 1：
设 $f$ 是 $\{(x,y)|x^2+y^2\leq 1\}$上的二次连续可微函数，
   
$$\frac{\partial^2 f(x,y)}{\partial x^2}+\frac{\partial^2 f(x,y)}{\partial y^2}=x^2 y^2$$

计算积分

$$I = \iint \limits_{x^2+y^2 \leq 1}[\frac{x}{\sqrt{x^2+y^2}}\frac{\partial f(x,y)}{\partial x}+\frac{y}{\sqrt{x^2+y^2}}\frac{\partial f(x,y)}{\partial y}]\mathrm{d}x \mathrm{d}y$$

解：记 $r=\sqrt{x^2+y^2}$, 令$\mathbf{n}$, $\mathrm{d}s$为$x^2+y^2=1$的外法向量和长度元，则由Green公式，

$$\begin{align*}
I &= \iint \limits_{x^2+y^2 \leq 1} \nabla r \cdot \nabla f \mathrm{d}x \mathrm{d}y\\
&=-\iint \limits_{x^2+y^2 \leq 1} r \Delta f \mathrm{d}x \mathrm{d}y + \int_{x^2+y^2 = 1} r \frac{\partial f}{\partial \mathbf{n}} \mathrm{d}s\\
&=-\iint \limits_{x^2+y^2 \leq 1} r \Delta f \mathrm{d}x \mathrm{d}y + \int_{x^2+y^2 = 1} \frac{\partial f}{\partial \mathbf{n}} \mathrm{d}s = \iint \limits_{x^2+y^2 \leq 1} (1-r) \Delta f \mathrm{d}x \mathrm{d}y \\
&= \iint \limits_{x^2+y^2 \leq 1} (1-r)x^2y^2 \mathrm{d}x \mathrm{d}y= \int_0^{2\pi} \mathrm{d}\theta \int_0^1(1-r)r^4 \cos^2{\theta}\sin^2{\theta} r \mathrm{d} r\\
&= (\frac{1}{6}-\frac{1}{7})\int_0^{2\pi} \frac{\sin^2{2\theta}}{4} \mathrm{d} \theta = \frac{\pi}{168}. 
\end{align*}$$

### Question 2
设$f$在$[0,1]$上Riemann可积，在点1处可导，$f(1)=0,f^{\prime}(1) = a.$ 证明：
   
$$\lim_{n \to +\infty} n^2  \int_0^1 x^n f(x)\mathrm{d}x = -a$$

证：令$F(x) = f(x) - a(x-1)$，对于 $r \in (0,1]$，记

$$\omega(r)=\sup_{0 < \left | x - 1 \right | \leq r}\frac{\left | F(x) \right |}{1-x}$$

我们有 $\lim\limits_{r \to 0^+} \omega(r) = 0$. 于是对任何 $\delta \in (0,1)$, 有

$$\begin{align*}
\left| n^2 \int_0^1 x^n F(x) \mathrm{d} x \right| &\leq n^2 \omega(1)\int_0^{1-\delta}x^n(1-x)\mathrm{d}x+n^2\omega(\delta)\int_{1-\delta}^1 x^n(1-x)\mathrm{d}x\\
& \leq n^2 \omega(1) \int_0^{1-\delta}x^n\mathrm{d}x + n^2\omega(\delta)\int_0^1 x^n(1-x)\mathrm{d}x\\
& \leq n^2 \omega(1)(1-\delta)^{n+1}+\omega(\delta).
\end{align*}
$$

于是，

$$\overline{\lim \limits_{n \to +\infty}}\left| n^2 \int_0^1 x^n F(x) \mathrm{d} x \right| \leq \omega(\delta)$$

令 $\delta \to 0^+$得到，

$$\lim \limits_{n \to +\infty} n^2 \int_0^1 x^n F(x) \mathrm{d} x = 0.$$

这就是

$$\lim \limits_{n \to +\infty} n^2 \int_0^1 x^n f(x) \mathrm{d} x = -a.$$

$\blacksquare$

### Question 3

已知$\varphi: (0,+\infty) \to (0,+\infty)$是一个严格单调的连续函数，满足$\lim \limits_{t \to 0^+} \varphi(t) = + \infty$，且

$$\int_0^{+\infty} \varphi(t) \mathrm{d}t = \int_0^{+\infty} \varphi^{-1}(t)\mathrm{d}t = a < +\infty$$

其中$\varphi^{-1}$表示$\varphi$的反函数。求证：

$$\int_0^{+\infty} [\varphi(t)]^2 \mathrm{d}t + \int_0^{+\infty} [\varphi^{-1}(t)]^2\mathrm{d}t \geq \frac{1}{2} a^{\frac{3}{2}}$$

证：令$D$为封闭区域$\left\{ (x,y) \| 0 \leq y \leq \varphi(x),x \geq 0 \right\}$，则$\iint \limits_D \mathrm{d}x\mathrm{d}y = a$. 对于$s>0$, 记$\Delta_s$为以$(0,0),(s,0),(0,s)$为顶点的三角形区域。则有

$$\begin{align*}
\int_0^{+\infty}[\varphi(t)]^2 \mathrm{d}t + \int_0^{+\infty}[\varphi^{-1}(t)]^2\mathrm{d}t &= 2 \iint \limits_D (x+y) \mathrm{d}x\mathrm{d}y \\
& \geq 2s\iint \limits_{D\backslash \Delta_s} \mathrm{d}x\mathrm{d}y\\
& \leq 2s\left(a-\frac{1}{2}s^2\right)
\end{align*}
$$

取$s = \sqrt{\frac{2a}{3}}$即得

$$\int_0^{+\infty}[\varphi(t)]^2 \mathrm{d}t + \int_0^{+\infty}[\varphi^{-1}(t)]^2\mathrm{d}t \geq \frac{4\sqrt{6}}{9} a^{\frac{3}{2}}>\frac{1}{2}a^{\frac{3}{2}}$$

$\blacksquare$

### Question 4

