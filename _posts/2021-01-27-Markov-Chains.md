---
layout: post
title:  "应用随机过程|第3章 马尔可夫链"
date:   2021-01-27
categories: applied-stochastic-process
tags: applied-stochastic-process stochastic-process Markov-chains
author: Jingxuan Yang
---

* content
{:toc}

## 3.1 定义与例子

**定义 马尔可夫链**

若随机序列 $\{X_n:n\geqslant 0\}$ 对任意
$$
  i_0,i_1,\ldots,i_n,i_{n+1}\in S,\ n\in\mathbb{N}_0
$$
及
$$
  P(X_0=i_0,X_1=i_1,\cdots,X_n=i_n)>0
$$
有
$$
  P(X_{n+1}=i_{n+1}|X_0=i_0,X_1=i_1,\cdots,X_n=i_n)=P(X_{n+1}=i_{n+1}|X_n=i_n)
$$
则称其为**马尔可夫链** (Markov chain).





**注释**

马尔可夫链的定义式揭示了马尔可夫链的特性, 即马尔可夫性或无后效性: 将来
$$
  X_{n+1}=i_{n+1}
$$
与过去
$$
  X_0=i_0,X_1=i_1,\cdots,X_{n-1}=i_{n-1}
$$
关于现在 $X_n=i_n$ **条件独立**.

**定义 一步转移概率与转移矩阵**

$\forall~i,j\in S$,
$$
  P(X_{n+1}=j|X_n=i)\triangleq p_{ij}(n)
$$
称为时刻 $n$ 从 $i$ 到 $j$ 的一步转移概率.

若 $\forall~i,j\in S,\ p_{ij}(n)=p_{ij}$ 不依赖于 $n$, 则称 $X=\{X_n,n\geqslant 0\}$ 为**时齐马氏链** (HMC, Homogeneous Markov Chain). 记 $\pmb{P}=(p_{ij})_{i,j\in S}$, 则称 $\pmb{P}$ 为 $X$ 的**一步转移概率矩阵**, 简称为**转移矩阵** (transition matrix).

**定义 转移图**

**转移图**是一个有向图 $G=(V,E)$, $V=S$,
$$
  E=\Big\{\overrightarrow{ij}~|~i,j\in S,~p_{ij}>0\Big\}
$$

**例 随机游动**

独立同分布随机变量序列 $\{\xi_n,n\geqslant1\}$ 取整数值, 整数值随机变量 $X_0$ 与 $\{\xi_n,n\geqslant1\}$ 独立,
$$
  X_n=X_0+\sum_{k=1}^n\xi_k,\ \forall~n\geqslant1
$$
则 $\{X_n,n\geqslant0\}$ 是时齐马氏链.

**证明**: $\forall~n\in\mathbb{N},\ i_0,i_1,\ldots,i_{n-1},i,j\in \mathbb{Z}$,
$$
  \begin{aligned}
    & P(X_{n+1}=j|X_0=i_0,X_1=i_1,\cdots,X_{n-1}=i_{n-1},X_n=i)\\
    =& P(X_n+\xi_{n+1}=j|X_0=i_0,X_1=i_1,\cdots,X_{n-1}=i_{n-1},X_n=i)\\
    =& P(i+\xi_{n+1}=j|X_0=i_0,X_1=i_1,\cdots,X_{n-1}=i_{n-1},X_n=i)\\
    =& P(\xi_{n+1}=j-i)\\
  \end{aligned}
$$
另一方面
$$
  \begin{aligned}
    P(X_{n+1}=j|X_n=i)
      &=P(i+\xi_{n+1}=j|X_n=i)\\
      &=P(\xi_{n+1}=j-i)\\
  \end{aligned}
$$
则
$$
  P(X_{n+1}=j|X_0=i_0,X_1=i_1,\cdots,X_{n-1}=i_{n-1},X_n=i)=P(X_{n+1}=j|X_n=i)
$$
所以 $\{X_n,n\geqslant0\}$ 是时齐马氏链.

