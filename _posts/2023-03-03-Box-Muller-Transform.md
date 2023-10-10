---
title: 深入理解Box-Muller变换
tags: [统计学]
summary: 静态页面Markdown渲染与LaTex数学公式引擎MathJax之间的冲突及其解决方案
published: true
math: true
---


通过计算机程序模拟生成服从均匀分布非常容易，但我们更常使用的是正态分布随机数。Box-Muller变换可以高效地利用均匀分布随机数生成正态分布随机数。

假设$(X,Y)$是平面上的一个随机的点，并假设其坐标$X$和$Y$是独立的标准正态随机变量。我们感兴趣的是$R,\Theta$的联合分布，即$(x,y)$的极坐标表示。

先假设$X$和$Y$都是正数。对于正的$x$和$y$，令 $r=\sqrt{x^2+y^2}$ 和 $\theta=\tan^{-1}y/x$，我们可以看出

$$
 \begin{aligned} \frac{\partial g_1}{\partial x} & =\frac{x}{\sqrt{x^2+y^2}} \\ \frac{\partial g_1}{\partial y} & =\frac{y}{\sqrt{x^2+y^2}} \end{aligned} 
$$

$$ 
\begin{aligned}
 & \frac{\partial g_2}{\partial x}=\frac{1}{1+(y / x)^2}\left(\frac{-y}{x^2}\right)=\frac{-y}{x^2+y^2} \\ & \frac{\partial g_2}{\partial y}=\frac{1}{x\left[1+(y / x)^2\right]}=\frac{x}{x^2+y^2} 
 \end{aligned} 
$$ 

因此， 

$$ 
J(x, y)=\frac{x^2}{\left(x^2+y^2\right)^{3 / 2}}+\frac{y^2}{\left(x^2+y^2\right)^{3 / 2}}=\frac{1}{\sqrt{x^2+y^2}}=\frac{1}{r} 
$$

由于在$X$和$Y$都为正的条件下，$X,Y$的条件联合密度函数是

$$ 
f(x, y \mid X>0, Y>0)=\frac{f(x, y)}{P(X>0, Y>0)}=\frac{2}{\pi} e^{-\left(x^2+y^2\right) / 2}, x>0, y>0 
$$ 

我们可以看出当$X$和$Y$都为正时$R=\sqrt{X^2+Y^2}$ 和 $\Theta=\tan ^{-1}(Y / X)$的条件联合密度函数是

$$
f(r, \theta \mid X>0, Y>0)=\frac{2}{\pi} r e^{-r^{2 / 2}}, \quad 0<\theta<\pi / 2, \quad 0<r<\infty 
$$

由于我们研究的情况具有对称性, 很容易验证上面的联合密度函数对$X$和$Y$不都为正时也成立, 于是有

$$ f(r, \theta)=\frac{1}{2 \pi} r e^{-r^2 / 2} \quad 0<\theta<2 \pi, \quad 0<r<\infty $$
 现在，这个联合密度函数可以分解为$R$和$\Theta$的边缘密度函数，因此$R$和$\Theta$是相互独立的随机变量，其中$\Theta$均匀地分布于 $(0,2 \pi)$，$R$具有参数为$\frac{1}{2}$的Rayleigh分布，其密度函数为 

$$
f(r)=r e^{-r^2 / 2} \quad 0<r<\infty 
$$

> 当一个弓箭手瞄准靶心时，如果水平和垂直的误差距离是独立的标准正态分布，误差的绝对值就服从Rayleigh分布。

这是个很符合直觉的结论，若二维平面上点的横纵坐标服从$iid$的正态分布，其方位角不仅是均匀分布的，并且与向量到原点的距离无关。
现在, 我们还想知道$R^2$和$\Theta$的联合分布，由于变换$d=g_1(x, y)=x^2+y^2$和$\theta=g_2(x, y)=\tan^{-1}y / x$的雅可比行列式为 

$$
J=\left|
\begin{array}{cc} 2 x & 2 y \\
\frac{-y}{x^2+y^2} & \frac{x}{x^2+y^2} \end{array}
\right|=2 
$$

因此，经过变量替换，我们得到 
$$ f(d, \theta)=\frac{1}{2} e^{-d / 2} \frac{1}{2 \pi} \quad 0<d<\infty, \quad 0<\theta<2 \pi $$ 因此，$R^2$和$\Theta$是独立的，其中$R^2$具有参数为$\frac{1}{2}$的指数分布。

> 也可以利用卡方分布的构造, 根据$R^2=X^2+Y^2$，也可以发现$R^2$是具有2个自由度的卡方分布, 即指数分布。

不要忘了我们的目标是把均匀分布转换为正态分布, 或者说, 用均匀分布把正态分布表示出来.
既然满足正态分布的$X_1=R\cos\Theta$, 且$\Theta$服从$(0,2\pi)$上的均匀分布, 只剩服从指数分布的$R^2$需要处理, 也就是说, **现在我们只需要把均匀分布转换为指数分布**. 

设$U_1$和$U_2$是独立随机变量，服从区间$(0,1)$上的均匀分布。很容易验证对于$x>0$，$-2 \log U_1$服从指数分布，因为

$$ 
\begin{aligned} 
P\left(-2 \log U_1<x\right) & =P\left(\log U_1>-\frac{x}{2}\right) \\ & =P\left(U_1>e^{-x / 2}\right) \\ & =1-e^{-x / 2} 
\end{aligned}
$$

而$2\pi U_2$是一个$(0,2\pi)$上的均匀分布的随机变量，我们可以用它来生成$\Theta$。令 

$$
\begin{aligned} & R^2=-2 \log U_1 \\ & \Theta=2 \pi U_2 \end{aligned} 
$$

现在，由于$X_1=R\cos\Theta, X_2=R\sin\Theta$，可以得到 

$$
\begin{aligned} 
& X_1=\sqrt{-2 \log U_1} \cos \left(2 \pi U_2\right) \\ & X_2=\sqrt{-2 \log U_1} \sin \left(2 \pi U_2\right) 
\end{aligned} 
$$ 

是独立的标准正态分布随机变量。