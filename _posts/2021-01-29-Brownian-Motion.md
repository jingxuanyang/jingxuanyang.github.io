---
layout: post
title:  "应用随机过程|第5章 布朗运动"
date:   2021-01-29
categories: applied-stochastic-process
tags: applied-stochastic-process stochastic-process Brownian-motion
author: Jingxuan Yang
---

* content
{:toc}

## 引言

+ **布朗运动**作为具有**连续时间参数**和**连续状态空间**的一个随机过程, 是一个最基本最简单同时又是最重要的随机过程, 许多其他的随机过程常常可以看作是它的泛函或某种意义下的推广. 它又是迄今了解得最清楚, 性质最丰富多彩的随机过程之一. 今天, 布朗运动及其推广已广泛地出现在许多纯科学领域中, 如物理, 经济, 通信理论, 生物, 管理科学与数理统计等, 同时, 由于布朗运动与微分方程如热传导方程等有密切的联系, 它又成为**概率与分析**联系的重要渠道.





## 5.1 布朗运动的定义

+ 考虑在一直线上的**简单的**, **对称的**随机游动. 设质点每经过 $\Delta t$ 时间, 随机地以概率 $p=1/2$ 向右移 $\Delta x>0$, 以概率 $q=1/2$ 向左移动一个 $\Delta x$, 且**每次移动相互独立**. 若 $X_t$ 表示 $t$ 时刻质点的位置, 且有 $\Delta t\to0$ 时 $\Delta x=c\sqrt{\Delta t}$, 则
$$
  X_t\sim N(0,c^2t)
$$

**定义 布朗运动**

若一个随机过程 $\{X_t:t\geqslant0\}$ 满足
+ $X_t$ 是**独立增量**过程
+ **增量平稳**且服从期望为0, 方差为 $c^2t$ 的**正态分布**, 即
  $$
    X_{s+t}-X_s\sim N(0,c^2t)
  $$
+ $X_t$ 关于 $t$ 是**连续函数**

则称 $\{X_t:t\geqslant0\}$ 是**布朗运动**或**维纳过程**.

当 $c=1$ 时, 称 $\{X_t:t\geqslant0\}$ 为**标准布朗运动**, 此时若 $X_0=0$, 则称为**零初值标准布朗运动**, 此时
$$
  X_t\sim N(0,t)
$$

本章仅讨论**标准布朗运动**, 记为
$$
  \{B_t:t\geqslant0\}
$$

其在 $t$ 时刻的**概率密度**为
$$
  p(x;t)=\frac{1}{\sqrt{2\pi t}}\exp\left(-\frac{x^2}{2t}\right)
$$
即固定 $t$ 时, 布朗运动 $X_t$ 就是一个遵循正态分布 $N(0,t)$ 的随机变量.

### 布朗运动矩母函数

$B_t$ 的**矩母函数**为
$$
  \phi(s)=E(\mathrm{e}^{sB_t})=\mathrm{e}^{s^2t/2}
$$

### 布朗运动联合概率密度

**定理 布朗运动联合概率密度**

设 $\{B_t:t\geqslant0\}$ 为零初值标准布朗运动, 令 $x_0=0,~t_0=0$, 对
$$
  \forall~0 < t_1 < t_2 < \cdots < t_n
$$
$(B_{t_1},B_{t_2},\cdots,B_{t_n})$ 的联合概率密度函数为
$$
  g(x_1,x_2,\cdots,x_n;t_1,t_2,\cdots,t_n)=\prod_{i=1}^np(x_i-x_{i-1};t_i-t_{i-1})
$$

其中
$$
  p(x;t)=\frac{1}{\sqrt{2\pi t}}\exp\left(-\frac{x^2}{2t}\right)
$$

**证明**: 布朗运动增量独立且遵循正态分布, 则增量联合概率密度等于他们概率密度函数的直接累乘. 布朗运动等于增量求和的变换行列式为1, 则可直接带入得出布朗运动的联合概率密度函数.

给定初始条件 $B_{t_0}=x_0$, 对于任意的 $t>0$, 布朗运动在 $t_0+t$ 时刻的位置高于或低于初始位置的概率相等, 均为 $1/2$, 此即布朗运动的**对称性**.

### 布朗运动马尔可夫性

+ **正向马尔可夫性**

  $\forall~t_1 < t_2 < \cdots < t_n$, 在给定 $B_{t_1},B_{t_2},\cdots,B_{t_{n-1}}$ 下, $B_{t_n}$ 的条件概率密度函数与只给定 $B_{t_{n-1}}$ 下 $B_{t_n}$ 的条件概率密度相同

