---
aliases: [Field Euler-Lagrange Equation, Euler–Lagrange Field Equation]
english_name: Field Euler-Lagrange Equation
tags: [物理学, 经典场论, 变分法, 弦理论先修]
prerequisites:
  - "[[弦理论/物理学/经典场论]]"
  - "[[弦理论/数学/Euler-Lagrange 方程]]"
  - "[[弦理论/数学/变分法]]"
  - "[[弦理论/数学/偏导数]]"
  - "[[弦理论/数学/Stokes 定理]]"
used_by:
  - "[[弦理论/物理学/能动张量]]"
  - "[[弦理论/物理学/Klein-Gordon 方程]]"
  - "[[弦理论/物理学/Maxwell 作用量]]"
  - "[[弦理论/物理学/Polyakov 作用量]]"
evidence_status: 教材事实
---

# 场的 Euler-Lagrange 方程（Field Euler-Lagrange Equation）

## 一句话解释

场的 Euler–Lagrange 方程把“整个场配置使作用量驻定”翻译成每个时空点都必须满足的局部偏微分方程。

## 为什么要学它

经典场论、量子场论和弦理论通常先写作用量，再由变分得到运动方程。标量场方程、Maxwell 方程和弦坐标的二维波动方程，都可由同一个场变分公式推出。

## 从粒子方程到场方程

粒子坐标 $q(t)$ 只依赖一个独立变量 $t$。其 Euler–Lagrange 方程是：

$$
\frac{d}{dt}
\left(
\frac{\partial L}{\partial\dot q}
\right)
-
\frac{\partial L}{\partial q}=0.
$$

场 $\phi(x)$ 依赖多个时空坐标 $x^\mu$。因此：

- 普通坐标 $q$ 变成场值 $\phi$；
- 速度 $\dot q$ 变成各方向导数 $\partial_\mu\phi$；
- 时间全导数 $d/dt$ 变成各时空方向偏导数之和 $\partial_\mu$；
- Lagrangian $L$ 变成 Lagrangian 密度 $\mathcal L$。

这给出场方程的基本结构。

## 正式公式

若作用量只依赖场和场的一阶导数：

$$
S[\phi]=\int_\Omega d^Dx\,
\mathcal L\bigl(\phi^A,\partial_\mu\phi^A,x\bigr),
$$

则每个场分量 $\phi^A$ 满足：

$$
\frac{\partial\mathcal L}{\partial\phi^A}
-
\partial_\mu
\left[
\frac{\partial\mathcal L}
{\partial(\partial_\mu\phi^A)}
\right]=0.
$$

也常把两项反向排列：

$$
\partial_\mu
\left[
\frac{\partial\mathcal L}
{\partial(\partial_\mu\phi^A)}
\right]
-
\frac{\partial\mathcal L}{\partial\phi^A}=0.
$$

两种写法只差整体乘以 $-1$，内容相同。

## 公式中每个符号的意思

- $S[\phi]$：作用量泛函，输入整套场配置；
- $\Omega$：进行积分的时空区域；
- $D$：时空总维数；
- $d^Dx$：时空体积元；
- $\mathcal L$：Lagrangian 密度；
- $\phi^A$：第 $A$ 个场或场分量；
- $\partial_\mu\phi^A$：场沿第 $\mu$ 个时空方向的变化率；
- $A$：场种类或内部分量标签；
- $\mu$：时空方向标签，重复的 $\mu$ 要求和；
- $\partial\mathcal L/\partial\phi^A$：固定场导数后，$\mathcal L$ 对场值的偏导；
- $\partial\mathcal L/\partial(\partial_\mu\phi^A)$：把各个场导数暂时当成独立变量所求的偏导。

该公式适用于 $\mathcal L$ 只含场及其一阶导数的常见情形。若 Lagrangian 密度含二阶或更高阶导数，方程会增加更高阶项。

## 推导第一步：改变场

令场发生一个很小的允许变化：

$$
\phi^A(x)\to
\phi^A(x)+\varepsilon\eta^A(x),
$$

其中：

