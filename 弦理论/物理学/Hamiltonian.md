---
aliases: [Hamiltonian]
english_name: Hamiltonian
tags: [物理学, 分析力学, 弦理论先修]
prerequisites:
  - "[[弦理论/物理学/Lagrangian]]"
  - "[[弦理论/物理学/广义坐标]]"
  - "[[弦理论/物理学/Noether 定理]]"
used_by:
  - "[[弦理论/物理学/Poisson 括号]]"
  - "[[弦理论/物理学/场的正则量子化]]"
  - "[[弦理论/物理学/量子算符]]"
evidence_status: 教材事实
---

# 哈密顿量（Hamiltonian）

## 一句话解释

Hamiltonian 是相空间中的动力学函数；它通过坐标和共轭动量决定系统怎样随时间演化。

## 为什么要学它

Hamilton 形式直接通向 Poisson 括号、正则量子化和量子 Hamiltonian。弦的每个振动模式量子化时，也会从经典 Hamiltonian 过渡到振子算符。

## 从 Lagrangian 到 Hamiltonian

先定义共轭动量：

$$
p_i=\frac{\partial L}{\partial\dot q^i}.
$$

若能把速度写成 $q,p,t$ 的函数，Hamiltonian 定义为 Legendre 变换：

$$
H(q,p,t)=\sum_i p_i\dot q^i-L(q,\dot q,t).
$$

速度必须在右边消去，最终 $H$ 的独立变量是 $q,p,t$。

## 普通粒子例子

若：

$$
L=\frac12m\dot x^2-U(x),
$$

则：

$$
p=m\dot x,
\qquad
\dot x=\frac pm.
$$

所以：

$$
H=p\dot x-L
=
\frac{p^2}{2m}+U(x).
$$

在这个常见系统中，Hamiltonian 等于总能量。但对显含时间、带约束或特殊速度耦合的系统，不能无条件把 $H$ 与能量等同。

## Hamilton 方程

$$
\dot q^i=\frac{\partial H}{\partial p_i},
$$

$$
\dot p_i=-\frac{\partial H}{\partial q^i}.
$$

它们是一组一阶方程。第一条说明动量怎样决定坐标变化，第二条说明坐标依赖怎样改变动量。

对 $H=p^2/(2m)+U(q)$：

$$
\dot q=\frac pm,
\qquad
\dot p=-\frac{dU}{dq}=F,
$$

与 Newton 方程一致。

## 相空间

$n$ 个自由度的状态由：

$$
(q^1,\ldots,q^n,p_1,\ldots,p_n)
$$

描述，组成 $2n$ 维相空间。系统随时间的演化是一条相空间轨迹。

构型空间只记录位置；相空间同时记录位置和动量，因此一个点通常足以指定瞬时经典状态。

## Hamiltonian 的时间变化

沿运动轨迹：

$$
\frac{dH}{dt}=\frac{\partial H}{\partial t}.
$$

所以若 $H$ 不显含时间：

$$
\frac{dH}{dt}=0.
$$

Hamiltonian 守恒。

## 简谐振子

$$
H=\frac{p^2}{2m}+\frac12m\omega^2q^2.
$$

相空间轨迹满足：

$$
\frac{p^2}{2m}+\frac12m\omega^2q^2=E,
$$

是一族椭圆。坐标和动量在能量固定的轨道上周期变化。

## 正则坐标

$(q^i,p_i)$ 是正则共轭变量。保持 Hamilton 方程或辛结构的变量变换叫正则变换。它比普通坐标变换有更强要求。

## 约束系统

若速度—动量关系不能求逆，Legendre 变换是退化的，会出现约束。规范理论和弦的重新参数化不变性都会导致此类约束，需要 Dirac 约束 Hamilton 体系，而不是机械套用普通公式。

## 量子化预告

正则量子化形式上把：

$$
q^i,p_j
$$

提升为算符，并把经典 Poisson 括号关系转成对易关系。量子 Hamiltonian 决定 Schrödinger 时间演化。

## 常见误区

1. **Hamiltonian 永远等于总能量。** 只在适当系统与条件下成立。
2. **Legendre 变换后仍把 $\dot q$ 当独立变量。** 最终应改写为 $q,p,t$。
3. **相空间维数等于自由度数。** $n$ 个自由度通常给 $2n$ 维相空间。
4. **Hamilton 方程仍是一个二阶方程。** 它是一对一阶方程。
5. **有规范对称的系统可无条件使用普通 Legendre 变换。** 退化系统会产生约束。

## 练习

1. 对 $L=m\dot q^2/2-U(q)$ 求 $p$ 与 $H$。
2. 用 Hamilton 方程恢复 $\dot q=p/m$。
3. 一个三自由度系统的相空间通常多少维？
4. $H$ 不显含时间时满足什么守恒关系？
5. 为什么退化 Legendre 变换提示约束？

## 答案与提示

1. $p=m\dot q$，$H=p^2/(2m)+U$。
2. $\partial H/\partial p=p/m$。
3. 六维。
4. $dH/dt=0$。
5. 不能由动量唯一恢复所有速度，说明变量并非全部独立。

## 与其他概念的关系

- Hamiltonian 由 [[弦理论/物理学/Lagrangian]] 的 Legendre 变换得到；
- [[弦理论/物理学/Poisson 括号]] 简洁表达 Hamilton 演化；
- 正则量子化把它提升为量子演化算符；
- 弦的每个经典模式都有相应振子 Hamiltonian。

## 参考资料

- [MIT OCW 8.09, Hamiltonian Mechanics](https://ocw.mit.edu/courses/8-09-classical-mechanics-iii-fall-2014/)
- Herbert Goldstein, Charles Poole, John Safko, *Classical Mechanics*, 3rd ed.