+ **逆向马尔可夫性**

  $\forall~t_1>t_2>\cdots>t_n$, 在给定 $B_{t_1},B_{t_2},\cdots,B_{t_{n-1}}$ 下, $B_{t_n}$ 的条件概率密度函数与只给定 $B_{t_{n-1}}$ 下 $B_{t_n}$ 的条件概率密度相同

+ **中间关于两边的马尔可夫性**

  $\forall~t_1 < t_2 < \cdots < t_n$, 在给定 $B_{t_1},\cdots,B_{t_{i-1}},B_{t_{i+1}},\cdots,B_{t_{n}}$ 下, $B_{t_i}$ 的条件概率密度函数与只给定 $B_{t_{i-1}},B_{t_{i+1}}$ 下 $B_{t_i}$ 的条件概率密度相同

由以上三种马尔可夫性可知, 布朗运动的条件概率密度函数只和与其**刚好相邻**的事件有关.

**定理 给定两边求中间分布**

对 $0\leqslant t_1 < t < t_2$, 给定 $B_{t_1}=a$, $B_{t_2}=b$, $B_0=0$, 则 $B_t$ 的条件概率密度是正态密度, 其均值为
$$
  \mu=a+\frac{(b-a)(t-t_1)}{t_2-t_1}
$$
方差为
$$
  \sigma^2=\frac{(t_2-t)(t-t_1)}{t_2-t_1}
$$

**证明**: 条件概率密度函数即为 $(B_{t_1},B_t,B_{t_2})$ 联合密度与 $(B_{t_1},B_{t_2})$ 联合密度的直接相除, 通过化简和配方即可得到期望与方差.

### 布朗运动与正态过程

**定义 正态过程**

若随机过程 $X=\{X_t:t\in T\}$ 对任意 $t_i\in T,~i=1,2,\cdots,n$, 有
$$
  (X_{t_1},X_{t_2},\cdots,X_{t_n})
$$
的**联合分布为 $n$ 维正态分布**, 则称 $X$ 为**正态过程**.

**定理 布朗运动的充要条件**

设 $\{B_t:t\geqslant0\}$ 为**正态过程**, **轨道连续**, $B_0=0$, $\forall~s,t>0$, 有
$$
  EB_t=0,~E[B_sB_t]=s\wedge t
$$
则 $\{B_t:t\geqslant0\}$ 为布朗运动, 反之亦然.

**定理 由正态过程导出的布朗运动**

设 $\{B_t:t\geqslant0\}$ 为布朗运动, 则
+ $\{B_{t+\tau}-B_\tau:t\geqslant0\}$, $\forall~\tau\geqslant0$
+ $\displaystyle\left\{\frac{1}{\sqrt{\lambda}}B_{\lambda t}:t\geqslant0\right\}$, $\lambda>0$
+ $\displaystyle\left\{tB\left(\frac{1}{t}\right):t\geqslant0\right\}$, 其中
  $$
    tB\left(\frac{1}{t}\right)\bigg|_{t=0}\triangleq0
  $$
+ $\{B_{t_0+s}-B_{t_0}:0\leqslant s\leqslant t_0\}$, $t_0>0$

仍为布朗运动.

**证明**: 由正态过程, 轨道连续, 期望和协方差可知这些过程满足布朗运动的充要条件.

### 布朗运动的鞅性

**定理 布朗运动的鞅性**

设 $\{B_t:t\geqslant0\}$ 为布朗运动, 则
+ $\{B_t:t\geqslant0\}$
+ $\{B_t^2-t:t\geqslant0\}$
+ $\{\exp(\lambda B_t-\lambda^2t/2):t\geqslant0\}$
+ $\{\exp(\mathrm{i}\lambda B_t+\lambda^2t/2):t\geqslant0\}$

关于布朗运动 $\{B_t:t\geqslant0\}$ 均为鞅.

**证明**: 利用**增量独立性**, 作如下变换
$$
  B_{t_{n+1}}=(B_{t_{n+1}}-B_{t_{n}})+B_{t_{n}}
$$
之后 $(B_{t_{n+1}}-B_{t_{n}})$ 相关项保留期望符号并计算相应的期望值, $B_{t_{n}}$ 相关项直接提出到期望之外, 即得结论.

+ $\{B_t^2-t:t\geqslant0\}$

首先验证绝对值的期望有限,
$$
  E|B_t^2-t|\leqslant E|B_t|^2+t= 2t < \infty
$$

对于
$$
  \forall~0\leqslant t_1 < \cdots < t_n < t_{n+1}
