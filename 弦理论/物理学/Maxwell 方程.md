---
aliases: [Maxwell's Equations]
english_name: Maxwell's Equations
tags: [物理学, 电磁学, 弦理论先修]
prerequisites:
  - "[[弦理论/物理学/电场]]"
  - "[[弦理论/数学/散度]]"
  - "[[弦理论/数学/旋度]]"
  - "[[弦理论/数学/Stokes 定理]]"
used_by:
  - "[[弦理论/物理学/规范对称性]]"
  - "[[弦理论/物理学/经典场论]]"
  - "[[弦理论/物理学/Maxwell 场量子化]]"
evidence_status: 教材事实
---

# Maxwell 方程（Maxwell's Equations）

## 一句话解释

Maxwell 方程用四条局部方程统一描述电荷、电流、电场和磁场怎样相互产生并传播。

## 为什么要学它

电磁学是最重要的经典场论和规范理论范例。它展示了局部场、势、对称性、守恒流和波如何统一，也是理解 Yang–Mills 理论的起点。

## 四条微分方程

在含电荷和电流源、采用真空介电常数与真空磁导率的 SI 单位制中：

$$
\nabla\cdot\mathbf E=\frac{\rho}{\varepsilon_0},
$$

$$
\nabla\cdot\mathbf B=0,
$$

$$
\nabla\times\mathbf E=-
\frac{\partial\mathbf B}{\partial t},
$$

$$
\nabla\times\mathbf B=
\mu_0\mathbf J+
\mu_0\varepsilon_0
\frac{\partial\mathbf E}{\partial t}.
$$

符号含义：

- $\mathbf E$：电场；
- $\mathbf B$：磁感应强度，也常简称磁场；
- $\rho$：电荷密度；
- $\mathbf J$：电流密度；
- $\nabla\cdot$：散度，衡量场从一点向外流出的程度；
- $\nabla\times$：旋度，衡量场在一点附近的环绕趋势；
- $\varepsilon_0$：真空介电常数；
- $\mu_0$：真空磁导率；
- $t$：时间；
- $\partial/\partial t$：对时间的偏导数。

这组写法允许 $\rho$ 和 $\mathbf J$ 非零，因此不是无源真空方程。只有在真空无源区域额外令 $\rho=0$、$\mathbf J=0$。若介质被宏观极化或磁化，还可改用 $\mathbf D$、$\mathbf H$ 等介质形式，不能把介质响应直接忽略。

## Gauss 电定律

$$
\nabla\cdot\mathbf E=\rho/\varepsilon_0
$$

表示电荷是电场的源汇。积分形式为：

$$
\oint_{\partial V}\mathbf E\cdot d\mathbf S
=\frac{Q_{\rm inside}}{\varepsilon_0}.
$$

闭合面总电通量由内部总电荷决定。

## Gauss 磁定律

$$
\nabla\cdot\mathbf B=0
$$

表示经典 Maxwell 理论中没有观测到孤立磁单极子，磁场线没有普通源点，通常形成闭环或延伸到无穷远。

这不是逻辑上证明磁单极子绝不可能存在；它是标准无磁荷 Maxwell 方程的内容。

## Faraday 感应定律

变化的磁场产生环形电场：

$$
\oint_C\mathbf E\cdot d\mathbf r
=-\frac d{dt}
\int_S\mathbf B\cdot d\mathbf S.
$$

负号体现 Lenz 定律：感应效应反抗磁通变化。

## Ampère–Maxwell 定律

磁场旋度由电流和变化电场产生。Maxwell 增加的位移电流项

$$
\mu_0\varepsilon_0\partial_t\mathbf E
$$

保证电荷连续性并允许真空电磁波。

## 电荷守恒

对 Ampère–Maxwell 方程取散度，利用 $\nabla\cdot(\nabla\times\mathbf B)=0$，得到：

$$
\frac{\partial\rho}{\partial t}
+
\nabla\cdot\mathbf J=0.
$$

这是局部电荷守恒方程。

## 真空电磁波

在 $\rho=0$、$\mathbf J=0$ 区域，方程推出：

$$
\nabla^2\mathbf E-
\frac1{c^2}\partial_t^2\mathbf E=0,
$$

$$
\nabla^2\mathbf B-
\frac1{c^2}\partial_t^2\mathbf B=0,
$$

其中：

$$
c=\frac1{\sqrt{\mu_0\varepsilon_0}}.
$$

这与真空光速一致，说明光是电磁波。

## 电磁势

由 $\nabla\cdot\mathbf B=0$，局部可写：

$$
\mathbf B=\nabla\times\mathbf A.
$$

再写：

$$
\mathbf E=-\nabla V-
\frac{\partial\mathbf A}{\partial t}.
$$

$V$ 是标量势，$\mathbf A$ 是向量势。不同的势可能产生相同电磁场，引出规范对称性。

## 相对论形式预告

把 $\mathbf E,\mathbf B$ 组合成反对称场强张量 $F_{\mu\nu}$，Maxwell 方程可写成 Lorentz 协变形式：

$$
\partial_\mu F^{\mu\nu}=\mu_0J^\nu,
$$

以及 Bianchi 恒等式。该形式表明电场和磁场是同一相对论场在不同观察者下的分量。

## 常见误区

1. **四条方程彼此完全独立。** 它们还与电荷守恒和势的结构相互约束。
2. **$\nabla\cdot\mathbf B=0$ 已证明磁单极子逻辑上不可能。** 错。
3. **变化电场不产生磁场。** 位移电流项正描述这一点。
4. **势是唯一的。** 错，存在规范冗余。
5. **光速是人为塞进 Maxwell 方程的。** 它由 $\mu_0,\varepsilon_0$ 决定的波速自然出现。

## 练习

1. 哪条方程说明电荷是电场源？
2. 哪条方程描述电磁感应？
3. 位移电流项为何重要？
4. 真空电磁波速度是多少？
5. 为什么可以用向量势表示磁场？

## 答案与提示

1. $\nabla\cdot\mathbf E=\rho/\varepsilon_0$。
2. Faraday 定律。
3. 它保证电荷守恒并允许变化电场产生磁场。
4. $1/\sqrt{\mu_0\varepsilon_0}$。
5. 无散磁场在适当区域局部可写成某向量场的旋度。

## 与其他概念的关系

- 方程使用 [[弦理论/数学/散度]]、[[弦理论/数学/旋度]] 和 Stokes 定理；
- 电磁势引出 [[弦理论/物理学/规范对称性]]；
- 相对论形式使用 Minkowski 时空与张量；
- Maxwell 场是量子场论中最基本的规范场。

## 参考资料

- [MIT OCW 8.02, Electricity and Magnetism](https://ocw.mit.edu/courses/8-02-physics-ii-electricity-and-magnetism-spring-2019/)
- [OpenStax, University Physics Volume 2](https://openstax.org/details/books/university-physics-volume-2)
- David J. Griffiths, *Introduction to Electrodynamics*, 4th ed.
