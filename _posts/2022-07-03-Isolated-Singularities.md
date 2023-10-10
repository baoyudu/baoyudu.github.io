---
title: 孤立奇点
math: true
---
Laurent级数是研究全纯函数在孤立奇点附近性质的有力工具.

# 定义

## 通过附近的极限情况来定义

如果 $f$ 在无心圆盘 $\{z: 0<|z-z_{0}|<R\}$ 中解析, 就称 $z_{0}$ 是 $f$ 的**孤立奇点**.
$f$ 在孤立奇点 $z_{0}$ 附近可能有三种情形:

(1) $\lim_{z \rightarrow z_{0}} f(z)=a, a$ 是一有限数, 这时称 $z_{0}$ 是 $f$ 的**可去奇点**;

(2) $\lim_{z \rightarrow z_{0}} f(z)=\infty$, 这时称 $z_{0}$ 是 $f$ 的**极点**;

(3) $\lim_{z \rightarrow z_{0}} f(z)$ 不存在, 这时称 $z_{0}$ 是 $f$ 的**本性奇点**.

## 通过Laurent展开来定义


i. 如果当 $n=-1,-2,-3, \cdots$ 时, $\alpha_{n}=0$, 那么我们说 $z_{0}$ 是函数 $f(z)$ 的**可去奇点**, 或者说 $f(z)$ 在 $z_{0}$ 有可去奇点. 这是因为令 $f\left(z_{0}\right)=\alpha_{0}$, 就得到在整个圆盘 $\mid z-$ $z_{0} \mid<R$ 内解析的函数 $f(z)$.

ii. 如果只有有限个(至少一个) 整数 $n<0$, 使得 $\alpha_{n} \neq 0$, 那么我们说 $z_{0}$ 是函 数 $f(z)$ 的**极点**. 设对于正整数 $m, \alpha_{-m} \neq 0$; 而当 $n<-m$ 时, $\alpha_{n}=0$. 那么我们就说 $z_{0}$ 是 $f(z)$ 的 **$m$ 阶极点**. 

iii. 如果有无限个整数 $n<0$, 使得 $\alpha_{n} \neq 0$, 那么我们说 $z_{0}$ 是 $f(z)$ 的**本质奇点**.



> 
> 0 分别是 $\frac{\sin z}{z}, \frac{\sin z}{z^{2}}$ 及 $\mathrm{e}^{\frac{1}{z}}$ 的可去奇点、单极点及 本质奇点.
> 

# 性质


(Weierstrass) 设 $z_{0}$ 是 $f$ 的本性奇点,那么对任意 $A \in \mathbb{C}_{\infty}$, 必存在趋于 $z_{0}$ 的点列 $\left \\{ z_{n}\right\\}$, 使得 $\lim _{n \rightarrow \infty} f\left(z_{n}\right)=A$.


证:
先设 $A=\infty$. 因为 $z_{0}$ 是 $f$ 的本性奇点, 故 $f$ 在 $z_{0}$ 附近无界. 于是对任意自然 数 $n$, 总能找到 $z_{n}$, 使得 $\left|z_{n}-z_{0}\right|<\frac{1}{n}$, 但 $\left|f\left(z_{n}\right)\right|>n$, 这说明 $\lim _{n \rightarrow \infty} f\left(z_{n}\right)=\infty$.

再设 $A$ 是一个有限数. 
令 $\varphi(z)=\frac{1}{f(z)-A}$, 我们证明 $\varphi$ 在 $z_{0}$ 的邻域中无界. 不然的话, $z_{0}$ 是 $\varphi$ 的可去奇点, 适当选择 $\varphi\left(z_{0}\right)$ 的值, 可使 $\varphi$ 在 $z_{0}$ 处全纯. 如果 $\varphi\left(z_{0}\right) \neq 0$, 则因 $f(z)=\frac{1}{\varphi(z)}+A, f$ 也在 $z_{0}$ 处全纯, 这不可能. 故必有$\varphi\left(z_{0}\right)=0$, 这说明 $z_{0}$ 是 $f$ 的极点, 也不可能. 所以, $\varphi$ 在 $z_{0}$ 的邻域中无界. 于是, 对任意自然数 $n$, 存在 $z_{n}$, 使得 $\left|z_{n}-z_{0}\right|<\frac{1}{n}$, 但 $\frac{1}{|f(z)-A|}>n$, 即 $|f(z)-A|<\frac{1}{n}$. 这就证明了 $\lim _{n \rightarrow \infty} f\left(z_{n}\right)=A$.