**定理 由当前事件和独立序列生成的马氏链**

独立同分布随机变量序列 $\{\xi_n,n\geqslant1\}$ 均取值于 $S$,
$$
  f:S\times S\to S
$$
$$
  X_n=f(X_{n-1},\xi_n)
$$
$X_0$ 与 $\{\xi_n,n\geqslant1\}$ 相互独立, 则 $X=\{X_n,n\geqslant0\}$ 是时齐马氏链, 转移概率
$$
  p_{ij}=P(f(i,\xi_1)=j)
$$

**证明**: 对
$$
  \forall~i_0,i_1,\cdots,i_{n-1},i,j\in S
$$
有
$$
  \begin{aligned}
    & P(X_{n+1}=j|X_0=i_0,X_1=i_1,\cdots,X_{n-1}=i_{n-1},X_n=i)\\
    =& P(f(X_n,\xi_{n+1})=j|X_0=i_0,X_1=i_1,\cdots,X_{n-1}=i_{n-1},X_n=i)\\
    =& P(f(i,\xi_{n+1})=j|X_0=i_0,X_1=i_1,\cdots,X_{n-1}=i_{n-1},X_n=i)\\
    =& P(f(i,\xi_{n+1})=j)\\
    =& P(f(i,\xi_1)=j)
  \end{aligned}
$$
另一方面
$$
  \begin{aligned}
    P(X_{n+1}=j|X_n=i)
      &=P(f(i,\xi_{n+1})=j|X_n=i)\\
      &=P(f(i,\xi_{n+1})=j)\\
  \end{aligned}
$$
则
$$
  P(X_{n+1}=j|X_0=i_0,X_1=i_1,\cdots,X_{n-1}=i_{n-1},X_n=i)=P(X_{n+1}=j|X_n=i)
$$
所以 $\{X_n,n\geqslant0\}$ 是时齐马氏链.

## 3.2 转移概率矩阵

设 $X=\{X_n,n\geqslant0\}$ 是时齐马氏链, 一步转移概率矩阵 $\pmb{P}=(p_{ij})_{i,j\in S}$,
$$
  \begin{aligned}
    p_{ij}
      &=P(X_{n+1}=j|X_n=i)\\
      &=P(X_1=j|X_0=i)\\
  \end{aligned}
$$
则显然有
$$
  p_{ij}\geqslant0,~\sum_{j\in S}p_{ij}=1
$$
这两条来自条件概率测度 $P(\cdot|X_n=i)$ 的基本性质.

**定义 转移矩阵**

称矩阵 $\pmb{A}=(a_{ij})_{i,j\in S}$ 为**转移矩阵**, 若 $a_{ij}\geqslant0$, 且
$$
  \sum_{j\in S}a_{ij}=1
$$

记 $\pi_i(n)=P(X_n=i)$,
$$
  \pmb{\pi}(n)=(\pi_1(n),\pi_2(n),\cdots,\pi_i(n),\cdots)
$$
表示 $n$ 时刻 $X_n$ 的**概率分布向量**, $X_0\sim\pmb{\pi}(0)$ 称为 $X$ 的初始分布.

**定理 概率分布的全概率公式**

$$\pmb{\pi}(n+1)=\pmb{\pi}(n)\pmb{P},\quad \pmb{\pi}(n)=\pmb{\pi}(0)\pmb{P}^n$$

**证明**: 由全概率公式可知
$$
  \begin{aligned}
    P(X_{n+1}=j)&=\sum_{i\in S}P(X_n=i)P(X_{n+1}=j|X_n=i)\\
    &=\sum_{i\in S} \pi_i(n)p_{ij}
  \end{aligned}
$$
写成向量形式为
$$
  \pmb{\pi}(n+1)=\pmb{\pi}(n)\pmb{P}
$$
反复应用则有
$$
  \pmb{\pi}(n)=\pmb{\pi}(0)\pmb{P}^n
$$

**注释**

