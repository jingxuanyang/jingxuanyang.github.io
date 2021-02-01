---
layout: post
title:  "应用随机过程|第4章 离散鞅引论"
date:   2021-01-28
categories: applied-stochastic-process
tags: applied-stochastic-process stochastic-process Martingale
author: Jingxuan Yang
mathjax: true
---

* content
{:toc}

## 4.1 定义与例子

**定义 关于自己是鞅**

随机过程 $\{X_n:n\geqslant0\}$ 是**鞅**, 若 $\forall~n\geqslant0$, 有
+ $E|X_n|<\infty$
+ $E(X_{n+1}|X_0,X_1,\cdots,X_n)=X_n$





**定义 关于另一个过程是鞅**

设有两个过程, $\{X_n:n\geqslant0\}$ 和 $\{Y_n:n\geqslant0\}$, 称 $\{X_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是**鞅**, 若
+ $E|X_n|<\infty$
+ $E(X_{n+1}|Y_0,Y_1,\cdots,Y_n)=X_n$

由全期望公式易知鞅在任何时刻的期望均相等,
$$
  \begin{aligned}
    EX_{n+1}
      &=E[E(X_{n+1}|Y_0,Y_1,\cdots,Y_n)]\\
      &=EX_n=EX_0\\
  \end{aligned}
$$

**例题 似然比构成的鞅**

设 $Y_0,Y_1,\cdots,Y_n,\cdots$ 是独立同分布随机变量序列, $f_0$ 和 $f_1$ 是概率密度函数, 令
$$
  X_n=\frac{f_1(Y_0)f_1(Y_1)\cdots f_1(Y_n)}{f_0(Y_0)f_0(Y_1)\cdots f_0(Y_n)},~ n\geqslant0
$$

假设 $\forall y\in\mathbb{R}$, $f_0(y)>0$, 且 $Y_n$ 的概率密度函数为 $f_0$, 则 $\{X_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是鞅.

**证明**: 首先计算单个比值的期望, $\forall~i=0,1,\cdots$, 有
$$
  E\left[\frac{f_1(Y_{i})}{f_0(Y_{i})}\right]=\int_{-\infty}^\infty\frac{f_1(y)}{f_0(y)}f_0(y)\mathrm{d}y=1
$$

则同理由**独立同分布**可证连乘的绝对值期望有限
$$
  \begin{aligned}
    E|X_n|
    &=E\left[\frac{f_1(Y_0)f_1(Y_1)\cdots f_1(Y_n)}{f_0(Y_0)f_0(Y_1)\cdots f_0(Y_n)}\right]\\
    &=\prod_{i=0}^nE\left[\frac{f_1(Y_{i})}{f_0(Y_{i})}\right]\\
    &=1<\infty
  \end{aligned}
$$

其次有
$$
  \begin{aligned}
    E(X_{n+1}|Y_0,Y_1,\cdots,Y_n)
    &=E\left[X_n\frac{f_1(Y_{n+1})}{f_0(Y_{n+1})}|Y_0,Y_1,\cdots,Y_n\right]\\
    &=X_nE\left[\frac{f_1(Y_{n+1})}{f_0(Y_{n+1})}\right]\\
    &=X_n\\
  \end{aligned}
$$

因此 $\{X_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是鞅.

**例题 Doob 鞅过程**

设 $Y_0,Y_1,\cdots,Y_n,\cdots$ 是任一随机变量序列, 有随机变量 $X$ 满足 $E|X|<\infty$, 令
$$
  X_n=E(X|Y_0,Y_1,\cdots,Y_n)
$$

$\{X_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是鞅, 并称之为 **Doob 过程**.

**证明**: 易知
$$
  \begin{aligned}
    E|X_n|
    &=E|E(X\big|Y_0,Y_1,\cdots,Y_n)|\\
    &\leqslant E[E(|X|\big|Y_0,Y_1,\cdots,Y_n)]\\
    &=E|X|<\infty
  \end{aligned}
$$

又由**多元随机变量的全期望公式**可得
$$
  \begin{aligned}
     &E(X_{n+1}|Y_0,Y_1,\cdots,Y_n)\\
    =&E[E(X|Y_0,Y_1,\cdots,Y_{n+1})|Y_0,Y_1,\cdots,Y_n]\\
    =&E(X|Y_0,Y_1,\cdots,Y_n)\\
    =&X_n\\
  \end{aligned}
$$

因此 $\{X_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是鞅.

## 4.2 上下鞅及分解定理

**定义 上鞅**

设 $\{X_n:n\geqslant0\}$ 与 $\{Y_n:n\geqslant0\}$ 是随机过程, 称 $\{X_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是**上鞅**, 若
+ $E|X_n|<\infty$
+ $E(X_{n+1}|Y_0,Y_1,\cdots,Y_n)\leqslant X_n$
+ $X_n$ 是 $Y_0,Y_1,\cdots,Y_n$ 的函数

**定义 下鞅**

设 $\{X_n:n\geqslant0\}$ 与 $\{Y_n:n\geqslant0\}$ 是随机过程, 称 $\{X_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是**下鞅**, 若
+ $E|X_n|<\infty$
+ $E(X_{n+1}|Y_0,Y_1,\cdots,Y_n)\geqslant X_n$
+ $X_n$ 是 $Y_0,Y_1,\cdots,Y_n$ 的函数

**定理 期望 Jensen 不等式**

设 $\phi(x)$ 为凸函数, 则由 Jensen 不等式可知

$$
  E(\phi(X))\geqslant\phi(EX)
$$

**引理 凸函数构造下鞅**

若 $\{X_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是鞅, $\phi(x)$ 为**凸函数**且 $\forall~n\geqslant0$, $E|\phi(X_n)|<\infty$, 则 $\{\phi(X_n):n\geqslant0\}$ 是关于 $\{Y_n:n\geqslant0\}$ 的**下鞅**.

**推论**

若 $\{X_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是鞅, 且 $\forall~n\geqslant0$, $E|X_n|^2<\infty$, 则 $\{|X_n|:n\geqslant0\}$ 与 $\{X_n^2:n\geqslant0\}$ 是关于 $\{Y_n:n\geqslant0\}$ 的**下鞅**.

**上下鞅的基本性质**

+ 若 $\{X_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是上鞅, 则
$$
  E(X_{n+k}|Y_0,Y_1,\cdots,Y_n)\leqslant X_n,~\forall~k\geqslant0
$$
+ 若 $\{X_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是上鞅, 则
$$
  EX_n\leqslant EX_k\leqslant EX_0,~\forall~0\leqslant k\leqslant n
$$
+ 若 $\{X_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是上鞅, $g$ 是关于 $Y_0,Y_1,\cdots,Y_n$ 的非负函数, 则
$$
  E[g(Y_0,Y_1,\cdots,Y_n)X_{n+k}|Y_0,Y_1,\cdots,Y_n]\leqslant g(Y_0,Y_1,\cdots,Y_n)X_n,~\forall~k\geqslant0
$$

**定理 鞅分解定理**

若 $\{X_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是下鞅, 则必存在过程 $\{M_n:n\geqslant0\}$ 与 $\{Z_n:n\geqslant0\}$, 使得
+ $\{M_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是鞅
+ $Z_n$ 是 $Y_0,Y_1,\cdots,Y_{n-1}$ 的函数, 且 $Z_0=0$, $Z_n\leqslant Z_{n+1}$, $EZ_n<\infty$,$\forall~n\geqslant1$
+ $X_n=M_n+Z_n,~\forall~n\geqslant0$

由本定理可知, 一个下鞅总可分解为一个鞅与一增过程之和.

## 4.3 停时与停时定理

**定义 停时**

设取值为非负整数的随机变量 $T$ 及随机序列 $\{Y_n:n\geqslant0\}$,
$$
  \mathcal{F}_n=\sigma(Y_0,Y_1,\cdots,Y_n)
$$
若对 $\forall~n\geqslant0$, 有
$$
  \{\omega:T(\omega)=n\}\in\mathcal{F}_n
$$
则称 $T$ 是关于 $\{Y_n:n\geqslant0\}$ 的**停时**.

**注释 停时**

设取值为非负整数的随机变量 $T$ 及随机序列 $\{Y_n:n\geqslant0\}$, 若对 $\forall~n\geqslant0$, 事件 $\{\omega:T(\omega)=n\}$ 的示性函数 $\pmb{1}_{\{T(\omega)=n\}}(\omega)$ **仅是** $Y_0,Y_1,\cdots,Y_n$ 的函数, 则称 $T$ 是关于 $\{Y_n:n\geqslant0\}$ 的**停时**.

定义中要求的事件是 $\{T=n\}$, 实际上也可以用 $\{T\leqslant n\}$, $\{T< n\}$, $\{T\geqslant n\}$, $\{T>n\}$ 代替.

$\pmb{1}_{\{T(\omega)=n\}}(\omega)$ **仅是** $Y_0,Y_1,\cdots,Y_n$ 的函数则在**计算条件期望**的时候可以直接提出.

**停时性质**

+ $T=k,~k\in\mathbb{N}$ 是停时, 即常数是停时
+ 设 $T_1,T_2$ 是关于 $\{Y_n:n\geqslant0\}$ 的两个停时, 则
  $$
    T_1+T_2,~T_1\wedge T_2,~T_1\vee T_2
  $$
  均是停时

**引理 降序号**

设 $\{X_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是鞅, $T$ 是关于 $\{Y_n:n\geqslant0\}$ 的停时, 则 $\forall~n\geqslant k$, 有
$$
  E(X_n\pmb{1}_{\{T=k\}})=E(X_k\pmb{1}_{\{T=k\}})
$$

**引理 取小停时的期望**

设 $\{X_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是鞅, $T$ 是关于 $\{Y_n:n\geqslant0\}$ 的停时, 则 $\forall~n\geqslant 1$, 有
$$
  EX_0=EX_{T\wedge n}=EX_n
$$

**引理**

设 $X$ 是随机变量满足 $E|X|<\infty$, $T$ 是关于 $\{Y_n:n\geqslant0\}$ 的停时, 且 $P(Y<\infty)=1$, 则
$$
  \begin{aligned}
    \lim_{n\to\infty}E(X\pmb{1}_{\{T>n\}})&=0\\
    \lim_{n\to\infty}E(X\pmb{1}_{\{T\leqslant n\}})&=1\\
  \end{aligned}
$$

**定理 停时定理**

设 $\{X_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是鞅, $T$ 是关于 $\{Y_n:n\geqslant0\}$ 的停时,
$$
  P(T<\infty)=1
$$
且
$$
  E\left(\sup_{n\geqslant0}|X_{T\wedge n}|\right)<\infty
$$

则
$$
  EX_T=EX_0
$$

**推论 停时定理**

设 $\{X_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是鞅, $T$ 是关于 $\{Y_n:n\geqslant0\}$ 的停时, 若 $ET<\infty$, 且存在常数 $b<\infty$ 满足对 $\forall~n< T$, 有
$$
  E(|X_{n+1}-X_n|\big|Y_0,Y_1,\cdots,Y_n)\leqslant b
$$

则
$$
  EX_T=EX_0
$$

**定理 停时定理**

设 $\{X_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是鞅, $T$ 是关于 $\{Y_n:n\geqslant0\}$ 的停时, 若
+ $P(T<\infty)=1$
+ $E|X_T|<\infty$
+ $\lim_{n\to\infty}E|X_n\pmb{1}_{\{T>n\}}|=0$

则
$$
  EX_T=EX_0
$$

**推论 停时定理**

设 $\{X_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是鞅, $T$ 是关于 $\{Y_n:n\geqslant0\}$ 的停时, 若
+ $P(T<\infty)=1$
+ 对某个 $k<\infty$, $\forall~n\geqslant0$,
  $$
    E(X_{T\wedge n}^2)\leqslant k
  $$
则
$$
  EX_T=EX_0
$$

**推论 停时定理**

设 $Y_0=0$, $\{Y_k:k\geqslant1\}$ 独立同分布, $EY_k=\mu$, $DY_k=\sigma^2<\infty$, 令
$$
  S_0=0,~S_n=\sum_{k=1}^nY_k,~X_n=S_n-n\mu
$$
若 $T$ 为停时, $ET<\infty$, 则 $E|X_T|<\infty$, 且
$$
  EX_T=ES_T-\mu ET=0
$$

## 4.4 鞅收敛定理

**引理 上穿不等式**

设 $\{X_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是下鞅, $V^{(n)}(a,b)$ 表示
$$
  \{X_k:0\leqslant k< n\}
$$
上穿区间 $(a,b)$ 的次数, $a< b$, 则
$$
  E[V^{(n)}(a,b)]\leqslant\frac{E(X_n-a)^+-E(X_0-a)^+}{b-a}\leqslant\frac{EX_n^++|a|}{b-a}
$$

这里记
$$
  a^+=\max\{a,0\}=a\vee0
$$

**定理 鞅收敛定理**

设 $\{X_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是**下鞅**,
$$
  \sup_nE|X_n|<\infty
$$

则存在随机变量 $X_\infty$, 使得
$$
  P\left(\lim_{n\to\infty}X_n=X_\infty\right)=1
$$

且 $E|X_\infty|<\infty$.

**证明**: 由于
$$
  EX_n^+\leqslant E|X_n|\leqslant 2EX_n^+-EX_n
$$

故
$$
  \sup_nE|X_n|<\infty\Leftrightarrow\sup_nEX_n^+<\infty
$$

当 $n\to\infty$ 时,
$$
  V^{(n)}(a,b)\to V(a,b)
$$
即 $X_n$ 上穿 $(a,b)$ 的次数, 故
$$
  \begin{aligned}
    E[V(a,b)]
      &=E\left[\lim_{n\to\infty}V^{(n)}(a,b)\right]\\
      &=\lim_{n\to\infty}E\left[V^{(n)}(a,b)\right]\\
      &\leqslant \lim_{n\to\infty}\frac{EX_n^++|a|}{b-a}\\
      &\leqslant\frac{\sup_{n}EX_n^++|a|}{b-a}\\
      &<\infty\\
  \end{aligned}
$$

因此
$$
  P(V(a,b)<\infty)=1
$$

即当 $n\to\infty$ 时, $X_n(\omega)$ 以概率 $1$ 存在极限, 设
$$
  \lim_{n\to\infty}X_n=X_\infty
$$

则
$$
  P\left(\lim_{n\to\infty}X_n=X_\infty\right)=1
$$

另外, 由 **Fatou 引理**
$$
  \begin{aligned}
    E|X_\infty|
      &=E\left(\lim_{n\to\infty}|X_n|\right)\\
      &\leqslant\lim_{n\to\infty}E|X_n|\\
      &\leqslant\sup_nE|X_n|\\
      &<\infty\\
  \end{aligned}
$$

即
$$
  E|X_\infty|<\infty
$$

**定理 Chebyshev 不等式与 Kolmogorov 不等式**

设 $\{Y_k:k\geqslant0\}$ 独立同分布, $EY_k=0$, $EY_k^2=\sigma^2<\infty$, 令
$$
  X_0=0,~X_n=\sum_{k=1}^nY_k
$$
则由 Chebyshev 不等式有
$$
  \varepsilon^2P(|X_n|>\varepsilon)\leqslant n\sigma^2
$$

由 Kolmogorov 不等式有
$$
  \varepsilon^2P\left(\max_{0\leqslant k\leqslant n}|X_k|>\varepsilon\right)\leqslant n\sigma^2
$$

由
$$
  \begin{aligned}
    EX_n^2
      &=E\left(\sum_{k=1}^nY_k\right)^2\\
      &=\sum_{k=1}^nEY_k^2\\
      &=n\sigma^2\\
  \end{aligned}
$$

可知
$$
  \begin{aligned}
    \varepsilon^2P\left(\max_{0\leqslant k\leqslant n}|X_k|>\varepsilon\right)
    &=\varepsilon^2P\left(\max_{0\leqslant k\leqslant n}X_k^2>\varepsilon^2\right)\\
    &\leqslant EX_n^2\\
  \end{aligned}
$$

**定理 最大值不等式**

设 $\{X_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是**下鞅**, 且 $\forall~n\geqslant0$ 有 $X_n\geqslant0$, 则对 $\forall~\lambda>0$ 有
$$
  \lambda P\left(\max_{0\leqslant k\leqslant n}X_k>\lambda\right)\leqslant EX_n
$$

**推论**

设 $\{X_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是**鞅**, 则对 $\forall~\lambda>0$ 有
$$
  \lambda P\left(\max_{0\leqslant k\leqslant n}|X_k|>\lambda\right)\leqslant E|X_n|
$$

**证明**: 易知 $\forall~n\geqslant0$ 有 $|X_n|\geqslant0$ 且是下鞅, 则由最大值不等式立即可得.

**定理**

设 $\{X_n:n\geqslant0\}$ 关于 $\{Y_n:n\geqslant0\}$ 是**鞅**, 且存在常数 $k$ 使得 $\forall~n\geqslant0$ 有
$$
  EX_n^2\leqslant k<\infty
$$
则存在有限随机变量 $X_\infty$, 使得 $\{X_n:n\geqslant0\}$ 不仅**依概率收敛**
$$
  P\left(\lim_{n\to\infty}X_n=X_\infty\right)=1
$$

而且**均方收敛**
$$
  \lim_{n\to\infty}E|X_n-X_\infty|^2=0
$$

**例题 最大值不等式**

设 $\forall~n\geqslant1$, $EX_n^2\leqslant k<\infty$. 令
$$
  S_n=\sum_{k=1}^nX_k
$$
已知 $\{S_n:n\geqslant1\}$ 是鞅, 证明 $\forall~\varepsilon>0$, 有
$$
  \lim_{n\to\infty}P\left(\left|\frac{S_n}{n}\right|>\varepsilon\right)=0
$$

**证明**: 易知 $X_i=S_i-S_{i-1}$, 则对 $\forall~i< j$ 由**全期望公式**, **条件期望平滑性**以及**鞅的降序性**有
$$
  \begin{aligned}
    E(X_iX_j)
      &=E[(S_i-S_{i-1})(S_j-S_{j-1})]\\
      &=E(S_iS_j-S_{i-1}S_j-S_iS_{j-1}+S_{i-1}S_{j-1})\\
      &=E[E(S_iS_j-S_{i-1}S_j-S_iS_{j-1}+S_{i-1}S_{j-1}|S_1,S_2,\cdots,S_i)]\\
      &=E(S_i^2-S_{i-1}S_i-S_i^2+S_{i-1}S_i)\\
      &=0\\
  \end{aligned}
$$

故由题给不等式有
$$
  \begin{aligned}
    ES_n^2
      &=E\left(\sum_{k=1}^nX_k\right)^2\\
      &=\sum_{k=1}^nEX_k^2+2\sum_{i< j}E(X_iX_j)\\
      &\leqslant nk\\
  \end{aligned}
$$

则由最大值不等式可得
$$
  \begin{aligned}
    P\left(\left|\frac{S_n}{n}\right|>\varepsilon\right)
      &=P(|S_n|>n\varepsilon)\\
      &=P\left(S_n^2>n^2\varepsilon^2\right)\\
      &\leqslant\frac{ES_n^2}{n^2\varepsilon^2}\\
      &\leqslant\frac{nk}{n^2\varepsilon^2}\\
      &=\frac{k}{n\varepsilon^2}\\
  \end{aligned}
$$

所以
$$
  \lim_{n\to\infty}P\left(\left|\frac{S_n}{n}\right|>\varepsilon\right)\leqslant\lim_{n\to\infty}\frac{k}{n\varepsilon^2}=0
$$

故
$$
  \lim_{n\to\infty}P\left(\left|\frac{S_n}{n}\right|>\varepsilon\right)=0
$$

**例题 最大值不等式**

设 $\{X_n:n\geqslant0\}$ 是鞅, 且对某一 $\alpha>1$, $E|X_n|^\alpha<\infty,~\forall~n\geqslant0$. 证明
$$
  E\left(\max_{0\leqslant k\leqslant n}|X_k|\right)\leqslant\frac{\alpha}{\alpha-1}(E|X_n|^\alpha)^{1/\alpha}
$$

**证明**: 易知 $|X_n|^\alpha$ 是下鞅, 则由非负随机变量的期望计算方法, 概率值恒小于等于 $1$ 以及最大值不等式有
$$
  \begin{aligned}
    E\left(\max_{0\leqslant k\leqslant n}|X_k|\right)
      &=\int_0^\infty P\left(\max_{0\leqslant k\leqslant n}|X_k|>t\right)\mathrm{d}t\\
      &=\int_0^\infty P\left(\max_{0\leqslant k\leqslant n}|X_k|^\alpha>t^\alpha\right)\mathrm{d}t\\
      &\leqslant\int_0^{(E|X_n|^\alpha)^{1/\alpha}}1\mathrm{d}t+\int_{(E|X_n|^\alpha)^{1/\alpha}}^\infty P\left(\max_{0\leqslant k\leqslant n}|X_k|^\alpha>t^\alpha\right)\mathrm{d}t\\
      &\leqslant(E|X_n|^\alpha)^{1/\alpha}+\int_{(E|X_n|^\alpha)^{1/\alpha}}^\infty\frac{E|X_n|^\alpha}{t^\alpha}\mathrm{d}t\\
      &=(E|X_n|^\alpha)^{1/\alpha}+\frac{1}{-\alpha+1}E|X_n|^\alpha t^{-\alpha+1}\Big|_{(E|X_n|^\alpha)^{1/\alpha}}^\infty\\
      &=(E|X_n|^\alpha)^{1/\alpha}+\frac{1}{\alpha-1}(E|X_n|^\alpha)^{1/\alpha}\\
      &=\frac{\alpha}{\alpha-1}(E|X_n|^\alpha)^{1/\alpha}
  \end{aligned}
$$

## 4.5 连续参数鞅

**定义 鞅**

随机过程 $\{X_t:t\geqslant0\}$ 是**鞅**, 若
+ $\forall~t\geqslant0$, 有 $E|X_t|<\infty$
+ $\forall~0\leqslant  t_1<\cdots< t_n< t_{n+1}$, 有
$$
  E(X_{t_{n+1}}|X_{t_1},X_{t_2},\cdots,X_{t_n})=X_{t_n}
$$

**定义 停时**

对随机过程 $X=\{X_t:t\geqslant0\}$, 若取值于 $[0,\infty]$ 上的随机变量 $T$ 满足 $\forall~t\geqslant0$, $\{T\leqslant t\}$ 由
$$
  \{X_s:0\leqslant s\leqslant t\}
$$
决定, 则称 $T$ 关于 $X$ 是**停时**.

**定理 停时定理**

设 $\{X_t:t\geqslant0\}$ 是鞅, $T$ 是停时, 若
$$
  P(T<\infty)=1
$$
且
$$
  E\left(\sup_{t\geqslant0}|X_{T\wedge t}|\right)<\infty
$$

则
$$
  EX_T=EX_0
$$

## 参考文献

+ 林元烈. 应用随机过程[M]. 北京: 清华大学出版社, 2002.
+ 何声武. 随机过程导论[M]. 北京: 高等教育出版社, 1999.
+ Ross S M. Stochastic Processes[M]. John Wiley and Sons, 1993.
