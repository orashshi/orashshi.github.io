---
title: Continuity of multivariate functions
date: 2023-03-27 05:05:27 -0500
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

## Continuity of multivariate functions

Let $E$ be a set in the space $\mathbb{R}^m$ and the function $f:E \rightarrow \mathbb{R}^n$ is defined on $E$ and takes values in $\mathbb{R}^n$.

#### Definition 1: 
Given the function $f:E\rightarrow \mathbb{R}^n$. If for any neighborhood $V(f(a))$ of the value $f(a)$ of this function at the point $a$, there always exists a neighborhood $U_{E}(a)$ of the point $a$ in the set $E$ such that its image $f(U_{E}(a))$ lies in $V(f(a))$. We call the function $f:E\rightarrow \mathbb{R}^n$ $\textbf{continuous}$ at $a \in E$.

Hence,

($ f:E\rightarrow \mathbb{R}^n$ is continuous at $a \in E$)$ :=$ $(\forall V(f(a))\exists U_E(a)(f(U_E(a))\subset V(f(a))))$

In fact, the Definition $1$ is identical to our definition of continuity of the real-valued functions. Therefore, we can also give the following expression of this definition as we did there:
($ f:E\rightarrow \mathbb{R}^n$ is continuous at $a \in E$)

$\qquad \qquad$ $:=$ $(\forall \varepsilon > 0 \exists \delta>0\forall x \in E(d(x,a)<\delta \Rightarrow d(f(x),f(a))<\varepsilon))$,

or, if the point $a$ is the limit point of $E$, then

($ f:E\rightarrow \mathbb{R}^n$ is continuous at $a \in E$)$ :=$ ($\lim_{x \in E \to a}f(x)=f(a)$).

Obviously, the concept of continuity makes sense only when the point $a \in E$ is the limit point of the set $E$ and the function $f$ has been defined on $E$.

From Definition 1