一个马尔可夫链的特性完全由它的一步转移概率矩阵 $\pmb{P}$ 及初始分布向量 $\pmb{\pi}(0)$ 决定.

**定理 Kolmogorov-Chapman 方程 多步转移的全概率公式**

记 $p_{ij}^{(m)}=P(X_{n+m}=j|X_n=i)$ 为 $m$ **步转移概率**, $\pmb{P}^{(m)}=\{p_{ij}^{(m)}\}$ 为 $m$ **步转移概率矩阵**, 则
$$
  \begin{aligned}
    p_{ij}^{(m+n)}&=\sum_{k\in S}p_{ik}^{(m)}p_{kj}^{(n)}\\
    \pmb{P}^{(m+n)}&=\pmb{P}^{(m)}\pmb{P}^{(n)}\\
    \pmb{P}^{(n)}&=\pmb{P}^n
  \end{aligned}
$$

**证明**: 由**条件概率形式的全概率公式**可知
$$
  \begin{aligned}
    p_{ij}^{(m+n)}&=P(X_{m+n}=j|X_0=i)\\
    &=\sum_{k\in S}P(X_m=k|X_0=i)P(X_{m+n}=j|X_0=i,X_m=k)\\
    &=\sum_{k\in S}P(X_m=k|X_0=i)P(X_{m+n}=j|X_m=k)\\
    &=\sum_{k\in S} p_{ik}^{(m)}p_{kj}^{(n)}
  \end{aligned}
$$
写成向量形式为
$$
  \pmb{P}^{(m+n)}=\pmb{P}^{(m)}\pmb{P}^{(n)}
$$

**注释**

一个马尔可夫链运动规律的概率特性取决于它的转移概率矩阵特性.

## 3.3 状态的分类

**定义 吸收态可达与互通**

+ **吸收态**: 称 $i\in S$ 为吸收态, 若 $p_{ii}=1$, 即到达 $i$ 之后就不再移动了
+ **可达**: 若 $i,j\in S$, 存在 $n\geqslant0$ 使得 $p_{ij}^{(n)}>0$, 则称 $i$ 可达 $j$, 记为 $i\rightarrow j$, 即转移图中存在从 $i$ 到 $j$ 的通路
+ **互通**: 若 $i\rightarrow j$ 且 $j\rightarrow i$, 则称 $i$ 与 $j$ 互通, 记为 $i\leftrightarrow j$

**定理 互通为等价关系**

状态相通关系为**等价关系**因其满足

+ **自反性**: $i\leftrightarrow i$
+ **对称性**: 若 $i\leftrightarrow j$, 则 $j\leftrightarrow i$
+ **传递性**: 若 $i\leftrightarrow j$ 且 $j\leftrightarrow k$, 则 $i\leftrightarrow k$

**注释**

利用等价关系, 可以把马尔可夫链的状态空间分为若干等价类. 在统一等价类内的状态彼此相通, 在不同等价类中的状态不可能彼此相通. 然而, 从某一类出发以正的概率到达另一类的情形是可能的. 如一马尔可夫链的所有状态属于同一等价类, 则称它是**不可约链**.

**定义 首达时间与首达概率**

+ **首达时间**: 从 $i$ 出发首次到达 $j$ 的时间定义为
  $$
    T_{ij}=\min_{n\geqslant1}\{n:X_n=j,~X_0=i\}
  $$
  若右侧为空集, 则令 $T_{ij}=\infty$
+ **首达概率**: 从 $i$ 出发经 $n$ 步首次到达 $j$ 的概率定义为
  $$
    \begin{aligned}
      f_{ij}^{(n)}
      &=P(T_{ij}=n|X_0=i)\\
      &=P(X_n=j,~X_k\neq j,1\leqslant k\leqslant n-1|X_0=i)\\
    \end{aligned}
  $$
+ **有限步首达概率**: 从 $i$ 出发经有限步首次到达 $j$ 的概率定义为
  $$
    f_{ij}=\sum_{n=1}^\infty f_{ij}^{(n)}
  $$

**定义 常返与非常返**