- $\varepsilon$ 是用来标记变化大小的小参数；
- $\eta^A(x)$ 是任意足够光滑的测试变化；
- 在固定边界条件下，$\eta^A$ 在区域边界 $\partial\Omega$ 上为零。

场的导数随之变化：

$$
\partial_\mu\phi^A
\to
\partial_\mu\phi^A+
\varepsilon\partial_\mu\eta^A.
$$

## 推导第二步：计算一阶变分

只保留 $\varepsilon$ 的一阶项：

$$
\delta S=
\int_\Omega d^Dx
\left[
\frac{\partial\mathcal L}{\partial\phi^A}
\eta^A
+
\frac{\partial\mathcal L}
{\partial(\partial_\mu\phi^A)}
\partial_\mu\eta^A
\right].
$$

第一项来自场值本身变化，第二项来自场导数变化。

这里对重复的 $A$ 和 $\mu$ 都求和。若只有一个标量场，可以暂时去掉 $A$。

## 推导第三步：多维分部积分

使用乘积法则：

$$
\partial_\mu
\left(
P^\mu\eta
\right)
=
(\partial_\mu P^\mu)\eta
+
P^\mu\partial_\mu\eta,
$$

其中暂记：

$$
P^\mu=
\frac{\partial\mathcal L}
{\partial(\partial_\mu\phi)}.
$$

所以：

$$
P^\mu\partial_\mu\eta
=
\partial_\mu(P^\mu\eta)
-
(\partial_\mu P^\mu)\eta.
$$

代回作用量变分：

$$
\delta S=
\int_\Omega d^Dx
\left[
\frac{\partial\mathcal L}{\partial\phi}
-
\partial_\mu
\left(
\frac{\partial\mathcal L}
{\partial(\partial_\mu\phi)}
\right)
\right]
\eta
+
\int_\Omega d^Dx\,
\partial_\mu(P^\mu\eta).
$$

最后一项是总散度。由多维 Stokes 定理，它可改写成边界积分。

## 推导第四步：处理边界项

总散度项变成：

$$
\int_\Omega d^Dx\,
\partial_\mu(P^\mu\eta)
=
\int_{\partial\Omega}d\Sigma_\mu\,P^\mu\eta.
$$

这里 $d\Sigma_\mu$ 是带方向的边界面积元。

若固定边界上的场值，则：

$$
\eta|_{\partial\Omega}=0,
$$

所以边界项消失。于是：

$$
\delta S=
\int_\Omega d^Dx
\left[
\frac{\partial\mathcal L}{\partial\phi}
-
\partial_\mu
\left(
\frac{\partial\mathcal L}
{\partial(\partial_\mu\phi)}
\right)
\right]
\eta.
$$

由于区域内部的 $\eta(x)$ 可以任意选择，要让所有允许变化都满足 $\delta S=0$，方括号必须在每一点为零。这就得到场的 Euler–Lagrange 方程。

## 为什么“积分为零”能推出“每点为零”

设方括号记为 $F(x)$。如果某处 $F(x)$ 明显不为零，就可以选择一个只集中在该小区域、并与 $F$ 同号的平滑变化 $\eta(x)$，使积分不为零。

因此：

$$
\int_\Omega F(x)\eta(x)d^Dx=0
$$

若对所有合适的 $\eta$ 都成立，就迫使 $F(x)=0$。这称为变分法基本引理。

它不是说“某一个函数的积分为零，所以函数处处为零”；关键条件是等式对所有允许测试变化都成立。

## 例一：自由实标量场

采用 mostly-minus 度量和自然单位：

$$
\mathcal L=
\frac12\partial_\mu\phi\partial^\mu\phi
-
\frac12m^2\phi^2.
$$

先计算：

$$
\frac{\partial\mathcal L}{\partial\phi}
=-m^2\phi.
$$

再计算导数项：

$$
\frac{\partial\mathcal L}
{\partial(\partial_\mu\phi)}
=
\partial^\mu\phi.
$$

代入场方程：

$$
-m^2\phi-
\partial_\mu\partial^\mu\phi=0.
$$

整体乘以 $-1$：

$$
(\Box+m^2)\phi=0,
\qquad
\Box=\partial_\mu\partial^\mu.
$$

