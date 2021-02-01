---
layout: post
title:  "应用随机过程|第1章 概率论与随机过程的基本概念"
date:   2021-01-25
categories: applied-stochastic-process
tags: applied-stochastic-process stochastic-process probability
author: Jingxuan Yang
---

* content
{:toc}

## 1.1 概率

+ 概率论的一个基本概念是**随机试验**. 一个试验或观察, 若它的结果预先无法确定, 则称之为随机试验, 简称为试验. 所有试验的可能结果组成的集合, 称为**样本空间**, 记作 $\Omega$. $\Omega$ 中的元素则称为**样本点**, 用 $\omega$ 表示. 由 $\Omega$ 的某些样本点构成的**子集合**, 常用大写字母 $A,B,C$ 等表示, 由 $\Omega$ 中的若干子集构成的集合称为**集类**, 用花写字母 $\mathcal{A},\mathcal{B},\mathcal{F}$ 等表示





+ 由于并不是在所有的 $\Omega$ 的子集上都能方便地定义概率, 一般只限制在满足一定条件的集类 $\mathcal{F}$ 上研究概率性质, 为此引入 $\sigma$ 域的概念

**定义 $\sigma$ 域与可测空间**

设 $\mathcal{F}$ 为由 $\Omega$ 的某些子集构成的非空集类, 若满足

+ 若 $A\in\mathcal{F}$, 则 $A^c\in\mathcal{F}$, $A^c$ 是 $A$ 的补集, 即
$$
  A^c=\bar{A}=\Omega-A
$$

+ 若 $A_n\in\mathcal{F}$, $n\in\mathbb{N}$, 则

$$
  \bigcup_{n=1}^\infty A_n\in\mathcal{F}
$$

则称 $\mathcal{F}$ 为 $\sigma$ 域, 或 $\sigma$ 代数,  称 $(\Omega,\mathcal{F})$ 为可测空间.

**$\sigma$ 域性质**

若 $\mathcal{F}$ 为 $\sigma$ 域, 则 $\mathcal{F}$ 对可列次交、并、差等运算封闭, 即 $\mathcal{F}$ 中的任何元素经可列次运算后仍属于 $\mathcal{F}$.

**定义 最小 $\sigma$ 域**

设 $\mathcal{A}$ 为由 $\Omega$ 的某些子集构成的集类, 一切包含 $\mathcal{A}$ 的 $\sigma$ 域的交, 记为 $\sigma(A)$, 称 $\sigma(A)$ 为由 $\mathcal{A}$ 生成的 $\sigma$ 域, 或称为包含 $\mathcal{A}$ 的最小 $\sigma$ 域. 一维 Borel $\sigma$ 域即为包含 $\mathbb{R}$ 上所有形如集合 $(-\infty,a]$ 的最小 $\sigma$ 域, 记为
$$
  \mathcal{B}_{\mathbb{R}}=\sigma\{(-\infty,a],~\forall~ a\in\mathbb{R}\}
$$

**定义 概率测度与概率空间**

设 $(\Omega,\mathcal{F})$ 为可测空间, $P:\mathcal{F}\to\mathbb{R}$ 是一个定义在 $\mathcal{F}$ 上的函数, 若满足

+ **非负性**: $P(A)\geqslant0,~\forall~ A\in\mathcal{F}$
+ **归一性**: $P(\Omega)=1$
+ **可列可加性**: 若 $A_i\in\mathcal{F},~i=1,2,\cdots$, 且 $A_iA_j=\varnothing,~\forall~ i\neq j$ 有

$$
  P\left(\bigcup_{i=1}^\infty A_i\right)=\sum_{i=1}^\infty P(A_i)
$$

则称 $P$ 为可测空间 $(\Omega,\mathcal{F})$ 上的一个**概率测度**, 简称概率. 称 $(\Omega,\mathcal{F},P)$ 为**概率空间**, 称 $\mathcal{F}$ 为事件域. 若 $A\in\mathcal{F}$, 则称 $A$ 为**随机事件**, 简称为事件, 称 $P(A)$ 为事件 $A$ 的概率.

**概率的基本性质**

+ **补集概率**: $P(\varnothing)=0$,
$$
  P(A^c)=1-P(A)
$$

+ **有限可加性**: 若 $A_i\in\mathcal{F},~i=1,2,\cdots,n$ 互不相容则
$$
  P\left(\bigcup_{i=1}^n A_i\right)=\sum_{i=1}^n P(A_i)
$$

+ **交集和并集概率**:
$$
  P(A\cup B)=P(A)+P(B)-P(AB)
$$

$$
  P(A-B)=P(A)-P(AB)
$$

+ **概率比较大小**: 若 $A\subset B$, 则
$$
  P(A)\leqslant P(B)
$$

+ **次可列可加性**: 若 $A_i\in\mathcal{F},~i=1,2,\cdots,n$, 则

$$
  P\left(\bigcup_{i=1}^n A_i\right)\leqslant\sum_{i=1}^n P(A_i)
$$
+ **可列交并等式**: 若 $A_i\in\mathcal{F},~i=1,2,\cdots,n$, 则

$$
  P\left(\bigcup_{i=1}^n A_i\right)=\sum_{k=1}^n\left[(-1)^{k+1}\sum_{1\leqslant i_1 < i_2 < \cdots < i_k \leqslant n}P\left(A_{i_1}\cap A_{i_2} \cap\cdots\cap A_{i_k}\right)\right]
$$

**定义 事件列的单调性与极限**

+ 一事件列 $\{A_n:n\geqslant1\}$ 称为**单调增序列**, 若 $A_n\subset A_{n+1},~n\geqslant1$; 称为**単调减序列**, 若 $A_n\supset A_{n+1},~n\geqslant1$.
+ 如果 $\{A_n:n\geqslant1\}$ 是单调增序列, 定义**事件列的极限**
$$
  \lim_{n\to\infty}A_n=\bigcup_{i=1}^\infty A_i
$$

如果 $\{A_n:n\geqslant1\}$ 是单调减序列, 定义**事件列的极限**
$$
  \lim_{n\to\infty}A_n=\bigcap_{i=1}^\infty A_i
$$

**命题 连续性定理**

若 $\{A_n:n\geqslant1\}$ 是单调增或单调减序列, 则极限与概率测度可换序
$$
  \lim_{n\to\infty}P(A_n)=P\left(\lim_{n\to\infty}A_n\right)
$$

**命题 Borel-Cantelli 引理**

设 $\{A_n:n\geqslant1\}$ 是一事件序列, 若
$$
  \sum_{i=1}^\infty P(A_i) < \infty
$$

则
$$
  P\left(\limsup_{i\to\infty}A_i\right)=0
$$

其中

$$
  \limsup_{i\to\infty}A_i\triangleq\bigcap_{n=1}^\infty\bigcup_{i=n}^\infty A_i
$$

**定义 事件独立**

**两个事件** $A,B\in\mathcal{F}$, 若满足
$$
  P(AB)=P(A)P(B)
$$

则称 $A$ 与 $B$ 相互独立.

容易证明下列命题等价:

