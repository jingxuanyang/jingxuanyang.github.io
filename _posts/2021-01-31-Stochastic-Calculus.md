---
layout: post
title:  "应用随机过程|第7章 随机微分方程"
date:   2021-01-31
categories: applied-stochastic-process
tags: applied-stochastic-process stochastic-process stochastic-calculus
author: Jingxuan Yang
mathjax: true
---

* content
{:toc}


## 7.1 H 空间和均方收敛

+ 在许多情况下, 人们关心的是一个过程的一阶矩、二阶矩特征, 这是比较容易得到的随机变量的外部数字特征. 因此, 研究二阶矩存在的随机变量是一个重要的方向, 通过深入分析来探知这类随机变量有哪些共同的性质
+ 为了对存在二阶矩的随机变量的全体进行统一考察, 引出 $H$ 空间的概念, 为研充这一类随机变量提供数学框架与几何直观解释





**定义 H 空间**

$H\triangleq\{X:E|X|^2 < \infty\}$, 即 $H$ 是由二阶矩存在的随机变量全体构成的集合, 称作 $H$ 空间.

**H 空间性质**

$H$ 空间是线性空间, 即 $\forall~X_1,X_2\in H$ 及常数 $\alpha_1,\alpha_2\in\mathbb{R}$, 都有
$$
  \alpha_1X_1+\alpha_2X_2\in H
$$
成立.

**证明**: 由 Cauchy-Schwartz 公式可得
$$
  \begin{aligned}
    E|\alpha_1X_1+\alpha_2X_2|^2&=E|\alpha_1^2X_1^2+2\alpha_1\alpha_2X_1X_2+\alpha_2^2X_2^2|\\
    &\leqslant \alpha_1^2E|X_1|^2+2|\alpha_1\alpha_2|E|X_1X_2|+\alpha_2^2E|X_2|^2\\
    &\leqslant\alpha_1^2E|X_1|^2+2|\alpha_1\alpha_2|\sqrt{E|X_1|^2E|X_2|^2}+\alpha_2^2E|X_2|^2\\
    & < +\infty
  \end{aligned}
$$
所以 $\alpha_1X_1+\alpha_2X_2\in H$.

**定义 内积**

$\forall~X,Y\in H$, 定义内积为
$$
  \langle X,Y\rangle=E(XY)
$$

**内积性质**

+ **共轭对称**: $\langle Y,X\rangle=\langle X,Y\rangle$
+ **齐次性**: $\langle cX,Y\rangle=c\langle X,Y\rangle$, $c\in\mathbb{R}$
+ **线性**: $\langle X_1+X_2,Y\rangle=\langle X_1,Y\rangle+\langle X_2,Y\rangle$
+ **非负性**: $\langle X,X\rangle=E|X|^2\geqslant0$, $\langle X,X\rangle=0\Leftrightarrow X=0$ (a.e.)

**定义 正交**

若 $\langle X,Y\rangle=0$, 则称 $X$ 与 $Y$ 正交, 记为 $X\perp Y$.

**定义 范数**

对 $\forall~X\in H$, 定义范数为
$$
  \|X\|=\sqrt{\langle X,X\rangle}=\sqrt{E|X|^2}
$$

**范数性质**

+ **非负性**: $\|X\|\geqslant0$, $\|X\|=0\Leftrightarrow X=0$ (a.e.)
+ **齐次性**: $\|cX\|=|c|\|X\|$, $c\in\mathbb{R}$
+ **三角不等式**: $\|X_1+X_2\|\leqslant\|X_1\|+\|X_2\|$
+ **不等式**: $|EX|\leqslant E|X|\leqslant\|X\|$, 由凸函数性质和 Cauchy-Schwartz 公式可得

**定义 距离**

对 $\forall~X,Y\in H$, 定义距离为
$$
  \begin{aligned}
    d(X,Y)
      &=\|X-Y\|\\
      &=\sqrt{\langle X-Y,X-Y\rangle}\\
      &=\sqrt{E|X-Y|^2}\\
  \end{aligned}
$$

**距离性质**

+ **非负性**: $d(X,Y)\geqslant0$, $d(X,Y)=0\Leftrightarrow X=Y$ (a.e.)
+ **对称性**: $d(X,Y)=d(Y,X)$
+ **三角不等式**: $d(X,Z)\leqslant d(X,Y)+d(Y,Z)$

**定义 极限与收敛**

设 $X,X_n\in H,~n\geqslant1$, 若
$$
  \begin{aligned}
    \lim_{n\to\infty}d(X_n,X)
      &=\lim_{n\to\infty}\|X_n-X\|\\
      &=\lim_{n\to\infty}\sqrt{E|X_n-X|^2}\\
      &=0\\
  \end{aligned}
$$

则称 $X$ 为序列 $\{X_n,n\geqslant1\}$ 的**均方极限**, 记作
$$
  \lim_{n\to\infty}X_n\overset{\mathrm{m.s.}}{=}X
$$
其中 m.s. 表示 mean square, 简记为
$$
  \lim_{n\to\infty}X_n=X,~X_n\overset{\mathrm{m.s.}}{\rightarrow}X
$$
即序列 $\{X_n,n\geqslant1\}$ **均方收敛**于 $X$.

**定义 Cauchy 序列**

设 $X_n\in H,~n\geqslant1$, 若
$$
  \lim_{m,~n\to\infty}d(X_m,X_n)=0
$$
则称 $\{X_n,n\geqslant1\}$ 是 **Cauchy 序列**.

**命题 完备的赋范线性空间**

设 $\{X_n,n\geqslant1\}$ 为 $H$ 空间中的 Cauchy 序列, 则必存在随机变量 $X\in H$ 使得
$$
  X_n\overset{\mathrm{m.s.}}{\rightarrow}X
$$

**命题 均方极限的运算法则**

设 $X_n,X,Y_n,Y\in H$, 且
$$
  X_n\overset{\mathrm{m.s.}}{\rightarrow}X,~Y_n\overset{\mathrm{m.s.}}{\rightarrow}Y
$$
则
+ **极限与期望可交换**:
  $$
    \lim_{n\to\infty}EX_n=EX=E\lim_{n\to\infty}X_n
  $$
  $$
    \lim_{n\to\infty}E|X_n|^2=E|X|^2
  $$
+ **极限与内积可交换**:
  $$
    \lim_{m,~n\to\infty}\langle X_m,Y_n\rangle=\langle X,Y\rangle
  $$
+ **线性**:
  $$
    \lim_{n\to\infty}(\alpha X_n+\beta Y_n)=\alpha X+\beta Y,~\forall~\alpha,\beta\in\mathbb{R}
  $$

**命题 收敛的充要条件**

$$
  \lim_{n\to\infty}X_n=X\Leftrightarrow\lim_{m,~n\to\infty}\langle X_m,X_n\rangle=C,~C\in\mathbb{R}
$$
且此时
$$
  \lim_{m,~n\to\infty}\langle X_m,X_n\rangle=C=E|X|^2=\|X\|^2
$$

**命题 均方收敛与依概率、分布收敛的关系**

若序列 $\{X_n,n\geqslant1\}$ 均方收敛
$$
  \lim_{n\to\infty}X_n\overset{\mathrm{m.s.}}{=}X
$$
则
+ **依概率收敛**:
  $$
    \lim_{n\to\infty}X_n\overset{P}{=}X
  $$
+ **依分布收敛**:
  $$
    \lim_{n\to\infty}P(X_n\leqslant x)=P(X\leqslant x)
  $$
  其中 $x\in\mathbb{R}$ 是 $P(X\leqslant x)$ 的连续点, 即
  $$
    X_n\overset{d}{\to}X~(n\to\infty)
  $$

## 7.2 均方分析

+ 在引出**均方极限**之后, 就可以对过程的均方分析特性展开深入的讨论. 类似于数学分析中的概念, 本节介绍**均方分析**, 亦称为**随机微积分**, 即均方连续性, 均方可导, 均方积分

**定义 二阶矩过程**

设 $\{X_t:t\geqslant0\}$ 为一随机过程, 若
$$
  \forall~t\geqslant0,X_t\in H
$$
则称 $\{X_t:t\geqslant0\}$ 为**二阶矩过程**.

### 均方连续性

**定义 均方连续**

设二阶矩过程 $\{X_t:t\in T\}$ 对 $\forall~t_0\geqslant0$ 有
$$
  \lim_{t\to t_0}X_t\overset{\mathrm{m.s.}}{=}X_{t_0}
$$
即
$$
  \quad\lim_{t\to t_0}X_t-X_{t_0}\overset{\mathrm{m.s.}}{=}0
$$
则称 $X_t$ 在 $t_0$ 点**均方连续**.