这就是自由实标量场的 Klein–Gordon 方程。

## 例二：带势能的标量场

若：

$$
\mathcal L=
\frac12\partial_\mu\phi\partial^\mu\phi
-V(\phi),
$$

则：

$$
\frac{\partial\mathcal L}{\partial\phi}
=-V'(\phi),
\qquad
\frac{\partial\mathcal L}
{\partial(\partial_\mu\phi)}
=\partial^\mu\phi.
$$

因此：

$$
\Box\phi+V'(\phi)=0.
$$

若 $V(\phi)=m^2\phi^2/2$，便回到 Klein–Gordon 方程；若势能含 $\phi^4$，运动方程会变成非线性方程。

## 例三：连续弦的波动方程

一维连续弦的 Lagrangian 密度为：

$$
\mathcal L=
\frac{\mu}{2}(\partial_t y)^2
-
\frac{T}{2}(\partial_x y)^2.
$$

它不显含 $y$，所以：

$$
\frac{\partial\mathcal L}{\partial y}=0.
$$

另外：

$$
\frac{\partial\mathcal L}
{\partial(\partial_t y)}
=\mu\partial_t y,
\qquad
\frac{\partial\mathcal L}
{\partial(\partial_x y)}
=-T\partial_x y.
$$

场方程给出：

$$
\mu\partial_t^2y-T\partial_x^2y=0.
$$

除以 $\mu$：

$$
\partial_t^2y-
\frac{T}{\mu}\partial_x^2y=0.
$$

因此波速是 $\sqrt{T/\mu}$。

## 例四：平直背景中的弦坐标

在共形规范下，平直目标时空中的 Polyakov 作用量可写成：

$$
S=-\frac{T}{2}
\int d\tau\,d\sigma\,
\eta^{ab}
\partial_aX^\mu\partial_bX_\mu.
$$

对 $X^\mu$ 变分，得到：

$$
\partial_a\partial^aX^\mu=0.
$$

在常用世界面坐标约定下，它就是二维波动方程：

$$
(\partial_\tau^2-\partial_\sigma^2)X^\mu=0.
$$

这里：

- $\tau$：世界面时间坐标；
- $\sigma$：沿弦的空间坐标；
- $a=0,1$：世界面指标；
- $\mu=0,1,\ldots,D-1$：目标时空指标；
- $T$：弦张力。

这说明每个目标时空坐标 $X^\mu$ 从世界面角度看都满足二维自由场方程。但弦还必须满足由世界面度量变分产生的能动张量约束，因此不能只把它当成若干彼此无约束的普通标量场。

## 边界条件为什么重要

推导中被移除的边界项包含真实信息。对一维弦，空间边界项形如：

$$
\left.
T\,\partial_\sigma X_\mu\,
\delta X^\mu
\right|_{\text{边界}}.
$$

要让它为零，可以选择：

- 固定端点位置，即边界上 $\delta X^\mu=0$；
- 允许端点自由移动，但要求边界上 $\partial_\sigma X^\mu=0$；
- 对闭弦使用周期条件，使两端其实是同一点并彼此抵消。

这些选择分别通向 Dirichlet、Neumann 或周期边界条件。边界条件不是推导后的装饰，而是理论定义的一部分。

## 多个场与指标

若有多个场 $\phi^A$，每个 $A$ 都有一条方程：

$$
\frac{\partial\mathcal L}{\partial\phi^A}
-
\partial_\mu
\left[
\frac{\partial\mathcal L}
{\partial(\partial_\mu\phi^A)}
\right]=0.
$$

不同方程可能通过 $\mathcal L$ 中的耦合项联系。例如：

$$
\mathcal L_{\mathrm{int}}=-g\phi^2\chi^2
$$

会让 $\phi$ 的方程含 $\chi$，也让 $\chi$ 的方程含 $\phi$。

指标 $A$ 可以表示不同场，也可以表示同一向量场或内部空间中的不同分量。求偏导时必须明确哪些分量暂时视为独立变量。

## 适用条件与推广

本篇基本公式依赖以下条件：