+ $A$ 与 $B$ 独立
+ $A$ 与 $B^c$ 独立
+ $P(A|B)=P(A)$
+ $P(A|B^c)=P(A)$

**三个事件** $A,B,C\in\mathcal{F}$, 若满足
$$
  P(AB)=P(A)P(B)
$$

$$
  P(AC)=P(A)P(C)
$$

$$
  P(BC)=P(B)P(C)
$$

及

$$
  P(ABC)=P(A)P(B)P(C)
$$

则称 $A,B,C$ 相互独立.

若 $A,B,C$ 相互独立, 则 $A\cup B$ 与 $C$, $AB$ 与 $C$, $A-B$ 与 $C$ 相互独立.

**$n$ 个事件** $A_1,A_2,\cdots,A_n\in\mathcal{F}$, 若对其中任意 $k~(2\leqslant k\leqslant n)$ 个事件 $A_{i_1},A_{i_2},\cdots,A_{i_k}$, 其中 $1\leqslant i_1\leqslant i_2\leqslant\cdots\leqslant i_k\leqslant n$, 有
$$
P(A_{i_1}A_{i_2}\cdots A_{i_k})=P(A_{i_1})P(A_{i_2})\cdots P(A_{i_k})
$$

则称 $A_1,A_2,\cdots,A_n$ 相互独立.

若 $A_1,A_2,\cdots,A_n$ 相互独立, 取 $1 \leqslant m < n$, 记

$$
  \mathcal{F}_1=\sigma(A_k,1\leqslant k\leqslant m),~\mathcal{F}_2=\sigma(A_k,m+1\leqslant k\leqslant n)
$$

任取 $B_1\in\mathcal{F}_1,~B_2\in\mathcal{F}_2$, 则 $B_1$ 与 $B_2$ 独立.

**命题 独立事件 Borel-Cantelli 引理**

若 $\{A_n:n\geqslant1\}$ 是**相互独立**的事件序列, 且

$$
  \sum_{n=1}^\infty P(A_n)=\infty
$$

则有
$$
  \begin{aligned}
    P\left(\limsup_{i\to\infty}A_i\right)
      &=P\left(\bigcap_{n=1}^\infty\bigcup_{i=n}^\infty A_i\right)\\
      &=\lim_{n\to\infty}P\left(\bigcup_{i=n}^\infty A_i\right)\\
      &=\lim_{n\to\infty}P\left(\sup_{i\geqslant n} A_i\right)\\
      &=1\\
  \end{aligned}
$$

## 1.2 随机变量、分布函数及数字特征

### 随机变量与分布函数

**定义 随机变量**

设 $(\Omega,\mathcal{F},P)$ 是一概率空间, $X(\omega):\Omega\to\mathbb{R}$ 是定义在 $\Omega$ 上的単值实函数, 如果对 $\forall~ a\in\mathbb{R}$, 有
$$
  \{\omega:X(\omega)\leqslant a\}\in\mathcal{F}
$$

则称 $X(\omega)$ 为**随机变量**.

常简记
$$
  \begin{aligned}
    \{\omega:X(\omega)\leqslant a\}
      &=\{X\leqslant a\}\\
      &=\{X\in(-\infty,a]\}\\
  \end{aligned}
$$

$X^{-1}(B)=\{\omega:X(\omega)\in B\}$, 且若 $X(\omega)$ 满足 $\{\omega:X(\omega)\leqslant a\}\in\mathcal{F}$, 则 $\forall~ a,b\in\mathbb{R}$, 有 $\{X>a\}$, $\{X < a\}$, $\{X=a\}$, $\{a < X\leqslant b\}$, $\{a\leqslant X < b\}$, $\{a < X < b\}$, $\{A\leqslant X\leqslant b\}\in\mathcal{F}$.

**定义 分布函数**

设 $X$ 为 $(\Omega,\mathcal{F},P)$ 上的随机变量, 对 $\forall~ x\in\mathbb{R}$, 定义
$$
  F(x)=P(X\leqslant x)=P(X\in(-\infty,x])
$$

称 $F(x)$ 为 $X$ 的**分布函数**.

**定义 连续型与离散型随机变量**

+ **离散型随机变量**: 分布函数为**分段右连续**的**阶梯函数**
+ **连续型随机变量**: 分布函数为**几乎处处连续**的函数

**定义 概率密度函数**

对随机变量 $X$ 的分布函数 $F(x)$, 若存在一非负函数 $f(x)$, 对$\forall~ x\in\mathbb{R}$, 有
$$
  F(x)=\int_{-\infty}^xf(u)\mathrm{d}u
$$

则称 $f(x)$ 为随机变量 $X$ 的**概率密度函数**.

若 $f(x)$ 连续, 则
$$
  \frac{\mathrm{d}F(x)}{\mathrm{d}x}=f(x)
$$

即
$$
\lim_{h\to0}\frac{P(x < X\leqslant x+h)}{h}=f(x)
$$

或
$$
  P(x < X\leqslant x+h)=f(x)h+o(h)
$$

**定义 联合分布**

**二维随机变量** $(X,Y)$ 的**联合分布函数** $F(x,y)$ 定义为
$$
  F(x,y)=P(X\leqslant x,~Y\leqslant y)
$$

$X$ 和 $Y$ 的**边缘分布**分别定义为
$$
  F_X(x)= P(X\leqslant x)= \lim_{y\to\infty} F(x, y)=F(x,\infty)
$$

$$
  F_Y(y)= P(Y\leqslant y)= \lim_{x\to\infty} F(x, y)=F(\infty,y)
$$

若存在一非负函数 $f(x,y)$, 对 $\forall~(x,y)\in\mathbb{R}^2$ 有
$$
  F(x,y)=\int_{-\infty}^x\int_{-\infty}^yf(u,v)\mathrm{d}u\mathrm{d}v
$$

则称 $f(x,y)$ 为 $(X,Y)$ 的**联合概率密度函数**.

**$n$ 维随机向量** $(X_1,X_2,\cdots,X_n)$ 的**联合分布函数**定义为

$$
  F(x_1,x_2,\cdots,x_n)=P(X_1\leqslant x_1,X_2\leqslant x_2,\cdots,X_n\leqslant x_n)
$$

**定理 分布函数与事件独立的关系**

称随机变量 $X$ 与 $Y$ 相互独立, 若对 $\forall~(x,y)\in\mathbb{R}^2$, 有
$$
  F(x, y)=F_X(x)F_Y(y)
$$

若对 $\forall~(x_1,x_2,\cdots,x_n)\in\mathbb{R}^n$ 有
$$
  F(x_1,x_2,\cdots,x_n)=F_1(x_1)F_2(x_2)\cdots F_n(x_n)
$$

则称 $X_1,X_2,\cdots,X_n$ 相互独立, 这里
$$
  F_i(x_i)=F_{X_i}(x_i)=P(X_i\leqslant x_i),~\forall~ i=1,2,\ldots,n
$$

