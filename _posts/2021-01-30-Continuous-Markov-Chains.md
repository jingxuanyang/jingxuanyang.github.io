---
layout: post
title:  "应用随机过程|第6章 连续时间参数马尔可夫链"
date:   2021-01-30
categories: applied-stochastic-process
tags: applied-stochastic-process stochastic-process continuous-Markov-chains
author: Jingxuan Yang
mathjax: true
---

* content
{:toc}


## 引言

在第3章中, 曾详细地讨论了**离散参数**马尔可夫链的有关问题, 本章将着重研究**连续参数可列状态空间**的马尔可夫过程.





## 6.1 定义与若干基本概念

仍记状态空间为 $S=\{0,1,2,\cdots\}$.

**定义 连续参数马氏链**

设随机过程 $X=\{X_t:t\geqslant0\}$ 对
$$
  \forall~0\leqslant t_0 < t_1 < \cdots < t_n < t_{n+1}
$$
$i_k\in S,~0\leqslant k\leqslant n+1$, 若
$$
  P(X_{t_0}=i_0,X_{t_1}=i_1,\cdots,X_{t_n}=i_n)>0
$$

有
$$
  P(X_{t_{n+1}}=i_{n+1}|X_{t_0}=i_0,X_{t_1}=i_1,\cdots,X_{t_n}=i_n)=P(X_{t_{n+1}}=i_{n+1}|X_{t_n}=i_n)
$$

则称 $X$ 为**连续时间参数马氏链**.

若对 $\forall~s,t\geqslant0,~i,j\in S$, 有
$$
  \begin{aligned}
    P(X_{s+t}=j|X_s=i)
      &=P(X_t=j|X_0=i)\\
      &\triangleq P_{ij}(t)\\
  \end{aligned}
$$

即**增量转移概率只与时间增量有关**, 则称 $X$ 为**时齐马氏链**. 称
$$
  \pmb{P}(t)=[P_{ij}(t)],~i,j\in S
$$
为**转移概率矩阵**, 易知它满足
+ **非负性**:
$$
  P_{ij}(t)\geqslant0,~\forall~i,j\in S
$$

+ **归一性**: 条件概率测度下的概率归一性
$$
  \sum_{j\in S}P_{ij}(t)=1,~\forall~i\in S
$$

+ **Kolmogorov-Chapman 方程**: 注意到状态空间的可列性则有 $\forall~s,t\geqslant0$
$$
  P_{ij}(s+t)=\sum_{k\in S}P_{ik}(s)P_{kj}(t),~\forall~i,j\in S
$$

$$
  \pmb{P}(s+t)=\pmb{P}(s)\pmb{P}(t)
$$

+ **初值条件**: 使用 Kronecker $\delta$ 符号有
$$
  P_{ij}(0)=\delta_{ij},~\forall~i,j\in S
$$

$$
  \pmb{P}(0)=\pmb{I}
$$

+ **连续性条件**: $P_{ij}(t)$ 在原点连续
$$
  \lim_{t\to0}P_{ij}(t)=P_{ij}(0)=\delta_{ij},~\forall~i,j\in S
$$

$$
  \lim_{t\to0}\pmb{P}(t)=\pmb{P}(0)=\pmb{I}
$$

**命题 一致连续性**

若 $\pmb{P}(t)=[P_{ij}(t)]$, $i,j\in S$ 为标准转移概率矩阵, 则
+ 对 $\forall~i\in S$, $P_{ij}(t)$ 在 $[0,\infty)$ 上**一致连续**, 且此时一致性对 $j$ 亦成立
+ $\forall~t\geqslant0,~i\in S$,
  $$
    P_{ii}(t)>0
  $$

**证明**: 由 Kolmogorov-Chapman 方程, 对 $\forall~t,h > 0$, 有
$$
  P_{ij}(t+h)-P_{ij}(t)=\sum_{k\neq i}P_{ik}(h)P_{kj}(t)-P_{ij}(t)[1-P_{ii}(h)]