$$
有
$$
  \begin{aligned}
    &~E(B_{t_{n+1}}^2-t_{n+1}\big|B_{t_1},B_{t_2},\cdots,B_{t_n})\\
    =&~E[(B_{t_{n+1}}-B_{t_n})^2-t_{n+1}+2B_{t_{n+1}}B_{t_n}-B_{t_n}^2\big|B_{t_1},B_{t_2},\cdots,B_{t_n}]\\
    =&~(t_{n+1}-t_n)-t_{n+1}+2B_{t_n}E[B_{t_{n+1}}-B_{t_n}+B_{t_n}\big|B_{t_1},B_{t_2},\cdots,B_{t_n}]-B_{t_n}^2\\
    =&~2B_{t_n}^2-B_{t_n}^2-t_n\\
    =&~B_{t_n}^2-t_n\\
  \end{aligned}
$$

则 $\{B_t^2-t:t\geqslant0\}$ 关于布朗运动 $\{B_t:t\geqslant0\}$ 是鞅.

+ $\{\exp(\lambda B_t-\lambda^2t/2):t\geqslant0\}$

注意到, 令 $\{X_t=B_t+\mu t:t\geqslant0\}$ 是漂移系数为 $\mu$ 的布朗运动, 令 $\lambda=-2\mu$, 则 $V_t=\mathrm{e}^{-2\mu X_t}$ 是鞅, 故其在用鞅的停时定理求取漂移布朗运动停时大小概率时颇为有用.

首先验证绝对值的期望有限,
$$
  \begin{aligned}
    &~E|\exp(\lambda B_t-\lambda^2t/2)|\\
    =&~\exp(-\lambda^2t/2)E[\exp(\lambda B_t)]\\
    =&~\exp(-\lambda^2t/2)\int_{-\infty}^\infty\mathrm{e}^{\lambda x}\frac{1}{\sqrt{2\pi t}}\exp\left(-\frac{x^2}{2t}\right)\mathrm{d}x\\
    =&~\exp(-\lambda^2t/2)\int_{-\infty}^\infty\frac{1}{\sqrt{2\pi t}}\exp\left(-\frac{(x-t\lambda)^2-t^2\lambda^2}{2t}\right)\mathrm{d}x\\
    =&~\exp(-\lambda^2t/2)\exp(\lambda^2t/2)\int_{-\infty}^\infty\frac{1}{\sqrt{2\pi t}}\exp\left(-\frac{(x-t\lambda)^2}{2t}\right)\mathrm{d}x\\
    =&~1 < \infty\\
  \end{aligned}
$$

对于
$$
  \forall~0\leqslant t_0 < t_1 < \cdots < t_n < t_{n+1}
$$
有
$$
  \begin{aligned}
    &~E(\exp(\lambda B_{t_{n+1}}-\lambda^2t_{n+1}/2)\big|B_{t_1},B_{t_2},\cdots,B_{t_n})\\
    =&~E(\exp(\lambda(B_{t_{n+1}}-B_{t_n})+\lambda B_{t_n}-\lambda^2t_{n+1}/2)\big|B_{t_1},B_{t_2},\cdots,B_{t_n})\\
    =&~\exp(\lambda B_{t_n}-\lambda^2t_{n+1}/2)E[\exp(\lambda(B_{t_{n+1}}-B_{t_n}))]\\
    =&~\exp(\lambda B_{t_n}-\lambda^2t_{n+1}/2)E[\exp(\lambda B_{t_{n+1}-t_n})]\\
    =&~\exp(\lambda B_{t_n}-\lambda^2t_{n+1}/2)\exp(\lambda^2({t_{n+1}-t_n})/2)\\
    =&~\exp(\lambda B_{t_n}-\lambda^2t_{n}/2)\\
  \end{aligned}
$$

则 $\{\exp(\lambda B_t-\lambda^2t/2):t\geqslant0\}$ 关于布朗运动 $\{B_t:t\geqslant0\}$ 是鞅.

> 由以上结论可知, 布朗运动本身**既是马尔可夫过程**, **又是连续参数鞅**. 这个结果很别致, 但并不奇怪. 因为已讨论的泊松过程, 马尔可夫链, 鞅, 布朗运动等随机过程, 不过是对一些随机过程**某些方面的特殊性质**进行了专门的、分类的讨论, 并不排斥这些性质可以交叉, 可以共存于一个随机过程中. 在介绍这些概念时只能串行讲述, 但实际上要能够**并行应用, 融会贯通.**

## 5.2 布朗运动轨道的性质

**定理**

对给定的 $t>0$, 有
$$
  P\left(\lim_{n\to\infty}\sum_{k=1}^{2^n}\left(B_{\frac{kt}{2^n}}-B_{\frac{(k-1)t}{2^n}}\right)^2=t\right)=1
