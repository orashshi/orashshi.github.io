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

## Commutative Algebra Notes: Rings and Ideals

## Chapter 1: Rings and Ideals
### 1.1
Let $x$ be a nilpotent element of a ring $A$. Show that $1 + x$ is a unit of $A$. Deduce that the sum of a nilpotent element and a unit is a unit.

The nilradical is a subset of the Jacobson radical, and by (1.9), for any $x \in \mathbb{R}$ we have $1 + x = 1 − (−x)$ a unit. Now if $x$ is nilpotent and u a unit, then $u^{−1}x$ is nilpotent as well and $u + x = u(1 + u^{−1}x)$ is invertible.

### 1.2 
Let $A$ be a ring and let $A[x]$ be the ring of polynomials in an indeterminate $x$, with coefficients in $A$. Let $f = a_0+a_1x+\cdots+a_nx^n \in A[x]$. Prove that:

#### 1.2.1
$f(x)$ is a unit in $A[x] \iff a_0$ is a unit in $A$ and $a_1,\cdots,a_n$ are nilpotent.

$\Leftarrow$: From the question we could know that $a_0$ is the unit in $A[x]$ and $a_1,\cdots,a_n$ are nilpotent. Hence $a_1x,\cdots,a_nx^n$ is the nilpotent in $A[x]$. From Exercise $1$, 

$$f = a_0+a_1x+\cdots+a_nx^n \in A[x]$$ 

is invertible in $A[x]$.

$\Rightarrow$: Assume

$$f = a_0+a_1x+\cdots+a_nx^n \in A[x]$$ 

is invertible in $A[x]$. The inverse is:

$$g = b_0+b_1x+\cdots+b_mx^m \in A[x]$$

Then according to $fg=1$, we could know:

$$1=a_0b_0+(a_1b_0+a_0b_1)x+\cdots+(a_{n-1}b_m+a_nb_{m-1})x^{m+n-1}+a_nb_mx^{m+n}$$

Hence,

$$
\begin{cases}
1=a_0b_0\\
0=a_1b_0+a_0b_1\\
\cdots\\
0=a_{n-1}b_m+a_nb_{m-1}\\
0=a_nb_m
\end{cases}
$$

Then we will prove $a_n^{r+1}b_{m-r}=0$, $\forall 0 \leq r \leq m$, we use Mathematical Induction.

It is obvious that $r = 0$ was established. Hence, we assume we have:

$$a_n^rb_{m-r+1}+a_{n-1}b_{m-r+1}+\cdots+a_{n-r}b_m=0$$

Mutiply $a_n^r$ on both sides and combine with the induction assumption, we will have $a_n^{r+1}b_{m-r}=0$. Hence, $a_n^{r+1}b_{m-r}=0$, $\forall 0 \leq r \leq m$, $a_n^{m+1}b_0=0$. From $a_0b_0=1$, we could know that $b_0$ is unit. Hence, $a_n^{m+1}=0$. It means that $a_n$ is nilpotent, and $-a_nx^n$ is also nilpotent.

Then use Mathematical Induction on $n$. It is obvious that $n=0$ is established. When $n \geq 1$, $f(x)$ is invertible and $-a_nx^n$ is nilpotent. Hence, we can know from Exercise 1 that:

$$f-a_nx^n=a_0+a_1x+\cdots+a_{n-1}x^{n-1} \in A[x]$$

is invertible. From the induction assumption, $a_0$ is invertible and $a_1,\cdots,a_{n-1}$ are nilpotents, $a_0$ is revertible and $a_1,\cdots,a_{n-1},a_n$ are nilpotents.

$Q.E.D.$

#### 1.2.2
$f$ is nilpotent $\iff$ $a_0,a_1,\cdots,a_n$ are nilpotent.

$\Leftarrow$: $a_0,a_1,\cdots,a_n$ are nilpotent, then $a_0,a_1x,\cdots,a_nx^n \in A[x]$ are nilpotent. Hence, there exist an $N$ which is big enough that $a_0^N=(a_1x)^N=\cdots=(a_nx^n)^N=0$, hence

