---
aliases: [Poisson Bracket]
english_name: Poisson Bracket
tags: [物理学, 分析力学, 弦理论先修]
prerequisites:
  - "[[弦理论/物理学/Hamiltonian]]"
  - "[[弦理论/数学/偏导数]]"
used_by:
  - "[[弦理论/物理学/场的正则量子化]]"
  - "[[弦理论/物理学/对易关系]]"
  - "[[弦理论/物理学/BRST 对称性]]"
evidence_status: 教材事实
---

# Poisson 括号（Poisson Bracket）

## 一句话解释

Poisson 括号衡量两个相空间函数在正则结构下怎样相互生成变化，并能把 Hamilton 演化写成统一形式。

## 为什么要学它

经典 Poisson 括号是量子对易子的直接前身。守恒量、对称变换、角动量代数和约束系统都可用括号统一处理。

## 定义

对相空间函数 $A(q,p,t)$、$B(q,p,t)$：

$$
\{A,B\}=
\sum_i
\left(
\frac{\partial A}{\partial q^i}
\frac{\partial B}{\partial p_i}
-
\frac{\partial A}{\partial p_i}
\frac{\partial B}{\partial q^i}
\right).
$$

结果仍是相空间函数。

## 基本正则括号

$$
\{q^i,q^j\}=0,
$$

$$
\{p_i,p_j\}=0,
$$

$$
\{q^i,p_j\}=\delta^i{}_j.
$$

Kronecker delta 在 $i=j$ 时为 $1$，否则为 $0$。

## Hamilton 演化

任意相空间函数 $A$ 沿运动的全时间变化为：

$$
\frac{dA}{dt}
=
\{A,H\}+
\frac{\partial A}{\partial t}.
$$

取 $A=q^i$ 或 $p_i$，就恢复 Hamilton 方程：

$$
\dot q^i=\{q^i,H\},
\qquad
\dot p_i=\{p_i,H\}.
$$

Hamiltonian 是时间演化的生成元。

## 守恒量

若 $A$ 不显含时间，且：

$$
\{A,H\}=0,
$$

则：

$$
\frac{dA}{dt}=0.
$$

因此判断一个量是否守恒，可检查它与 Hamiltonian 的 Poisson 括号。

## 代数性质

反对称性：

$$
\{A,B\}=-\{B,A\}.
$$

线性和 Leibniz 法则：

$$
\{A,BC\}=
\{A,B\}C+B\{A,C\}.
$$

Jacobi 恒等式：

$$
\{A,\{B,C\}\}
+
\{B,\{C,A\}\}
+
\{C,\{A,B\}\}=0.
$$

这些性质使相空间函数在 Poisson 括号下形成 Lie 代数结构。

## 生成无穷小变换

若 $G$ 是某种变换的生成元，则：

$$
\delta A=\varepsilon\{A,G\}.
$$

例如动量生成空间平移，角动量生成旋转，Hamiltonian 生成时间演化。

## 角动量括号

三维角动量满足：

$$
\{L_i,L_j\}=\epsilon_{ijk}L_k.
$$

这表示连续旋转的组合结构。量子化后变成角动量算符的对易关系。

## 场论推广

场变量的基本括号包含空间 delta：

$$
\{\phi(\mathbf x),
\pi(\mathbf y)\}
=
\delta^{(d)}(
\mathbf x-
\mathbf y).
$$

它是离散自由度 $\{q^i,p_j\}=\delta^i_j$ 的连续版本。

## 量子化对应

经典到量子的常见形式对应是：

$$
\{A,B\}_{PB}
\longrightarrow
\frac1{i\hbar}[
\hat A,\hat B].
$$

这是一条重要指导原则，但不是对任意经典函数都无歧义、完全机械的量子化算法；算符排序等会产生问题。

## 约束与规范变换

在 Dirac 约束理论中，一类约束通过 Poisson 括号生成规范变换。第二类约束则需要引入 Dirac 括号。这对规范场和弦的 Hamilton 量子化很重要。

## 常见误区

1. **Poisson 括号是普通乘法交换子 $AB-BA$。** 经典相空间函数通常可交换，括号由偏导数组成。
2. **$\{A,H\}=0$ 总保证守恒。** 还要检查 $A$ 是否显含时间。
3. **所有 Poisson 括号都为零。** 坐标与共轭动量的括号非零。
4. **量子化只需无条件把括号换成对易子。** 存在排序和全局问题。
5. **生成元只是被动标签。** 它通过括号实际产生无穷小变换。

## 练习

1. 计算一自由度下 $\{q,p\}$。
2. 计算 $\{q,H\}$，其中 $H=p^2/(2m)+U(q)$。
3. 一个不显含时间的 $A$ 满足什么条件时守恒？
4. Poisson 括号是否反对称？
5. 场论基本括号为何出现 Dirac delta？

## 答案与提示

1. $1$。
2. $p/m=\dot q$。
3. $\{A,H\}=0$。
4. 是，$\{A,B\}=-\{B,A\}$。
5. 连续空间标签替代离散指标，delta 表示同一点的正则配对。

## 与其他概念的关系

- Poisson 括号建立在 [[弦理论/物理学/Hamiltonian]] 相空间上；
- 量子 [[弦理论/物理学/对易关系]] 是其对应结构；
- 场的正则括号使用 [[弦理论/数学/Dirac delta]]；
- 约束和 [[弦理论/物理学/BRST 对称性]] 的经典结构依赖括号代数。

## 参考资料

- [MIT OCW 8.09, Hamiltonian Mechanics](https://ocw.mit.edu/courses/8-09-classical-mechanics-iii-fall-2014/)
- Herbert Goldstein, Charles Poole, John Safko, *Classical Mechanics*, 3rd ed.
- Paul Dirac, *Lectures on Quantum Mechanics*