$$

由此得
$$
  \begin{aligned}
    P_{ij}(t+h)-P_{ij}(t)
      &\leqslant\sum_{k\neq i}P_{ik}(h)P_{kj}(t)\\
      &\leqslant\sum_{k\neq i}P_{ik}(h)\\
      &=1-P_{ii}(h)\\
  \end{aligned}
$$
以及
$$
  \begin{aligned}
    P_{ij}(t+h)-P_{ij}(t)
      &\geqslant-P_{ij}(t)[1-P_{ii}(h)]\\
      &\geqslant-[1-P_{ii}(h)]\\
  \end{aligned}
$$

从而有
$$
  |P_{ij}(t+h)-P_{ij}(t)|\leqslant 1-P_{ii}(h)
$$

类似地, 当 $h < 0$ 时, 有
$$
  |P_{ij}(t)-P_{ij}(t+h)|\leqslant 1-P_{ii}(h)
$$

因此 $P_{ij}(t)$ 在 $[0,\infty)$ 上一致连续, 且此时一致性对 $j$ 亦成立.

由 $P_{ii}(0) > 0$ 及连续性条件
$$
  \lim_{t\to0}P_{ii}(t)=1
$$
可知, 对任意固定 $t > 0$, 当 $n$ 充分大时, 有
$$
  P_{ii}\left(\frac{t}{n}\right)>0
$$

再由 Kolmogorov-Chapman 方程
$$
  \begin{aligned}
    P_{ii}(s+t)
      &=\sum_{k\in S}P_{ik}(s)P_{ki}(t)\\
      &\geqslant P_{ii}(s)P_{ii}(t)\\
  \end{aligned}
$$

可得
$$
  P_{ii}(t)\geqslant \left[P_{ii}\left(\frac{t}{n}\right)\right]^n > 0
$$

**定义 概率分布**

记
$$
  \pi_i(t)=P(X_t=i),~\forall~t\geqslant0,~i\in S
$$
称
$$
  \pmb{\pi}(t)=(\pi_i(t),~i\in S)
$$

为马尔可夫链在 $t$ 时刻的**分布**, 称 $\pmb{\pi}(0)$ 为**初始分布**, 且有
$$
  \pmb{\pi}(t)=\pmb{\pi}(0)\pmb{P}(t)
$$

**定义 离散骨架**

对于连续时间马尔可夫链 $X=\{X_t:t\geqslant0\}$, 任取 $h>0$, 定义
$$
  X_n(h)=X(nh),~n\geqslant0
$$

由马尔可夫性可知, $\{X_n(h):n\geqslant0\}$ 是一个离散时间的马尔可夫链, 称其为以 $h$ 为步长的 $h$-**离散骨架**, 简称 $h$ 骨架, 它的 $n$ 步转移概率矩阵为 $\pmb{P}(nh)$.

对于连续参数马尔可夫链与离散参数马尔可夫链, 由于它们都具有马尔可夫性, 且状态空间均为可数集或有限集, 因而许多概念和性质有**相同或相似之处**, 例如状态相通, 状态分类, 不可约链, 平稳分布与极限分布等.

**定义 可达与互通**

+ **可达**: 若 $\exists~t>0$, $P_{ij}(t)>0$, 则称由状态 $i$ **可达**状态 $j$, 记为 $i\to j$

+ **不可达**: 若 $\forall~t>0$, $P_{ij}(t)=0$, 则称由状态 $i$ **不可达**状态 $j$, 记为 $i\nrightarrow j$

+ **互通**: 若 $i\to j$ 且 $j\to i$, 则称状态 $i$ 与 $j$ **相通**, 记为 $i\leftrightarrow j$

