---
layout: post
title:  "应用随机过程|第2章 泊松过程"
date:   2021-01-26
categories: applied-stochastic-process
tags: applied-stochastic-process stochastic-process Poisson-process
author: Jingxuan Yang
---

* content
{:toc}

## 2.1 定义及其背景

**定义 时齐泊松过程**

随机过程 $\{N_t:t\geqslant0\}$ 称为时齐泊松过程, 若满足
+ **计数过程**, 且初值为 $0$
  $$
    N_0=0
  $$





+ **独立增量过程**, 即
  $$
    \forall~0 < t_1 < t_2 < \cdots < t_n
  $$
  有
  $$
    N_{t_1},N_{t_2}-N_{t_1},\cdots,N_{t_n}-N_{t_{n-1}}
  $$
  相互独立

+ **增量平稳性**, 即 $\forall~s,t\geqslant0,~n\geqslant0$,
  $$
    P(N_{s+t}-N_s=n)=P(N_t=n)
  $$

+ **增 $1$ 同 $\lambda$ 阶**
  $$
    \begin{aligned}
      P(N_{t+\Delta t}-N_t=1)&=\lambda\Delta t+o(\Delta t)\\
      P(N_{t+\Delta t}-N_t=2)&=o(\Delta t)\\
    \end{aligned}
  $$

**定理 泊松过程的分布**

若 $\{N_t:t\geqslant0\}$ 为泊松过程, 则 $\forall~s,t\geqslant0$, 有
$$
  \begin{aligned}
    P(N_{s+t}-N_s=k)
      &=P(N_t=k)\\
      &=\frac{(\lambda t)^k}{k!}\mathrm{e}^{-\lambda t}
  \end{aligned}
$$

即
$$
  N_{s+t}-N_s\overset{d}{=}N_t\sim P(\lambda t)
$$

**定义 泊松过程**

**计数过程** $\{N_t:t\geqslant0\}$ 称为参数是 $\lambda$ 的泊松过程, 若满足
+ **初值为 $0$**
$$
  N_0=0
$$

+ **独立增量过程**
+ **增量**是参数为 $\lambda t$ 的**泊松分布**, 即 $\forall~s,t\geqslant0$,
$$
  N_{s+t}-N_s\sim P(\lambda t)
$$

## 2.2 相邻事件的时间间隔

设 $\{N_t:t\geqslant0\}$ 是计数过程, $N_t$ 是 $[0,t]$ 内事件发生次数. 令 $S_0=0$, 第 $n$ 次事件发生的时刻为
$$
  \begin{aligned}
    S_n
      &=\inf_{t\geqslant0}\{t:N_t\geqslant n\}\\
      &=\inf\{t:t>S_{n-1},~N_t=n\}\\
  \end{aligned}
$$

第 $n-1$ 个事件与第 $n$ 个事件发生的时间间隔为
$$
  X_n=S_n-S_{n-1},\quad n\geqslant1
$$

固定 $\omega\in\Omega$, 观察随机过程的一条轨道, 即一条时间轴, 可知此时存在**事件等价**
$$
  \begin{aligned}
    \{t:N_t\geqslant n\}
      &=\{t:t\geqslant S_n\}\\
      &=\{t:S_n\leqslant t\}\\
  \end{aligned}
$$

$$
  \begin{aligned}
    \{t:N_t=n\}
      &=\{t:S_n\leqslant t< S_{n+1}\}\\
      &=\{t:S_n\leqslant t\}\setminus\{t:S_{n+1}\leqslant t\}\\
  \end{aligned}
$$

因此 $S_n$ 的**分布函数**为
$$
  \begin{aligned}
    P(S_n\leqslant t)
      &=P(N_t\geqslant n)\\
      &=1-P(N_t\leqslant n-1)\\
      &=1-\sum_{k=0}^{n-1}\frac{(\lambda t)^k}{k!}\mathrm{e}^{-\lambda t},\quad t\geqslant0\\
  \end{aligned}
$$

则 $S_n$ 的**概率密度函数**为
$$
  \begin{aligned}
    f_{S_n}(t)
    &=-\sum_{k=1}^{n-1}\frac{k\lambda(\lambda t)^{k-1}}{k!}\mathrm{e}^{-\lambda t}+\lambda\sum_{k=0}^{n-1}\frac{(\lambda t)^k}{k!}\mathrm{e}^{-\lambda t}\\
    &=\left[\sum_{k=0}^{n-1}\frac{(\lambda t)^k}{k!}-\sum_{k=0}^{n-2}\frac{(\lambda t)^k}{k!}\right]\lambda\mathrm{e}^{-\lambda t}\\
    &=\frac{\lambda(\lambda t)^{n-1}}{(n-1)!}\mathrm{e}^{-\lambda t},\quad t\geqslant0\\
  \end{aligned}