若 $X,Y,Z$ 相互独立, 则 $X\pm Y$ 与 $Z$ 独立, $X\cdot Y$ 与 $Z$ 独立, $X/Y(Y\neq0)$ 与 $Z$ 独立, 更一般有 $g_1(X,Y)$ 与 $g_2(Z)$ 独立, 其中 $g_1(X,Y),~g_2(Z)$ 可以是逐段单调函数或逐段连续函数.

### Riemann-Stieltjes 积分

**定义 Riemann-Stieltjes 积分**

设 $F(x)$ 为 $(-\infty,\infty)$ 上的单调不减右连续函数, $g(x)$ 为 $(-\infty,\infty)$ 上的单值实函数, $\forall~ a < b$, 任取分点
$$
  a=x_0 < x_1 < x_2 < \cdots < x_{i-1} < x_i < \cdots < x_n=b
$$

$\forall~ u_i\in[x_{i-1},x_i]$, 作积分和式
$$
  \sum_{i=1}^ng(u_i)\Delta F(x_i)=\sum_{i=1}^ng(u_i)[F(x_i)-F(x_{i-1})]
$$

令
$$
  \lambda=\max_{1\leqslant i\leqslant n}\Delta x_i=\max_{1\leqslant i\leqslant n}(x_i-x_{i-1})
$$

若极限
$$
  J(a,b)=\lim_{\lambda\to0}\sum_{i=1}^ng(u_i)\Delta F(x_i)
$$

存在, 则记
$$
  J(a,b)=\int_a^bg(x)\mathrm{d}F(x)
$$

称极限 $J(a,b)$ 为 $g(x)$ 关于 $F(x)$ 在 $[a,b]$ 上的 **Riemann-Stieltjes 积分**.

当取 $F(x)=x$ 时, Riemann-Stieltjes 积分化为原来的 Riemann 积分, 所以 Riemann-Stieltjes 积分是 Riemann 积分的推广.

当 $a\to-\infty,~b\to\infty$ 时, 若极限
$$
  J(-\infty,\infty)=\lim_{a\to-\infty,~b\to\infty}\int_a^bg(x)\mathrm{d}F(x)
$$

存在, 则称
$$
  J(-\infty,\infty)=\int_{-\infty}^\infty g(x)\mathrm{d}F(x)
$$

为 $g(x)$ 关于 $F(x)$ 在 $(-\infty,\infty)$ 上的 Riemann-Stieltjes 积分.

**Riemann-Stieltjes 积分的基本性质**

+ **分段相加**: 当
  $$
    a=c_0 < c_1 < \cdots < c_n < c_{n+1}=b
  $$
  时, 有
  $$
    \int_a^bg(x)\mathrm{d}F(x)=\sum_{i=0}^n\int_{c_i}^{c_{i+1}}g(x)\mathrm{d}F(x)
  $$

+ **对被积函数线性**:
$$
\int_a^b\sum_{i=1}^ng_i(x)\mathrm{d}F(x)=\sum_{i=1}^n\int_a^bg_i(x)\mathrm{d}F(x)
$$

+ **非负性**: 若 $g(x)\geqslant0$ 且 $a < b$ 则
$$
  \int_a^bg(x)\mathrm{d}F(x)\geqslant0
$$

+ **对被微函数线性**: 若 $F_1(x),~F_2(x)$ 为两个分布函数, $c_1,c_2>0$ 为常数, 则
$$
  \int_a^bg(x)\mathrm{d}[c_1F_1(x)+c_2F_2(x)]=c_1\int_a^bg(x)\mathrm{d}F_1(x)+c_2\int_a^bg(x)\mathrm{d}F_2(x)
$$

+ **被积函数为1**: 若 $g(x)=1$, 则
$$
  \begin{aligned}
    \int_a^bg(x)\mathrm{d}F(x)
      &=\int_a^b1\mathrm{d}F(x)\\
      &=F(b)-F(a)\\
      &=P(a < X\leqslant b)\\
  \end{aligned}
$$

+ **离散型随机变量**: 若 $X$ 为离散型随机变量, 即 $P(X=c_i)=p_i,~i=1,2,\ldots,$ 则
  $$
    F(x)=\sum_{c_i\leqslant x}p_i
  $$
  是一跳跃型分布函数, 即 $F(x)$ 的变化只在 $c_1,c_2,\ldots$ 这些点且其跃度为 $p_i$, 则 Riemann-Stieltjes 积分
  $$
    \begin{aligned}
      \int_{-\infty}^\infty g(x)\mathrm{d}F(x)
      &=\sum_{n=1}^\infty g(c_n)[F(c_n+0)-F(c_n-0)]\\
      &=\sum_{n=1}^\infty g(c_n)p_n\\
    \end{aligned}
  $$
  化成了一个级数

### 数字特征

**定义 数学期望**

设 $X$ 为随机变量, $F(x)$ 为 $X$ 的分布函数, 若
$$
  \int_{-\infty}^\infty |x|\mathrm{d}F(x)
$$

存在, 则称
$$
  EX=\int_{-\infty}^\infty x\mathrm{d}F(x)
$$

为随机变量 $X$ 的**数学期望**.

若 $X$ 为**非负随机变量**, 则有
$$
  \begin{aligned}
    EX
    &=\int_{0}^\infty x\mathrm{d}F(x)\\
    &=\int_{0}^\infty\int_0^x1\mathrm{d}t\mathrm{d}F(x)\\
    &=\int_{0}^\infty\int_t^\infty1\mathrm{d}F(x)\mathrm{d}t\\
    &=\int_0^\infty P(X>t)\mathrm{d}t
  \end{aligned}
$$

同理可知, 对**一般随机变量** $X$ 有
$$
  \begin{aligned}
    EX
    &=\int_0^\infty P(X>t)\mathrm{d}t+\int_{-\infty}^0P(X\leqslant t)\mathrm{d}t\\
    &=\int_0^\infty P(X>t)\mathrm{d}t-\int_0^\infty P(X\leqslant -t)\mathrm{d}t\\
  \end{aligned}
$$

**期望性质**

+ **线性**:
$$
  E\left(\sum_{i=1}^nc_iX_i\right)=\sum_{i=1}^nc_iEX_i
$$

+ **函数复合随机变量**:
$$
E[g(X)]=\int_{-\infty}^\infty g(x)\mathrm{d}F(x)
$$

+ **离散型随机变量**: $P(X=x_n)=p_n,~n\in\mathbb{N}$,
$$
  EX=\sum_{n=1}^\infty x_np_n
$$

+ **连续型随机变量**: 概率密度函数 $f(x)$
$$
EX=\int_{-\infty}^\infty x\mathrm{d}F(x)=\int_{-\infty}^\infty xf(x)\mathrm{d}x
$$

**定义 方差**

随机变量 $X$ 的方差为
$$
  \begin{aligned}
    \mathrm{var}X
      &=\sigma_X^2=DX\\
      &\triangleq E(X-EX)^2\\
      &=EX^2-(EX)^2
  \end{aligned}
$$

**定义 协方差**

对两个随机变量 $(X,Y)$ 定义协方差为
$$
  \begin{aligned}
    \mathrm{cov}(X,Y)
      &\triangleq E[(X-EX)(Y-EY)]\\
      &=E(XY)-(EX)(EY)
  \end{aligned}