由 $\forall~i\in S$, $P_{ii}(t)>0$, 即 $i\leftrightarrow i$, 可知相通关系具有**自反性、对称性、传递性**, 故相通关系是**等价关系**, 从而可以按相通关系给状态分类, 相通的状态组成一个状态类. 若**整个状态空间是一个状态类**, 则称该马尔可夫链是**不可约的**.

对于连续时间的马尔可夫链, 对所有 $h>0$ 及正整数 $n$,
$$
P_{ii}(nh) > 0, ~ \forall~i\in S
$$

这意味着对每一个离散的骨架 $X_n(h)$, **每一个状态立都是非周期的**, 故可知对 $\forall~j\in S$, $\forall~h>0$, 有
$$
  \lim_{n\to\infty}P_{ij}(nh)=\pi_{ij}
$$
总存在. 所以对连续时间的马尔可夫链就无需引入周期的概念, 而且利用 $P_{ij}(t)$ 在$[0,\infty)$ 上**一致连续性**及
$$
  \lim_{n\to\infty}P_{ij}(nh)=\pi_{ij}
$$
总存在, 可以证明 $P_{ij}(t)$ 在 $t\to\infty$ 时**极限总存在**.

**命题**

$\forall~i,j\in S$, 下述极限总存在
$$
  \lim_{t\to\infty}P_{ij}(t)=\pi_{ij}
$$

**定义 常返与平稳分布**

+ **常返**: 若
  $$
    \int_0^\infty P_{ii}(t)\mathrm{d}t=\infty
  $$
  则称状态 $i$ 为**常返状态**, 否则称为**非常返状态**

+ **正常返**: 若
  $$
    \lim_{t\to\infty}P_{ii}(t)>0
  $$
  则称状态 $i$ 为**正常返状态**, 否则若
  $$
    \lim_{t\to\infty}P_{ii}(t)=0
  $$
  则称状态 $i$ 为**零常返状态**

+ **平稳分布**: 若概率分布 $\pmb{\pi}=(\pi_i,~i\in S)$ 满足
  $$
    \pmb{\pi}=\pmb{\pi}\pmb{P}(t),~\forall~t\geqslant0
  $$
  则称 $\pmb{\pi}$ 为马氏链的**平稳分布**

+ **极限分布**: 若对 $\forall~i\in S$,
  $$
    \lim_{n\to\infty}\pi_i(t)=\pi_i^*
  $$
  存在, 则称
  $$
    \pmb{\pi}^*\triangleq\{\pi_i^*:i\in S\}
  $$
  为马氏链的**极限分布**

可总结**离散时间参数**马氏链与**连续时间参数**马氏链**常返与正常返**相关判断依据如下表.

| 状态 | 非常返 | 常返 | 正常返 | 零常返 |
|:-|:-|:-|:-|:-|
| **离散 MC** | $f_{ii}<1$ | $f_{ii}=1$ | $\mu_i=\infty$ | $\mu_i<\infty$ |
| **离散 MC** | $G_{ii}=\dfrac{1}{1-f_{ii}}<\infty$ | $G_{ii}=\infty$ | $p_{ii}^{(n)}\to\dfrac{1}{\mu_i}>0$ | $p_{ii}^{(n)}\to0$ |
| **连续 MC** | $\displaystyle\int_0^\infty P_{ii}(t)\mathrm{d}t<\infty$ | $\displaystyle\int_0^\infty P_{ii}(t)\mathrm{d}t=\infty$ | $P_{ii}(t)\to C>0$ | $P_{ii}(t)\to0$ |

$$
  \begin{array}{l|lll}
    \text{状态} & \text{非常返} & \text{常返} & \text{正常返} & \text{零常返}\\
    \hline
    \text{离散 MC} & f_{ii}<1 & f_{ii}=1 & \mu_i=\infty & \mu_i<\infty \\
    \text{离散 MC} & G_{ii}=\dfrac{1}{1-f_{ii}}<\infty & G_{ii}=\infty & p_{ii}^{(n)}\to\dfrac{1}{\mu_i}>0 & p_{ii}^{(n)}\to0 \\
    \text{连续 MC} & \displaystyle\int_0^\infty P_{ii}(t)\mathrm{d}t<\infty & \displaystyle\int_0^\infty P_{ii}(t)\mathrm{d}t=\infty & P_{ii}(t)\to C>0 & P_{ii}(t)\to0 \\
  \end{array}