$$

即
$$
  S_n\sim\Gamma(n,\lambda)
$$

**定理**

**计数过程** $\{N_t:t\geqslant0\}$ 是**泊松过程**的**充分必要条件**是 $\{X_n:n\geqslant1\}$ 是**独立**且参数同 $\lambda$ 的**指数分布**.

**例题**

求 $(S_1,S_2)$ 的联合概率密度, 并证明 $S_1,S_2-S_1$ 独立.

**解**: 令 $0< t_1 < t_2$, 取充分小的 $h>0$, 使得
$$
  t_1-\frac{h}{2} < t_1 < t_1 + \frac{h}{2} < t_2-\frac{h}{2} < t_2 < t_2 + \frac{h}{2}
$$

由
$$
  \begin{aligned}
    &~\left\{t_1-\frac{h}{2} < S_1 \leqslant t_1 + \frac{h}{2} < t_2-\frac{h}{2} < S_2 \leqslant t_2 + \frac{h}{2}\right\}\\
    =&~\bigg\{N\left(t_1-\frac{h}{2}\right)=0,N\left(t_1+\frac{h}{2}\right)-N\left(t_1-\frac{h}{2}\right)=1,\\
    &\quad~N\left(t_2-\frac{h}{2}\right)-N\left(t_1+\frac{h}{2}\right)=0,N\left(t_2+\frac{h}{2}\right)-N\left(t_2-\frac{h}{2}\right)=1\bigg\}\bigcup H_n\\
  \end{aligned}
$$

其中
$$
  \begin{aligned}
    H_n=&~\bigg\{N\left(t_1-\frac{h}{2}\right)=0,N\left(t_1+\frac{h}{2}\right)-N\left(t_1-\frac{h}{2}\right)=1,\\
    &\quad~N\left(t_2-\frac{h}{2}\right)-N\left(t_1+\frac{h}{2}\right)=0,N\left(t_2+\frac{h}{2}\right)-N\left(t_2-\frac{h}{2}\right)\geqslant2\bigg\}\\
  \end{aligned}
$$

得
$$
  \begin{aligned}
    P\left(t_1-\frac{h}{2}< S_1 \leqslant t_1 + \frac{h}{2} < t_2-\frac{h}{2} < S_2 \leqslant t_2 + \frac{h}{2}\right)
    &=(\lambda h)^2\mathrm{e}^{-\lambda(t_2+h/2)}+o(h^2)\\
    &=\lambda^2h^2\mathrm{e}^{-\lambda t_2}+o(h^2)\\
  \end{aligned}
$$

所以 $(S_1,S_2)$ 的**联合概率密度**为
$$
  f_{(S_1,S_2)}(t_1,t_2)=\frac{\partial^2 P}{\partial h^2}=
  \begin{cases}
    \lambda^2\mathrm{e}^{-\lambda t_2}, &\text{if}~0< t_1 < t_2,\\
    0, &\text{o.w.}\\
  \end{cases}
$$

为证明 $X_1,X_2$ 的独立性, 下面求 $(X_1,X_2)$ 的联合概率密度.

注意到
$$
  X_1=S_1,~X_2=S_2-S_1
$$
令
$$
  x_1=t_1,~x_2=t_2-t_1
$$
则此变换的**雅克比行列式**为
$$
  \begin{aligned}
    J
      &=\left|\frac{\partial[t_1(x_1,x_2),t_2(x_1,x_2)]}{\partial(x_1,x_2)}\right|\\
      &=\left|\begin{matrix}1 & 0\\ 1&1\end{matrix}\right|\\
      &=1
  \end{aligned}
$$

此处可以直观地理解为**全微分相等**
$$
  g_{(X_1,X_2)}(x_1,x_2)\partial(x_1,x_2)=f_{(S_1,S_2)}(t_1,t_2)\partial(t_1,t_2)
$$

则相互转换需要乘以雅克比行列式作为**转换系数**, 即
$$
  g_{(X_1,X_2)}(x_1,x_2)=f_{(S_1,S_2)}(t_1,t_2)\frac{\partial(t_1,t_2)}{\partial(x_1,x_2)}
$$

于是 $X_1,X_2$ 的**联合概率密度**为
$$
  \begin{aligned}
    g_{(X_1,X_2)}(x_1,x_2)&=f_{(S_1,S_2)}[t_1(x_1,x_2),t_2(x_1,x_2)]\cdot J\\
    &=\begin{cases}
      \lambda^2\mathrm{e}^{-\lambda (x_1+x_2)}, &\text{if}~x_1,x_2\geqslant0,\\
      0, &\text{o.w.}\\
    \end{cases}
  \end{aligned}
$$