后来,Picard 又证明了比 Weierstrass 定理更进一步的结果：



(Picard) 全纯函数在本性奇点的邻域内**无穷多次地取到每个有穷复值**, 最多只有一个例外.


例如, 考虑函数 $f(z)=\mathrm{e}^{\frac{1}{z}}$, 它在 $z=0$ 附近是全纯的. 若让 $z$ 沿着 $x$ 轴分别从 0 的 左边和右边趋于 0 , 可得

$$
\begin{aligned}
&\lim _{z=x \rightarrow 0^{-}} \mathrm{e}^{\frac{1}{z}}=\lim _{x \rightarrow 0^{-}} \mathrm{e}^{\frac{1}{x}}=0, \\
&\lim _{z=x \rightarrow 0^{+}} \mathrm{e}^{\frac{1}{z}}=\lim _{x \rightarrow 0^{+}} \mathrm{e}^{\frac{1}{x}}=\infty
\end{aligned}
$$

这说明 $\lim _{z \rightarrow 0} \mathrm{e}^{\frac{1}{z}}$ 不存在, 所以 $z=0$ 是 $\mathrm{e}^{\frac{1}{z}}$ 的本性奇点. 对于任意复数 $a \neq 0$, 若取 $z_{n}=(\log a+2 n \pi \mathrm{i})^{-1}$, 则 $f\left(z_{n}\right)=\mathrm{e}^{\log a+2 n \pi \mathrm{i}}=a$. 由于 $z_{n} \rightarrow 0$, 这说明 $\mathrm{e}^{\frac{1}{z}}$ 在 $z=0$ 的邻域中可以无穷多次地取到非零值 $a$, 但 0 是它的唯一的例外值.

# 无穷远为孤立奇点


如果 $f$ 在无穷远点的去心邻域(不包括无穷远点)$\\{z: 0 \leqslant R\<\vert z\vert \<\infty\\}$ 中全纯, 就称 $\infty$ 是 $f$ 的孤立奇点.


在这种情形下, 作变换 $z=\frac{1}{\zeta}$, 记

$$
g(\zeta)=f\left(\frac{1}{\zeta}\right)
$$

则 $g$ 在 $0<\vert \zeta \vert <\frac{1}{R}$ 中全纯, 即 $\zeta=0$ 是 $g$ 的孤立奇点. 


如果 $\zeta=0$ 是 $g$ 的可去奇点、 $m$ 阶极点或本性奇点, 那么我们相应地称 $z=\infty$ 是 $f$ 的可去奇点、 $m$ 阶极点或本性奇点.


因为 $g$ 在原点的邻域中有 Laurent 展开:

$$
g(\zeta)=\sum_{n=-\infty}^{\infty} b_{n} \zeta^{n}, 0<\vert \zeta \vert <\frac{1}{R}
$$

所以 $f$ 在 $R<\vert z \vert <\infty$ 中有下面的 Laurent 展开:

$$
f(z)=\sum_{n=-\infty}^{\infty} a_{n} z^{n}
$$

其中 $a_{n}=b_{-n}, n=0, \pm 1, \cdots$.

## 无穷为可去奇点

如果 $z=\infty$ 是 $f$ 的可去奇点, 即 $\zeta=0$ 是 $g$ 的可去奇点, 因而 $b_{n}=0$ $(n=-1,-2, \cdots)$, 即$g$的负次幂的系数都为零, 所以 $f$ 只剩下解析部分和常数, 其Laurent 展开为

$$
f(z)=\sum_{n=0}^{\infty} a_{-n} z^{-n}
$$

## 无穷为极点或本性奇点

如果 $z=\infty$ 分别是 $f$ 的 $m$ 阶极点或本性奇点, 那么 $f$ 在 $ R < \vert z \vert < \infty$ 中分别有下面的 Laurent 展开式:

$$
f(z)=a_{m} z^{m}+\cdots+a_{1}+a_{0}+a_{-1} z^{-1}+\cdots
$$

或

$$
f(z)=\cdots+a_{m} z^{m}+\cdots+a_{1} z+a_{0}+a_{-1} z^{-1}+\cdots .
$$

> 
> 对于无穷远为孤立奇点的情况, 反过来称 $\sum_{n=1}^{\infty} a_{n} z^{n}$ 为 $f$ 的主要部分, $\sum_{n=0}^{\infty} a_{-n} z^{-n}$ 为 $f$ 的解析部分.