$$

**定理 平稳分布与极限分布**

**不可约链**是**正常返**的**充要条件**是它存在**平稳分布**, 且此时**平稳分布就等于极限分布**.

## 6.2 转移率矩阵及其概率意义

在离散参数马尔可夫链中, 我们知道由一步转移概率矩阵 $\pmb{P}=[P_{ij}]$ 可以完全确定 $n$ 步转移矩阵, 即有
$$
  \pmb{P}^{(n)}=\pmb{P}^n=\mathrm{e}^{n\ln\pmb{P}}
$$

那么对连续参数马尔可夫链, 是否有类似的表达式, 即
$$
  \pmb{P}(t)=\mathrm{e}^{t\pmb{Q}}
$$

呢? 其中 $\pmb{Q}$ 为与 $t$ 无关的实数矩阵, 假如上式存在, 则应有
$$
  \begin{aligned}
    \pmb{P}'(0)
    &=\lim_{t\to0}\frac{\pmb{P}(t)-\pmb{P}(0)}{t}\\
    &=\lim_{t\to0}\frac{\mathrm{e}^{t\pmb{Q}}-\pmb{I}}{t}\\
    &=\pmb{Q}
  \end{aligned}
$$

直观来说, 即
$$
  \begin{aligned}
    \pmb{Q}
    &=
    \left(
      \begin{bmatrix}
        P_{00}(t) & P_{01}(t) & P_{02}(t) & \cdots \\
        P_{10}(t) & P_{11}(t) & P_{12}(t) & \cdots \\
        P_{00}(t) & P_{01}(t) & P_{02}(t) & \cdots \\
        \vdots & \vdots & \vdots & \ddots \\
      \end{bmatrix}
      -
      \begin{bmatrix}
        1 & 0 & 0 & \cdots \\
        0 & 1 & 0 & \cdots \\
        0 & 0 & 1 & \cdots \\
        \vdots & \vdots & \vdots & \ddots \\
      \end{bmatrix}
    \right)_t'\\
    &=
    \begin{bmatrix}
        P_{00}(t)-1 & P_{01}(t) & P_{02}(t) & \cdots \\
        P_{10}(t) & P_{11}(t)-1 & P_{12}(t) & \cdots \\
        P_{00}(t) & P_{01}(t) & P_{02}(t)-1 & \cdots \\
        \vdots & \vdots & \vdots & \ddots \\
      \end{bmatrix}_t'\\
    &\triangleq
    \begin{bmatrix}
        -q_0\triangleq q_{00} & q_{01} & q_{02} & \cdots \\
        q_{10} & -q_1\triangleq q_{11} & q_{12} & \cdots \\
        q_{20} & q_{21} & -q_2\triangleq q_{22} & \cdots \\
        \vdots & \vdots & \vdots & \ddots \\
    \end{bmatrix}
  \end{aligned}
$$

这就提示我们先要研究 $\pmb{P}(t)$ 在 $t=0$ 的导数即变化率是否存在的问题.

**定理**

对 $\forall~i\in S$, 极限
$$
  q_i=-q_{ii}\triangleq\lim_{t\to0}\frac{1-P_{ii}(t)}{t}
$$

存在, 但可能是无限.

**定理**

对 $\forall~i,j\in S,~j\neq i$, 极限
$$
  q_{ij}\triangleq P_{ij}'(0)=\lim_{t\to0}\frac{P_{ij}(t)}{t}
$$

存在且有限.

**推论**

对 $\forall~i\in S$,
$$
  q_i\geqslant\sum_{j\neq i}q_{ij}\geqslant0