对联合概率密度求**边缘分布**可知 $X_1,X_2$ 的概率密度分别为
$$
  g_{X_1}(x_1)=\lambda\mathrm{e}^{-\lambda x_1},~ g_{X_2}(x_2)=\lambda\mathrm{e}^{-\lambda x_2}
$$

所以
$$
  g_{(X_1,X_2)}(x_1,x_2)=g_{X_1}(x_1)g_{X_2}(x_2)
$$

故 $X_1,X_2$ 独立, 即 $S_1,S_2-S_1$ 独立.

## 2.3 剩余寿命与年龄

设 $N_t$ 表示在 $[0,t]$ 上事件发生的个数, $S_n$ 表示第 $n$ 个事件发生的时刻, 那么
+ $S_{N_t}$ 表示在 $t$ 时刻前最后一个事件发生的时刻
+ $S_{N_t+1}$ 表示 $t$ 时刻后首次事件发生的时刻

令
$$
  \begin{aligned}
    W_t&=S_{N_t+1}-t\\
    V_t&=t-S_{N_t}\\
  \end{aligned}
$$

则
+ **年龄**: $V_t=t-S_{N_t}\in[0,t]$
+ **剩余寿命**: $W_t=S_{N_t+1}-t\geqslant0$

**定理 剩余寿命与年龄的分布**

设 $\{N_t:t\geqslant0\}\sim PP(\lambda)$ 是参数为 $\lambda$ 的泊松过程, 则
+ **剩余寿命分布**: $W_t$ 与 $\{X_n:n\geqslant1\}$ 同分布, 即
$$
  \begin{aligned}
    P(W_t\leqslant x)
    &=1-P(W_t>x)\\
    &=1-P(N_{t+x}-N_t=0)\\
    &=1-P(N_x=0)\\
    &=1-\frac{(\lambda x)^0}{0!}\mathrm{e}^{-\lambda x}\\
    &=1-\mathrm{e}^{-\lambda x},\quad x\geqslant0\\
  \end{aligned}
$$

+ **年龄分布**: $V_t$ 是截尾的指数分布, 即对 $x < t$ 有
$$
  \begin{aligned}
    P(V_t\leqslant x)
    &=1-P(V_t>x)\\
    &=1-P(N_t-N_{t-x}=0)\\
    &=1-P(N_x=0)\\
    &=1-\frac{(\lambda x)^0}{0!}\mathrm{e}^{-\lambda x}\\
    &=1-\mathrm{e}^{-\lambda x}, \quad 0 \leqslant x < t\\
  \end{aligned}
$$

故
$$
  P(V_t\leqslant x)=
  \begin{cases}
    1-\mathrm{e}^{-\lambda x}, &\text{if}~ 0 \leqslant x < t\\
    1, & \text{if}~x\geqslant t
  \end{cases}
$$

由于 $V_t$ 取单点 $t$ 的概率大于零, 即分布函数有跳跃, 则其是**混合型随机变量**.

**定理**

若 $\{X_n:n\geqslant1\}$ 独立同分布, 又对 $\forall~t\geqslant0$, $W_t$ 与 $\{X_n:n\geqslant1\}$ 同分布, 分布函数为 $F(x)$, 且 $F(0)=0$, 则 $\{N_t:t\geqslant0\}$ 为泊松过程.

## 2.4 到达时间的条件分布

本节讨论在给定 $N_t=n$ 的条件下, $S_1,S_2,\cdots,S_n$ 的条件分布, 有关性质及其应用.

**定理**

设 $\{N_t:t\geqslant0\}$ 是泊松过程, 则对 $\forall~0 < s < t$, 有
$$
  P(X_1\leqslant s|N_t=1)=\frac{s}{t}
$$

**证明**:
$$
  \begin{aligned}
    P(X_1\leqslant s|N_t=1)
      &=\frac{P(X_1\leqslant s,N_t=1)}{P(N_t=1)}\\
      &=\frac{P(N_s=1,N_t-N_s=0)}{P(N_t=1)}\\
      &=\frac{P(N_s=1)P(N_t-N_s=0)}{P(N_t=1)}\\
      &=\frac{\dfrac{(\lambda s)^1}{1!}\mathrm{e}^{-\lambda s}\dfrac{(\lambda (t-s))^0}{0!}\mathrm{e}^{-\lambda (t-s)}}{\dfrac{(\lambda t)^1}{1!}\mathrm{e}^{-\lambda t}}\\
      &=\frac{s}{t}\\
  \end{aligned}
$$

独立同分布非负随机变量的顺序统计量的联合概率密度为
$$
  f(y_1,y_2,\cdots,y_n)=
  \begin{cases}
    \displaystyle n!\prod_{i=1}^n f(y_i), &\text{if}~0 < y_1 < y_2 < \cdots < y_n,\\
    0, &\text{o.w.}
  \end{cases}
$$

