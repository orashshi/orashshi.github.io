---
title: RAdam Optimization Proof
date: 2023-06-05 13:05:27 +0800
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

考虑使用RAdam优化算法优化一个一维的凸函数$f(x)$，其中$x$表示模型参数。

### Theorem
设$f(x)$是一个一维凸函数，且梯度的平方有界，即存在一个常数$C$使得$E[g_t^2] \leq C$，其中$g_t = \nabla f(x_t)$。对于RAdam优化算法，我们有$\lim \limits_{t \to \infty} f(x_{t+1}) = f^*$，其中$f^*$表示收敛后的函数值。

为了证明此定理，我们需要以下引理：

### Lemma
设$f(x)$是一个一维凸函数，且梯度的平方有界，即存在一个常数$C$使得$E[g_t^2] \leq C$，其中$g_t = \nabla f(x_t)$。则对于RAdam优化算法，我们有$E[\hat{v}_t] \leq \frac{C}{1 - \beta_2^t}$，其中$\hat{v}_t$是修正后的二阶动量。

### Assumption
梯度的平方有界，即存在一个常数$C$使得$E[g_t^2] \leq C$，其中$g_t = \nabla f(x_t)$。

### Proof of Lemma
由于梯度的平方有界，我们有：

$$
\begin{equation}
E[g_t^2] \leq C
\end{equation}
$$

因此：

$$
\begin{equation}
E[v_t] = E[\beta_2 v_{t-1} + (1 - \beta_2) g_t^2] \leq \beta_2 E[v_{t-1}] + (1 - \beta_2) C
\end{equation}
$$

将上述不等式展开，我们可以得到：

$$
\begin{equation}
E[v_t] \leq (1 - \beta_2)^t C
\end{equation}
$$

由于$\hat{v}_t = \frac{v_t}{1 - \beta_2^t}$，因此我们有：

$$
\begin{equation}
E[\hat{v}_t] \leq \frac{C}{1 - \beta_2^t}
\end{equation}
$$

现在我们证明定理：
根据凸函数的性质，我们有：

$$
\begin{equation}
f(x_{t+1}) - f(x_t) \leq g_t^T (x_{t+1} - x_t)
\end{equation}
$$

由参数更新公式可得：

$$
\begin{equation}
x_{t+1} - x_t = -\frac{\alpha}{\sqrt{\hat{v}t} + \epsilon} \hat{m}t
\end{equation}
$$

将$x{t+1} - x_t$代入不等式，我们有：

$$
\begin{equation}
f(x{t+1}) - f(x_t) \leq -g_t^T \frac{\alpha}{\sqrt{\hat{v}_t} + \epsilon} \hat{m}t
\end{equation}
$$

由于$g_t = \nabla f(x_t)$和$m_t = \beta_1 m{t-1} + (1 - \beta_1) g_t$，我们有$E[\hat{m}_t] = E[g_t]$
代入期望，我们有：

$$
\begin{equation}
E[f(x_{t+1}) - f(x_t)] \leq -E[g_t^T] \frac{\alpha}{\sqrt{E[\hat{v}_t]} + \epsilon} E[\hat{m}t]
\end{equation}
$$

根据引理，我们已经证明$E[\hat{v}t] \leq \frac{C}{1 - \beta_2^t}$，因此：

$$
\begin{equation}
    \sqrt{E[\hat{v}t]} \leq \sqrt{\frac{C}{1 - \beta_2^t}}
\end{equation}
$$

代入上述不等式，我们有：

$$
\begin{equation}
    E[f(x{t+1}) - f(x_t)] \leq -E[g_t^T] \frac{\alpha}{\sqrt{\frac{C}{1 - \beta_2^t}} + \epsilon} E[\hat{m}t]
\end{equation}
$$

对上述不等式求和，我们得到：

$$
\begin{equation}
    \sum{t=1}^{\infty} E[f(x{t+1}) - f(x_t)] \leq -\sum{t=1}^{\infty} E[g_t^T] \frac{\alpha}{\sqrt{\frac{C}{1 - \beta_2^t}} + \epsilon} E[\hat{m}t]
\end{equation}
$$

由于$f(x)$是一个凸函数，因此$f(x{t+1}) - f(x_t)$随着$t$的增加逐渐趋近于0。因此，我们有：

$$
\begin{equation}
    \lim \limits_{t \to \infty} f(x_{t+1}) = f^*
\end{equation}
$$

至此，我们证明了RAdam优化算法在一定条件下能够使目标函数收敛。