+ **常返状态**: 称状态 $i$ 为常返状态, 若 $f_{ii}=1$
+ **非常返状态**: 称状态 $i$ 为非常返状态, 若 $f_{ii}<1$

**定义 正频率常返与零频率常返**

当 $f_{ii}=1$ 时, $\Big\{f_{ii}^{(n)}:n\geqslant1\Big\}$ 是一个**概率分布**. 记 $\mu_i$ 表示从 $i$ 出发再回到 $i$ 的**平均回转时间** $ET_{ii}$, 即
$$
  \begin{aligned}
    \mu_i
      &=ET_{ii}\\
      &=\sum_{n=1}^\infty n P(T_{ii}=n|X_0=i)\\
      &=\sum_{n=1}^\infty nf_{ii}^{(n)}\\
  \end{aligned}
$$

+ **正常返状态**: 称状态 $i$ 为正常返状态, 若 $\mu_i=ET_{ii}<\infty$, 此时**平均返回频率**
$$
  \nu_i=\frac{1}{\mu_i}=\frac{1}{ET_{ii}}>0
$$

+ **零常返状态**: 称状态 $i$ 为零常返状态, 若 $\mu_i=ET_{ii}=\infty$, 此时**平均返回频率**
$$
  \nu_i=\frac{1}{\mu_i}=\frac{1}{ET_{ii}}=0
$$

**定义 周期与遍历**

+ **周期**: 若**返回步数**集合
  $$
    \Big\{n:n\geqslant1,~p_{ii}^{(n)}>0\Big\}\neq\varnothing,
  $$

  则称该集合的**最大公约数** $d(i)$ 为状态 $i$ 的周期

+ **周期状态**: $d(i)>1$
+ **非周期状态**: $d(i)=1$
+ **遍历状态**: 状态 $i$ 为**正常返**状态且**非周期**

**定理 首达全概率公式**

对 $\forall~i,j\in S$, $n\geqslant1$, 有
+ **$n$ 步转移概率**
$$
  p_{ij}^{(n)}=\sum_{l=1}^n f_{ij}^{(l)}p_{jj}^{(n-l)}
$$

+ **$n$ 步首达概率**
$$
  f_{ij}^{(n)}=\sum_{k\neq j}p_{ik}f_{kj}^{(n-1)}\pmb{1}_{\{n>1\}}+p_{ij}\pmb{1}_{\{n=1\}}
$$

+ **可达与互通的有限步首达概率表示**
$$
  \begin{aligned}
    i\to j&\Leftrightarrow f_{ij}>0\\ i\leftrightarrow j&\Leftrightarrow f_{ij}f_{ji}>0
  \end{aligned}
$$

**定理 常返与非常返的充要条件**

状态 $i$ 为**常返状态**, $f_{ii}=1$, 当且仅当
$$
  G_{ii}\triangleq\sum_{n=0}^\infty p_{ii}^{(n)}=\infty,
$$

状态 $i$ 为**非常返状态**, $f_{ii}<1$, 当且仅当
$$
  G_{ii}=\sum_{n=0}^\infty p_{ii}^{(n)}=\frac{1}{1-f_{ii}}<\infty.
$$

**证明**: 约定 $p_{ii}^{(0)}=1,~f_{ii}^{(0)}=0$. 记生成函数
$$
  \begin{aligned}
    P(\rho)&=\sum_{n=0}^\infty p_{ii}^{(n)}\rho^n\\
    F(\rho)&=\sum_{n=0}^\infty f_{ii}^{(n)}\rho^n
  \end{aligned}
$$

通过交换求和次序可知
$$
  P(\rho)-1=P(\rho)F(\rho),
$$

即
$$
  P(\rho)=\frac{1}{1-F(\rho)},\quad0\leqslant\rho<1,
$$

两边令 $\rho\uparrow1$ 可得
$$
  G_{ii}=\frac{1}{1-f_{ii}},
$$

故由常返和非常返定义可得结论.

**定理 正常返与零常返的充要条件**