$$

若 $X$ 与 $Y$ 独立, 则
$$
  \begin{aligned}
    \mathrm{cov}(X,Y)
      &=E(XY)-(EX)(EY)\\
      &=(EX)(EY)-(EX)(EY)\\
      &=0\\
  \end{aligned}
$$

**定义 相关系数**

若
$$
  0 < DX=\sigma_X^2 < \infty
$$

$$
  0 < DY=\sigma_Y^2 < \infty
$$

则称
$$
  \rho(X,Y)=\frac{\mathrm{cov}(X,Y)}{\sigma_X\sigma_Y}=\frac{\mathrm{cov}(X,Y)}{\sqrt{(DX)(DY)}}
$$

为 $X$ 与 $Y$ 的**相关系数**. $\rho(X,Y)$ 刻画了 $X,Y$ 之间线性关系的密切程度, 若 $\rho=0$, 则称 $X,Y$ **不相关**.

**定义 矩**

随机变量 $X$ 的 $k\geqslant1$ 阶矩定义为
$$
  E(X^k)=\int_{-\infty}^\infty x^k\mathrm{d}F_X(x)
$$

**数字特征性质**

+ **方差平方线性且相关**:
$$
  D\left(\sum_{i=1}^nc_iX_i\right)=\sum_{i=1}^nc_i^2DX_i+2\sum_{i < j}c_ic_j\mathrm{cov}(X_i,X_j)
$$

+ **Schwartz 不等式**: 若随机变量 $X,Y$ 的二阶矩存在, 则
$$
  |E(XY)|^2\leqslant E(X^2)E(Y^2)
$$

### 常用随机变量的分布

+ **二项分布**: $X\sim B(n,p)$,
  $$
    EX=np,~DX=np(1-p)
  $$
  $$
    P(X=k)=\binom{n}{k}p^k(1-p)^{n-k},~0\leqslant k\leqslant n
  $$

+ **泊松分布**: $X\sim P(\lambda)$,
  $$
    EX=\lambda,~DX=\lambda
  $$
  $$
    P(X=k)=\frac{\lambda^k}{k!}\mathrm{e}^{-\lambda},\quad k=0,1,2,\ldots
  $$

+ **几何分布**: $X\sim G(p)$,
  $$
    EX=\frac{1}{p},~DX=\frac{1-p}{p^2}
  $$
  $$
    P(X=k)=(1-p)^{k-1}p,\quad k=1,2,\ldots
  $$

+ **均匀分布**: $X\sim U(a,b)$,
  $$
    EX=\frac{a+b}{2},~DX=\frac{(b-a)^2}{12}
  $$
  $$
    f(x)=
      \begin{cases}
        \dfrac{1}{b-a},&\text{if}~a < x < b\\
        0,&\text{o.w.}
      \end{cases}
  $$

+ **正态分布**: $X\sim N(\mu,\sigma^2)$,
  $$
    EX=\mu,~DX=\sigma^2
  $$
  $$
    E(X-\mu)^{2k}=(2k-1)!!~\sigma^{2k}
  $$
  $$
    f(x)=\frac{1}{\sqrt{2\pi\sigma^2}}\exp\left\{-\frac{(x-\mu)^2}{2\sigma^2}\right\}
  $$

+ **指数分布**: $X\sim E(\lambda)$,
  $$
    EX=\frac{1}{\lambda},~DX=\frac{1}{\lambda^2}
  $$
  $$
    f(x)=
      \begin{cases}
        \lambda\mathrm{e}^{-\lambda x},&\text{if}~x\geqslant0\\
        0,&\text{o.w.}
      \end{cases}
  $$

+ **gamma 分布**: $X\sim \Gamma(\alpha,\lambda)$,
  $$
    EX=\frac{\alpha}{\lambda},~DX=\frac{\alpha}{\lambda^2}
  $$
  $$
    f(x)=
      \begin{cases}
        \dfrac{\lambda\mathrm{e}^{-\lambda x}(\lambda x)^{\alpha-1}}{\Gamma(\alpha)},&\text{if}~\alpha>0\\
        0,&\text{o.w.}
      \end{cases}
  $$

  这里 gamma 函数为
  $$
    \Gamma(\alpha)=\int_0^\infty \mathrm{e}^{-t}t^{\alpha-1}\mathrm{d}t,\quad\forall~ \alpha>0
  $$

+ **beta 分布**: $X\sim \mathrm{beta}(\alpha,\beta)$,
  $$
    EX=\frac{\alpha}{\alpha+\beta},~DX=\frac{\alpha\beta}{(\alpha+\beta+1)(\alpha+\beta)^2}
  $$
  $$
    f(x)=\begin{cases}\dfrac{x^{\alpha-1}(1-x)^{\beta-1}}{B(\alpha,\beta)},&\text{if}~0 < x < 1\\0,&\text{o.w.}\end{cases}
  $$

  这里 beta 函数为
  $$
    \begin{aligned}
      B(\alpha,\beta)
      &=\int_0^1 x^{\alpha-1}(1-x)^{\beta-1}\mathrm{d}x\\
      &=\frac{\Gamma(\alpha)\cdot\Gamma(\beta)}{\Gamma(\alpha+\beta)}\\
    \end{aligned}
  $$

### 示性函数的线性组合

+ **非负随机变量可由事件示性函数的线性组合表示**: 设 $X(\omega)$ 为**非负随机变量**, $P(X < \infty)=1$, 令
  $$
    X_n(\omega)=\sum_{k=0}^{n2^n-1}\frac{k}{2^n}\mathbf{1}_{\{\frac{k}{2^n}\leqslant X < \frac{k+1}{2^n}\}}(\omega)+n\mathbf{1}_{\{X\geqslant n\}}(\omega)
  $$

  则 $X_n(\omega)$ 是随机变量, 且 $\forall~\omega\in\Omega$, 有
  $$
    \lim_{n\to\infty}X_n(\omega)=X(\omega)
  $$

+ **一般随机变量可由事件示性函数的线性组合表示**: 设 $X(\omega)$ 为**一般的随机变量**, 令
  $$
    X^+=X\vee0=\max(X,0)
  $$
  $$
    X^-=-(X\wedge0)=-\min(X,0)
  $$

  显然 $X^+,X^-\geqslant0$. 由上面的结论, 对 $X^+,X^-$ 存在 $X_n^+\uparrow X^+,~X_m^-\uparrow X^-$, 若令
  $$
    X_n=X_n^+-X_n^-
  $$

  则 $X_n\uparrow X$.

## 1.3 矩母函数、特征函数和拉普拉斯变换

### 矩母函数

**定义 矩母函数或生成函数**

随机变量 $X$ 的**矩母函数**或称**生成函数**定义为
$$
  \varphi(t)=E(\mathrm{e}^{tX})=\int_{-\infty}^\infty\mathrm{e}^{tx}\mathrm{d}F_X(x)
$$

显然, 如 $X$ 的 $k$ 阶矩存在, 则
$$
  E(X^k)=\varphi^{(k)}(0)
$$

矩母函数由此得名, 可以证明矩母函数与分布函数是一一对应的.

