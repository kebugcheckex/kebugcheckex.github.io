---
title: Fourier Analysis Notes - Chapter 2 - 1
layout: post
category: math
tags:
- fourier-analysis
- mathematics
---

My notes when reading _Fourier Analysis An Introduction_ by Stein and Shakarchi. This is for chapter 2 Basic Properties of Fourier Series, section 1 Examples and formulation of the problem.

<!--more-->

# 1 Examples and formulation of the problem

## Riemann Integrable

A real-valued function $$f$$ defined on [0, L] is **Riemann integrable** if it is*bounded*, and if for every $$\epsilon >0$$, there is a subdivision $$0=x_0<x_1<\cdots <x_{N-1}<x_N=L$$ of the interval $$[0,L]$$, so that if $$\mathcal{U}$$ and $$\mathcal{L}$$ are, respectively, the upper and lower sum of $$f$$ for this subdivision, namely

$$
\mathcal{U}=\sum_{j=1}^N[\sup_{x_{j-1}\leq x\leq x_j} f(x)](x_j-x_{j-1})
$$

and

$$
\mathcal{L}=\sum_{j=1}^N[\inf_{x_{j-1}\leq x\leq x_j} f(x)](x_j-x_{j-1})
$$

then we have $$\mathcal{U}-\mathcal{L}<\epsilon$$.

## 1.1 Main definitions and some examples

## Fourier Coefficients

If $$f$$ is an integrable function given on an interval $$[a,b]$$ of length $$L$$ (that is, $$b-a=L$$), then the n-th **Fourier coeffcient** of $$f$$ is defined as

$$
\hat{f}(n)=\frac{1}{L}\int_a^bf(x)e^{-2\pi inx/L}dx\mathrm{,}\quad n\in\mathbb{Z}
$$

The **Fourier series** of $$f$$ is given formally by

$$
\sum_{n=-\infty}^{\infty}\hat{f}(n)e^{2\pi inx/L}\mathrm{.}
$$

## Dirichlet kernel

The trigonometric polynomial defined for $$x\in [-\pi,\pi]$$ by

$$
D_N(x)=\sum_{n=-N}^N e^{inx}
$$

is called the _N-th_ **Dirichlet kernel**. Its Fourier coefficients $$a_n$$ have the property that $$a_n=1$$ if $$\lvert n\rvert\leq N$$ and $$a_n=0$$ otherwise.

## Poisson kernel

The function $$P_r(\theta)$$, called the **Poisson kernel**, is defined for $$\theta\in[-\pi,\pi]$$ and $$0\leq r<1$$ by the absolutely and uniformly convergent series

$$
P_r(\theta)=\sum_{n=-\infty}^\infty r^{\lvert n\rvert}e^{in\theta}\mathrm{.}
$$