$$(a_0+a_1x+\cdots+a_nx^n)^{(n+1)N}=0$$

This proves that the sum of the nilpotent is also nilpotent.

$\Rightarrow$: It is trivial when $n=0$, assume it is established for $n-1$. Then if $f=a-0+a_1x+\cdots+a_nx^n$ is nilpotent, there exist $N$, s.t.

$$(a_0+a_1x+\cdots+a_nx^n)^N=0$$

After expansion, we will find $(a_nx^n)^N=0$($a_n$ and $-a_nx^n$ are nilpotent). From the former part, we will find that

$$a_0+a_1x+\cdots+a_{n-1}x^{n-1}=f-a_nx^n$$

is nilpotent. From the assumption we could know that $a_0,\cdots,a_{n-1}$ are nilpotent, hence all the parameters are nilpotent.

$Q.E.D.$

#### 1.2.3
$f$ is a zero-divisor $\iff$ there exists $a \neq 0$ in $A$ such that $af=0$.

$\Leftarrow$: 
trivial.

$\Rightarrow$: if $f=a_0+a_1x+\cdots+a_nx^n$ is a zero-divisor, then there exists a non-zero polynomial with the lowest degree $g=b_0+b_1x+\cdots+b_mx^m$, s.t. $fg=0$, which means that

$$(a_0+a_1x+\cdots+a_nx^n)(b_0+b_1x+\cdots+b_mx^m)=0$$

Hence, $a_nb_m=0$, then $a_ng=0$. Or, $deg(a_ng)<m,(a_ng)f=0$. This is conflict with that $g$ has the lowest degree. Hence,

$$0=fg=(a_0+a_1x+\cdots+a_{n-1}x^{n-1})g$$

Similarly, we will have $a_{n-1}b_m=0$ and $a_{n-1}g=0$. Or $deg(a_{n-1}g)<m$,$(a_{n-1}g)f=0$. And then, we will have:

$$a_{n-r}g=0,\forall 0 \leq r \leq n$$

Because $g$ is not $0$, so there exists a $b_i \neq 0$, then 

$$a_{n-r}b_i = 0, \forall 0 \leq r \leq n$$

This means that $b_if=0$.

$Q.E.D.$

#### 1.2.4
$f$ is said to be primitive if $(a_0, a_1, \cdots , a_n) = (1)$. Prove that if $f, g \in A[x]$, then $fg$ is primitive $\iff$ $f$ and $g$ are primitive.

Assume $f = a_0 +a_1x+ \cdots +a_nx^n, g = b_0+b_1x+\cdots+b_mx^m$. Then,

$$fg = a_0b_0+(a_0b_1+a_1b_0)x+ \cdots +a_nb_mx^{n+m}$$

$\Rightarrow$:
if $fg$ is primitive, according to the definition,

$$(a_0b_0,a_0b_1+a_1b_0,\cdots,a_nb_m)=(1)$$

Obviously, we will have,

$$a_0b_0,a_0b_1 + a_1b_0, \cdots , a_nb_m \in (a_0, a_1,\cdots, a_n)$$

$$a_0b_0, a_0b_1 + a_1b_0, \cdots , a_nb_m \in (b_0, b_1, \cdots, b_n)$$

hence,

$$(a_0b_0, a_0b_1 + a_1b_0, \cdots , a_nb_m)\subseteq (a_0, a_1, \cdots, a_n)$$

$$(a_0b_0, a_0b_1 + a_1b_0, \cdots , a_nb_m)\subseteq (b_0, b_1, \cdots, b_n)$$

Hence, there's only one circumstance.

$$(a_0,a_1,\cdots,a_n) = (b_0,b_1,\cdots,b_n)=(1)$$

According to the definition, $f$ and $g$ are primitive.

$\Leftarrow$: if $f$ and $g$ are primitive, which means

$$(a_0,a_1,\cdots,a_n) = (b_0,b_1,\cdots,b_n)=(1)$$