$$

**推论**

当 $S$ 为**有限状态空间**时, $\forall~i\in S$, 有
$$
  0\leqslant q_i=\sum_{j\neq i}q_{ij}<\infty
$$

**定义  Q 矩阵**

记 $\pmb{Q}=[q_{ij}],~i,j\in S$, 称 $\pmb{Q}$ 为 $X=\{X_t:t\geqslant0\}$ 的转移率矩阵.

若转移率矩阵满足 $\forall~i\in S$,
$$
  q_i=\sum_{j\neq i}q_{ij}<\infty
$$

则称 $\pmb{Q}$ 为**保守 Q 矩阵**. 易知当 $S$ 为有限状态空间时, $\pmb{Q}$ 必保守.

**定义 逗留时间**

令 $\tau_1$ 表示马氏链**逗留在初始状态的时间**, 即
$$
  \tau_1=\inf_{t>0}\{t:X_t\neq X_0\}
$$

**定理 逗留时间服从指数分布**

设马尔可夫链 $X=\{X_t:t\geqslant0\}$ 轨道右连续, 则对 $\forall~i\in S,~t\geqslant0$, 有
$$
  P(\tau_1>t|X_0=i)=\mathrm{e}^{-q_it}
$$

这说明系统逗留在 $X_0=i$ 状态的时间 $\tau_1$ 服从参数为 $q_i$ 的指数分布, 其期望为
$$
  \begin{aligned}
    E[\tau_1|X_0=i]
    &=\int_0^\infty P(\tau_1>t|X_0=i)\mathrm{d}t\\
    &=\int_0^\infty\mathrm{e}^{-q_it}\mathrm{d}t\\
    &=\frac{1}{q_i}
  \end{aligned}
$$

**定义 吸收状态, 瞬时状态与逗留状态**

+ **吸收状态**: $q_i=0$, 即从 $i$ 出发, 过程以概率 $1$ **永远停留**在 $i$ 状态
+ **瞬时状态**: $q_i=\infty$, 这说明 $X$ 在 $i$ 状态**几乎不停留**立即跳到别的状态
+ **逗留状态**: $0 < q_i < \infty$, 过程停留在状态 $i$, 若干时间后跳到其他状态, 且停留时间服从**指数分布**

**定理**

设马尔可夫链 $X=\{X_t:t\geqslant0\}$ 轨道右连续, 且 $0 < q_i < \infty$, 则对 $\forall~t\geqslant0,~j\neq i$, 有
$$
  P(\tau_1\leqslant t,~X_{\tau_1}=j|X_0=i)=\frac{q_{ij}}{q_i}(1-\mathrm{e}^{-q_it})
$$

$$
  P(X_{\tau_1}=j|X_0=i)=\frac{q_{ij}}{q_i}
$$

**推论 逗留时间与前跳状态条件独立**

设马尔可夫链 $X=\{X_t:t\geqslant0\}$ 轨道右连续, $\pmb{Q}$ 为保守 Q 矩阵, $0 < q_i < \infty$, 则 $\forall~i\in S$, $X_{\tau_1}$ 与 $\tau_1$ 关于 $X_0=i$ **条件独立**, 换句话说, 已知当前状态, 逗留时间与下一步跳到哪里去是条件独立的.

## 6.3 Kolmogorov 向前向后微分方程

**定理 Kolmogorov 向前向后微分方程**

设马尔可夫链 $X=\{X_t:t\geqslant0\}$, $\pmb{P}(t)=[P_{ij}(t)]$, $\pmb{Q}=[q_{ij}]$, $i,j\in S$, 当 $S$ 为有限状态空间时, 有
$$
  \pmb{P}'(t)=\pmb{P}(t)\pmb{Q}
$$

$$
  \pmb{P}'(t)=\pmb{Q}\pmb{P}(t)
$$

其中 $\pmb{P}(t)$ 在前面称为**向前微分方程**, $\pmb{P}(t)$ 在后面称为**向后微分方程**.