若 $X_t$ 对 $\forall~t\in T$ 都均方连续, 则称 $\{X_t:t\in T\}$ 在 $T$ 上均方连续.

**定理 均方连续的充要条件**

记
$$
  R(s,t)=E(X_sX_t)=\langle X_s,X_t\rangle
$$

则 $\{X_t:t\geqslant0\}$ 在 $t_0$ 点**均方连续的充要条件**为 $R(s,t)$ 在 $(t_0,t_0)$ 点连续.

**推论 全定义域均方连续的充要条件**

$\{X_t:t\in T\}$ 在 $T$ 上均方连续的充要条件为 $R(s,t)$ 在 $\{(t,t):t\in T\}$ 上二元连续.

**推论 全区域均方连续与对角线均方连续等价**

若 $R(s,t)$ 在 $\{(t,t):t\in T\}$ 上连续, 则它在 $T\times T$ 上连续. 即对协方差 $R(s,t)$ 而言, 它在整个区域 $T\times T$ 上连续与它在 $T\times T$ 的对角线上连续是等价的.

### 均方可导

**定义 均方导数与均方微分**

称二阶矩过程 $\{X_t:t\in T\}$ 在 $t_0\in T$ 点上**均方可导**, 若
$$
  \lim_{h\to0}\frac{X_{t_0+h}-X_{t_0}}{h}\overset{\mathrm{m.s.}}{=}X_{t_0}'
$$
存在, 此时称 $X_{t_0}'$ 与 $X_{t_0}'\mathrm{d}t$ 分别为 $X_t$ 在 $t_0$ 点的**均方导数**与**均方微分**.

若 $X_t$ 对 $\forall~t\in T$ 均方可导, 则称 $\{X_t:t\in T\}$ 在 $T$ 上是均方可导的, 此时记
$$
  \lim_{h\to0}\frac{X_{t+h}-X_{t}}{h}\overset{\mathrm{m.s.}}{=}X_{t}'
$$
$X_{t}'$ 与 $X_{t}'\mathrm{d}t$ 分别称为 $X_t$ 在 $T$ 上的**均方导数**与**均方微分**.

**定理 均方可导判定准则**

二阶矩过程 $\{X_t:t\in T\}$ 在 $t$ 点**均方可导的充要条件**是
$$
  \lim_{h,~l\to0}\frac{R(t+h,t+l)-R(t+h,t)-R(t,t+l)+R(t,t)}{hl}
$$
存在, 即要求函数 $R(s,t)$ 在 $(t,t)$ 点**广义二次可微**.

**定理 均方可导的性质**

若 $\{X_t:t\in T\},\{X_{1,t},X_{2,t}:t\in T\}$ 在 $T$ 上均方可导, $f(t)$ 为一般函数且在 $T$ 上可导, 则
+ **可导必连续**: $X_t,X_{1,t},X_{2,t}$ 在 $T$ 上均方连续
+ **线性**:
  $$
    (c_1X_{1,t}+c_2X_{2,t})'=c_1X_{1,t}'+c_2X_{2,t}',~\forall~c_1,c_2\in\mathbb{R}
  $$

+ **乘积求导公式**:
  $$
    [f(t)X_t]'=f'(t)X_t+f(t)X_t'
  $$

+ **期望与求导换序**:
  $$
    EX_t'=(EX_t)'
  $$

+ **内积与求导换序**:
  $$
    \langle X_s',X_t'\rangle=\frac{\partial^2R(s,t)}{\partial s\partial t}
  $$

### 均方积分

**定义 Riemann 均方积分**

设 $\{X_t:t\in T\}$ 为二阶矩过程, $f(t),~t\in T$ 为定义在 $T$ 上的函数, $[a,b]\in T$, 任取
$$
  a=t_0 < t_1 < \cdots < t_n=b
$$

$\Delta t_k=t_k-t_{k-1}$, 令
$$
  \lambda=\max_{1\leqslant k\leqslant n}\Delta t_k
$$
任取 $u_k\in[t_{k-1},t_k]$. 若
$$
  \lim_{\lambda\to0}\sum_{k=1}^nf(u_k)X_{u_k}\Delta t_k\overset{\mathrm{m.s.}}{=}\int_a^bf(t)X_t\mathrm{d}t
$$
均方极限存在, 则称
$$
  \int_a^bf(t)X_t\mathrm{d}t
$$
为 $f(t)X_t$ 在 $[a,b]$ 上的 Riemann 均方积分.

若
$$
  \lim_{m,~n\to\infty}\int_a^bf(t)X_t\mathrm{d}t\overset{\mathrm{m.s.}}{=}\int_{-\infty}^\infty f(t)X_t\mathrm{d}t
$$
均方极限存在, 则称上述极限为 $f(t)X_t$ 在 $(-\infty,\infty)$ 上的 Riemann 均方积分.

**定理 均方可积的充分条件**

若
$$
  \int_a^b\int_a^bf(s)f(t)R(s,t)\mathrm{d}s\mathrm{d}t
$$
存在, 则
$$
  \int_a^bf(t)X_t\mathrm{d}t
$$
也存在.

**推论 无穷区间均方可积的充分条件**

若
$$
  \int_{-\infty}^\infty\int_{-\infty}^\infty f(s)f(t)R(s,t)\mathrm{d}s\mathrm{d}t
$$
存在, 则
$$
  \int_{-\infty}^\infty f(t)X_t\mathrm{d}t
$$
也存在.

**定理 均方积分的性质**

设 $f(t)X_t,~f_k(t)X_{k,t}$ 在 $[a,b]$ 上均方可积, 则
+ **期望与积分换序**:
  $$
    E\int_a^bf(t)X_t\mathrm{d}t=\int_a^bf(t)EX_t\mathrm{d}t
  $$
  $$
    E\left(\int_a^bf(s)X_s\mathrm{d}s\int_a^bf(t)X_t\mathrm{d}t\right)=\int_a^b\int_a^bf(s)f(t)R(s,t)\mathrm{d}s\mathrm{d}t
  $$
+ **求和与积分换序**, **线性**:
  $$
    \int_a^b\sum_kc_kf_k(t)X_{k,t}\mathrm{d}t=\sum_k\int_a^bc_kf_k(t)X_{k,t}\mathrm{d}t,~\forall~c_k\in\mathbb{R}
  $$
+ **分段积分**:
  $$
    \int_a^cf(t)X_t\mathrm{d}t+\int_c^bf(t)X_t\mathrm{d}t=\int_a^bf(t)X_t\mathrm{d}t,~\forall~c\in[a,b]
  $$

**定理 均方连续与均方积分的关系**

设 $X_t$ 在 $[a,b]$ 上均方连续, 则
+ **连续必可积**: $X_t$ 在 $[a,b]$ 上均方可积, 即
  $$
    \displaystyle\int_a^bf(t)X_t\mathrm{d}t
  $$
  存在
+ **积分不等式**:
  $$
    \left\|\int_a^bf(t)X_t\mathrm{d}t\right\|\leqslant\int_a^bf(s)\|X_s\|\mathrm{d}s
  $$
+ **变上限积分均方连续可导**: 记
  $$
    Y_t=\int_a^tf(u)X_u\mathrm{d}u
  $$
  则 $\{Y_t:t\geqslant0\}$ 在 $[a,b]$ 上均方连续, 均方可导且
  $$
    Y_t'=X_t
  $$

**推论 均方积分 Newton-Leibniz 公式**

设 $X_t'$ 在 $[a,b]$ 上均方连续, 则
$$
  X_t-X_a=\int_a^tX_s'\mathrm{d}s,~\forall~t\in[a,b]
$$

## 7.3 Itô 随机积分

**定义 $\sigma$ 域流**

若可测空间 $(\Omega,\mathcal{F})$ 上子 $\sigma$ 域族 $\{\mathcal{F}_t:t\geqslant0\}$ 使得 $\forall~0\leqslant s < t < \infty$, 有
$$
  \mathcal{F}_s\subset\mathcal{F}_t\subset\mathcal{F}
$$

则称 $\{\mathcal{F}_t:t\geqslant0\}$ 是 $(\Omega,\mathcal{F})$ 上的 $\sigma$ 域流.

**注释**

+ 对给定的随机过程 $X=\{X_t:t\geqslant0\}$, 其 $\sigma$ 域流为
  $$
    \begin{aligned}
      \mathcal{F}_t^X
        &=\sigma(X_s:0\leqslant s\leqslant t)\\
        &=\sigma\left(\bigcup_{0\leqslant s\leqslant t}X_s^{-1}(\mathcal{B}_{\mathbb{R}})\right)\\
    \end{aligned}
  $$
  其中
  $$
    X_s^{-1}(\mathcal{B}_{\mathbb{R}})=\Big\{\{\omega\in\Omega:X_s(\omega)\in A\}|A\in\mathcal{B}_{\mathbb{R}}\Big\}\subset\mathcal{F}
  $$