$$

**引理**

令
$$
  Y_n=\max_{1\leqslant k\leqslant2^n}\left|B_{\frac{kt}{2^n}}-B_{\frac{(k-1)t}{2^n}}\right|
$$

则
$$
  P\left(\lim_{n\to\infty}Y_n=0\right)=1
$$

**定理 布朗运动非有限变差**

$$
  P\left(\lim_{n\to\infty}\sum_{k=1}^{2^n}\left|B_{\frac{kt}{2^n}}-B_{\frac{(k-1)t}{2^n}}\right|=\infty\right)=1
$$

**定理 均方收敛**

固定 $t>0$, 设
$$
  0=t_0 < t_1 < \cdots < t_n=t
$$
记
$$
  \lambda=\max_{1\leqslant k\leqslant n}(t_k-t_{k-1})
$$
则布朗运动差值平方和**均方收敛**到 $t$
$$
  \lim_{\lambda\to0}\sum_{k=1}^n(B_{t_k}-B_{t_{k-1}})^2\overset{\text{m.s.}}{=}t
$$

即两端差值平方的期望极限为 $0$
$$
  \lim_{\lambda\to0}E\left[\sum_{k=1}^n(B_{t_k}-B_{t_{k-1}})^2-t\right]^2=0
$$

**证明**: 记 $Y_k=B_{t_k}-B_{t_{k-1}}$, $1\leqslant k\leqslant n$, 则 $Y_k\sim N(0,t_k-t_{k-1})$.

由**正态分布的性质**可知
$$
  \begin{aligned}
    EY_k^2&=t_k-t_{k-1}\\
    EY_k^4&=3(t_k-t_{k-1})^2\\
  \end{aligned}
$$

又 $Y_k^2$ 相互独立, 故当 $k\neq l$ 时, 有
$$
  \begin{aligned}
    E(Y_k^2Y_l^2)
      &=EY_k^2EY_l^2\\
      &=(t_k-t_{k-1})(t_l-t_{l-1})\\
  \end{aligned}
$$

因此
$$
  \begin{aligned}
    &~E\left[\sum_{k=1}^n(B_{t_k}-B_{t_{k-1}})^2-t\right]^2\\
    =&~E\left(\sum_{k=1}^nY_k^2-t\right)^2\\
    =&~E\left(\sum_{k=1}^nY_k^2\right)^2-2tE\left(\sum_{k=1}^nY_k^2\right)+t^2\\
    =&~\sum_{k=1}^nEY_k^4+2\sum_{k < l}E(Y_k^2Y_l^2)-2t\sum_{k=1}^nEY_k^2+t^2\\
    =&~3\sum_{k=1}^n(t_k-t_{k-1})^2+2\sum_{k < l}(t_k-t_{k-1})(t_l-t_{l-1})-2t\sum_{k=1}^n(t_k-t_{k-1})+t^2\\
    =&~2\sum_{k=1}^n(t_k-t_{k-1})^2+\left(\sum_{k=1}^n(t_k-t_{k-1})\right)^2-2t^2+t^2\\
    =&~2\sum_{k=1}^n(t_k-t_{k-1})^2+t^2-t^2\\
    =&~2\sum_{k=1}^n(t_k-t_{k-1})^2\\
    \leqslant&~2\lambda\sum_{k=1}^n(t_k-t_{k-1})\\
    =&~2\lambda t\to0~(\lambda\to0)\\
  \end{aligned}
$$

其中用到了**求和平方的逆运算**
$$
  \left(\sum_{k=1}^n(t_k-t_{k-1})\right)^2=\sum_{k=1}^n(t_k-t_{k-1})^2+2\sum_{k < l}(t_k-t_{k-1})(t_l-t_{l-1})
$$

故
$$
  \lim_{\lambda\to0}E\left[\sum_{k=1}^n(B_{t_k}-B_{t_{k-1}})^2-t\right]^2=0
$$

所以
$$
  \lim_{\lambda\to0}\sum_{k=1}^n(B_{t_k}-B_{t_{k-1}})^2\overset{\text{m.s.}}{=}t
$$

**定理**

$$
  \lim_{\lambda\to0}\sum_{k=1}^nB_{t_{k-1}}(B_{t_k}-B_{t_{k-1}})\overset{\text{m.s.}}{=}\frac{B_t^2-t}{2}
$$

$$
  \lim_{\lambda\to0}\sum_{k=1}^nB_{t_{k}}(B_{t_k}-B_{t_{k-1}})\overset{\text{m.s.}}{=}\frac{B_t^2+t}{2}
$$