此时
$$
  \pmb{P}(t)=\mathrm{e}^{t\pmb{Q}}\triangleq\sum_{k=0}^\infty\frac{t^k}{k!}\pmb{Q}^k
$$

**证明**: 考虑右导数, 向前微分方程为
$$
  \begin{aligned}
    P_{ij}'(t+)
      &=\lim_{h\downarrow0}\frac{P_{ij}(t+h)-P_{ij}(t)}{h}\\
      &=\lim_{h\downarrow0}\frac{\sum\limits_{k\in S}P_{ik}(t)P_{kj}(h)-\sum\limits_{k\in S}P_{ik}(t)\delta_{kj}}{h}\\
      &=\lim_{h\downarrow0}\frac{\sum\limits_{k\in S}P_{ik}(t)[P_{kj}(h)-\delta_{kj}]}{h}\\
      &=\sum_{k\in S}\lim_{h\downarrow0}\frac{P_{ik}(t)[P_{kj}(h)-\delta_{kj}]}{h}\\
      &=\sum_{k\in S}P_{ik}(t)q_{kj}
  \end{aligned}
$$

同理可得向后微分方程
$$
  \begin{aligned}
    P_{ij}'(t+)
      &=\lim_{h\downarrow0}\frac{P_{ij}(t+h)-P_{ij}(t)}{h}\\
      &=\lim_{h\downarrow0}\frac{\sum\limits_{k\in S}P_{ik}(t)P_{kj}(h)-\sum\limits_{k\in S}\delta_{ik}P_{kj}(t)}{h}\\
      &=\lim_{h\downarrow0}\frac{\sum\limits_{k\in S}[P_{ik}(h)-\delta_{ik}]P_{kj}(t)}{h}\\
      &=\sum_{k\in S}\lim_{h\downarrow0}\frac{[P_{ik}(h)-\delta_{ik}]P_{kj}(t)}{h}\\
      &=\sum_{k\in S}q_{ik}P_{kj}(t)
  \end{aligned}
$$

**定理 Fokker-Planck 方程**

当 $S$ 为**有限状态空间**时, 成立下列 **Fokker-Planck 方程**
$$
  \begin{aligned}
    \pmb{\pi}'(t)
      &=\pmb{\pi}(0)\pmb{P}'(t)\\
      &=\pmb{\pi}(0)\pmb{P}(t)\pmb{Q}\\
      &=\pmb{\pi}(t)\pmb{Q}\\
  \end{aligned}
$$

**例题 解 Kolmogorov 向前向后微分方程**

设有连续时间参数 Markov 链 $X$, 其轨道右连续,
$$
  \tau_1=\inf_{t>0}\{t:X_t\neq X_0\},
$$

已知
$$
  \begin{aligned}
    P(\tau_1>t|X_0=0)&=\mathrm{e}^{-\lambda t}\\
    P(\tau_1>t|X_0=1)&=\mathrm{e}^{-\mu t}\\
  \end{aligned}
$$

写出关于 $p_{00}(t),~p_{11}(t)$ 的 Kolmogorov 向前微分方程, 并求解得到表达式.

**解**: 由题意可知
$$
q_0=\lambda,~q_1=\mu
$$

即
$$
  q_{00}=-\lambda,~q_{11}=-\mu
$$

故 $\pmb{Q}$ 矩阵为
$$
  \pmb{Q}=
  \begin{bmatrix}
    -\lambda & \lambda \\
    \mu & -\mu
  \end{bmatrix}
$$

则由 Kolmogorov 向前微分方程
$$
  \pmb{P}'(t)=\pmb{P}(t)\pmb{Q}
$$