+ $\sigma$ 域流可看作**信息流**, 即 $t$ 时刻前随机过程的全部信息.

**定义 关于 $\sigma$ 域流适应**

若可测空间 $(\Omega,\mathcal{F})$ 上随机过程 $X=\{X_t:t\geqslant0\}$, $\sigma$ 域流 $\{\mathcal{F}_t:t\geqslant0\}$ 使得 $\forall~t\geqslant0$, $X_t$ 关于 $\mathcal{F}_t$ 可测, 即 $\forall~x\in\mathbb{R}$,
$$
  \{\omega\in\Omega:X_t(\omega)\in(-\infty,x]\}\subset\mathcal{F}_t
$$
记为 $X_t\in\mathcal{F}_t$, 则称 $X$ 是 $\{\mathcal{F}_t\}$ **适应**的.

**定义 布朗运动**

若概率空间 $(\Omega,\mathcal{F},P)$ 上**连续轨道适应过程**
$$
  \{B_t,~\mathcal{F}_t:t\geqslant0\}
$$
满足
+ $B_0=0$
+ $\forall~0\leqslant s < t$, $B_t-B_s$ 与 $\mathcal{F}_s$ 独立, 即 $\forall~A\in\mathcal{F}_s$, $\pmb{1}_A$ 与 $B_t-B_s$ 独立, 且
  $$
    B_t-B_s\sim N(0,t-s)
  $$

则称 $B=\{B_t:t\geqslant0\}$ 为 $\{\mathcal{F}_t\}$ 布朗运动.

**注释**

$$
  \mathcal{F}_t^B=\sigma(B_s:\forall~0\leqslant s\leqslant t)\subset\mathcal{F}_t,~\forall~t\geqslant0
$$

**定义 乘积空间与乘积 $\sigma$ 域流**

乘积空间定义为
$$
  [0,T]\times\Omega=\{(t,\omega):0\leqslant t\leqslant T,~\omega\in\Omega\}
$$
乘积 $\sigma$ 域流定义为
$$
  \mathcal{B}_{[0,T]}\times\mathcal{F}_t=\sigma(\{B\times A:B\in\mathcal{B}_{[0,T]},~A\in\mathcal{F}_t\})
$$

事实上, 乘积 $\sigma$ 域流为包含所有可测矩形的 $\sigma$ 域流.

**定义 循序可测过程**

若 $\{\mathcal{F}_t:t\geqslant0\}$ 是 $(\Omega,\mathcal{F})$ 上 $\sigma$ 域流, $(\Omega,\mathcal{F})$ 上随机过程 $X=\{X_t:t\geqslant0\}$ 使得 $\forall~t>0$,
$$
  X:([0,t]\times\Omega,~\mathcal{B}_{[0,T]}\times\mathcal{F}_t)\to(\mathbb{R},~\mathcal{B}_{\mathbb{R}})
$$
可测, 则称 $X$ 是 $\{\mathcal{F}_t\}$ **循序可测**过程.

**定义 平方可积循序过程空间**

$\forall~T>0$, 设 $g(t,\omega)$ 为 $(\Omega,\mathcal{F})$ 上循序可测过程, 记
$$
  \begin{aligned}
    \mathcal{L}_T^2
    &\triangleq\bigg\{ g(t,\omega): \displaystyle\int_0^TE[g^2(t,\omega)]\mathrm{d}t < \infty\bigg\}\\
    &=L^2([0,T]\times\Omega,~\mathcal{P}_g,~\lambda\times P)
  \end{aligned}
$$
其中
$$
  \lambda\times P(B\times A)=\lambda(B)\times P(A)
$$
$\lambda$ 为 Lebesgue 测度, 定义里的积分也可写为
$$
  \int_0^TE[g^2(t,\omega)]\mathrm{d}t=\int_\Omega\int_0^Tg^2(t,\omega)\mathrm{d}t\mathrm{d}P
$$
记
$$
  \begin{aligned}
    \mathcal{L}_2
      &\triangleq\bigcap\limits_{T>0}\mathcal{L}_T^2\\
      &=\bigg\{g(t,\omega): \forall~T>0, ~\int_0^TE[g^2(t,\omega)]\mathrm{d}t < \infty\bigg\}\\
  \end{aligned}
$$

**定义 准范数**

$\forall~g\in\mathcal{L}_2$, 定义准范数
$$
  \|g\|_2\triangleq\frac{\|g\|_{2,n}\wedge1}{2^n}
$$
其中
$$
  \|g\|_{2,n}^2=\int_0^nE[g^2(t,\omega)]\mathrm{d}t
$$

**定义 L0**

定义
$$
\begin{aligned}
  \mathcal{L}_0\triangleq\Bigg\{g(t,\omega)
    &=g_0(t,\omega)\pmb{1}_{\{0\}}(t)+\sum_{k=0}^\infty g_k(t,\omega)\pmb{1}_{(t_k,t_{k-1}]}(t)\\
    &:0=t_0 < t_1 < \cdots < t_n\uparrow\infty,\\
    &~~~~g_0\in\mathcal{F}_0,~g_k\in\mathcal{F}_{t_k},~Eg_0^2 < \infty,~Eg_k^2 < \infty\Bigg\}\\
\end{aligned}
$$
$\mathcal{L}_0$ 在 $\|\cdot\|_2$ 下是 $\mathcal{L}_2$ **线性稠密子集**.

**定义 简单过程的随机积分**

设 $B=\{B_t,\mathcal{F}_t:t\geqslant0\}$ 为布朗运动, $\forall~g\in\mathcal{L}_0$,
$$
  g(t,\omega)=g_0(t,\omega)\pmb{1}_{\{0\}}(t)+\sum_{k=0}^\infty g_k(t,\omega)\pmb{1}_{(t_k,t_{k-1}]}(t)
$$
定义 Itô 随机积分为
$$
  \begin{aligned}
    I_g(t)
      &\triangleq\int_0^tg_s\mathrm{d}B_s\\
      &=\sum_{k=0}^\infty g_k(B_{t_{k+1}\wedge t}-B_{t_{k}\wedge t})\\
  \end{aligned}
$$

给定 $t>0$, 不妨将 $t$ 加入序列 $\{t_k\}$, 则
$$
  \forall~ 0=t_0 < t_1 < \cdots < t_n=t
$$
$\forall~ 0\leqslant s\leqslant t$, 有
$$
  g(s,\omega)=g_0(s,\omega)\pmb{1}_{\{0\}}(s)+\sum_{k=0}^{n-1} g_k(s,\omega)\pmb{1}_{(t_k,t_{k-1}]}(s)
$$
则 Itô 随机积分
$$
  \begin{aligned}
    I_g(t)
      &=\int_0^tg_s\mathrm{d}B_s\\
      &=\sum_{k=0}^{n-1}g_k(B_{t_{k+1}}-B_{t_k})\\
  \end{aligned}
$$

**Itô 积分性质-L0**

设 $g\in\mathcal{L}_0$, 则有

+ **线性**: $\forall~g_1,g_2\in\mathcal{L}_0,~\alpha_1,\alpha_2\in\mathbb{R}$, 有
  $$
    \int_0^t(\alpha_1g_{1,s}+\alpha_2g_{2,s})\mathrm{d}B_s=\alpha_1\int_0^tg_{1,s}\mathrm{d}B_s+\alpha_2\int_0^tg_{2,s}\mathrm{d}B_s
  $$
+ **期望**: $EI_g(t)=0$
+ **二阶矩**:
  $$
    EI_g^2(t)=\int_0^tEg_s^2\mathrm{d}s
  $$
+ **鞅**:
  $$
    \left\{I_g(t)\triangleq\int_0^tg_s\mathrm{d}B_s:t\geqslant0\right\}
  $$
  关于 $\{\mathcal{F}_t\}$ 是鞅

**定义 L2 随机积分**

$\forall~g\in\mathcal{L}_2$, 因 $\mathcal{L}_0$ 在 $\|\cdot\|_2$ 下是 $\mathcal{L}_2$ 线性稠密子集, 则 $\exists~g_n\in\mathcal{L}_0$, $n\geqslant1$, 使得
$$
  \lim_{n\to\infty}\|g_n-g\|_2=0
$$
从而
$$
  \lim_{m,~n\to\infty}\|g_n-g_m\|_2=0