若为均匀分布, 则
$$
  f(y_1,y_2,\cdots,y_n)=
  \begin{cases}
    \displaystyle \frac{n!}{t^n}, &\text{if}~0 < y_1 < y_2 < \cdots < y_n \leqslant t,\\
    0, &\text{o.w.}
  \end{cases}
$$

**定理**

设 $\{N_t:t\geqslant0\}$ 是泊松过程, 在给定 $N_t=n$ 时, 事件相继发生的时间 $S_1,S_2,\cdots,S_n$ 的条件概率密度为
$$
  f(t_1,t_2,\cdots,t_n)=
  \begin{cases}
    \displaystyle \frac{n!}{t^n}, &\text{if}~0 < t_1 < t_2 < \cdots < t_n \leqslant t,\\
    0, &\text{o.w.}
  \end{cases}
$$

本定理说明在给定 $N_t=n$ 的条件下, $S_1,S_2,\cdots,S_n$ 的**条件分布函数**与 $n$ 个在 $[0,t]$ 上**相互独立同均匀分布**的**顺序统计量**的分布函数相同.

**定理**

设 $\{N_t:t\geqslant0\}$ 是计数过程, $X_n$ 为第 $n$ 个事件与第 $n-1$ 个事件的时间间隔, $\{X_n:n\geqslant1\}$ 独立同分布且
$$
  F(x)=P(X_n\leqslant x)
$$

若 $F(0)=0$, 且对 $\forall~0 \leqslant s \leqslant t$, 有
$$
  P(X_1\leqslant s|N_t=1)=\frac{s}{t}
$$

则 $\{N_t:t\geqslant0\}$ 是泊松过程.

**定理**

设 $\{N_t:t\geqslant0\}$ 是计数过程, $X_n$ 为第 $n$ 个事件与第 $n-1$ 个事件的时间间隔, $\{X_n:n\geqslant1\}$ 独立同分布且
$$
  F(x)=P(X_n\leqslant x)
$$

若 $EX_n < \infty,~F(0)=0$, 且对 $\forall~0 \leqslant s \leqslant t,~n\geqslant1$, 有
$$
  P(S_n\leqslant s|N_t=n)=\left(\frac{s}{t}\right)^n
$$

则 $\{N_t:t\geqslant0\}$ 是泊松过程.

**定理**

设 $\{N_t:t\geqslant0\}\sim PP(\lambda)$ 是参数为 $\lambda$ 的泊松过程, $S_k,~k\geqslant1$ 为其到达时刻, 则对任意 $[0,\infty)$ 上的可积函数 $f$ 有
$$
  E\left[f(S_n)\right]=\lambda\int_0^\infty f(t)\mathrm{d}t
$$

**例题**

设到达火车站的顾客流遵照参数 $\lambda$ 的泊松流 $\{N_t:t\geqslant0\}$, 火车 $t$ 时刻离开车站, 求在 $[0,t]$ 到达车站的顾客等待时间总和的期望值.

**解**: 设第 $i$ 个顾客到达火车站的时刻为 $S_i$, 则 $[0,t]$ 到达车站的顾客等待时间总和为
$$
  S(t)=\sum_{i=1}^{N_t}(t-S_i)
$$

其求和上限为随机变量, 故先计算条件期望
$$
  \begin{aligned}
    E[S(t)|N_t=n]
      &=E\left[\sum_{i=1}^{N_t}(t-S_i)\bigg|N_t=n\right]\\
      &=E\left[\sum_{i=1}^{n}(t-S_i)\bigg|N_t=n\right]\\
      &=nt-E\left(\sum_{i=1}^{n}S_i\bigg|N_t=n\right)
  \end{aligned}
$$

由于在给定 $N_t=n$ 的条件下, $S_1,S_2,\cdots,S_n$ 的条件分布函数与 $n$ 个在 $[0,t]$ 上相互独立同均匀分布的顺序统计量的分布函数相同, 则有
$$
  E\left(\sum_{i=1}^{n}S_i\bigg|N_t=n\right)=\frac{nt}{2}
$$

故
$$
  E[S(t)|N_t=n]=nt-\frac{nt}{2}=\frac{nt}{2}
$$

所以
$$
  \begin{aligned}
    E[S(t)]
      &=\sum_{n=0}^\infty E[S(t)|N_t=n]P(N_t=n)\\
      &=\sum_{n=0}^\infty P(N_t=n)\frac{nt}{2}\\
      &=\frac{t}{2}EN_t\\
      &=\frac{\lambda t^2}{2}\\
  \end{aligned}
$$

## 参考文献

+ 林元烈. 应用随机过程[M]. 北京: 清华大学出版社, 2002.
+ 何声武. 随机过程导论[M]. 北京: 高等教育出版社, 1999.
+ Ross S M. Stochastic Processes[M]. John Wiley and Sons, 1993.