$$
  \lim_{\lambda\to0}\sum_{k=1}^nB_{t_{k}+\theta(t_k-t_{k-1})}(B_{t_k}-B_{t_{k-1}})\overset{\text{m.s.}}{=}\frac{B_t^2-t+2\theta t}{2},\quad0\leqslant\theta\leqslant1
$$

**证明**:
令
$$
  \begin{aligned}
    A_n&=\sum_{k=1}^nB_{t_{k-1}}(B_{t_k}-B_{t_{k-1}})\\
    C_n&=\sum_{k=1}^nB_{t_{k}}(B_{t_k}-B_{t_{k-1}})\\
  \end{aligned}
$$

则
$$
  A_n+C_n=B_t^2,\quad C_n-A_n\overset{\text{m.s.}}{\to}t
$$

故
$$
  A_n\overset{\text{m.s.}}{\to}\frac{B_t^2-t}{2},\quad C_n\overset{\text{m.s.}}{\to}\frac{B_t^2+t}{2}
$$

由于我们只知道区间差平方的均方收敛情况, 故需先将原式化为区间差的平方的组合
$$
  \begin{aligned}
  &\sum_{k=1}^nB_{t_{k}+\theta(t_k-t_{k-1})}(B_{t_k}-B_{t_{k-1}})\\
  =~&\frac{1}{2}\sum_{k=1}^n\Big[B_{t_k}^2-B_{t_{k-1}}^2+(B_{t_{k}+\theta(t_k-t_{k-1})}-B_{t_{k-1}})^2-(B_{t_k}-B_{t_{k}+\theta(t_k-t_{k-1})})^2\Big]\\
  \overset{\text{m.s.}}{\to}~&\frac{1}{2}[B_t^2+\theta t-(1-\theta)t]\\
  =~&\frac{B_t^2-t+2\theta t}{2}.\\
  \end{aligned}
$$

**定理 布朗运动轨道不存在有限导数**

设 $\{B_t:t\geqslant0\}$ 为标准布朗运动, 则对任意固定的 $t\geqslant0$ 和 $h>0$, 有
$$
  P\left(\limsup_{h\downarrow0}\frac{B_{t+h}-B_t}{h}=+\infty\right)=1
$$

$$
  P\left(\liminf_{h\downarrow0}\frac{B_{t+h}-B_t}{h}=-\infty\right)=1
$$

可知布朗运动对几乎所有轨道 $\omega$ 都**没有有限的导数**.

## 5.3 首达时与最大值

### 首达时的分布

设 $\{B_t:t\geqslant0\}$ 为零初值标准布朗运动, 令
$$
  T_a=\inf_{t>0}\{t:B_t=a\}
$$
则 $T_a$ 表示首次到达 $a$ 的时间.

对 $\forall~t>0$,
$$
  M_t=\max_{0\leqslant u\leqslant t}B_u\geqslant0
$$
表示 $[0,t]$ 上布朗运动达到的最大值.

当 $a>0$ 时, 有下列**事件等价关系**
$$
  \{T_a\leqslant t\}=\{M_t\geqslant a\}
$$

即到达 $a$ 的时间若想要小于等于 $t$, 则布朗运动在 $[0,t]$ 上到达的最大值必须大于等于 $a$.

因此有
$$
  P(T_a\leqslant t)=P(M_t\geqslant a)
$$
又由**全概率公式**有
$$
  P(B_t\geqslant a)=P(T_a\leqslant t)P(B_t\geqslant a|T_a\leqslant t)+P(T_a>t)P(B_t\geqslant a|T_a>t)
$$

显然可知
$$
  P(B_t\geqslant a|T_a>t)=0
$$
又由**布朗运动的对称性**可知, 在 $T_a\leqslant t$ 的条件下, 即 $B_{T_a}=a$ 时, $\{B_t\geqslant a\}$ 与 $\{B_t < a\}$ 是等可能的, 即
$$
  P(B_t\geqslant a|T_a\leqslant t)=P(B_t < a|T_a\leqslant t)=\frac{1}{2}
$$

故
$$
  P(T_a\leqslant t)=2P(B_t\geqslant a)
$$

于是 $a>0$ 时有
$$
  \begin{aligned}
    P(T_a\leqslant t)
    &=2P(B_t\geqslant a)\\
    &=2\frac{1}{\sqrt{2\pi t}}\int_a^\infty\exp\left(-\frac{u^2}{2t}\right)\mathrm{d}u\\
    &=2\left[1-\Phi\left(\frac{a}{\sqrt{t}}\right)\right]\\
  \end{aligned}
$$

