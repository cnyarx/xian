---
aliases: [Lagrangian]
english_name: Lagrangian
tags: [物理学, 分析力学, 弦理论先修]
prerequisites:
  - "[[弦理论/物理学/作用量]]"
  - "[[弦理论/物理学/广义坐标]]"
  - "[[弦理论/物理学/能量]]"
used_by:
  - "[[弦理论/物理学/Hamilton 原理]]"
  - "[[弦理论/物理学/Noether 定理]]"
  - "[[弦理论/物理学/Hamiltonian]]"
evidence_status: 教材事实
---

# 拉格朗日量（Lagrangian）

## 一句话解释

Lagrangian 是构成作用量的瞬时函数；在常见保守粒子系统中，它等于动能减势能。

## 为什么要学它

选定合适 Lagrangian 后，无需逐个写约束力，就能通过统一的 Euler–Lagrange 方程得到运动。相对论、场论和弦论都以 Lagrangian 密度为核心语言。

## 定义

对广义坐标 $q^i$：

$$
L=L(q^i,\dot q^i,t),
$$

作用量为：

$$
S[q]=\int L\,dt.
$$

对许多经典保守系统：

$$
L=T-U,
$$

但这不是 Lagrangian 的普遍定义。带电粒子、相对论系统和场论可有其他形式。

## 从 Lagrangian 得到运动

每个广义坐标满足：

$$
\frac d{dt}
\left(\frac{\partial L}{\partial\dot q^i}\right)
-
\frac{\partial L}{\partial q^i}=0.
$$

因此 Lagrangian 通过它对坐标和速度的依赖编码动力学。

## 自由粒子

$$
L=\frac12m\dot{\mathbf r}^{\,2}.
$$

Euler–Lagrange 方程给出：

$$
m\ddot{\mathbf r}=0.
$$

自由粒子保持恒定速度。

## 弹簧振子

$$
L=\frac12m\dot x^2-\frac12kx^2.
$$

代入方程：

$$
m\ddot x+kx=0.
$$

这就是简谐振动方程。

## 单摆

以角度 $\theta$ 为广义坐标：

$$
T=\frac12m\ell^2\dot\theta^2,
\qquad
U=mg\ell(1-
\cos\theta).
$$

因此：

$$
L=\frac12m\ell^2\dot\theta^2
-mg\ell(1-
\cos\theta).
$$

运动方程为：

$$
\ddot\theta+\frac g\ell\sin\theta=0.
$$

无需单独求张力，因为角度坐标已自动满足绳长约束。

## 共轭动量

定义：

$$
p_i=\frac{\partial L}{\partial\dot q^i}.
$$

它不一定等于普通 $m\dot q^i$。只有在常见 Cartesian 动能形式下才如此。

若 $L$ 不显含某个 $q^i$：

$$
\dot p_i=0,
$$

对应动量守恒。

## Lagrangian 不唯一

若：

$$
L'=L+\frac d{dt}F(q,t),
$$

在适当固定边界条件下，两者给出相同内部运动方程。因此 Lagrangian 是描述工具，不是逐点可直接测量且唯一的物理量。

## 场论中的密度

场论作用量写成：

$$
S=\int d^Dx\,\mathcal L.
$$

$\mathcal L$ 是 Lagrangian 密度，而非普通总 Lagrangian。空间积分后可得到某时刻的 $L$：

$$
L(t)=\int d^{D-1}x\,\mathcal L.
$$

## 弦理论中的角色

Polyakov 作用量的世界面 Lagrangian 密度由 $X^\mu$ 的偏导数和世界面度量组成。其对称性决定约束、守恒流及量子一致性条件。

## 常见误区

1. **Lagrangian 永远等于动能减势能。** 这只是常见系统中的形式。
2. **Lagrangian 就是总能量。** 一般不是；$T-U$ 与 $T+U$ 不同。
3. **共轭动量永远是 $m\mathbf v$。** 错，取决于 Lagrangian 和坐标。
4. **Lagrangian 必须唯一。** 相差总导数可给出相同运动。
5. **场论的 $\mathcal L$ 与粒子 $L$ 完全同量纲。** 前者是密度，需对空间积分。

## 练习

1. 写出一维自由粒子的 Lagrangian。
2. 从弹簧 Lagrangian 推出运动方程。
3. 若 $q$ 不出现在 $L$ 中，哪个量守恒？
4. 为什么单摆用 $\theta$ 比用 $x,y$ 简洁？
5. Lagrangian 加总时间导数后，固定端点的内部方程怎样变化？

## 答案与提示

1. $m\dot x^2/2$。
2. $m\ddot x+kx=0$。
3. $p_q=\partial L/\partial\dot q$。
4. 它自动满足固定绳长约束。
5. 不变。

## 与其他概念的关系

- Lagrangian 在时间上的积分是 [[弦理论/物理学/作用量]]；
- [[弦理论/物理学/Hamilton 原理]] 要求作用量驻定；
- [[弦理论/物理学/Noether 定理]] 从其连续对称性导出守恒量；
- Legendre 变换把它转为 [[弦理论/物理学/Hamiltonian]]。

## 参考资料

- [MIT OCW 8.09, Classical Mechanics III](https://ocw.mit.edu/courses/8-09-classical-mechanics-iii-fall-2014/)
- Herbert Goldstein, Charles Poole, John Safko, *Classical Mechanics*, 3rd ed.
