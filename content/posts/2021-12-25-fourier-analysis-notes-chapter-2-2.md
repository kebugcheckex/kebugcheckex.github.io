---
title: Fourier Analysis Notes - Chapter 2 - 2
layout: post
category: math
math: true # enable MathJax
tags:
  - fourier-analysis
  - mathematics
---

My notes when reading _Fourier Analysis An Introduction_ by Stein and Shakarchi. This is for chapter 2 Basic Properties of Fourier Series, section 2 Uniqueness of Fourier series.

<!--more-->

# 2 Uniqueness of Fourier series

**Thereom 2.1** _Supporse that $$f$$ is an integrable function on the circle with $$\hat{f}(n)=0$$ for all $$n\in\mathbb{Z}$$. Then $$f(\theta_0)=0$$ whenever $$f$$ is continuous at the point $$\theta_0$$._

**Corollary 2.2** _If $$f$$ is continuous on the circle and $$\hat{f}(n)=0$$ for all $$n\in\mathbb{Z}$$, then $$f=0$$._

**Corollary 2.3** _Suppose that $$f$$ is a continuous function on the circle and that the Fourier series of $$f$$ is absolutely convergent, $$\sum_{n=-\infty}^\infty \lvert\hat{f}(n)\rvert <\infty$$. Then, the Fourier series converges uniformly to $$f$$, that is_

$$
\lim_{N\to\infty} S_N(f)(\theta)=f(\theta)\quad\mathit{uniformly\:in}\:\theta\mathit{.}
$$

**Corollary 2.4** _Suppose that $$f$$ is a twice continuously differentiable function on the circle. Then_

$$
\hat{f}(n)=O(1/\lvert n\rvert ^2)\quad as \:\lvert n\rvert\to\infty
$$

_so that the Fourier series of $$f$$ converges absolutely and uniformly to $$f$$._[^1]

**Hölder Condition**: the Fourier series of $$f$$ converges absolutely (and hence uniformly to $$f$$) if $$f$$ satiesfies a **Hölder Condition** of order $$\alpha$$, with $$\alpha >1/2$$, that is,

$$
\sup_\theta\lvert f(\theta +t)-f(\theta)\rvert\leq A\lvert t\rvert^\alpha\quad\mathrm{for\:all}\:t\mathrm{.}
$$

### Footnotes

[^1]: $$O$$ notation mean upperbound (not rigorously).