对于取值非负整数的随机变量 $X$, 即
$$
  P(X=k)=p_k\geqslant0,~k\geqslant0,~\sum_{k=0}^\infty p_k=1
$$

则 $X$ 的**矩母函数**记为
$$
  g(s)=E(s^X)=\sum_{k=0}^\infty p_ks^k
$$

显然
$$
  p_k=\frac{g^{(k)}(0)}{k!}
$$

且有
$$
  E[X(X-1)\cdots(X-k+1)]=g^{(k)}(1)
$$

特别地,
$$
  E(X)=g'(1)
$$

$$
  E(X(X-1))=EX^2-EX=g''(1)
$$

则有
$$
  \begin{aligned}
    D(X)
      &=EX^2-(EX)^2\\
      &=g''(1)+g'(1)-[g'(1)]^2\\
  \end{aligned}
$$

若 $X_1,X_2$ **相互独立**, 其矩母函数分别记为 $g_1(s),g_2(s)$, 则 $X_1+X_2$ 的**矩母函数**为
$$
  g_{X_1+X_2}(s)=g_1(s)g_2(s)
$$

### 特征函数

**定义 特征函数**

随机变量 $X$ 的**特征函数**定义为
$$
  \phi(x)\triangleq E[\mathrm{e}^{\mathrm{i}tX}]=\int_{-\infty}^\infty\mathrm{e}^{\mathrm{i}tx}\mathrm{d}F_X(x)
$$

### Laplace-Stieltjes 变换

**定义 Laplace-Stieltjes 变换**

设非负随机变量 $X$, 分布函数 $F_X(x)$, $s=a+\mathrm{i}b$, 这里 $a>0,~b$ 是实数, 称
$$
  \hat{F}_X(s)=\int_0^\infty\mathrm{e}^{-sx}\mathrm{d}F_X(x)
$$

为 $F_X(x)$ 的 **Laplace-Stielties 变换**, 或称随机变量 $X$ 的 **Laplace-Stielties 变换**, 简记 L-S 变换.

$\hat{F}_X(s)$ 与 $F_X(x)$ 也有一一对应关系, 且对 $X_1,X_2>0$ 相互独立, 有
$$
  \hat{F}_{X_1+X_2}(s)=\hat{F}_{X_1}(s)\hat{F}_{X_2}(s)
$$

## 1.4 条件数学期望

### 离散型随机变量

设 $(X,Y)$ 为两个**离散型随机变量**, 其**联合分布律**为
$$
  P(X=x_i,Y=y_i)=p_{ij}\geqslant0,~\sum_{i,j}p_{ij}=1
$$

若
$$
  \begin{aligned}
    P(Y=y_j)
    &=\sum_iP(X=x_i,Y=y_i)\\
    &=\sum_ip_{ij}\\
    &> 0\\
  \end{aligned}
$$

则称
$$
  P(X=x_i|Y=y_j)=\frac{P(X=x_i,Y=y_i)}{P(Y=y_j)}
$$

为**给定** $Y=y_j$ 时, $X$ 的**条件分布律**.

称
$$
  E(X|Y=y_j)\triangleq\sum_ix_iP(X=x_i|Y=y_j)
$$

为**给定** $Y=y_j$ 时, $X$ 的**条件数学期望**.

记
$$
  E(X|Y)\triangleq\sum_j\mathbf{1}_{\{Y=y_j\}}(\omega)E(X|Y=y_j)
$$

称 $E(X|Y)$ 为 $X$ 关于 $Y$ 的**条件数学期望**.

随机变量 $E(X|Y)$ 是随机变量 $Y$ 的函数, 当 $\omega\in\{\omega:Y(\omega)=y_j\}$ 时, $E(X|Y)$ 的取值为 $E(X|Y=y_j)$, 其**数学期望**应为
$$
  \begin{aligned}
    E[E(X|Y)]
      &=\sum_jE(X|Y=y_j)P(Y=y_j)\\
      &=\sum_{i,j}x_iP(X=x_i|Y=y_j)P(Y=y_j)\\
      &=\sum_{i,j}x_i\frac{P(X=x_i,Y=y_i)}{P(Y=y_j)}P(Y=y_j)\\
      &=\sum_{i,j}x_iP(X=x_i,Y=y_i)\\
      &=\sum_{i}x_iP(X=x_i)\\
      &=EX
  \end{aligned}
$$

### 连续型随机变量

设 $(X,Y)$ 的联合概率密度函数为 $f(x,y)$, 若 $Y$ 的概率密度函数
$$
  f_Y(y)=\int_{-\infty}^\infty f(x,y)\mathrm{d}x>0
$$

则称
$$
  f_{X|Y=y}(x|y)=\frac{f(x,y)}{f_Y(y)}
$$

为**给定** $Y=y$ 时, $X$ 的**条件概率密度函数**.

条件分布函数为
$$
  \begin{aligned}
    F_{X|Y=y}(x|y)
      &=P(X\leqslant x|Y=y)\\
      &=\int_{-\infty}^x\frac{f(u,y)}{f_Y(y)}\mathrm{d}u\\
  \end{aligned}
$$

条件数学期望为
$$
  \begin{aligned}
    E(X|Y=y)
      &=\int_{-\infty}^\infty xf_{X|Y=y}(x|y)\mathrm{d}x\\
      &=\int_{-\infty}^\infty x\frac{f(x,y)}{f_Y(y)}\mathrm{d}x\\
  \end{aligned}
$$

考虑 $D\in\mathcal{B}_{\mathbb{R}}$, **给定** $Y\in D$, 若 $P(Y\in D)>0$, $X$ 的条件分布函数为
$$
  \begin{aligned}
    F_{X|Y\in D}(x|D)
      &=P(X\leqslant x|Y\in D)\\
      &=\frac{P(X\leqslant x,Y\in D)}{P(Y\in D)}\\
      &=\frac{\displaystyle\int_{-\infty}^x\int_{y\in D}f(x,y)\mathrm{d}y\mathrm{d}x}{\displaystyle\int_{y\in D}f_Y(y)\mathrm{d}y}
  \end{aligned}
$$

则**给定** $Y\in D$, $X$ 的**条件概率密度函数**为
$$
  \begin{aligned}
    f_{X|Y\in D}(x|D)
    &=\frac{\displaystyle\int_{y\in D}f(x,y)\mathrm{d}y}{\displaystyle\int_{y\in D}f_Y(y)\mathrm{d}y}\\
    &=\frac{\displaystyle\int_{y\in D}f(x,y)\mathrm{d}y}{P(Y\in D)}\\
  \end{aligned}
$$

