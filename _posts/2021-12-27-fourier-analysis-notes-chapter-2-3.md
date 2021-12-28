---
title: Fourier Analysis Notes - Chapter 2 - 3
layout: post
category: math
---

My notes when reading _Fourier Analysis An Introduction_ by Stein and Shakarchi. This is for chapter 2 Basic Properties of Fourier Series, section 3 Convolutions.

<!--more-->
# 3 Convolutions
Given two $$2\pi$$-periodic integrable functions $$f$$ and $$g$$ on $$\mathbb{R}$$, we define their **convolution** $$f*g$$ on $$[-\pi,\pi]$$ by

$$
(f*g)(x)=\frac{1}{2\pi}\int_{-\pi}^\pi f(y)g(x-y)dy\mathrm{.}
$$

**Proposition 3.1** *Suppose that $$f$$, $$g$$, and $$h$$ are $$2\pi$$-periodic integrable functions. Then:*
1. $$f*(g+h)=f*g+f*h$$.
2. $$(cf)*g=c(f*g)=f*(cg)$$ for any $$c\in\mathbb{C}$$.
3. $$f*g=g*f$$.
4. $$(f*g)*h=f*(g*h)$$.
5. $$f*g$$ is continuous.
6. $$\hat{f*g}(n)=\hat{f}(n)\hat{g}(n)$$[^1].

**Lemmar 3.2** *Suppose $$f$$ is integrable on the circle and bounded by $$B$$. Then there exists a sequence $$\{f_k\}^\infty_{k=1}$$ of continuous functions on the circle so that*

$$
\sup_{x\in[-\pi,\pi]}\lvert f_k (x)\rvert\leq B\quad\mathrm{for\:all}\:k=1,2,\dots\mathrm{,}
$$

and

$$
\int_{-\pi}^\pi \lvert f(x)-f_k (x)\rvert dx\to 0\quad as\: k\to\infty\mathrm{.}
$$

## Footnotes
[^1]: For some reason MathJax doesn't render the hat symbol over the whole $$f*g$$ part. This proposition means the Fourier series of the convolution of $$f$$ and $$g$$ equals to the product of the Fourier series of $$f$$ and $$g$$.