1. 作用量是对局部 Lagrangian 密度的积分；
2. $\mathcal L$ 至多依赖场的一阶导数；
3. 场及允许变化足够光滑，或在更广义的弱解框架中合理解释；
4. 边界条件足以处理变分产生的边界项；
5. 各场分量及其现实约束被正确识别。

若 $\mathcal L$ 含高阶导数，需要高阶 Euler–Lagrange 方程。若存在规范冗余，部分场方程之间可能并不独立，还需规范固定或约束分析。

## 常见误区

1. **把粒子公式中的 $d/dt$ 机械换成一个 $\partial_t$ 就完成场论推广。** 场依赖所有时空坐标，必须对重复的 $\mu$ 求和。
2. **$\partial\mathcal L/\partial(\partial_\mu\phi)$ 是把分母真的当作一个分数。** 它表示把 $\partial_\mu\phi$ 当成变量，对它求偏导。
3. **边界项总能直接丢掉。** 只有边界条件、衰减条件或不同边界贡献的抵消能够使它消失。
4. **某个积分为零就说明被积函数处处为零。** 只有积分对所有允许测试变化都为零时，才可用变分法基本引理得出局部方程。
5. **Lagrangian 密度加一个总散度必然改变内部运动方程。** 在边界处理适当时，它只改变边界项，不改变内部 Euler–Lagrange 方程。
6. **弦坐标满足波动方程就已经包含全部弦动力学。** 还要处理边界条件、重新参数化、Weyl 对称性和能动张量约束。

## 练习

1. 写出单个场的一阶导数型 Euler–Lagrange 方程，并解释重复指标 $\mu$ 的含义。
2. 对 $\mathcal L=\frac12\partial_\mu\phi\partial^\mu\phi-\frac12m^2\phi^2$，逐步求出两个偏导并得到运动方程。
3. 为什么多维分部积分会产生边界积分？
4. 对 $\mathcal L=\frac12(\partial_t y)^2-\frac{c^2}{2}(\partial_x y)^2$ 推导波动方程。
5. 判断并解释：“只要在边界上不固定场值，变分原理就失效。”
6. 平直背景弦坐标的运动方程是什么？为什么它还不是完整的弦约束？

## 答案与提示

1. $\partial\mathcal L/\partial\phi-\partial_\mu[\partial\mathcal L/\partial(\partial_\mu\phi)]=0$；重复的 $\mu$ 表示对全部时空方向求和。
2. 第一项给 $-m^2\phi$，导数项给 $\partial^\mu\phi$，所以 $(\Box+m^2)\phi=0$。
3. 因为乘积法则把含 $\partial_\mu\eta$ 的项改写成总散度，而 Stokes 定理把总散度的体积分转成边界通量。
4. 结果是 $\partial_t^2y-c^2\partial_x^2y=0$。
5. 错。可以选择使边界项为零的自然边界条件，或保留边界项并由它推出边界运动方程。
6. $\partial_a\partial^aX^\mu=0$；此外还要满足边界条件和世界面能动张量约束。

## 与其他概念的关系

- 它是 [[弦理论/数学/Euler-Lagrange 方程]] 从有限自由度到连续场的推广；
- [[弦理论/物理学/经典场论]] 提供场和 Lagrangian 密度的语言；
- [[弦理论/数学/Stokes 定理]] 负责把总散度体积分转换为边界积分；
- [[弦理论/物理学/能动张量]] 可由时空平移对称性或度量变分得到；
- [[弦理论/物理学/Polyakov 作用量]] 对 $X^\mu$ 的变分产生二维波动方程，对世界面度量的变分产生约束。

## 参考资料

- [David Tong, Lectures on Quantum Field Theory](https://www.damtp.cam.ac.uk/user/tong/qft.html)
- Mark Srednicki, *Quantum Field Theory*, Cambridge University Press, 2007, Chapters 1–3.
- I. M. Gelfand and S. V. Fomin, *Calculus of Variations*.
- [David Tong, Lectures on String Theory](https://arxiv.org/abs/0908.0333)
- Barton Zwiebach, *A First Course in String Theory*, 2nd ed., Cambridge University Press, 2009.