因此也有
$$
  \begin{aligned}
    P(M_t\leqslant a)
    &=1-P(M_t>a)\\
    &=1-2\left[1-\Phi\left(\frac{a}{\sqrt{t}}\right)\right]\\
    &=2\Phi\left(\frac{a}{\sqrt{t}}\right)-1\\
  \end{aligned}
$$

则 $M_t$ 分布函数为
$$
  F(a)=
  \begin{cases}
    \displaystyle2\frac{1}{\sqrt{2\pi t}}\int_{-\infty}^a\exp\left(-\frac{u^2}{2t}\right)\mathrm{d}u-1,&\text{if}~a>0\\
    0,&\text{if}~a\leqslant0
  \end{cases}
$$

可知 $F(a)$ 连续, 且除 $a=0$ 外其**导数存在且连续**, 故 $M_t$ 为**连续型随机变量**, 其**概率密度函数**为
$$
  p(a)=\frac{2}{\sqrt{2\pi t}}\exp\left(-\frac{a^2}{2t}\right)\pmb{1}_{\{a>0\}}
$$

当 $a < 0$ 时, 由**布朗运动的对称性**有 $P(T_{-a}\leqslant t)=P(T_a\leqslant t)$, 所以对一般的 $a\in\mathbb{R}$ 有
$$
  P(T_a\leqslant t)=2\left[1-\Phi\left(\frac{|a|}{\sqrt{t}}\right)\right]
$$

+ $T_a$ **几乎处处有限**, 因
$$
  \begin{aligned}
    P(T_a < \infty)
      &=\lim_{t\to\infty}P(T_a\leqslant t)\\
      &=2[1-\Phi(0)]\\
      &=1\\
  \end{aligned}
$$
+ $T_a$ **期望为无穷**, 通过**累次积分换序**并**截断积分**进行**放缩**有
$$
  \begin{aligned}
    ET_a
    &=\int_0^\infty P(T_a>t)\mathrm{d}t\\
    &=\frac{2}{\sqrt{2\pi}}\int_0^\infty \int_0^{|a|/\sqrt{t}}\exp\left(-\frac{x^2}{2}\right)\mathrm{d}x\mathrm{d}t\\
    &=\frac{2}{\sqrt{2\pi}}\int_0^\infty \int_0^{a^2/x^2}1\mathrm{d}t\exp\left(-\frac{x^2}{2}\right)\mathrm{d}x\\
    &=\frac{2}{\sqrt{2\pi}}\int_0^\infty \frac{a^2}{x^2}\exp\left(-\frac{x^2}{2}\right)\mathrm{d}x\\
    &\geqslant\frac{2a^2}{\sqrt{2\pi}}\int_0^1\frac{1}{x^2}\cdot\mathrm{e}^{-1/2}\mathrm{d}x=\infty\\
  \end{aligned}
$$

### 首达时的期望

令 $T=\inf\{t:B_t\notin(-r,2r)\},~r>0$, 即
$$
  T=\inf\{t:B_t=-r~\text{or}~B_t=2r\}
$$
由于 $T$ 是停时, 故可用鞅
$$
  \{Z_t=B_t^2-t:t\geqslant0\}
$$
的停时定理来求取 $ET$.

记 $\forall~a\in\mathbb{R}$,
$$
T_a=\inf\{t:B_t=a\}
$$
由 $T_{2r}\subset T$ 有
$$
  1\geqslant P(T < \infty)\geqslant P(T_{2r} < \infty)=1
$$

故
$$
  P(T < \infty)=1
$$
所以
$$
  \sup_{t\geqslant0}|T\wedge t| < \infty
$$
又 $|B_{T\wedge t}|\leqslant 2r$, 则
$$
  \begin{aligned}
    E\left(\sup_{t\geqslant0}|Z_{T\wedge t}|\right)
    &=E\left(\sup_{t\geqslant0}|B_{T\wedge t}^2-{T\wedge t}|\right)\\
    &\leqslant 4r^2+\sup_{t\geqslant0}|T\wedge t| < \infty
  \end{aligned}
$$

故由**连续时间参数鞅停时定理**有
$$
  EZ_{T}=EB_T^2-ET=EZ_0=0
$$

所以
$$
  \begin{aligned}
    ET&=EB_T^2\\
    &=(-r)^2P(T_{-r} < T_{2r})+(2r)^2P(T_{2r}\leqslant T_{-r})\\
    &=r^2\cdot\frac{2}{3}+4r^2\cdot\frac{1}{3}\\
    &=2r^2
  \end{aligned}
$$

其中, $P(T_{-a} < T_{b})$ 这种概率可由5.6节定理取 $\mu\to0$ 极限得到, 也可由鞅的停时定理求得.

令
$$
  T=\inf\{t:B_t=-a~\text{or}~B_t=b\}