于是给定 $Y\in D$, $X$ 的**条件数学期望**为
$$
  \begin{aligned}
    E(X|Y\in D)
      &=\int_{-\infty}^\infty xf_{X|Y\in D}(x|D)\mathrm{d}x\\
      &=\int_{-\infty}^\infty x\frac{\displaystyle\int_{y\in D}f(x,y)\mathrm{d}y}{P(Y\in D)}\mathrm{d}x\\
      &=\frac{1}{P(Y\in D)}\int_{-\infty}^\infty\int_{y\in D}xf(x,y)\mathrm{d}y\mathrm{d}x\\
      &=\frac{1}{P(Y\in D)}\int_{y\in D}\int_{-\infty}^\infty\frac{xf(x,y)}{f_Y(y)}f_Y(y)\mathrm{d}x\mathrm{d}y\\
      &=\frac{1}{P(Y\in D)}\int_{y\in D}E(X|Y=y)f_Y(y)\mathrm{d}y\\
      &=E[E(X|Y)|Y\in D]\\
  \end{aligned}
$$

若取 $D=\mathbb{R}$, 则有
$$
  \begin{aligned}
    E(X|Y\in\mathbb{R})
      &=E(X)\\
      &=E[E(X|Y)|Y\in \mathbb{R}]\\
      &=E[E(X|Y)]\\
  \end{aligned}
$$

此即是所谓**全期望公式**.

上面两点分别是对条件期望取单点值和区间值的要求, 基于此即可定义连续型随机变量条件数学期望.

**定义 连续型随机变量条件数学期望**

设 $(X,Y)$ 具有联合概率密度函数 $f(x,y)$, $Y$ 的概率密度函数为 $F_Y(y)>0$, $E|X| < \infty$, 若随机变量 $E(X|Y)$ 满足
+ $E(X|Y)$ 是随机变量 $Y$ 的函数, 当 $Y=y$ 时, 它的取值为 $E(X|Y=y)$
+ 对任意 $D\in\mathcal{B}_{\mathbb{R}}$, 有
  $$
    E[E(X|Y)|Y\in D]=E[X|Y\in D]
  $$
  则称随机变量 $E(X|Y)$ 为 $X$ 关于 $Y$ 的**条件数学期望**.

### 一般随机变量

设 $(X,Y)$ 为一般随机变量, 其联合分布函数为 $P(X\leqslant x,~Y\leqslant y)$. 以下假设 $E|X| < \infty$, 分两种情况讨论.

**定义 一般随机变量条件数学期望**

设 $D\in\mathcal{B}_{\mathbb{R}}$, $P(Y\in D)>0$. $\forall~ x\in\mathbb{R}$, 称
$$
  P(X\leqslant x|Y\in D)=\frac{P(X\leqslant x,Y\in D)}{P(Y\in D)}
$$

为 $X$ 关于事件 $\{\omega:Y(\omega)\in D\}$ 的**条件分布函数**.

称
$$
  E(X|Y\in D)=\int_{-\infty}^\infty x\mathrm{d}P(X\leqslant x|Y\in D)
$$

为 $X$ 关于事件 $\{\omega:Y(\omega)\in D\}$ 的**条件数学期望**.

在许多问题中常常需要考虑 $D$ 为单点集 $\{y\}$ 的情形. 若 $P(Y=y)>0$, 这时定义条件分布同上. 当 $P(Y=y)=0$ 时, 定义 $P(X\leqslant x|Y=y)$ 如下.

**定义 一般随机变量单点概率为零时条件数学期望**

设 $(x,y)\in\mathbb{R}^2$, 对充分小的 $h>0$, 有 $P(y < Y\leqslant y+h)>0$. 若
$$
  P(X\leqslant x|Y=y)\triangleq\lim_{h\to0}P(X\leqslant x|y < Y\leqslant y+h)
$$

存在, 则称 $P(X\leqslant x|Y=y)$ 为 $X$ 关于事件 $\{\omega:Y(\omega)=y\}$ 的**条件分布函数**.

称
$$
  E(X|Y=y)=\int_{-\infty}^\infty x\mathrm{d}P(X\leqslant x|Y=y)
$$

为 $X$ 关于事件 $\{\omega:Y(\omega)=y\}$ 的**条件数学期望**.

**定义 条件数学期望**

若随机变量 $E(X|Y)$ 满足
+ $E(X|Y)$ 是随机变量 $Y$ 的函数, 当 $Y=y$ 时, 它的取值为 $E(X|Y=y)$
+ 对任意 $D\in\mathcal{B}_{\mathbb{R}}$, 有
$$
  E[E(X|Y)|Y\in D]=E[X|Y\in D]
$$

则称随机变量 $E(X|Y)$ 为 $X$ 关于 $Y$ 的**条件数学期望**.

**定理 全期望公式**

设随机变量 $E(X|Y)$ 为 $X$ 关于 $Y$ 的条件数学期望, 则有
$$
  \begin{aligned}
    EX
      &=E[E(X|Y)]\\
      &=\int_{-\infty}^\infty E(X|Y=y)\mathrm{d}P(Y\leqslant y)\\
  \end{aligned}
$$

上式可看作是数学期望形式的全概率公式, 即**全期望公式**.

### 条件概率与条件分布函数

+ 条件概率, 条件分布函数均可用条件数学期望的概念及性质来处理.

由示性函数的定义有
$$
  P(B)=E[\mathbf{1}_B(\omega)]
$$

称
$$
  E[\mathbf{1}_B(\omega)|Y]=P(B|Y)
$$

为事件 $B$ 关于随机变量 $Y$ 的**条件概率**, 此时 $P(B|Y)$ 是随机变量且是 $Y$ 的函数.

对于 $\forall~ x\in\mathbb{R}$, 取 $B=(\omega:X(\omega)\leqslant x)$, 称
$$
  \begin{aligned}
    F(x|Y)
      &\triangleq P(X\leqslant x|Y)\\
      &=E[\mathbf{1}_{\{X(\omega)\leqslant x\}}(\omega)|Y]\\
  \end{aligned}
$$

为 $X$ 关于 $Y$ 的**条件分布函数**.

### 条件数学期望的基本性质

+ 两个随机变量 $Z_1,Z_2$, 如果
  $$
    P(Z_1=Z_2)=1
  $$
  则称 $Z_1,Z_2$ 几乎处处 (almost everywhere) 或几乎必然 (almost surely) 相等, 记作 $Z_1=Z_2$ a.e. 或 a.s.

**定理 条件数学期望的基本性质**

设 $X,Y,X_i,~1\leqslant i\leqslant n$ 为随机变量, $g(x),h(y)$ 为一般函数, 且 $E|X| < \infty$, $E|X_i| < \infty$, $1\leqslant i\leqslant n$, $E|g(X)h(Y)| < \infty$, $E|g(X)| < \infty$. 则有
+ **全期望公式**:
$$
  EX=E[E(X|Y)]
$$

+ **线性**: $\forall~ \alpha_i\in\mathbb{R},~1\leqslant i\leqslant n$, 有
$$
  E\left(\sum_{i=1}^n\alpha_iX_i\Big|Y\right)=\sum_{i=1}^n\alpha_iE(X_i|Y)
$$

+ **条件期望平滑性**:
$$
  E[g(X)h(Y)|Y]=h(Y)E[g(X)|Y]
$$

特别地, 有
$$
  E(X|X)=X
$$

$$
  \begin{aligned}
    E[g(X)h(Y)]
      &=E\{E[g(X)h(Y)|Y]\}\\
      &=E\{h(Y)E[g(X)|Y]\}\\
  \end{aligned}