可得
$$
  \begin{bmatrix}
    p_{00}'(t) & p_{01}'(t) \\
    p_{10}'(t) & p_{11}'(t) \\
  \end{bmatrix}
  =\begin{bmatrix}
    p_{00}(t) & p_{01}(t) \\
    p_{10}(t) & p_{11}(t) \\
  \end{bmatrix}
  \begin{bmatrix}
    -\lambda & \lambda \\
    \mu & -\mu
  \end{bmatrix}
$$

即
$$
  \begin{bmatrix}
    p_{00}'(t) & p_{01}'(t) \\
    p_{10}'(t) & p_{11}'(t) \\
  \end{bmatrix}
  =\begin{bmatrix}
    -\lambda p_{00}(t)+\mu p_{01}(t) & \lambda p_{00}(t)-\mu p_{01}(t) \\
    -\lambda p_{10}(t)+\mu p_{11}(t) & \lambda p_{10}(t)-\mu p_{11}(t) \\
  \end{bmatrix}
$$

又
$$
  \begin{aligned}
    p_{00}(t)+p_{01}(t)&=1\\
    p_{10}(t)+p_{11}(t)&=1\\
  \end{aligned}
$$

则关于 $p_{00}(t),~p_{11}(t)$ 的 Kolmogorov 向前微分方程为
$$
  \begin{aligned}
    p_{00}'(t)
    &=-\lambda p_{00}(t)+\mu [1-p_{00}(t)]=-(\lambda+\mu)p_{00}(t)+\mu\\
    p_{11}'(t)&=\lambda [1-p_{11}(t)]-\mu p_{11}(t)=-(\lambda+\mu)p_{11}(t)+\lambda\\
  \end{aligned}
$$

即
$$
  \begin{aligned}
    p_{00}'(t)+(\lambda+\mu)p_{00}(t)&=\mu\\
    p_{11}'(t)+(\lambda+\mu)p_{11}(t)&=\lambda\\
  \end{aligned}
$$

两边乘以积分因子
$$
  \begin{aligned}
    \exp[(\lambda+\mu)t][p_{00}'(t)+(\lambda+\mu)p_{00}(t)]&=\mu\exp[(\lambda+\mu)t]\\
    \exp[(\lambda+\mu)t][p_{11}'(t)+(\lambda+\mu)p_{11}(t)]&=\lambda\exp[(\lambda+\mu)t]\\
  \end{aligned}
$$

即
$$
  \begin{aligned}
    \{\exp[(\lambda+\mu)t]p_{00}(t)\}_t'&=\mu\exp[(\lambda+\mu)t]\\
    \{\exp[(\lambda+\mu)t]p_{11}(t)\}_t'&=\lambda\exp[(\lambda+\mu)t]\\
  \end{aligned}
$$

两边从 $0$ 到 $t$ 积分并利用初始条件
$$
  p_{00}(0)=p_{11}(0)=1
$$
可得
$$
  \begin{aligned}
    \exp[(\lambda+\mu)t]p_{00}(t)-1&=\frac{\mu}{\lambda+\mu}\exp[(\lambda+\mu)t]-\frac{\mu}{\lambda+\mu}\\
    \exp[(\lambda+\mu)t]p_{11}(t)-1&=\frac{\lambda}{\lambda+\mu}\exp[(\lambda+\mu)t]-\frac{\lambda}{\lambda+\mu}\\
  \end{aligned}
$$

故
$$
  \begin{aligned}
    p_{00}(t)&=\frac{\mu}{\lambda+\mu}+\frac{\lambda}{\lambda+\mu}\exp[-(\lambda+\mu)t]\\
    p_{11}(t)&=\frac{\lambda}{\lambda+\mu}+\frac{\mu}{\lambda+\mu}\exp[-(\lambda+\mu)t]\\
  \end{aligned}
$$

## 参考文献

+ 林元烈. 应用随机过程[M]. 北京: 清华大学出版社, 2002.
+ 何声武. 随机过程导论[M]. 北京: 高等教育出版社, 1999.
+ Ross S M. Stochastic Processes[M]. John Wiley and Sons, 1993.