$$
$a,b>0$, 易知 $T$ 关于 $B_t$ 是停时,
$$
  P(T < \infty)=1
$$
且
$$
  E\left(\sup_{t\geqslant0}|B_{T\wedge t}|\right)\leqslant \max\{a,b\} < \infty
$$

则由**连续时间参数鞅停时定理**有
$$
  EB_{T}=EB_0=0
$$

即
$$
  EB_T=(-a)P(T_{-a} < T_b)+b[1-P(T_{-a} < T_b)]
$$

所以
$$
  P(T_{-a} < T_b)=\frac{b}{a+b}
$$

## 5.4 布朗运动的变形与推广

### 在某点被吸收的布朗运动

设
$$
  Z_t=
    \begin{cases}
      B_t,&\text{if}~t < T_x\\
      x&\text{if}~t\geqslant T_x\\
    \end{cases}
$$

其中
$$
  T_x=\min_{t>0}\{t:B_t=x\}
$$

$\{Z_t:t\geqslant0\}$ 表示一旦随机过程第一次到达 $x$ 后即被吸收停留在 $x$, 称为在 $x$ 点被**吸收**的布朗运动, 其为**混合型随机变量**.

其分布函数为
$$
  \begin{cases}
    P(Z_t\leqslant y)=1,&\text{if}~y>x\\
    P(Z_t=y)=P(T_y\leqslant t),&\text{if}~y=x\\
    P(Z_t\leqslant y)=P(B_t\leqslant y,M_t < x),&\text{if}~y < x\\
  \end{cases}
$$

其中
$$
  \begin{aligned}
    P(B_t\leqslant y,M_t < x)
    &=P(B_t\leqslant y)-P(M_t\geqslant x,B_t\leqslant y)\\
    &=P(B_t\leqslant y)-P(B_t\geqslant x+x-y)\\
    &=P(B_t\leqslant y)-P(B_t\leqslant y-2x)\\
    &=P(y-2x\leqslant B_t\leqslant y)
  \end{aligned}
$$

### 在原点反射的布朗运动

令 $Y_t=|B_t|$, 则称 $\{Y_t:t\geqslant0\}$ 为在原点反射的布朗运动. 当 $y < 0$ 时,
$$
  P(Y_t\leqslant y)=0
$$

当 $y\geqslant0$ 时,
$$
  \begin{aligned}
    P(Y_t\leqslant y)
      &=P(|B_t|\leqslant y)\\
      &=P(-y\leqslant B_t\leqslant y)\\
      &=2P(B_t\leqslant y)-1\\
  \end{aligned}
$$

### 几何布朗运动

令 $W_t=\mathrm{e}^{B_t}$, 则称 $\{W_t:t\geqslant0\}$ 为几何布朗运动, 且由布朗运动矩母函数可直接得
$$
  EW_t=\mathrm{e}^{t/2},~EW_t=\mathrm{e}^{2t}-\mathrm{e}^{t}
$$

### 布朗运动的积分

令 $\displaystyle S_t=\int_0^tB_u\mathrm{d}u$, 则称 $\{S_t:t\geqslant0\}$ 为布朗运动的积分.
$$
  \begin{aligned}
    ES_t&=0\\
    ES_t^2&=\int_0^t (t-s)^2\mathrm{d}s=\frac{t^3}{3}\\
  \end{aligned}
$$

### 布朗运动的形式导数

令 $D_t=\dfrac{\Delta B_t}{\Delta t}$, 则称 $\{D_t:t\geqslant0\}$ 为布朗运动的形式导数, 是正态过程, 且
$$
  D_t\sim N(0,1/\Delta t)
$$

## 5.5 带有漂移的布朗运动

**定义 带有漂移的布朗运动**

设 $\{B_t:t\geqslant0\}$ 为标准布朗运动, 记
$$
  X_t=B_t+\mu t,~\mu\in\mathbb{R}
$$
称 $\{X_t:t\geqslant0\}$ 为带有漂移系数 $\mu$ 的布朗运动.

**定理 首达时大小关系**

设 $\{X_t=B_t+\mu t:t\geqslant0\}$ 是漂移系数为 $\mu$ 的布朗运动, 对 $a,b>0$, $-b < x < a$, 令
$$
  \begin{aligned}
    T_a&=\min\{t:t>0,X_t=a\}\\
    T_{-b}&=\min\{t:t>0,X_t=-b\}\\
  \end{aligned}
$$
有
$$
  \begin{aligned}
    f(x)
      &=P(T_a < T_{-b} < \infty|X_0=x)\\
      &=\frac{\mathrm{e}^{2\mu b}-\mathrm{e}^{-2\mu x}}{\mathrm{e}^{2\mu b}-\mathrm{e}^{-2\mu a}}\\
  \end{aligned}