设 $i$ 为**常返状态**, 则有

+ 状态 $i$ 为**零常返状态**, $\mu_i=ET_{ii}=\infty$, 当且仅当
$$
  \lim_{n\to\infty} p_{ii}^{(n)}=0,
$$

+ 状态 $i$ 为**正常返状态**且**非周期**, 即**遍历态**, $\mu_i=ET_{ii}<\infty$, 当且仅当
$$
  \lim_{n\to\infty} p_{ii}^{(n)}=\frac{1}{\mu_i}>0.
$$

**定理 常返可达必常返**

如果 $i$ 为常返状态, 且 $i\to j$, 则 $j$ 必为常返状态, 且
$$
  f_{ji}=1.
$$

**定理 状态互通必相同**

若 $i\leftrightarrow j$, 则

+ $i$ 与 $j$ 同为常返状态或非常返状态. 若为常返状态, 则它们同为正常返状态或同为零常返状态
+ $i$ 与 $j$ 或有相同的周期, 或同为非周期

## 3.4 状态空间的分解

**定义 闭集**

设 $C\subset S$, 若对 $\forall~i\in C,~j\notin C$, 有
$$
  p_{ij}=0
$$
则称 $C$ 为**闭集**, 即**闭集之内不可能走出去**. 若闭集 $C$ 的**状态相通**, 则称 $C$ 为**不可约**的.

**引理 闭集的充要条件**

$C$ 是**闭集**的充要条件为: 对 $\forall~i\in C,~j\notin C$, $n\geqslant1$, 有
$$
  p_{ij}^{(n)}=0.
$$

**注释**

+ 吸收态为单点集构成一个闭集
+ 整个状态空间也构成一个闭集
+ 所有常返状态构成闭集, 由常返可达必常返易得
+ 不可约马尔可夫链或者没有非常返状态或者没有常返状态

**定理 常返闭集分解定理**

设所有常返状态构成的闭集 $C\neq\varnothing$, 则它可以分解为若干个互不相交的闭集 $\{C_n\}$, 使得
$$
  C=C_1\cup C_2\cup\cdots
$$

且 $\{C_n\}$ 均为**互不相通不可约闭集**.

**推论 状态空间分解定理**

状态空间 $S$ 可分解为
$$
  S=T\cup C=T\cup C_1\cup C_2\cup\cdots
$$

其中 $\{C_n\}$ 为基本常返闭集, 非常返状态构成的集合 $T$ 不一定是闭集.

**注释 有限状态空间情形**

+ 若状态空间有限, 则非常返状态构成的集合 $T$ 一定不是闭集
+ **有限不可约**马尔可夫链的状态都是**常返状态**

**引理 闭集生成的转移矩阵**

设 $C_h\subset S$ 为闭集, 只考虑 $C_h$ 上所得的 $m$ 步子转移矩阵
$$
  \pmb{P}^{(m)}=\Big[p_{ij}^{(m)}\Big],\quad i,j\in C_h
$$

则它们也是**转移矩阵**.

## 3.5 转移矩阵的极限性态

### 转移矩阵的极限性态

**定理 非常返或零常返的极限性态**

若 $j$ 为非常返或零常返状态, 则对 $\forall~i\in S$, 有
$$
  \lim_{n\to\infty}p_{ij}^{(n)}=0
$$

**推论**

+ **有限**马尔可夫链**没有零常返**状态
+ **不可约**的**有限**马尔可夫链的状态都是**正常返**状态
+ 若马东可夫链有一零常返状态, 则必有无限多个零常返状态

**定理 正常返的极限性态**

若 $j$ 为正常返状态, 则对 $\forall~i\in S$ 及 $0\leqslant r\leqslant d-1$, 有
$$
  \begin{aligned}
    \lim_{n\to\infty}p_{ij}^{(nd+r)}&=f_{ij}(r)\frac{d}{\mu_j}\\
    f_{ij}(r)&=\sum_{m=0}^\infty f_{ij}^{(md+r)}
  \end{aligned}
