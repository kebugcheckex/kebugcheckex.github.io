---
title: 2023年高考全国甲卷理科数学
layout: post
category: math
math: true # enable MathJax
tags:
  - mathematics
---

本文简略探讨一下 2023 年高考全国甲卷理科数学的部分试题。

<!--more-->

## 第 20 题

设抛物线 $$C: y^2=2px\, (p>0)$$, 直线 $$x-2y+1=0$$ 与 $$C$$ 交于 $$A,B$$ 两点，且 $$\vert AB\vert =4\sqrt{15}$$.

1. 求 $$p$$ ;
2. 设 $$C$$ 的焦点为 $$F$$，$$M,N$$ 为 $$C$$ 上两点，$$\overline{MF}\cdot\overline{NF}=0$$，求 $$\triangle MNF$$ 的面积的最小值。

**解:**

1 . 联立抛物线与直线方程

$$
 \begin{cases}
   y^2=2px \\
   x-2y+1=0
 \end{cases}
$$

消去 $$x$$ 可求得

$$
y^2-4py+2p=0\qquad\qquad (1)
$$

另外，设 $$A, B$$ 分别为 $$(x_1, y_1)$$ 和 $$(x_2, y_2)$$，由 $$\vert AB\vert =4\sqrt{15}$$ 可得

$$
\sqrt{(x_1-x_2)^2+(y_1-y_2)^2}=4\sqrt{15}
$$

代入 $$x=2y-1$$ 整理后可得

$$
\vert y_1-y_2\vert =4\sqrt{15}
$$

注意到，$$y_1, y_2$$ 是上述方程(1)的两个实根。由一元二次方程求根公式可得 $$\vert y_1-y_2\vert =\sqrt{b^2-4ac}$$.

对比方程(1)，代入 $$a=1,b=-4p,c=2p$$ 可得 $$ \sqrt{16p^2-8p}=4\sqrt{15}$$.

由于 $$p>0$$, 解得 $$p=2$$.

2 . 由上可知， $$y^2=4x$$，此抛物线的焦点是 $$F(1, 0)$$.

设直线 $$MN$$ 的方程为 $$x=my+n$$，联立可得

$$
\begin{cases}
x=my+n \\
y^2=4x
\end{cases}
$$

消去 $$x$$ 解得

$$
y^2-4my-4n=0\qquad\qquad (2)
$$

设点 $$M,N$$ 的坐标分别为 $$(x_1,y_1)$$ 和 $$(x_2,y_2)$$. 由 $$\overline{MF}\cdot\overline{NF}=0$$ 可知，$$\overline{MF}$$ 与 $$\overline{NF}$$ 垂直，即 $$(x_1-1)(x_2-1)+y_1y_2=0$$. 代入直线方程

$$
\begin{align*}
(my_1+n-1)(my_2+n-1)+y_1y_2=0 \\
(m^2+1)y_1y_2+m(n-1)(y_1+y_2)+(n-1)^2=0
\end{align*}
$$

由于 $$y_1,y_2$$ 是方程(2)的两个根，由一元二次方程求根公式可以推得 $$y_1+y_2=4m,\, y_1y_2=-4n$$. 代入上式可得[^1]

$$
4(m^2+n)=(n-1)^2\qquad\qquad (3)
$$

设焦点 $$F$$ 到直线 $$MN$$ 的距离为 $$d$$，根据点到直线的距离公式可得

$$
d=\frac{\vert 1-n\vert}{\sqrt{1+m^2}}
$$

而直线 $$\vert MN\vert $$的长度为 $$\sqrt{(x_1-x_2)^2+(y_1-y_2)^2}=\sqrt{m^2-1}\vert y_1-y_2\vert$$.

<!-- 下面这行也许可以合并到82行 -->

由于 $$y_1,y_2$$ 是方程(2)的两个根，由一元二次方程求根公式可以推得 $$\vert y_1-y_2\vert =2\sqrt{m^2+n}$$. 所以 $$MN$$ 的长度 $$4\sqrt{(1+m^2)(m^2+n)}$$

从而 $$\triangle MNF$$ 的面积是

$$
\begin{align*}
S=\frac{1}{2}\frac{\vert 1-n\vert}{\sqrt{1+m^2}}\cdot 4\sqrt{(1+m^2)(m^2+n)} \\
S=2\vert 1-n\vert \sqrt{m^2+n}
\end{align*}
$$

代入等式(3)可得 $$S=(n-1)^2$$.

由等式(3)可得 $$4m^2=n^2-6n+1\geq 0$$, 故而 $$n\geq 3+2\sqrt{2}$$ 或 $$n\leq 3-2\sqrt{2}$$. 不难看出，当 $$n=3-2\sqrt{2}$$ 时 $$\triangle MNF$$ 的面积最小，为 $$12-8\sqrt{2}$$.

### 脚注

[^1]: 至此，计算三角形面积由两种不同的选择。由于 $$\triangle MNF$$ 是直角三角形，一种是用两条直角边的乘积来计算，另一种是以斜边为底边，用底乘以高来计算。如果选择了前者，计算的复杂程度将会大很多。