$$
而 $g_n-g_m\in\mathcal{L}_0$,
$$
  \begin{aligned}
    \|g_n-g_m\|_{2,t}^2&=\int_0^tE|g_{n,u}-g_{m,u}|^2\mathrm{d}u\\
    &=E\left[\int_0^t(g_{n,u}-g_{m,u})\mathrm{d}B_u\right]^2\\
    &=E\left(\int_0^tg_{n,u}\mathrm{d}B_u-\int_0^tg_{m,u}\mathrm{d}B_u\right)^2
  \end{aligned}
$$
可见 $\forall~t\geqslant0$, $\{I_{g_n}(t):n\geqslant0\}$ 是 $H=L_2(\Omega,\mathcal{F},P)$ 中的 Cauchy 列, 故 $\exists~I_g(t)$ 使得
$$
  \begin{aligned}
    I_g(t)
      &=L_2\text{-}\lim_{n\to\infty}I_{g_n}(t)\\
      &=L_2\text{-}\lim_{n\to\infty}\int_0^tg_{n,u}\mathrm{d}B_u\\
  \end{aligned}
$$

**Itô 积分性质-L2**

设 $g\in\mathcal{L}_2$, 则有

+ **线性**: $\forall~g_1,g_2\in\mathcal{L}_2,~\alpha_1,\alpha_2\in\mathbb{R}$, 有
  $$
    \int_0^t(\alpha_1g_{1,s}+\alpha_2g_{2,s})\mathrm{d}B_s=\alpha_1\int_0^tg_{1,s}\mathrm{d}B_s+\alpha_2\int_0^tg_{2,s}\mathrm{d}B_s
  $$
+ **期望**: $EI_g(t)=0$
+ **二阶矩**:
  $$
    EI_g^2(t)=\int_0^tEg_s^2\mathrm{d}s
  $$
+ **内积**:
  $$
    \begin{aligned}
      \langle I_{g_1}(t),I_{g_2}(t)\rangle
        &=E\left[\int_0^tg_{1,u}\mathrm{d}B_u\int_0^tg_{2,u}\mathrm{d}B_u\right]\\
        &=\int_0^t E(g_{1,u}g_{2,u})\mathrm{d}u\\
    \end{aligned}
  $$
  $$
    \begin{aligned}
      \langle I_{g}(s),I_{g}(t)\rangle
      &=E\left[\int_0^sg_{u}\mathrm{d}B_u\int_0^tg_{u}\mathrm{d}B_u\right]\\
      &=\int_0^s Eg_u^2\mathrm{d}u,~\forall~0\leqslant s\leqslant t\\
    \end{aligned}
  $$
+ **分段积分**:
  $$
    \int_0^tg_u\mathrm{d}B_u=\int_0^sg_u\mathrm{d}B_u+\int_s^tg_u\mathrm{d}B_u,~\forall~s\in[0,t]
  $$
+ **鞅性**:
  $$
    \left\{I_g(t)\triangleq\int_0^tg_s\mathrm{d}B_s:t\geqslant0\right\}
  $$
  关于 $\{\mathcal{F}_t\}$ 是鞅
+ **Doob 极大值不等式**: 记
  $$
    X_t=\int_0^tg_u\mathrm{d}B_u
  $$
  则 $\forall~t\geqslant0$, $\lambda>0$, $p\geqslant1$ 有
  $$
    P\left(\max_{0\leqslant u\leqslant t}|X_u|>\lambda\right)\leqslant\frac{E|X_t|^p}{\lambda^p}
  $$

**定理 鞅表示定理**

若 $\{X_t:t\geqslant0\}$ 关于 $\{\mathcal{F}_t\}$ 是鞅, $X_t\in H$, 则必存在唯一适应过程
$$
  \{g_t:t\geqslant0\}\in\mathcal{L}_T^2
$$
满足 $0\leqslant t\leqslant T$,
$$
  X_t-X_0=\int_0^tg_s\mathrm{d}B_s
$$

**例题 均方连续循序可测过程的 Itô 积分**

设 $\{\phi_t:t\geqslant0\}$ 均方连续, 关于 $\{\mathcal{F}_t\}$ 适应且循序可测, 定义
$$
  \begin{aligned}
    \phi_t^{(n)}
      &\triangleq\sum_{k=0}^{n-1}\phi_{t_k^{(n)}}\pmb{1}_{(t_k^{(n)},t_{k+1}^{(n)}]}(t)+\phi_0\pmb{1}_{\{0\}}(t)\\
      &\overset{\mathrm{\mathcal{L}_2}}{\to}\phi_t~(n\to\infty)\\
  \end{aligned}
$$
其中
$$
  \left\{t_k^{(n)}:0\leqslant k\leqslant n\right\}
$$
是 $[0,t]$ 的分割, 令
$$
  \lambda_n\triangleq\max_{0\leqslant k\leqslant n-1}\left\{t_{k+1}^{(n)}-t_{k}^{(n)}\right\}\to0~(n\to\infty)
$$
从而
$$
  \int_0^t\phi_u\mathrm{d}B_u=L_2\text{-}\lim_{n\to\infty}\sum_{k=0}^{n-1}\phi_{t_k^{(n)}}\left(B_{t_{k+1}^{(n)}}-B_{t_{k}^{(n)}}\right)
$$
上式也可以理解为 Itô 积分的**定义**.

## 7.4 Itô 过程与 Itô 公式

**定义 Itô 过程**

设随机过程 $X=\{X_t:t\geqslant0\}$ 满足如下的 **Itô 随机积分方程**: 对
$$
  \forall~0\leqslant t_0 < t < T
$$
有
$$
  X_t-X_{t_0}=\int_{t_0}^tb(s,X_s)\mathrm{d}s+\int_{t_0}^t\sigma(s,X_s)\mathrm{d}B_s
$$
或等价地写作 **Itô 随机微分方程**
$$
  \mathrm{d}X_t=b(t,X_t)\mathrm{d}t+\sigma(t,X_t)\mathrm{d}B_t
$$
其中 $b(t,X_t)$, $\sigma(t,X_t)$ 是二元连续函数, 且对 $\forall~x\in\mathbb{R}$,
$$
  b(t,X_t)\in\mathcal{L}_T^1,~ \sigma(t,X_t)\in\mathcal{L}_T^2
$$
则称 $X$ 为 **Itô 过程**.

**注释 Itô 过程与扩散过程**

Itô 过程在 $b(t,X_t)$, $\sigma(t,X_t)$ 具有比较好的性质的情况下也是**扩散过程**, 其中 $b(t,X_t)$ 称为**漂移系数**, $\sigma(t,X_t)$ 称为**扩散系数**.

**定理 Itô 公式**

设随机过程 $X=\{X_t:t\geqslant0\}$ 是 Itô 过程, $y=f(t,x)$ 是二元函数, 且具有连续偏导数
$$
  \frac{\partial f}{\partial t},~\frac{\partial f}{\partial x},\frac{\partial^2 f}{\partial x^2}
$$
令 $Y_t\triangleq f(t,X_t)$, 则过程 $Y=\{Y_t:t\geqslant0\}$ 也是随机过程, 且对 $\forall~0\leqslant t_0 < t$ 满足如下的 **Itô 积分方程**
$$
  Y_t-Y_{t_0}=\int_{t_0}^t\left[\frac{\partial f}{\partial t}+\frac{\partial f}{\partial x}b+\frac{1}{2}\frac{\partial^2 f}{\partial x^2}\sigma^2\right](s,X_s)\mathrm{d}s+\int_{t_0}^t\left(\frac{\partial f}{\partial x}\sigma\right)(s,X_s)\mathrm{d}B_s
$$
或等价的 **Itô 微分方程**
$$
  \mathrm{d}Y_t=\left[\frac{\partial f}{\partial t}+\frac{\partial f}{\partial x}b+\frac{1}{2}\frac{\partial^2 f}{\partial x^2}\sigma^2\right](t,X_t)\mathrm{d}t+\left[\frac{\partial f}{\partial x}\sigma\right](t,X_t)\mathrm{d}B_t~~(\text{a.e.})
$$

**定理 重对数律**

$$
  \limsup_{t\to\infty}\frac{B_t}{\sqrt{2t\ln\ln t}}=1~~(\text{a.s.})
$$

$$
  \liminf_{t\to\infty}\frac{B_t}{\sqrt{2t\ln\ln t}}=-1~~(\text{a.s.})
$$

$$
  \limsup_{t\to0}\frac{B_t}{\sqrt{2t\ln\ln (1/t)}}=1~~(\text{a.s.})
$$

$$
  \liminf_{t\to0}\frac{B_t}{\sqrt{2t\ln\ln (1/t)}}=-1~~(\text{a.s.})
$$