$$

+ **独立性**: 若 $X$ 与 $Y$ 相互独立, 则
$$
  E(X|Y)=EX
$$

### 多元随机变量的条件数学期望

+ **离散型随机变量**

  设三个随机变量 $(X,Y,Z)$, 其中 $(Y,Z)$ 为**离散型随机变量**, 称随机变量 $E(X|Y,Z)$ 是 $X$ 关于 $Y,Z$ 的**条件数学期望**, 若它满足

    + $E(X|Y,Z)$ 是 $(Y,Z)$ 的二元函数, 当 $Y=y_j,Z=z_k$ 时, $E(X|Y,Z)$ 的取值为 $E(X|Y=y_j,Z=z_k)$
    + 对任意 $D_j\in\mathcal{B}_{\mathbb{R}}$, $D_k\in\mathcal{B}_{\mathbb{R}}$, 有
      $$
        E[E(X|Y,Z)|Y\in D_j,Z\in D_k]=E(X|Y\in D_j,Z\in D_k)
      $$

      用示性函数表示, 即

      $$
        E(X|Y,Z)\triangleq\sum_{j,k}\mathbf{1}_{\{Y(\omega)=y_j,Z(\omega)=z_k\}}(\omega)E(X|Y=y_j,Z=z_k)
      $$

      当 $E|X| < \infty$ 时, 由对 $Z$ 的全期望公式和条件期望平滑性有
      $$
        E[E(X|Y,Z)|Y]=E(X|Y)=E[E(X|Y)|Y,Z]
      $$

+ **连续型随机变量**

  如 $(X,Y,Z)$ 为连续型随机变量, 联合概率密度函数为 $f(x,y,z)$, $(Y,Z)$ 的联合概率密度函数为 $f_{Y,Z}(y,z)$, $X$ 关于 $Y=y,Z=z$ 的条件概率密度函数为
  $$
    f_{X|(Y,Z)=(y,z)}(x|y,z)=\frac{f(x,y,z)}{f_{Y,Z}(y,z)}
  $$

  设 $E|X| < \infty$, $f_{Y,Z}(y,z)>0$, 若随机变量 $E(X|Y,Z)$ 满足

    + $E(X|Y,Z)$ 是 $(Y,Z)$ 的二元函数, 当 $Y=y,Z=z$ 时, $E(X|Y,Z)$ 的取值为 $E(X|Y=y,Z=z)$
    + 对任意 $D_1\in\mathcal{B}_{\mathbb{R}}$, $D_2\in\mathcal{B}_{\mathbb{R}}$, 有
      $$
        E[E(X|Y,Z)|Y\in D_1,Z\in D_2]=E(X|Y\in D_1,Z\in D_2)
      $$

      称随机变量 $E(X|Y,Z)$ 是 $X$ 关于 $Y,Z$ 的**条件数学期望**.

**定理 多元随机变量条件期望的性质**

设以下所涉及的期望全都有限, 则有
+ **全期望公式**:
$$
  EX=E[E(X|Y_1,Y_2,\cdots,Y_n)]
$$

+ **线性**: $\forall~ \alpha_i\in\mathbb{R},~1\leqslant i\leqslant n$, 有
  $$
    E\left(\sum_{i=1}^n\alpha_iX_i\Big|Y_1,Y_2,\cdots,Y_n\right)=\sum_{i=1}^n\alpha_iE(X_i|Y_1,Y_2,\cdots,Y_n)
  $$

+ **条件期望平滑性**:
  $$
    E[g(X)h(Y_1,Y_2,\cdots,Y_n)|Y_1,Y_2,\cdots,Y_n]=h(Y_1,Y_2,\cdots,Y_n)E[g(X)|Y_1,Y_2,\cdots,Y_n]
  $$

+ **独立性**: 若 $X$ 与 $Y_1,Y_2,\cdots,Y_n$ 独立, 则
  $$
    E(X|Y_1,Y_2,\cdots,Y_n)=EX
  $$

### 条件乘法公式与条件独立性

下面在**条件概率测度**下推广原本的概率乘法公式和事件独立性.

+ **条件概率的乘法公式**

  设 $A,B$ 为两个随机事件, 由条件概率的定义可知
  $$
    P(AB)=P(A)P(B|A)
  $$

与上面的概率乘法公式类似, 条件概率测度 $P(\cdot|A)$ 的乘法公式如下.

**定义 条件概率测度下的乘法公式**

设 $A,B,C$ 为随机事件, 则
$$
  P(BC|A)=P(B|A)P(C|AB)
$$

+ **条件独立性**

  当两个随机事件 $A,B$ 独立时, 有
  $$
    P(AB)=P(A)P(B)
  $$
  即
  $$
    P(A|B)=P(A)
  $$

与上面的独立性概念类似, 条件独立性的定义如下.

**定义 条件独立**

设 $A,B,C$ 为随机事件, 称事件 $A,B$ 关于事件 $C$ **条件独立**, 即在条件概率测度 $P(\cdot|C)$ 下独立, 若满足
$$
  P(A|BC)=P(A|C)
$$

**命题 条件独立的充要条件**

设 $A,B,C$ 为随机事件, 则事件 $A,B$ 关于事件 $C$ **条件独立的充要条件**为
$$
  P(AB|C)=P(A|C)P(B|C)
$$

此即事件独立定义在条件概率测度 $P(\cdot|C)$ 下的自然推广.

### 全概率公式

设 $\{B_k\},~k=1,2,\cdots$ 为 $\Omega$ 的一个**分割**, 则有**全概率公式**
$$
  P(A)=\sum_{k=1}^\infty P(B_k)P(A|B_k)
$$

## 1.5 随机过程的概念

在概率论中, 研究了随机变量, $n$ 维随机向量. 在极限定理中, 涉及到了无穷多个随机变量, 但局限在它们之间是**相互独立**的情形. 将上述情形加以推广, 即研究一族**无穷多个**、**相互有关**的随机变量, 这就是**随机过程**.

### 随机过程的定义

**定义 随机过程**

设 $T$ 是一个**指标集**, 如
$$
  T=\mathbb{Z},\mathbb{Z}^+,\mathbb{R},\mathbb{R}^+,[0,t]
$$

等. $\forall~ t\in T$, $X_t$ 是定义在概率空间 $(\Omega,\mathcal{F},P)$ 上取值于 $S$ 的随机变量, 则称
$$
  X=\{X_t:t\in T\}
$$

是定义在 $(\Omega,\mathcal{F},P)$ 上以 $S$ 为**状态空间**的**随机过程**.

+ 当 $T=\mathbb{Z},\mathbb{Z}^+$ 或其子集时, 称 $X$ 是**离散参数**随机过程, 当 $T=\mathbb{R},\mathbb{R}^+$ 或其子区间时, 称 $X$ 是**连续参数**随机过程.

+ 若 $S$ 是**有限集**或**可列无穷集**时, 称 $X$ 是**离散状态**的, 若 $S$ 是**连续流**, 则称 $X$ 是**连续状态**的.