$$

**推论**

+ 若 $j$ 为遍历状态, 则对 $\forall~i\in S$, 有
$$
  \lim_{n\to\infty}p_{ij}^{(n)}=\frac{f_{ij}}{\mu_j}
$$

+ 不可约遍历链对 $\forall~i,j\in S$, 有
$$
  \lim_{n\to\infty}p_{ij}^{(n)}=\frac{1}{\mu_j}
$$

+ 若 $j$ 为常返状态, 则对 $\forall~i\in S$, 有
$$
  \lim_{n\to\infty}\frac{1}{n}\sum_{l=1}^np_{ij}^{(l)}=\frac{f_{ij}}{\mu_j}.
$$

+ 不可约常返链对 $\forall~i,j\in S$, 有
$$
  \lim_{n\to\infty}\frac{1}{n}\sum_{l=1}^np_{ij}^{(l)}=\frac{1}{\mu_j}.
$$

**定理**

对**不可约遍历链**, $\Big\{\pi_i=\dfrac{1}{\mu_i}\Big\}$ 是方程组
$$
  x_j=\sum_{i\in S}x_ip_{ij}
$$

满足条件 $x_j\geqslant0,~j\in S,~\sum_{j\in S}x_j=1$ 的唯一解.

### 平稳分布

**定义 平稳分布**

一个定义在 $S$ 上的概率分布
$$
  \pmb{\pi}=\{\pi_1,\pi_2,\cdots\}
$$
称为**马尔可夫链的平稳分布**, 若
$$
  \pmb{\pi}=\pmb{\pi}\pmb{P}
$$

即 $\forall~j\in S$, 有
$$
  \pi_j=\sum_{i\in S}\pi_ip_{ij}
$$

**定理 平稳过程的充要条件**

设 $\{X_n:n\geqslant0\}$ 是马尔可夫链, 则其是平稳过程的充要条件是
$$
  \pmb{\pi}(0)=(\pi_i(0),~i\in S)
$$

是平稳分布, 即
$$
  \pmb{\pi}(0)=\pmb{\pi}(0)\pmb{P}
$$

**定理 不可约遍历链平稳分布**

**不可约遍历链**恒有唯一的平稳分布
$$
  \Big\{\pi_i=\dfrac{1}{\mu_i}\Big\}
$$
且
$$
  \pi_j=\lim_{n\to\infty}p_{ij}^{(n)}
$$

**定理 平稳分布存在定理**

令 $C^+$ 为马尔可夫链中全体正常返状态构成的集合, 则有

+ 平稳分布**不存在**的充要条件为 $C^+=\varnothing$
+ 平稳分布**唯一存在**的充要条件为**只有一个基本正常返闭集** $C_a=C^+$
+ **有限**状态马尔可夫链的平稳分布**总存在**
+ **有限不可约非周期**马尔可夫链**存在唯一**的平稳分布

### 极限分布

**定义 极限分布**

若马尔可夫链概率分布的极限
$$
  \lim_{n\to\infty}\pi_j(n)=\pi_j^*,\quad j\in S
$$

存在, 则称
$$
  \pmb{\pi}^*=\{\pi_1^*,\pi_2^*,\cdots\}
$$

为马尔可夫链的**极限分布**.

**定理**

**非周期不可约链**是**正常返**的充要条件是它存在**平稳分布**, 且此时**平稳分布就是极限分布**.

**例题 转移概率、平稳分布与极限分布**

设 $X$ 为时齐 Markov 链, 状态空间
$$
  S=\{1,2,3,4\}
$$
初始分布
$$
  \pmb{\pi}(0)=\left(\frac{1}{2},\frac{1}{2},0,0\right)
$$
且转移概率矩阵为
$$
  \pmb{P}=\begin{bmatrix}
    1/3 & 1/3 & 1/3 & 0\\
    0 & 0 &1/2 & 1/2\\
    1/2 & 1/2 & 0 & 0\\
    0 & 1/3 & 1/3 & 1/3\\
  \end{bmatrix}