粗略地说,
$$
  B_{s+\Delta t}-B_s\sim\sqrt{\Delta t}
$$
即 $\mathrm{d}B_t\sim\sqrt{\mathrm{d}t}$.

**Itô 公式理解**

由 Itô 过程定义可知

$$
  \mathrm{d}X_t=b(t,X_t)\mathrm{d}t+\sigma(t,X_t)\mathrm{d}B_t
$$

令 $Y_t\triangleq f(t,X_t)$, 欲求其关于 $\mathrm{d}t,~\mathrm{d}B_t$ 的全微分, 由 $\mathrm{d}B_t\sim\sqrt{\mathrm{d}t}$ 可知 $f(t,x)$ 对 $x$ 的偏导需要展开到二阶来获取那个与 $\mathrm{d}t$ 同阶的 $\mathrm{d}B_t^2$ 项.

简记 $f=f(t,X_t)$, 则 Itô 公式微分形式可以**粗略理解**为

$$
  \begin{aligned}
    \mathrm{d}Y_t&=\mathrm{d}f(t,X_t)\\
    &=\frac{\partial f}{\partial t}\mathrm{d}t+\frac{\partial f}{\partial x}\mathrm{d}X_t+\frac{1}{2}\frac{\partial^2 f}{\partial x^2}\mathrm{d}X_t^2\\
    &=\frac{\partial f}{\partial t}\mathrm{d}t+\frac{\partial f}{\partial x}(b\mathrm{d}t+\sigma\mathrm{d}B_t)+\frac{1}{2}\frac{\partial^2 f}{\partial x^2}(b\mathrm{d}t+\sigma\mathrm{d}B_t)^2\\
    &=\frac{\partial f}{\partial t}\mathrm{d}t+\frac{\partial f}{\partial x}b\mathrm{d}t+\frac{\partial f}{\partial x}\sigma\mathrm{d}B_t+\frac{1}{2}\frac{\partial^2 f}{\partial x^2}(\sigma^2\mathrm{d}t+o(\mathrm{d}t))\\
    &=\frac{\partial f}{\partial t}\mathrm{d}t+\frac{\partial f}{\partial x}b\mathrm{d}t+\frac{\partial f}{\partial x}\sigma\mathrm{d}B_t+\frac{1}{2}\frac{\partial^2 f}{\partial x^2}\sigma^2\mathrm{d}t\\
    &=\left(\frac{\partial f}{\partial t}+\frac{\partial f}{\partial x}b+\frac{1}{2}\frac{\partial^2 f}{\partial x^2}\sigma^2\right)\mathrm{d}t+\left(\frac{\partial f}{\partial x}\sigma\right)\mathrm{d}B_t\\
    &=\left[\frac{\partial f}{\partial t}+\frac{\partial f}{\partial x}b+\frac{1}{2}\frac{\partial^2 f}{\partial x^2}\sigma^2\right](t,X_t)\mathrm{d}t+\left[\frac{\partial f}{\partial x}\sigma\right](t,X_t)\mathrm{d}B_t
  \end{aligned}
$$

**例题 使用 Itô 公式求解 Itô 积分**

求证
$$
  \int_0^tB_s^2\mathrm{d}B_s=\frac{B_t^3}{3}-\int_0^tB_s\mathrm{d}s
$$

**证明**: 与该积分方程对应的微分方程为
$$
  B_t^2\mathrm{d}B_t=\mathrm{d}\left(\frac{B_t^3}{3}\right)-B_t\mathrm{d}t
$$

即
$$
  \mathrm{d}\left(\frac{B_t^3}{3}\right)=B_t\mathrm{d}t+B_t^2\mathrm{d}B_t
$$

对比上式与 Itô 公式可猜测函数 $f(t,x)=x^3/3$, 下面证明之.

布朗运动本身即是 Itô 过程, 满足 Itô 微分方程
$$
  \mathrm{d}B_t=0\times\mathrm{d}t+1\times\mathrm{d}B_t
$$

令
$$
f(t,x)=\frac{x^3}{3}
$$
则
$$
Y_t=f(t,B_t)=\frac{B_t^3}{3}
$$
所以由 **Itô 公式**可得
$$
  \begin{aligned}
  \mathrm{d}Y_t&=\mathrm{d}\left(\frac{B_t^3}{3}\right)\\
  &=\left(0+B_t^2\cdot0+\frac{1}{2}2B_t\cdot1^2\right)\mathrm{d}t+(B_t^2\cdot1)\mathrm{d}B_t\\
  &=B_t\mathrm{d}t+B_t^2\mathrm{d}B_t\\
  \end{aligned}
$$

对上式从 $0$ 到 $t$ 积分可得
$$
  \frac{B_t^3}{3}=\int_0^tB_s\mathrm{d}s+\int_0^tB_s^2\mathrm{d}B_s
$$

**例题 求解布朗运动自身的 $n$ 次 Itô 积分**

$\forall~n\geqslant1$, 求下面积分
$$
  \int_0^tB_s^n\mathrm{d}B_s
$$

**解**: 布朗运动本身即是 Itô 过程, 满足 Itô 微分方程
$$
  \mathrm{d}B_t=0\times\mathrm{d}t+1\times\mathrm{d}B_t
$$

令
$$
  f(t,x)=\frac{x^{n+1}}{n+1}
$$
则
$$
  Y_t=f(t,B_t)=\frac{B_t^{n+1}}{n+1}
$$
所以由 **Itô 公式**可得
$$
  \begin{aligned}
  \mathrm{d}Y_t&=\mathrm{d}\left(\frac{B_t^{n+1}}{n+1}\right)\\
  &=\left(0+B_t^n\cdot0+\frac{1}{2}nB_t^{n-1}\cdot1^2\right)\mathrm{d}t+(B_t^n\cdot1)\mathrm{d}B_t\\
  &=\frac{n}{2}B_t^{n-1}\mathrm{d}t+B_t^n\mathrm{d}B_t\\
  \end{aligned}
$$

对上式从 $0$ 到 $t$ 积分可得
$$
  \frac{B_t^{n+1}}{n+1}=\int_0^t\frac{n}{2}B_s^{n-1}\mathrm{d}s+\int_0^tB_s^n\mathrm{d}B_s
$$

即
$$
  \int_0^tB_s^n\mathrm{d}B_s=\frac{B_t^{n+1}}{n+1}-\int_0^t\frac{n}{2}B_s^{n-1}\mathrm{d}s
$$

**例题 求随机过程满足的 Itô 微分方程**

利用 Itô 公式, 求以下随机过程满足的 Itô 微分方程:
$$
  \begin{aligned}
    X_t&=\exp(ut+\alpha B_t)\\
    Y_t&=\exp(t/2)\cos B_t\\
  \end{aligned}
$$

**解**:  令
$$
  \begin{aligned}
    f(t,x)&=\exp(ut+\alpha x)\\
    g(t,x)&=\exp(t/2)\cos x\\
  \end{aligned}
$$
它们的相应偏导数为
$$
  \frac{\partial f}{\partial t}=u\exp(ut+\alpha x),~\frac{\partial f}{\partial x}=\alpha\exp(ut+\alpha x),\frac{\partial^2 f}{\partial x^2}=\alpha^2\exp(ut+\alpha x)
$$

$$
  \frac{\partial g}{\partial t}=\frac{1}{2}\exp(t/2)\cos x,~\frac{\partial g}{\partial x}=-\exp(t/2)\sin x,\frac{\partial^2 g}{\partial x^2}=-\exp(t/2)\cos x
$$

则由 Itô 公式可知
$$
  \begin{aligned}
    \mathrm{d}X_t&=\left[u\exp(ut+\alpha B_t)+0+\frac{1}{2}\alpha^2\exp(ut+\alpha B_t)\right]\mathrm{d}t+\alpha\exp(ut+\alpha B_t)\mathrm{d}B_t\\
    &=\exp(ut+\alpha B_t)\left[\left(u+\frac{1}{2}\alpha^2\right)\mathrm{d}t+\alpha\mathrm{d}B_t\right]\\
    &=\left(u+\frac{1}{2}\alpha^2\right)X_t\mathrm{d}t+\alpha X_t\mathrm{d}B_t
  \end{aligned}
$$

$$
  \begin{aligned}
    \mathrm{d}Y_t&=\left[\frac{1}{2}\exp(t/2)\cos B_t+0-\frac{1}{2}\exp(t/2)\cos B_t\right]\mathrm{d}t-\exp(t/2)\sin B_t~\mathrm{d}B_t\\
    &=-\exp(t/2)\sin B_t~\mathrm{d}B_t\\
  \end{aligned}
$$

**定义 多元 Itô 过程**