+ 有时记 $X_t(\omega)=X(t,\omega):T\times\Omega\to S$, 即 $X(\cdot,\cdot)$ 为 $T\times\Omega$ 上的**二元单值函数**.

+ 固定 $t\in T$, 函数 $X_t(\omega):\Omega\to S$ 是定义在样本空间 $\Omega$ 上的函数, 即为一**随机变量**.

+ 固定 $\omega\in\Omega$, 函数 $X_t(\omega):T\to S$ 称为 $X$ 的一条**样本轨道**.

### 随机过程的分布

随机过程的**概率特性**由其**有限维分布族**决定. 设 $S=\mathbb{R}$, $\forall~ n\geqslant1$, $t_1,t_2,\cdots,t_n\in T$, 记
$$
  F(t_1,t_2,\cdots,t_n;x_1,x_2,\cdots,x_n)=P(X_{t_1}\leqslant x_1,X_{t_2}\leqslant x_2,\cdots,X_{t_n}\leqslant x_n)
$$

为 $X_{t_1},X_{t_2},\cdots,X_{t_n}$ 的**联合分布函数**, 其全体
$$
  \{F(t_1,t_2,\cdots,t_n;x_1,x_2,\cdots,x_n):t_1,t_2,\cdots,t_n\in T,n\geqslant1\}
$$

称为 $X=\{X_t:t\in T\}$ 的**有限维分布族**, 具有以下性质.

+ **对称性**: 对 $(1,2,\cdots,n)$ 的任一排列 $(j_1,j_2,\cdots,j_n)$ 有
  $$
    F\Big(t_{j_1},t_{j_2},\cdots,t_{j_n};x_{j_1},x_{j_2},\cdots,x_{j_n}\Big)=F(t_1,t_2,\cdots,t_n;x_1,x_2,\cdots,x_n)
  $$

  即任意排列均不会改变分布函数

+ **相容性**: 对 $\forall~ m < n$ 有边缘分布
  $$
    F(t_1,\cdots,t_m,t_{m+1},\cdots,t_n;x_1,\cdots,x_m,\infty,\cdots,\infty)=F(t_1,t_2,\cdots,t_m;x_1,x_2,\cdots,x_m)
  $$

  即有限维分布族也可像普通分布函数那样求边缘分布

### 随机过程的分类

设 $X=\{X_t:t\in T\}$ 为随机过程, 按其**概率特征**分类如下.

+ **点过程或计数过程**

  一个随机过程 $\{N(A),A\subset T\}$ 是点过程, 若 $N(A)$ 表示在集合 $A$ 中事件发生的总数, 即它满足
    + 对 $\forall~ A\subset T$, $N(A)$ 是一取值非负整数的随机变量, $N(\varnothing)=0$
    + 对 $\forall~ A_1,A_2\subset T$, 若 $A_1A_2=\varnothing$, 则对每一个样本有
    $$
      N(A_1\cup A_2)=N(A_1)+N(A_2)
    $$
    + 参数集 $T$ 可以是 $\mathbb{R}^n$, 也可以是任意一抽象非空集
    + **泊松过程**是简单的点过程

+ **独立与平稳增量过程**
  + 对
    $$
      t_1 < t_2 < \cdots < t_n,~t_i\in T,~1\leqslant i\leqslant n
    $$
    若增量
    $$
      X_{t_1},X_{t_2}-X_{t_1},\cdots,X_{t_n}-X_{t_{n-1}}
    $$
    相互独立, 则称 $X$ 为**独立增量过程**
  + 若 $\forall~0\leqslant s < t$, 增量 $X_t-X_s$ 的分布只依赖于 $t-s$, 则称 $X$ 有**平稳增量**
  + 有平稳增量的独立増量过程简称为**独立平稳增量过程**
  + **泊松过程**和维纳过程或称**布朗运动**是两个最简单也是最重要的独立平稳增量过程

+ **马尔可夫过程与扩散过程**
  + 对
    $$
    t_1 < t_2 < \cdots < t_n < t,~t_i\in T,~x_i,~1\leqslant i\leqslant n
    $$
    及 $A\subset\mathbb{R}$, 若总有
    $$
      P(X_t\in A|X_{t_1}=x_1,X_{t_2}=x_2,\cdots,X_{t_n}=x_n)=P(X_t\in A|X_{t_n}=x_n)
    $$
    则称此过程为**马尔可夫过程**
  + **离散状态**马尔可夫过程称为**马尔可夫链**
  + **连续时间参数**且**连续状态**的马尔可夫过程称为**扩散过程**
  + **泊松过程**是一个最简单**连续时间**参数**马尔可夫链**
  + **布朗运动**是一个最简单的**扩散过程**

+ **鞅**
  + 若 $\forall~ t\in T,~E|X_t| < \infty$, 且对
    $$
      \forall~ t_1 < t_2 < \cdots < t_n < t_{n+1}
    $$
    有
    $$
      E(X_{t_{n+1}}|X_{t_1},X_{t_2},\cdots,X_{t_n})=X_{t_n}
    $$
    则称 $X$ 为鞅.
  + **布朗运动**关于自身是鞅
  + **Ito 积分**关于布朗运动是鞅

+ **二阶矩过程**
  + 若对 $\forall~ t\in T,~E|X_t|^2 < \infty$, 则称 $X$ 为**二阶矩过程**
  + **均方分析**中针对的均为二阶矩过程

+ **更新过程**
  + 设 $\{X_k:k\geqslant1\}$ 为**独立同分布**的正的随机变量序列, 对 $t>0$, 令
    $$
      S_0=0, S_n=\sum_{k=1}^nX_k
    $$
    并定义
    $$
      N_t=\max\{n:n\geqslant0,S_n\leqslant t\}
    $$
    称 $\{N_t:t\geqslant0\}$ 为**更新过程**
  + 更新过程可以解释为 $[0,t]$ 内**更换零件的个数**, 或系统来的**信号数**, 或服务站来的**顾客数**等

+ **宽平稳过程或协方差平稳过程**
  + 若对 $\forall~\tau,t\in T$, $DX_t < \infty$, 且
    $$
      EX_t=m,~\mathrm{cov}(X_t,X_{t+\tau})=R(\tau)
    $$
    仅依赖 $\tau$, 则称 $X$ 为**宽平稳过程**, 即它的**协方差不随时间推移而改变**

+ **严平稳过程**
  + 若对 $\forall~ t_1,t_2,\cdots,t_n\in T$, 及 $h>0$,
    $$
      (X_{t_1},X_{t_2},\cdots,X_{t_n})\overset{d}{=}(X_{t_1+h},X_{t_2+h},\cdots,X_{t_n+h})
    $$
    则称该过程为**严平稳过程**
  + 严平稳过程的一切**有限维分布**对**时间的推移保持不变**
  + 特别地, $(X_t,X_s)$ 的二维分布**只依赖**于 $(t-s)$

## 参考文献

+ 林元烈. 应用随机过程[M]. 北京: 清华大学出版社, 2002.
+ 何声武. 随机过程导论[M]. 北京: 高等教育出版社, 1999.
+ Ross S M. Stochastic Processes[M]. John Wiley and Sons, 1993.
