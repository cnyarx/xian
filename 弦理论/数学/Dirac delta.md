---
aliases: [Dirac Delta, Delta Distribution]
english_name: Dirac Delta Distribution
tags: [数学, 分布理论, 弦理论先修]
prerequisites:
  - "[[弦理论/数学/积分]]"
  - "[[弦理论/数学/Fourier 变换]]"
used_by:
  - "[[弦理论/数学/Green 函数]]"
  - "[[弦理论/物理学/传播子]]"
  - "[[弦理论/物理学/对易关系]]"
evidence_status: 教材事实
---

# 狄拉克 delta 分布（Dirac Delta Distribution）

## 一句话解释

Dirac delta 不是普通函数，而是一种分布：它通过积分从连续函数中精确挑出某一点的值。

## 为什么要学它

点电荷、瞬时冲击、平面波正交、连续谱归一化和 Green 函数都需要 delta。理论物理中若把它当普通无限高函数，会产生许多错误。

## 抽样性质

一维 delta 写作 $\delta(x-a)$，由作用在测试函数上的规则定义：

$$
\int_{-\infty}^{\infty}
\delta(x-a)f(x)\,dx=f(a).
$$

它只“读取”$x=a$ 处的函数值。

若积分区间包含 $a$：

$$
\int\delta(x-a)\,dx=1.
$$

若不包含 $a$，积分为零；端点情形取决于采用的约定和正则化。

## 不是普通函数

常用直观说法是：

$$
\delta(x)=0\quad(x\ne0),
$$

且总积分为 $1$。但不存在一个普通函数能同时满足这些性质。严格对象是线性泛函或分布，它的意义由积分作用决定。

## 作为窄峰极限

可以用一族越来越窄、面积始终为 $1$ 的 Gaussian 近似：

$$
\delta_\varepsilon(x)=
\frac1{\sqrt{2\pi}\varepsilon}
\exp\left(-\frac{x^2}{2\varepsilon^2}\right).
$$

当 $\varepsilon\to0$ 时，它不按普通逐点函数极限变成 delta，而是在积分作用于良好测试函数时趋近 delta。

## 缩放性质

对非零常数 $a$：

$$
\delta(ax)=\frac1{|a|}\delta(x).
$$

绝对值不能遗漏，因为变量缩放同时改变积分测度。

更一般地，若 $g(x_i)=0$ 且零点简单：

$$
\delta(g(x))=
\sum_i\frac{\delta(x-x_i)}{|g'(x_i)|}.
$$

## delta 的导数

分布导数通过分部积分定义：

$$
\int\delta'(x-a)f(x)\,dx=-f'(a).
$$

负号来自把导数从 delta 移到测试函数上。

## Fourier 表示

在一种常用约定下：

$$
\delta(x)=
\int_{-\infty}^{\infty}
\frac{dk}{2\pi}e^{ikx}.
$$

更一般地：

$$
\int_{-\infty}^{\infty}e^{i(k-k')x}\,dx
=2\pi\delta(k-k').
$$

这表达连续平面波的 delta 正交性。

## 多维 delta

$D$ 维中：

$$
\delta^{(D)}(\mathbf x-
\mathbf a)
$$

满足：

$$
\int d^Dx\,
\delta^{(D)}(\mathbf x-
\mathbf a)f(\mathbf x)
=f(\mathbf a).
$$

Cartesian 坐标中它可写成每个方向 delta 的乘积。

## 点源

位于原点、总电荷为 $q$ 的理想点电荷密度写成：

$$
\rho(\mathbf x)=q\delta^{(3)}(\mathbf x).
$$

积分整个空间得到总电荷 $q$。delta 把有限总量集中到理想化的零体积位置。

## 量纲

因为：

$$
\int dx\,\delta(x)=1,
$$

所以一维 $\delta(x)$ 的量纲是长度的倒数。$D$ 维 delta 的量纲是 $L^{-D}$。

## 常见误区

1. **$\delta(0)=\infty$ 是普通数值等式。** 错，这只是危险的直观简写。
2. **delta 是处处为零的普通函数。** 若是普通函数，积分也会为零。
3. **$\delta(ax)=\delta(x)$。** 错，要除以 $|a|$。
4. **delta 没有量纲。** 它的量纲抵消积分测度。
5. **所有含 delta 的操作都可按普通函数代数处理。** 错，必须在分布与测试函数意义下检验。

## 练习

1. 计算 $\int\delta(x-2)(x^2+1)dx$，区间覆盖 $2$。
2. $\delta(3x)$ 等于什么？
3. $\int\delta'(x)f(x)dx$ 等于什么？
4. 三维点质量 $M$ 的密度如何写？
5. 为什么 delta 的单位是倒长度？

## 答案与提示

1. $5$。
2. $\delta(x)/3$。
3. $-f'(0)$。
4. $M\delta^{(3)}(\mathbf x)$。
5. 它与 $dx$ 相乘积分得到无量纲的 $1$。

## 与其他概念的关系

- delta 的 Fourier 表示依赖 [[弦理论/数学/Fourier 变换]]；
- [[弦理论/数学/Green 函数]] 是微分算符对 delta 点源的响应；
- [[弦理论/物理学/传播子]] 可视作量子场论版本的 Green 函数；
- 连续谱的正交归一使用 delta 而非 Kronecker delta。

## 参考资料

- [MIT OCW 18.03SC, Delta Functions](https://ocw.mit.edu/courses/18-03sc-differential-equations-fall-2011/)
- M. J. Lighthill, *Introduction to Fourier Analysis and Generalised Functions*
- Laurent Schwartz, *Théorie des distributions*