$$

+ 求 $P(X_1=3,X_2=2,X_3=4)$
+ 函数 $f$ 自变量取值于 $S$, $f(1)=2.8$, $f(2)=2.1$, $f(3)=0.7$, $f(4)=4.2$, 求极限
$$
  \lim_{n\to\infty}\frac{1}{n}\sum_{i=0}^{n-1}f(X_i)
$$

**解**: 易知
$$
  \pmb{\pi}(1)=\pmb{\pi}(0)\pmb{P}=\left(\frac{1}{6},\frac{1}{6},\frac{5}{12},\frac{1}{4}\right)
$$
由条件概率计算公式可得
$$
  \begin{aligned}
    &P(X_1=3,X_2=2,X_3=4)\\
    =&P(X_1=3)P(X_2=2,X_3=4|X_1=3)\\
    =&P(X_1=3)P(X_2=2|X_1=3)P(X_3=4|X_1=3,X_2=2)\\
    =&P(X_1=3)P(X_2=2|X_1=3)P(X_3=4|X_2=2)\\
    =&\pi_3(1)\cdot p_{32}\cdot p_{24}\\
    =&\frac{5}{12}\times\frac{1}{2}\times\frac{1}{2}\\
    =&\frac{5}{48}\\
  \end{aligned}
$$

下面求极限分布暨平稳分布, 由 $\pmb{\pi}=\pmb{\pi}\pmb{P}$ 可得
$$
  (\pi_1,\pi_2,\pi_3,\pi_4)
  =(\pi_1,\pi_2,\pi_3,\pi_4)
  \begin{bmatrix}
    1/3 & 1/3 & 1/3 & 0   \\
    0   & 0   & 1/2 & 1/2 \\
    1/2 & 1/2 & 0   & 0   \\
    0   & 1/3 & 1/3 & 1/3 \\
  \end{bmatrix}
$$

又
$$
  \sum_{i=1}^4\pi_i=1
$$

则**打眼一瞪**可求得
$$
  \pmb{\pi}=\left(\frac{3}{14},\frac{4}{14},\frac{4}{14},\frac{3}{14}\right)
$$

> **打眼一瞪**：先求平稳分布的四个分子, 观察转移矩阵第一行与第四行分母均为3, 基于取整的思想可猜测平稳分布的第一个分子与第四个分子均为3, 而后由矩阵第一列的乘法 3=3/3+?/2 可推知平稳分布的第二个分子与第三个分子均为4, 则四个分子均已求得, 最后平稳分布的分母为四个分子之和: 3+4+4+3=14. **一言以蔽之, 转移矩阵的分母可猜测为平稳分布的分子.**

故
$$
  \begin{aligned}
    \lim_{n\to\infty}\frac{1}{n}\sum_{i=0}^{n-1}f(X_i)
    &=\lim_{i\to\infty}E[f(X_i)]\\
    &=\sum_{i=1}^4f(i)\pi_i\\
    &=2.8\times\frac{3}{14}+2.1\times\frac{4}{14}+0.7\times\frac{4}{14}+4.2\times\frac{3}{14}\\
    &=7\times\frac{3}{14}+2.8\times\frac{4}{14}\\
    &=1.5+0.8\\
    &=2.3\\
  \end{aligned}
$$

**例题 平稳分布与极限分布**

设 $X$ 为时齐 Markov 链, 其一步转移概率为
$$
  \pmb{P}=
  \begin{bmatrix}
    1/4 & 1/4 & 1/4 & 1/4 \\
    1/3 &  0  & 1/3 & 1/3 \\
    1/3 & 1/3 &  0  & 1/3 \\
    1/4 & 1/4 & 1/4 & 1/4 \\
  \end{bmatrix}
$$

+ 求不变分布 $\pmb{\pi}=(\pi_1,\pi_2,\pi_3,\pi_4)$
+ 设
$$
  P(X_0=1)=\frac{1}{3},P(X_0=2)=\frac{1}{3},P(X_0=3)=\frac{1}{3},P(X_0=4)=0
