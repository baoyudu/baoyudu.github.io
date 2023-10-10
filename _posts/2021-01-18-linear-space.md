---

title: 线性空间
date: 2021-01-18 15:00
author: Bao
tags: [Math]
summary: 映射,线性空间与n维向量空间的定义
math: true
---

## 基本定义

>若对应法则$f: A\rightarrow B$满足每个$a\in A$对应唯一的$b\in B$, 则称 $\mathrm{f}$ 是 $\mathrm{A}$ 到 $\mathrm{B}$ 的一个映射, $\mathrm{b}$ 是 $\mathrm{a}$ 在 $\mathrm{f}$ 下的像, 记作 $\mathrm{f}(\mathrm{a})$. 称 $\mathrm{a}$ 是 $\mathrm{b}$ 在 $\mathrm{f}$ 下的一个原像.
> A称为**定义域(Domain)**,B称为**陪域**(Codomain).$f(A):= \{f(a)\vert a\in A\}$称为**值域**.
{:.def}

> 若$f(A) = B$,则f称为一个**满射**.
> 如果$A$中不同元素在$f$下的像不同,称$f$为**单射**.
> 如果$f$既是单射又是满射,则f称为一个**双射**(一一对应).
{:.def}
---

> **定义 笛卡尔积**
>
> $S \times M :=\{(a,b)\|a \in S,b \in M\} $ 称为$S$与$M$的**笛卡尔积**.
{:.def}

---

>**定义**
>
>非空集合$S$上的一个**代数运算**是指$S\times S$到$S$的一个映射.
>
{:.def}

> 注意极限不是代数运算

---

>**定义**
>
> 设$V$是一个非空集合,$K$是一个数域.
> 如果$V$上有一个运算,称为加法,即
>
> $$(\alpha ,\beta ) \rightarrowtail \alpha+\beta$$
>
> $K$和$V$之间有一个运算,称为**数量乘法**.即 
> 
> $$
> K \times V \rightarrow V:(k,\alpha) \rightarrowtail k\alpha
> $$
> 
> 且满足8条运算性质
> V就称为数域K上的一个**线性空间**.
{:.def}


## 线性空间的例子:n维向量空间

令
$$
 K ^{n} = \{(a_1,a_2,...a_n)|a_i \in K,i = 1,2,...,n \} 
$$

 规定
 $$
  (a_1,a_2,...a_n)=(b _1,b _2,...,b _n)\\
  \stackrel{\triangle}{\iff} \\
  a_i = b_i,i=1,2,...,n.
 $$

 规定

$$
\begin{aligned}
    数量乘法\ &k(a_1,a_2,,...,a_n)=(k a_1,k a_2 ,...,k a_n)\\
 加法\ &(a_1,a_2,...a_n)+(b _1,b _2,...,b _n)=(a_1+b _1,a_2+b _2,...,a_n+b _n)
\end{aligned}
$$ 

并满足8条运算性质

|加法|数乘
|---|---
|交换律|单位元素
|结合律|交换律
|零元素|左分配律
|负元素|右分配率

则 $K^n是一个$K$上的$n$维向量空间.它是数域$K$上的一个线性空间.




## 其他性质

设$V$$是数域$K$上的一个线性空间

> V的零元唯一
{:.thm}
**证明**:
设 $O_1,O_2$都是V的零元,则
$$
     O_1 = O_1+\stackrel{零元}{O_2}  =O_2+\stackrel{零元}{O_1}= O_2 
$$

> 每个$\alpha \in V$的负元唯一
{:.thm}

**证明**:
设$\beta_1,\beta_2$都是 $\alpha$的负元,则

$$
  \beta _1 + \alpha +\beta _2=\beta _1+(\alpha + \beta _2)=(\beta_1+\alpha )+\beta _2 = \beta _1 = \beta _2
$$

> $0\alpha = \stackrel{零元}{ \vec{0}}$
{:.thm}

**证明**:
$$
 0\alpha = (0+0)\alpha=0 \alpha + 0\alpha 
$$

两边加$0\alpha$的负元,得
$$
 0 = 0 \alpha  
$$

> $k\vec{0}= \vec{0}$
{:.thm}

**证明思路**:
零元是加法的性质,$k0$是数量乘法,要利用他们的"桥梁"性质$8$
$$
 k0=k(0+0)=k0+k0
$$

两边加$k0$的负元

$$
  0 = k\vec{0}
$$

> $k\alpha = 0$则k = 0或者$\alpha = 0$
{:.thm}

**证明**:
假设k = 0,则

$$
 \alpha = 1\alpha = kk ^{-1} \alpha =k (k\alpha) = k\mathbf0 \xlongequal{由(4)} \mathbf{0}
$$

> $(-1)\alpha = -\alpha$
{:.thm}

**证明**:
$$
(-1)\alpha + \alpha =(-1)\alpha + 1 \alpha =(-1+1)\alpha  = 0 \alpha \xlongequal{由(3)}\mathbf0
$$

## 线性子空间

定义 设V是数域K上的一个线性空间,U是V的一个非空子集,如果U对于V的加法和数量乘法也成为数域K上的一个线性空间,那么称U是V的一个线性子空间.