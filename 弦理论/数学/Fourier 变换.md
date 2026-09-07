---
aliases: [Fourier Transform]
english_name: Fourier Transform
tags: [数学, 调和分析, 弦理论先修]
prerequisites:
  - "[[弦理论/数学/积分]]"
  - "[[弦理论/数学/复数]]"
  - "[[弦理论/数学/Fourier 级数]]"
used_by:
  - "[[弦理论/数学/Dirac delta]]"
  - "[[弦理论/数学/Green 函数]]"
  - "[[弦理论/物理学/传播子]]"
evidence_status: 教材事实
---

# Fourier 变换（Fourier Transform）

## 一句话解释

Fourier 变换把一个随位置或时间变化的函数改写成各个连续频率或波数成分的组合。

## 为什么要学它

微分在频率空间中变成乘法，偏微分方程因此更容易求解。量子场论的传播子、动量空间计算和弦散射都大量使用 Fourier 变换。

## 一种常用约定

定义：

$$
\tilde f(k)=
\int_{-\infty}^{\infty}
f(x)e^{-ikx}\,dx,
$$

逆变换为：

$$
f(x)=
\int_{-\infty}^{\infty}
\frac{dk}{2\pi}
\tilde f(k)e^{ikx}.
$$

其中 $k$ 是波数。不同教材会把 $2\pi$ 对称分配到正逆变换中；只要整套约定一致，物理结果相同。

## 与 Fourier 级数的区别

- 周期区间：离散整数模式，用 Fourier 级数求和；
- 无限区间：连续波数，用 Fourier 变换积分。

把周期 $L$ 越取越大时，离散间隔 $2\pi/L$ 越来越小，求和在极限中变为积分。

## 变换的意义

$f(x)$ 是位置空间描述，$\tilde f(k)$ 是波数空间描述。它们不是两个不同物理对象，而是同一对象在两组基中的坐标。

就像向量可在不同坐标基下表示，函数可在位置基或平面波基下表示。

## 导数变成乘法

在边界项适当消失时：

$$
\mathcal F[f'](k)=ik\tilde f(k),
$$

$$
\mathcal F[f''](k)=-k^2\tilde f(k).
$$

因此微分方程会变成关于 $k$ 的代数方程。这是 Fourier 变换最重要的计算优势之一。

## 卷积

卷积定义为：

$$
(f*g)(x)=
\int_{-\infty}^{\infty}
f(x-y)g(y)\,dy.
$$

卷积定理说：

$$
\mathcal F[f*g]=\tilde f\,\tilde g.
$$

位置空间中的卷积变成频率空间中的普通乘法；反过来，位置空间乘法对应频率空间卷积。

## Gaussian 例子

Gaussian 函数的 Fourier 变换仍是 Gaussian。函数在位置空间越窄，其变换在波数空间越宽。这是位置—动量不确定关系的数学影子之一。

## Parseval 与 Plancherel

在上述归一化下：

$$
\int_{-\infty}^{\infty}|f(x)|^2dx
=
\int_{-\infty}^{\infty}
\frac{dk}{2\pi}|\tilde f(k)|^2.
$$

同一函数的平方范数在两种表示中相同。

## 不确定性

函数不可能同时在位置和波数上任意狭窄。粗略地：

$$
\Delta x\,\Delta k\ge\frac12
$$

在标准归一化与方差定义下成立。量子力学中 $p=\hbar k$，从而得到位置—动量不确定关系。

## 多维变换

$D$ 维中常写：

$$
\tilde f(k)=\int d^Dx\,f(x)e^{-ik\cdot x},
$$

$$
f(x)=\int\frac{d^Dk}{(2\pi)^D}
\tilde f(k)e^{ik\cdot x}.
$$

在 Minkowski 时空中，点积符号与指数正负号约定必须明确。

## 分布的需要

常数函数和平面波通常不可按普通可积函数处理，其 Fourier 变换涉及 [[弦理论/数学/Dirac delta]]。理论物理经常在分布意义下使用变换，而不是假装所有积分都普通收敛。

## 常见误区

1. **Fourier 变换创造了新的物理信息。** 错，它改变表示方式。
2. **所有资料的 $2\pi$ 位置相同。** 错，归一化有多种约定。
3. **导数变成 $k$ 而没有 $i$ 或符号。** 要按指数约定计算。
4. **任何函数都能按普通积分直接变换。** 有些需要分布或广义函数。
5. **位置越窄，波数也越窄。** 通常相反。

## 练习

1. 写出本篇采用的正变换和逆变换。
2. $f''$ 的 Fourier 变换是什么？
3. 周期函数为何使用离散模式？
4. 卷积在 Fourier 空间变成什么？
5. 为什么平面波需要 Dirac delta 语言？

## 答案与提示

1. 见核心定义，逆变换含 $dk/(2\pi)$。
2. $-k^2\tilde f(k)$。
3. 周期条件只允许 $k_n=2\pi n/L$。
4. 普通乘法。
5. 平面波不在整个无限空间绝对可积或平方可积，其变换需按分布解释。

## 与其他概念的关系

- [[弦理论/数学/Fourier 级数]] 是离散频率版本；
- [[弦理论/数学/Dirac delta]] 表达连续平面波的正交与完备性；
- [[弦理论/数学/Green 函数]] 常通过 Fourier 空间求解；
- 量子场论的 [[弦理论/物理学/传播子]] 常在动量空间表示。

## 参考资料

- [MIT OCW 18.03SC, Fourier Transform](https://ocw.mit.edu/courses/18-03sc-differential-equations-fall-2011/)
- [MIT OCW 8.04, Quantum Physics I](https://ocw.mit.edu/courses/8-04-quantum-physics-i-spring-2016/)