$$

特别地, 当 $\mu=0$ 时, 有
$$
  \begin{aligned}
    f(x)
      &=P(T_a < T_{-b} < \infty|X_0=x)\\
      &=\frac{2\mu b+2\mu x}{2\mu b+2\mu a}\\
      &=\frac{b+x}{b+a}
  \end{aligned}
$$

当 $x=0,~\mu=0$ 时, 有
$$
  P(T_a < \infty|X_0=0)=\frac{b}{b+a}
$$

上式与用**连续鞅的停时定理**求出的概率相同.

**证明**: 首先假设 $X_0=0$, 记
$$
  T_{ab}=\inf\{t\geqslant0:X_t=a~\text{or}~X_t=b\}
$$
并且令
$$
  T\wedge n=\min\{T,n\},~T=T_{a(-b)}
$$

因为
$$
  \{B_t=X_t-\mu t:t\geqslant0\}
$$
是鞅, 又易知 $T\wedge n$, $n\geqslant1$ 关于 $B_t$ 是停时, 且
$$
  P(T\wedge n < \infty)=1
$$
故由停时定理有
$$
  0=EB_0=EB_{T\wedge n}=EX_{T\wedge n}-\mu E(T\wedge n)
$$

所以
$$
  E(T\wedge n)\leqslant\frac{1}{\mu}EX_{T\wedge n}\leqslant\frac{1}{\mu}(a+b) < \infty
$$

即对 $\forall~n\geqslant1$ 有
$$
  E(T\wedge n)\leqslant\frac{1}{\mu}(a+b) < \infty
$$

又 $\forall~n\geqslant1$,
$$
  T\wedge n\leqslant T\wedge (n+1)
$$

由**单调收敛定理**, 有
$$
  ET=\lim_{n\to\infty}E(T\wedge n)\leqslant\frac{1}{\mu}(a+b) < \infty
$$

从而
$$
  P(T < \infty)=1
$$

令 $V_t=\mathrm{e}^{-2\mu X_t}$, 前述定理已证明 $V_t$ 是鞅. 由连续鞅停时定理, 有
$$
  EV_T=EV_0=1
$$

则
$$
  P(X_T=a)\cdot\mathrm{e}^{-2\mu a}+P(X_T=-b)\cdot\mathrm{e}^{-2\mu (-b)}=1
$$

所以
$$
  P(X_T=a)=\frac{1-\mathrm{e}^{2\mu b}}{\mathrm{e}^{-2\mu a}-\mathrm{e}^{2\mu b}}
$$

将上述结果向下平移 $x$, 即 $a=a-x$, $-b=-b-x$, 可得
$$
  \begin{aligned}
    P(T_a < T_{-b} < \infty|X_0=x)
    &=\frac{1-\mathrm{e}^{2\mu (b+x)}}{\mathrm{e}^{-2\mu (a-x)}-\mathrm{e}^{2\mu (b+x)}}\\
    &=\frac{\mathrm{e}^{2\mu b}-\mathrm{e}^{-2\mu x}}{\mathrm{e}^{2\mu b}-\mathrm{e}^{-2\mu a}}
  \end{aligned}
$$

**推论**

设 $\{X_t=B_t+\mu t:t\geqslant0\}$ 是漂移系数为 $\mu$ 的布朗运动, 若 $\mu < 0$, 则
$$
  \begin{aligned}
    P(T_a < \infty|X_0=x)
      &=\lim_{b\to\infty}\frac{\mathrm{e}^{2\mu b}-\mathrm{e}^{-2\mu x}}{\mathrm{e}^{2\mu b}-\mathrm{e}^{-2\mu a}}\\
      &=\frac{0-\mathrm{e}^{-2\mu x}}{0-\mathrm{e}^{-2\mu a}}\\
      &=\mathrm{e}^{2\mu (a-x)}\\
  \end{aligned}
$$

特别地, 当 $x=0$ 时, 有
$$
  P(T_a < \infty|X_0=0)=\mathrm{e}^{2\mu a}
$$

当 $x=0,~\mu=0$ 时, 有
$$
  P(T_a < \infty|X_0=0)=1
$$

上式再次验证了 $T_a$ 几乎处处有限的事实.

## 参考文献

+ 林元烈. 应用随机过程[M]. 北京: 清华大学出版社, 2002.
+ 何声武. 随机过程导论[M]. 北京: 高等教育出版社, 1999.
+ Ross S M. Stochastic Processes[M]. John Wiley and Sons, 1993.