设随机过程
$$
  \pmb{X}=\{\pmb{X}_t=(X_{1,t},X_{2,t},\cdots,X_{n,t}):t\geqslant0\}
$$
满足如下的**多元 Itô 随机微分方程**
$$
  \mathrm{d}\pmb{X}_t=\pmb{b}(t,\pmb{X}_t)\mathrm{d}t+\pmb{\Sigma}(t,\pmb{X}_t)\mathrm{d}\pmb{B}_t
$$
其中
$$
  \pmb{b}(t,\pmb{X}_t)=[b_1(t,\pmb{X}_t),b_2(t,\pmb{X}_t),\cdots,b_n(t,\pmb{X}_t)]^T
$$
$$
  \pmb{\Sigma}(t,\pmb{X}_t)=[\sigma_{ij}(t,\pmb{X}_t)]_{n\times m}
$$
且
$$
  b_i(t,\pmb{X}_t)\in\mathcal{L}_T^1
$$
$$
  \sigma_{ij}(t,\pmb{X}_t)\in\mathcal{L}_T^2
$$
$$
  \pmb{B}_t=\left[B_{1,t},B_{2,t},\cdots,B_{m,t}\right]^T
$$
则称 $X$ 为 **$n$ 维 Itô 过程**.

**定理 多元 Itô 公式**

设随机过程 $\pmb{X}=\{\pmb{X}_t:t\geqslant0\}$ 是 $n$ 维 Itô 过程,
$$
  \pmb{f}(t,\pmb{x})=[f_1(t,\pmb{x}),f_2(t,\pmb{x}),\cdots,f_d(t,\pmb{x})]^T
$$
是 $[0,\infty)\times\mathbb{R}^n\to\mathbb{R}^d$ 上的函数, 其中
$$
  \pmb{x}=(x_1,x_2,\cdots,x_n)
$$
且具有连续偏导数
$$
  \frac{\partial f_k}{\partial t},~\frac{\partial f_k}{\partial x_i},\frac{\partial^2 f_k}{\partial x_i\partial x_j}
$$
令 $\pmb{Y}_t\triangleq \pmb{f}(t,\pmb{X}_t)$, 则过程 $\pmb{Y}=\{\pmb{Y}_t:t\geqslant0\}$ 是 $d$ 维 Itô 过程, 且对 $\forall~1\leqslant k\leqslant d$ 满足如下的 **多元 Itô 微分方程**
$$
  \mathrm{d}\pmb{Y}_{k,t}=\left[\frac{\partial f_k}{\partial t}+\frac{\partial f_k}{\partial x_i}b_i+\frac{1}{2}\frac{\partial^2 f_k}{\partial x_i\partial x_j}\sigma_{il}\sigma_{jl}\right](t,\pmb{X}_t)\mathrm{d}t+\left[\frac{\partial f_k}{\partial x_i}\sigma_{il}\right](t,\pmb{X}_t)\mathrm{d}B_{l,t}.
$$
需要指出的是上式使用了 Einstein 求和约定, 即重复指标自动求和.

## 7.5 Itô 随机微分方程

### 常系数的线性随机微分方程

**例题 Ornstein-Uhlenbeck 方程**

设 $\{X_t:t\geqslant0\}$ 满足 Ornstein-Uhlenbeck 方程
$$
  \mathrm{d}X_t=-b X_t\mathrm{d}t+\sigma\mathrm{d}B_t,~b,\sigma\in\mathbb{R},
$$

求解 $X_t$.

**解**: 方程两边同乘积分因子 $\mathrm{e}^{b t}$ 可得
$$
  \mathrm{e}^{b t}\mathrm{d}X_t+b\mathrm{e}^{b t} X_t\mathrm{d}t=\sigma\mathrm{e}^{b t}\mathrm{d}B_t
$$

令 $f(t,x)=\mathrm{e}^{b t}x$, 由 Itô 公式可知
$$
  \begin{aligned}
    \mathrm{d}(\mathrm{e}^{b t}X_t)
      &=b\mathrm{e}^{b t} X_t\mathrm{d}t+\mathrm{e}^{b t}\mathrm{d}X_t\\
      &=\sigma\mathrm{e}^{b t}\mathrm{d}B_t
  \end{aligned}
$$

两边从 $t_0$ 到 $t$ 积分可得
$$
  \mathrm{e}^{b t}X_t-\mathrm{e}^{b t_0}X_{t_0}=\int_{t_0}^t\sigma\mathrm{e}^{b s}\mathrm{d}B_s
$$

于是
$$
  X_t=\mathrm{e}^{-b (t-t_0)}X_{t_0}+\int_{t_0}^t\sigma\mathrm{e}^{-b (t-s)}\mathrm{d}B_s
$$

### 简单的线性齐次随机微分方程

**例题 Black-Scholes 模型**

设 $X_t$ 为 $t$ 时刻某种股票的价格, 在某些条件下它满足以下随机微分方程
$$
  \mathrm{d}X_t=b X_t\mathrm{d}t+\sigma X_t\mathrm{d}B_t,~b,\sigma\in\mathbb{R},
$$

求解 $X_t$.

**解**: 方程两边同除 $X_t$ 可得
$$
  \frac{\mathrm{d}X_t}{X_t}=b \mathrm{d}t+\sigma \mathrm{d}B_t
$$

遂令 $f(t,x)=\ln x$, 则 $Y_t=\ln X_t$, 由 Itô 公式可知
$$
  \begin{aligned}
    \mathrm{d}Y_t
      &=\mathrm{d}(\ln X_t)\\
      &=\left(0+\frac{1}{X_t}b X_t-\frac{1}{2}\frac{1}{X_t^2}\sigma^2 X_t^2\right)\mathrm{d}t+\frac{1}{X_t}\sigma X_t\mathrm{d}B_t\\
      &=\left(b-\frac{1}{2}\sigma^2\right)\mathrm{d}t+\sigma\mathrm{d}B_t\\
  \end{aligned}
$$

两边从 $0$ 到 $t$ 积分可得
$$
  \begin{aligned}
    \ln X_t-\ln X_0
      &=\int_{0}^t\left(b-\frac{1}{2}\sigma^2\right)\mathrm{d}t+\int_{0}^t\sigma\mathrm{d}B_t\\
      &=\left(b-\frac{1}{2}\sigma^2\right)t+\sigma B_t\\
  \end{aligned}
$$

于是
$$
  X_t=X_0\exp\left[\left(b-\frac{1}{2}\sigma^2\right)t+\sigma B_t\right]
$$

### 一般的线性非齐次随机微分方程

设 $\{X_t:t\geqslant0\}$ 满足
$$
  \mathrm{d}X_t=[b_1(t) X_t+b_2(t)]\mathrm{d}t+[\sigma_1(t) X_t+\sigma_2(t)]\mathrm{d}B_t
$$

求解 $X_t$.

**解**: 在求解**一般线性非齐次随机微分方程**之前, 先求解一类稍简单的**狭义随机微分方程**. 与线性常微分方程求解方法类似, 由简入繁, 先求齐次解, 再求非齐次解, 最大的不同在于随机微分方程中复合函数的求导法则由 Itô 公式决定, 多了**二阶偏导**项, 作微分运算时尤其需要**谨慎**.

+ **狭义随机微分方程**

先求解以下简单齐次线性随机微分方程
$$
  \mathrm{d}X_t=b_1(t) X_t\mathrm{d}t
$$

由 Black-Scholes 模型求解结果易得
$$
  X_t=X_{t_0}\exp\left(\int_{t_0}^tb_1(t)\mathrm{d}t\right)
$$

再求解以下**狭义随机微分方程**
$$
  \mathrm{d}X_t=[b_1(t) X_t+b_2(t)]\mathrm{d}t+\sigma_2(t)\mathrm{d}B_t
$$

移项变形可得
$$
  \mathrm{d}X_t-b_1(t) X_t\mathrm{d}t=b_2(t)\mathrm{d}t+\sigma_2(t)\mathrm{d}B_t
$$

由齐次解推测, 若两边同乘以下积分因子
$$
  \rho_{t_0}^{-1}(t)=\exp\left(-\int_{t_0}^tb_1(t)\mathrm{d}t\right)
$$

则可以通过 Itô 公式解上述微分方程, 即
$$
  \rho_{t_0}^{-1}(t)[\mathrm{d}X_t-b_1(t) X_t]\mathrm{d}t=\rho_{t_0}^{-1}(t)[b_2(t)\mathrm{d}t+\sigma_2(t)\mathrm{d}B_t]
$$

