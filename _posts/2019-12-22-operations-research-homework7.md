---
layout: post
title:  "Operations Research Homework 7"
date:   2019-12-22
categories: operations-research
tags: operations-research homework
author: Jingxuan Yang
---

* content
{:toc}


## Introduction


This is operations research homework 7, [original repo link](https://github.com/JingXuan-Yang/Operations-Research-Solutions/blob/master/Homework7). Corresponding textbook: Introduction to Operations Research, 10th edition, Frederick S. Hillier & Gerald J. Lieberman. The style used is Tsinghua coursework.




## Main file

```latex
% !Mode:: "TeX:UTF-8"
% !TEX program  = pdflatex
\documentclass[a4paper]{article}

% import settings, modify the number of homework in this file
\input{settings.tex}

\begin{document}
\courseheader
\name{JingXuan Yang, SZ160310217}

\begin{enumerate}
  \setlength{\itemsep}{3\parskip}

% first exercise
  \item Warren Buffy is an enormously wealthy investor who has built his fortune through his legendary investing acumen. He currently has been offered three major investments and he would like to choose one. The first one is a conservative investment that would perform very well in an improving economy and only suffer a small loss in a worsening economy. The second is a speculative investment that would perform extremely well in an improving economy but would do very badly in a worsening economy. The third is a countercyclical investment that would lose some money in an improving economy but would perform well in a worsening economy.
  
\hspace*{4ex}Warren believes that there are three possible scenarios over the lives of these potential investments: (1) an improving economy, (2) a stable economy, and (3) a worsening economy. He is pessimistic about where the economy is headed, and so has assigned prior probabilities of 0.1, 0.5, and 0.4, respectively, to these three scenarios. He also estimates that his profits under these respective scenarios are those given by the following table:
  \begin{table}[h]
  	\centering
  	\begin{tabular}{cccc}
  		\toprule[1.5pt]
  		&\multicolumn{3}{c}{Possible Scenarios}\\
  		\cmidrule{2-4}
  		Investment&Improving Economy&Stable Economy&Worsening Economy\\
  		\midrule
		Conservative&\$30 million&\$5 million&$-$\$10 million\\
		Speculative&\$40 million&\$10 million&$-$\$30 million\\
		Countercyclical&$-$\$10 million&0&\$15 million\\
		\midrule
		Prior probability&0.1&0.5&0.4\\
  		\bottomrule[1.5pt]
  	\end{tabular}
  \end{table}
  
  \hspace*{4ex}Which investment should Warren make under each of the following criteria?
  \begin{enumerate}
\item Maximin payoff criterion.
\begin{solution}
The application of maximin payoff criterion is shown in Tab.\ref{tabmpc}. Since this criterion requires to choose the maximum of the minimum payoffs, Warren should choose conservative investment or countercyclical investment.
\begin{table}[h]
  	\centering
  	\caption{Maximin payoff criterion to Warren Buffy problem}
  	\label{tabmpc}
  	\begin{tabular}{ccccc}
  		\toprule[1.5pt]
  		&\multicolumn{3}{c}{Possible Scenarios}&\\
  		\cmidrule{2-4}
  		Investment&Improving&Stable&Worsening&Minimum\\
  		\midrule
		Conservative&\$30 &\$5 &$-$\$10&$-$\$10 \\
		Speculative&\$40 &\$10 &$-$\$30&$-$\$30 \\
		Countercyclical&$-$\$10 &0&\$15&$-$\$10 \\
		\midrule
		Prior probability&0.1&0.5&0.4&\\
  		\bottomrule[1.5pt]
  	\end{tabular}
  \end{table}
\end{solution}

\item Maximum likelihood criterion.
\begin{solution}

	Since this criterion requires to choose the maximum payoff of decision alternatives with the largest prior probability, Warren should choose speculative investment.

\end{solution}

\item Bayes' decision rule.
\begin{solution}
First calculate the expected value of payoff for conservative, speculative and countercyclical investments, respectively.
\begin{equation*}\left\{
\begin{aligned}
E[\text{Payoff(Conservative)}]&=30\times0.1+5\times0.5-10\times0.4=1.5\\
E[\text{Payoff(Speculative)}]&=40\times0.1+10\times0.5-30\times0.4=-3\\
E[\text{Payoff(Countercyclical)}]&=-10\times0.1+0\times0.5+15\times0.4=5\\	
\end{aligned}\right.
\end{equation*}
Therefore,
$$
E[\text{Payoff(Countercyclical)}]>E[\text{Payoff(Conservative)}]>E[\text{Payoff(Speculative)}]
$$
By Bayes' decision rule, Warren should choose countercyclical investment.
\end{solution}
\end{enumerate}

\item Consider two weighted coins. Coin 1 has a probability of 0.3 of turning up heads, and coin 2 has a probability of 0.6 of turning up heads. A coin is tossed once; the probability that coin 1 is tossed is 0.6, and the probability that coin 2 is tossed is 0.4. The decision maker uses Bayes' decision rule to decide which coin is tossed. The payoff table is as follows:
\begin{table}[h]
  	\centering
  	\begin{tabular}{ccc}
  		\toprule[1.5pt]
  		&\multicolumn{2}{c}{State of Nature}\\
  		\cmidrule{2-3}  		
  		Alternative &Coin 1 Tossed&Coin 2 Tossed\\
  		\midrule
		Say coin 1 tossed&0&$-1$\\
		Say coin 2 tossed&$-1$&0\\
		\midrule
		Prior probability&0.6&0.4\\
  		\bottomrule[1.5pt]
  	\end{tabular}
  \end{table}
  \begin{enumerate}
\item What is the optimal alternative before the coin is tossed?
\begin{solution}

First calculate the expected value of payoff for ``Say coin 1 tossed'' and ``Say coin 2 tossed'', respectively.
\begin{equation*}\left\{
\begin{aligned}
E[\text{Payoff(Say coin 1 tossed)}]&=0\times0.6-1\times0.4=-0.4\\
E[\text{Payoff(Say coin 2 tossed)}]&=-1\times0.6+0\times0.4=-0.6\\
\end{aligned}\right.
\end{equation*}
Therefore,
$$
E[\text{Payoff(Say coin 1 tossed)}]>E[\text{Payoff(Say coin 2 tossed)}].
$$
By Bayes' decision rule, the optimal alternative is to say coin 1 tossed.
\end{solution}

\item What is the optimal alternative after the coin is tossed if the outcome is heads? If it is tails?
\begin{solution}

The probability tree diagram is shown in Fig.\ref{HW7}.
\begin{figure}[!h]
\centering
\caption{Probability tree diagram}
\label{HW7}
\includegraphics[width=.8\textwidth]{HW7}
\end{figure}

\hspace*{4ex} If the outcome is heads, the new payoff table is shown in Tab.\ref{tabheads}.
\begin{table}[h]
  	\centering
  	\caption{Payoff table if the outcome is heads}
  	\label{tabheads}
  	\begin{tabular}{ccc}
  		\toprule[1.5pt]
  		&\multicolumn{2}{c}{State of Nature}\\
  		\cmidrule{2-3}  		
  		Alternative &Coin 1 Tossed&Coin 2 Tossed\\
  		\midrule
		Say coin 1 tossed&0&$-1$\\
		Say coin 2 tossed&$-1$&0\\
		\midrule
		Prior probability&$\frac{3}{7}$&$\frac{4}{7}$\\
  		\bottomrule[1.5pt]
  	\end{tabular}
  \end{table}
  
  \hspace{4ex} The expected value of payoff for ``Say coin 1 tossed'' and ``Say coin 2 tossed'', respectively, is
\begin{equation*}\left\{
\begin{aligned}
E[\text{Payoff(Say coin 1 tossed)}]&=0\times\frac{3}{7}-1\times\frac{4}{7}=-\frac{4}{7}\\
E[\text{Payoff(Say coin 2 tossed)}]&=-1\times\frac{3}{7}+0\times\frac{4}{7}=-\frac{3}{7}\\
\end{aligned}\right.
\end{equation*}

Since
$$
E[\text{Payoff(Say coin 2 tossed)}]>E[\text{Payoff(Say coin 1 tossed)}],
$$
by Bayes' decision rule, the optimal alternative is to say coin 2 tossed.

\vspace{0.5em}
\hspace*{4ex} If the outcome is tails, the new payoff table is shown in Tab.\ref{tabtails}.
\begin{table}[H]
  	\centering
  	\caption{Payoff table if the outcome is tails}
  	\label{tabtails}
  	\begin{tabular}{ccc}
  		\toprule[1.5pt]
  		&\multicolumn{2}{c}{State of Nature}\\
  		\cmidrule{2-3}  		
  		Alternative &Coin 1 Tossed&Coin 2 Tossed\\
  		\midrule
		Say coin 1 tossed&0&$-1$\\
		Say coin 2 tossed&$-1$&0\\
		\midrule
		Prior probability&$\frac{21}{29}$&$\frac{8}{29}$\\
  		\bottomrule[1.5pt]
  	\end{tabular}
  \end{table}
  
  The expected value of payoff for ``Say coin 1 tossed'' and ``Say coin 2 tossed'', respectively, is
\begin{equation*}\left\{
\begin{aligned}
E[\text{Payoff(Say coin 1 tossed)}]&=0\times\frac{21}{29}-1\times\frac{8}{29}=-\frac{8}{29}\\
E[\text{Payoff(Say coin 2 tossed)}]&=-1\times\frac{21}{29}+0\times\frac{8}{29}=-\frac{21}{29}\\
\end{aligned}\right.
\end{equation*}

Since
$$
E[\text{Payoff(Say coin 1 tossed)}]>E[\text{Payoff(Say coin 2 tossed)}],
$$
by Bayes' decision rule, the optimal alternative is to say coin 1 tossed.
\end{solution}
\end{enumerate}

% w.r.t the external
\end{enumerate}
%  The source code to plot Figure \ref{fig:1} could be found in Appendix \ref{sec:a:code}. Here are the core codes:
%  \lstinputlisting[firstline=6,lastline=7, firstnumber=6]{matlabscript.m}

%  \newpage
%  \appendix
%  \section{Source code}
%  \label{sec:a:code}
%  % \lstlistoflistings
%  Source code for plotting Figure \ref{fig:1} is shown as follows.
%  \lstinputlisting[caption=FigurePlot]{matlabscript.m}
  
\end{document}
```

## Setting file

Associated settings file is:

```latex

\usepackage[T1]{fontenc}
\usepackage{amsmath, amssymb, amsthm}
% amsmath: equation*, amssymb: mathbb, amsthm: proof
\usepackage{moreenum}
\usepackage{multirow}
\usepackage{mathtools}
\usepackage{float}
\usepackage{url}
\usepackage{graphicx}
\usepackage{subcaption}
\usepackage{booktabs} 
\usepackage[mathcal]{eucal}
\usepackage{dsfont}
\usepackage{geometry}
\usepackage{diagbox}
\geometry{left=30mm,right=30mm,	top=42mm, bottom=33mm}

\usepackage[numbered,framed]{matlab-prettifier}
\lstset{
	style              = Matlab-editor,
	captionpos         =b,
	basicstyle         = \mlttfamily,
	escapechar         = ",
	mlshowsectionrules = true,
}

% set the homework count number
\usepackage[thehwcnt = 7]{iidef}

\newcommand\dif{\text{d}}
\newcommand\no{\noindent}
\newcommand\dis{\displaystyle}
\newcommand\ls{\leqslant}
\newcommand\gs{\geqslant}

\newcommand\limit{\dis\lim\limits}
\newcommand\limn{\dis\lim\limits_{n\to\infty}}
\newcommand\limxz{\dis\lim\limits_{x\to0}}
\newcommand\limxi{\dis\lim\limits_{x\to\infty}}
\newcommand\limxpi{\dis\lim\limits_{x\to+\infty}}
\newcommand\limxni{\dis\lim\limits_{x\to-\infty}}
\newcommand\limtpi{\dis\lim\limits_{t\to+\infty}}
\newcommand\limtni{\dis\lim\limits_{t\to-\infty}}

\newcommand\sumn{\dis\sum\limits_{n=1}^{\infty}}
\newcommand\sumnz{\dis\sum\limits_{n=0}^{\infty}}

\newcommand\sumi{\dis\sum\limits_{i=1}^{\infty}}
\newcommand\sumiz{\dis\sum\limits_{i=0}^{\infty}}
\newcommand\sumin{\dis\sum\limits_{i=1}^{n}}
\newcommand\sumizn{\dis\sum\limits_{i=0}^{n}}

\newcommand\sumk{\dis\sum\limits_{k=1}^{\infty}}
\newcommand\sumkz{\dis\sum\limits_{k=0}^{\infty}}
\newcommand\sumkn{\dis\sum\limits_{k=0}^n}
\newcommand\sumkfn{\dis\sum\limits_{k=1}^n}

\newcommand\pzx{\dis\frac{\partial z}{\partial x}}
\newcommand\pzy{\dis\frac{\partial z}{\partial y}}

\newcommand\pfx{\dis\frac{\partial f}{\partial x}}
\newcommand\pfy{\dis\frac{\partial f}{\partial y}}

\newcommand\pzxx{\dis\frac{\partial^2 z}{\partial x^2}}
\newcommand\pzxy{\dis\frac{\partial^2 z}{\partial x\partial y}}
\newcommand\pzyx{\dis\frac{\partial^2 z}{\partial y\partial x}}
\newcommand\pzyy{\dis\frac{\partial^2 z}{\partial y^2}}

\newcommand\pfxx{\dis\frac{\partial^2 f}{\partial x^2}}
\newcommand\pfxy{\dis\frac{\partial^2 f}{\partial x\partial y}}
\newcommand\pfyx{\dis\frac{\partial^2 f}{\partial y\partial x}}
\newcommand\pfyy{\dis\frac{\partial^2 f}{\partial y^2}}

\newcommand\intzi{\dis\int_{0}^{+\infty}}
\newcommand\intd{\dis\int}
\newcommand\intab{\dis\int_a^b}

\newcommand{\degree}{^\circ}

\newcommand\ma{\mathcal{A}}
\newcommand\mc{\mathbf{c}}
\newcommand\me{\mathcal{E}}
\newcommand\mg{\mathcal{g}}

\newcommand\mcc{\mathbb{C}}
\newcommand\mrr{\mathbb{R}}
\newcommand\mzz{\mathbb{Z}}

\newcommand\mx{\bf{x}}
\newcommand\mX{\bf{X}}
\newcommand\my{\mathbf{y}}
\newcommand\mY{\bf{Y}}
\newcommand\mS{\mathbf{S}}
\newcommand\mb{\mathbf{b}}
\newcommand\mz{\mathbf{z}}
\newcommand\mA{\mathbf{A}}
%%=============================================

%%=====定义新数学符号===============================
\DeclareMathOperator{\sgn}{sgn}
\DeclareMathOperator{\arccot}{arccot}
\DeclareMathOperator{\arccosh}{arccosh}
\DeclareMathOperator{\arcsinh}{arcsinh}
\DeclareMathOperator{\arctanh}{arctanh}
\DeclareMathOperator{\arccoth}{arccoth}
\DeclareMathOperator{\grad}{\bf{grad}}
%\DeclareMathOperator{\argmax}{argmax}
%\DeclareMathOperator{\argmin}{argmin}
%\DeclareMathOperator{\diag}{diag}
\DeclareMathOperator{\csign}{csign}
%===============================================

\thecourseinstitute{Harbin Institute of Technology, ShenZhen}
\thecoursename{Operations Research}
\theterm{Fall 2019}
\hwname{Homework}
```
