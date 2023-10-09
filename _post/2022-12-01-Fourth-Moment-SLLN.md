---
layout: post
title: 最容易证明的强大数定律
tags: [数学]
summary: 
math: true
---

四阶矩强大数定律虽然对“有限$4$阶矩”的条件作了限制，但并没有假设$\left(X_n\right)$序列的同分布, 而且这个很好的结论并不需要复杂的证明.

> **Theorem**
> 假设$X_1, X_2, \ldots$是独立的随机变量，并且存在$[0,\infty)$中的一个常数$K$，使得： 
>
> $$\mathrm{E}\left(X_k\right)=0, \quad \mathrm{E}\left(X_k^4\right) \leq K, \quad \forall k .
> $$
> 
> 令 $S_n=X_1+X_2+\cdots+X_n$. 则
> 
> $$
>\mathbf{P}\left(n^{-1} S_n \rightarrow 0\right)=1,
> $$
> 
> 即
> 
> $$
> S_n / n \rightarrow 0, a.s.
> $$
> 
{:.thm}

证明： 我们有

$$
\begin{aligned} 
\mathrm{E}\left(S_n^4\right) & =\mathrm{E}\left[\left(X_1+X_2+\cdots+X_n\right)^4\right] \\ & =\mathrm{E}\left(\sum_k X_k^4+6 \sum \sum_{i<j} X_i^2 X_j^2\right), 
\end{aligned} 
$$

因为，对于不同的$i, j, k$和$l$，

$$ 
\mathrm{E}\left(X_i X_j^3\right)=\mathrm{E}\left(X_i X_j^2 X_k\right)=\mathrm{E}\left(X_i X_j X_k X_l\right)=0, 
$$

利用独立性和$\mathrm{E}\left(X_i\right)=0$。

注意$\mathrm{E}\left(X_j^4\right)<\infty$意味着$\mathrm{E}\left(X_j^3\right)<\infty$，(因为“$\mathcal{L}^p$范数的单调性”)。因此，$X_i$和$X_j^3$都在$\mathcal{L}^{\mathbf{1}}$中。

我们知道 

$$ 
\left[\mathrm{E}\left(X_i^2\right)\right]^2 \leq \mathrm{E}\left(X_i^4\right) \leq K, \quad \forall i . 
$$ 

因此，再次利用独立性，对于$i \neq j$， 

$$
 \mathrm{E}\left(X_i^2 X_j^2\right)=\mathrm{E}\left(X_i^2\right) \mathrm{E}\left(X_j^2\right) \leq K 
$$ 

 因此， 

$$
  \mathrm{E}\left(S_n^4\right) \leq n K+3 n(n-1) K \leq 3 K n^2, 
$$ 

和 

$$ 
\mathrm{E} \sum\left(S_n / n\right)^4 \leq 3 K \sum n^{-2}<\infty 
$$ 

因此$\sum\left(S_n / n\right)^4<\infty, a.s.$，，且 
 
$$ S_n / n \rightarrow 0, \quad a.s. $$

> **Corollary**
> 如果定理中的条件$\mathrm{E}\left(X_k\right)=0$被替换为$\mathrm{E}\left(X_k\right)=\mu$，其中$\mu$是常数，则定理的结论为$n^{-1}S_n\rightarrow\mu , a.s.$ .
{:.thm}

证明： 显然，令$Y_k:=X_k-\mu$,就可以将将定理应用于序列$\left(Y_k\right)$，但我们需要

$$\sup _k \mathrm{E}\left(Y_k^4\right)<\infty$$ 

这可以通过Minkowski不等式 $$ \left\|X_k-\mu\right\|_4 \leq\left\|X_k\right\|_4+\|\mu\| $$ 得到.