令 $f(t,x)=\rho_{t_0}^{-1}(t)x$, 则由 Itô 公式可知
$$
  \begin{aligned}
    \mathrm{d}\left[\rho_{t_0}^{-1}(t)X_t\right]
      &=\rho_{t_0}^{-1}(t)[\mathrm{d}X_t-b_1(t) X_t]\mathrm{d}t\\
      &=\rho_{t_0}^{-1}(t)[b_2(t)\mathrm{d}t+\sigma_2(t)\mathrm{d}B_t]\\
  \end{aligned}
$$

两边从 $t_0$ 到 $t$ 积分可得
$$
  \begin{aligned}
    &\rho_{t_0}^{-1}(t)X_t-\rho_{t_0}^{-1}(t_0)X_{t_0}\\
    =&\rho_{t_0}^{-1}(t)X_t-X_{t_0}\\
    =&\int_{t_0}^t\rho_{t_0}^{-1}(s)b_2(s)\mathrm{d}s+\int_{t_0}^t\rho_{t_0}^{-1}(s)\sigma_2(s)\mathrm{d}B_s\\
  \end{aligned}
$$

故
$$
  X_t=\rho_{t_0}(t)\left[X_{t_0}+\int_{t_0}^t\rho_{t_0}^{-1}(s)b_2(s)\mathrm{d}s+\int_{t_0}^t\rho_{t_0}^{-1}(s)\sigma_2(s)\mathrm{d}B_s\right]
$$

+ **一般线性非齐次随机微分方程**

先求解以下**齐次线性随机微分方程**
$$
  \mathrm{d}X_t=b_1(t) X_t\mathrm{d}t+\sigma_1(t) X_t\mathrm{d}B_t
$$

由 Black-Scholes 模型求解结果易得
$$
  X_t=X_{t_0}\exp\left[\int_{t_0}^t\left(b_1(t)-\frac{1}{2}\sigma_1^2(t)\right)\mathrm{d}t+\int_{t_0}^t\sigma_1(t) \mathrm{d}B_t\right]
$$

与前述求解过程类似, 下面仍然使用积分因子的思想求解随机微分方程. 记**积分因子**
$$
  \rho_{t_0}(t)=\exp\left[\int_{t_0}^t\left(b_1(t)-\frac{1}{2}\sigma_1^2(t)\right)\mathrm{d}t+\int_{t_0}^t\sigma_1(t) \mathrm{d}B_t\right]
$$

则积分因子满足以下 **Itô 微分方程**
$$
  \mathrm{d}\rho_{t_0}(t)=b_1(t) \rho_{t_0}(t)\mathrm{d}t+\sigma_1(t) \rho_{t_0}(t)\mathrm{d}B_t
$$

令 $f(t,x)=1/x$, 则由 **Itô 公式**可知 $\rho_{t_0}^{-1}(t)$ 满足以下 **Itô 微分方程**
$$
  \begin{aligned}
    \mathrm{d}\rho_{t_0}^{-1}(t)
      &=\left[0-\frac{1}{\rho_{t_0}^2(t)}b_1(t) \rho_{t_0}(t)+\frac{1}{2}\frac{2}{\rho_{t_0}^3(t)}\sigma_1^2(t) \rho_{t_0}^2(t)\right]\mathrm{d}t-\frac{1}{\rho_{t_0}^2(t)}\sigma_1(t) \rho_{t_0}(t)\mathrm{d}B_t\\
      &=\rho_{t_0}^{-1}(t)[\sigma_1^2(t)-b_1(t)]\mathrm{d}t-\rho_{t_0}^{-1}(t)\sigma_1(t)\mathrm{d}B_t
  \end{aligned}
$$

又
$$
  \mathrm{d}X_t=[b_1(t) X_t+b_2(t)]\mathrm{d}t+[\sigma_1(t) X_t+\sigma_2(t)]\mathrm{d}B_t
$$

令 $g(t,x_1,x_2)=x_1x_2$, 则由**二维 Itô 公式**可知
$$
  \begin{aligned}
    \mathrm{d}[\rho_{t_0}^{-1}(t)X_t]
      =~&\rho_{t_0}^{-1}(t)\Big\{X_t[\sigma_1^2(t)-b_1(t)]+[b_1(t) X_t+b_2(t)]-\sigma_1(t)[\sigma_1(t) X_t+\sigma_2(t)]\Big\}\mathrm{d}t\\
      &+\Big\{X_t[-\rho_{t_0}^{-1}(t)\sigma_1(t)]+\rho_{t_0}^{-1}[\sigma_1(t) X_t+\sigma_2(t)]\Big\}\mathrm{d}B_t\\
      =~&\rho_{t_0}^{-1}(t)[b_2(t)-\sigma_1(t)\sigma_2(t)]\mathrm{d}t+\rho_{t_0}^{-1}(t)\sigma_2(t)\mathrm{d}B_t\\
  \end{aligned}
$$

两边从 $t_0$ 到 $t$ 积分可得
$$
  \begin{aligned}
    \rho_{t_0}^{-1}(t)X_t-\rho_{t_0}^{-1}(t_0)X_{t_0}
      &=\rho_{t_0}^{-1}(t)X_t-X_{t_0}\\
      &=\int_{t_0}^t\rho_{t_0}^{-1}(s)[b_2(s)-\sigma_1(s)\sigma_2(s)]\mathrm{d}s+\int_{t_0}^t\rho_{t_0}^{-1}(s)\sigma_2(s)\mathrm{d}B_s\\
  \end{aligned}
$$

故
$$
  X_t=\rho_{t_0}(t)\left[X_{t_0}+\int_{t_0}^t\rho_{t_0}^{-1}(s)[b_2(s)-\sigma_1(s)\sigma_2(s)]\mathrm{d}s+\int_{t_0}^t\rho_{t_0}^{-1}(s)\sigma_2(s)\mathrm{d}B_s\right]
$$

**例题 求解 Itô 微分方程**

+ **通用公式**

设 $\{X_t:t\geqslant0\}$ 满足
$$
  \mathrm{d}X_t=[b_1(t) X_t+b_2(t)]\mathrm{d}t+[\sigma_1(t) X_t+\sigma_2(t)]\mathrm{d}B_t
$$

则
$$
  \rho_{t_0}(t)=\exp\left[\int_{t_0}^t\left(b_1(t)-\frac{1}{2}\sigma_1^2(t)\right)\mathrm{d}t+\int_{t_0}^t\sigma_1(t) \mathrm{d}B_t\right]
$$

$$
  X_t=\rho_{t_0}(t)\left[X_{t_0}+\int_{t_0}^t\rho_{t_0}^{-1}(s)[b_2(s)-\sigma_1(s)\sigma_2(s)]\mathrm{d}s+\int_{t_0}^t\rho_{t_0}^{-1}(s)\sigma_2(s)\mathrm{d}B_s\right]
$$

+ $\mathrm{d}X_t=-X_t\mathrm{d}t+\mathrm{e}^{-t}\mathrm{d}B_t$

**解**: 通过观察可知
$$
  b_1(t)=-1,~b_2(t)=0,~\sigma_1(t)=0,~\sigma_2(t)=\mathrm{e}^{-t}
$$
则
$$
  \rho_{t_0}(t)=\exp\left[\int_{t_0}^t\left(-1-0\right)\mathrm{d}t+\int_{t_0}^t0 \mathrm{d}B_t\right]=\mathrm{e}^{-(t-t_0)}
$$

$$
  \begin{aligned}
    X_t
      &=\mathrm{e}^{-(t-t_0)}\left[X_{t_0}+\int_{t_0}^t\mathrm{e}^{(s-t_0)}[0-0]\mathrm{d}s+\int_{t_0}^t\mathrm{e}^{(s-t_0)}\mathrm{e}^{-s}\mathrm{d}B_s\right]\\
      &=\mathrm{e}^{-(t-t_0)}\left[X_{t_0}+\mathrm{e}^{-t_0}(B_t-B_{t_0})\right]\\
      &=\mathrm{e}^{-(t-t_0)}X_{t_0}+\mathrm{e}^{-t}(B_t-B_{t_0})\\
  \end{aligned}
$$

+ $\mathrm{d}X_t=\gamma\mathrm{d}t+\alpha X_t\mathrm{d}B_t,~\gamma,\alpha\in\mathbb{R}$

**解**: 通过观察可知
$$
  b_1(t)=0,~b_2(t)=\gamma,~\sigma_1(t)=\alpha,~\sigma_2(t)=0
$$
则
$$
  \begin{aligned}
    \rho_{t_0}(t)
      &=\exp\left[\int_{t_0}^t\left(0-\frac{1}{2}\alpha^2\right)\mathrm{d}t+\int_{t_0}^t\alpha \mathrm{d}B_t\right]\\
      &=\exp\left[-\frac{1}{2}\alpha^2(t-t_0)+\alpha (B_t-B_{t_0})\right]\\
  \end{aligned}