$$

求
$$
  \lim_{n\to\infty}P(X_n=i),~i=1,2,3,4
$$

**解**:

由 $\pmb{\pi}=\pmb{\pi}\pmb{P}$ 可得
$$
  (\pi_1,\pi_2,\pi_3,\pi_4)
  =(\pi_1,\pi_2,\pi_3,\pi_4)
  \begin{bmatrix}
    1/4 & 1/4 & 1/4 & 1/4 \\
    1/3 &  0  & 1/3 & 1/3 \\
    1/3 & 1/3 &  0  & 1/3 \\
    1/4 & 1/4 & 1/4 & 1/4 \\
  \end{bmatrix}
$$

又
$$
  \sum_{i=1}^4\pi_i=1
$$

则**打眼一瞪**可求得
$$
  \pmb{\pi}=\left(\frac{4}{14},\frac{3}{14},\frac{3}{14},\frac{4}{14}\right)
$$

故有
$$
  \lim_{n\to\infty}\pmb{P}^n=
  \begin{bmatrix}
    \pmb{\pi}\\\pmb{\pi}\\\pmb{\pi}\\\pmb{\pi}
  \end{bmatrix}
$$

又由题给条件有
$$
  \pmb{\pi}(0)=\left(\frac{1}{3},\frac{1}{3},\frac{1}{3},0\right)
$$

则
$$
  \begin{aligned}
    \lim_{n\to\infty}\pmb{\pi}(n)
    &=\lim_{n\to\infty}\pmb{\pi}(0)\pmb{P}^n\\
    &=\left(\frac{1}{3},\frac{1}{3},\frac{1}{3},0\right)
    \begin{bmatrix}
      4/14 & 3/14 & 3/14 & 4/14 \\
      4/14 & 3/14 & 3/14 & 4/14 \\
      4/14 & 3/14 & 3/14 & 4/14 \\
      4/14 & 3/14 & 3/14 & 4/14 \\
    \end{bmatrix}\\
    &=\left(\frac{4}{14},\frac{3}{14},\frac{3}{14},\frac{4}{14}\right)
  \end{aligned}
$$

故
$$
  \lim_{n\to\infty}P(X_n=i)=\pi_i,\quad i=1,2,3,4
$$

> 事实上, 此链是有限不可约非周期的, 其极限分布与平稳分布相同, 此处可以直接写出结果.

**例题 首达概率与正常返**

取值非负整数的 Markov 链 $X$, 其一步转移概率为
$$
  p_{n,n+1}=p\in(0,1),\quad p_{n,0}=1-p,\quad n=0,1,2,\cdots
$$
其他元素为 $0$, 设
$$
  T_0=\inf\{n>0:X_n=0\}
$$

+ 求 $P(T_0=n|X_0=0)$
+ 该马氏链是否为正常返链, 说明理由

**解**: 由**转移图**可知

$$
  P(T_0=n|X_0=0)=f_{00}^{(n)}=p^{n-1}(1-p)
$$

则 $T_0|_{X_0=0}$ 服从**几何分布**, 即
$$
  T_0|_{X_0=0}\sim G(1-p)
$$

由几何分布的相关公式可得
$$
 f_{00}=\sum_{n=1}^\infty f_{00}^{(n)}=\sum_{n=1}^\infty p^{n-1}(1-p)=1
$$

且
$$
  \mu_0=\sum_{n=1}^\infty nf_{00}^{(n)}=\sum_{n=1}^\infty np^{n-1}(1-p)=\frac{1}{1-p}<\infty
$$

则 $0$ 状态正常返, 又此马氏链是**不可约**的, 故整个马氏链正常返.

## 参考文献

+ 林元烈. 应用随机过程[M]. 北京: 清华大学出版社, 2002.
+ 何声武. 随机过程导论[M]. 北京: 高等教育出版社, 1999.
+ Ross S M. Stochastic Processes[M]. John Wiley and Sons, 1993.