$$

$$
  \begin{aligned}
    X_t
    &=\rho_{t_0}(t)\left[X_{t_0}+\int_{t_0}^t\gamma\rho_{t_0}^{-1}(s)\mathrm{d}s\right]\\
    &=\exp\left[-\frac{1}{2}\alpha^2(t-t_0)+\alpha (B_t-B_{t_0})\right]\left\{X_{t_0}+\int_{t_0}^t\gamma\exp\left[\frac{1}{2}\alpha^2(s-t_0)-\alpha (B_s-B_{t_0})\right]\mathrm{d}s\right\}\\
    &=\exp\left(-\frac{1}{2}\alpha^2t+\alpha B_t\right)\left[\exp\left(\frac{1}{2}\alpha^2t_0-\alpha B_{t_0}\right)X_{t_0}+\gamma\int_{t_0}^t\exp\left(\frac{1}{2}\alpha^2s-\alpha B_s\right)\mathrm{d}s\right]\\
  \end{aligned}
$$

+ $\mathrm{d}X_t=(\mathrm{e}^{-t}+X_t)\mathrm{d}t+\sigma X_t\mathrm{d}B_t$, $\sigma>0$

**解**: 通过观察可知
$$
  b_1(t)=1,~b_2(t)=\mathrm{e}^{-t},~\sigma_1(t)=\sigma,~\sigma_2(t)=0
$$
则
$$
  \begin{aligned}
    \rho_{t_0}(t)
      &=\exp\left[\int_{t_0}^t\left(1-\frac{1}{2}\sigma^2\right)\mathrm{d}t+\int_{t_0}^t\sigma \mathrm{d}B_t\right]\\
      &=\exp\left[\left(1-\frac{1}{2}\sigma^2\right)(t-t_0)+\sigma (B_t-B_{t_0})\right]\\
  \end{aligned}
$$

$$
  \begin{aligned}
    X_t
    &=\rho_{t_0}(t)\left[X_{t_0}+\int_{t_0}^t\mathrm{e}^{-s}\rho_{t_0}^{-1}(s)\mathrm{d}s\right]\\
    &=\rho_{t_0}(t)\left\{X_{t_0}+\int_{t_0}^t\mathrm{e}^{-s}\exp\left[-\left(1-\frac{1}{2}\sigma^2\right)(s-t_0)-\sigma (B_s-B_{t_0})\right]\mathrm{d}s\right\}\\
    &=\rho_{t_0}(t)\left\{X_{t_0}+\exp\left[\left(1-\frac{1}{2}\sigma^2\right)t+\sigma B_t\right]\int_{t_0}^t\exp\left[\left(\frac{1}{2}\sigma^2-2\right)s-\sigma B_s\right]\mathrm{d}s\right\}\\
  \end{aligned}
$$

+ $\mathrm{d}X_t=f(t)B_t\mathrm{d}t$

**解**: 布朗运动本身即为 Itô 过程, 有 Itô 微分方程
$$
  \mathrm{d}B_t=0\times\mathrm{d}t+1\times\mathrm{d}B_t
$$

函数 $f$ 在 $[0,+\infty)$ 上连续则可积, 令其原函数为
$$
  F(t)\triangleq\int_0^tf(s)\mathrm{d}s
$$

令 $h(t,x)=F(t)x$, 其相应偏导数为
$$
  \frac{\partial h}{\partial t}=f(t)x,~
  \frac{\partial h}{\partial x}=F(t),~
  \frac{\partial^2 h}{\partial x^2}=0
$$

令 $W_t=F(t)B_t$, 由 Itô 公式可知
$$
  \begin{aligned}
    \mathrm{d}W_t
      &=\left[f(t)B_t+F(t)\cdot0+\frac{1}{2}\cdot0\cdot1^2\right]\mathrm{d}t+[F(t)\cdot1]\mathrm{d}B_t\\
      &=f(t)B_t\mathrm{d}t+F(t)\mathrm{d}B_t\\
  \end{aligned}
$$

注意到 $B_t$ 零初值即 $B_0=0$, 那么上式两边从 $0$ 到 $t$ 积分可得
$$
  \begin{aligned}
    W_t-W_0
      &=F(t)B_t-0\\
      &=\int_0^tf(s)B_s\mathrm{d}s+\int_0^tF(s)\mathrm{d}B_s\\
  \end{aligned}
$$

故由 Itô 积分的一阶矩和二阶矩性质可知
$$
  \begin{aligned}
  X_t
    &=\int_0^tf(s)B_s\mathrm{d}s\\
    &=F(t)B_t-\int_0^tF(s)\mathrm{d}B_s\\
    &=\int_0^t[F(t)-F(s)]\mathrm{d}B_s\\
    &\sim N\left(0,\int_0^t[F(t)-F(s)]^2\mathrm{d}s\right)\\
  \end{aligned}
$$

即 $X_t$ 的概率分布是期望为 $0$, 方差为
$$
  \int_0^t[F(t)-F(s)]^2\mathrm{d}s
$$
的正态分布.

+ $\mathrm{d}Y_t=f(t)B_t\mathrm{d}B_t$

**解**: 布朗运动本身即为 Itô 过程, 有 Itô 微分方程
$$
  \mathrm{d}B_t=0\times\mathrm{d}t+1\times\mathrm{d}B_t
$$

令 $g(t,x)=f(t)x^2/2$, 其相应偏导数为
$$
  \frac{\partial g}{\partial t}=f'(t)\frac{x^2}{2},~
  \frac{\partial g}{\partial x}=f(t)x,~
  \frac{\partial^2 g}{\partial x^2}=f(t)
$$

令 $Z_t=f(t)B_t^2/2$, 由 Itô 公式可知
$$
  \begin{aligned}
    \mathrm{d}Z_t
      &=\left[f'(t)\frac{B_t^2}{2}+f(t)B_t\cdot0+\frac{1}{2}f(t)\cdot1^2\right]\mathrm{d}t+[f(t)B_t\cdot1]\mathrm{d}B_t\\
      &=\frac{1}{2}[f'(t)B_t^2+f(t)]\mathrm{d}t+f(t)B_t\mathrm{d}B_t\\
  \end{aligned}
$$

注意到 $B_t$ 零初值即 $B_0=0$, 那么上式两边从 $0$ 到 $t$ 积分可得
$$
  \begin{aligned}
    Z_t-Z_0
      &=\frac{1}{2}f(t)B_t^2-0\\
      &=\int_0^t\frac{1}{2}\left[f'(s)B_s^2+f(s)\right]\mathrm{d}s+\int_0^tf(s)B_s\mathrm{d}B_s\\
  \end{aligned}
$$

故
$$
  \begin{aligned}
    Y_t
      &=\int_0^tf(s)B_s\mathrm{d}B_s\\
      &=\frac{1}{2}\left\{f(t)B_t^2-\int_0^t\Big[f(s)+f'(s)B_s^2\Big]\mathrm{d}s\right\}\\
  \end{aligned}
$$

## 7.6 解的存在性和唯一性问题

**定理 随机微分方程解的存在和唯一性**

设对 $\forall~t\geqslant0$, $x,y\in\mathbb{R}$, $K>0$, $b(t,x)$, $\sigma(t,x)$ 满足**整体 Lipschitz 条件**
$$
  |b(t,x)-b(t,y)|+|\sigma(t,x)-\sigma(t,y)|\leqslant K|x-y|
$$

和**线性增长条件**
$$
  |b(t,x)|+|\sigma(t,x)|\leqslant K(1+|x|)
$$

$B=\{B_t,~\mathcal{F}_t^B:t\geqslant0\}$ 是 $(\Omega,\mathcal{F},P)$ 上的布朗运动, $\xi$ 是 $(\Omega,\mathcal{F},P)$ 上的随机变量且与布朗运动**独立**, $E|\xi|^2 < \infty$, 则随机微分方程
$$
  \mathrm{d}X_t=b(t,X_t)\mathrm{d}t+\sigma(t,X_t)\mathrm{d}B_t,~X_0=\xi
$$

**存在唯一强解**, 而且 $\exists~C>0$, $C$ 可以依赖于 $(K,T)$, 使得 $\forall~0\leqslant t\leqslant T$, 有
$$
  E|X_t|^2\leqslant C(1+E|\xi|^2)\mathrm{e}^{Ct}
$$

## 参考文献

+ 林元烈. 应用随机过程[M]. 北京: 清华大学出版社, 2002.
+ 何声武. 随机过程导论[M]. 北京: 高等教育出版社, 1999.
+ Ross S M. Stochastic Processes[M]. John Wiley and Sons, 1993.
