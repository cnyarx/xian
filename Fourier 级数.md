---
aliases: [Fourier Series]
english_name: Fourier Series
tags: [数学, 调和分析, 弦理论先修, 弦理论]
prerequisites:
  - "[[级数]]"
  - "[[三角函数]]"
  - "[[Euler 公式]]"
  - "[[内积空间]]"
used_by:
  - "[[Fourier 变换]]"
  - "[[正规模]]"
  - "[[弦的模展开]]"
evidence_status: 教材事实
---

# Fourier 级数（Fourier Series）

## 一句话解释

Fourier 级数把合适的周期函数分解成许多不同整数频率的正弦、余弦或复指数之和。

## 为什么要学它

固定区间或圆周上的波只允许离散模式。弦的形状和运动可按这些模式展开，每个模式独立振动；量子化后，每个模式对应一个振子。

## 实三角形式

周期为 $2\pi$ 的函数可写成：

$$
f(x)\sim\frac{a_0}{2}+
\sum_{n=1}^{\infty}
[a_n\cos(nx)+b_n\sin(nx)].
$$

系数为：

$$
a_n=\frac1\pi\int_{-\pi}^{\pi}f(x)\cos(nx)\,dx,
$$

$$
b_n=\frac1\pi\int_{-\pi}^{\pi}f(x)\sin(nx)\,dx.
$$

符号 $\sim$ 暂表示由 Fourier 系数形成展开；是否逐点等于原函数需检查收敛条件。

## 为什么能抽取系数

不同整数频率在 $[-\pi,\pi]$ 上正交。例如：

$$
\int_{-\pi}^{\pi}\cos(nx)\cos(mx)\,dx=0
\quad(n\ne m).
$$

因此把 $f$ 与某个基函数做内积，会消掉其他频率，只留下相应系数。

## 复指数形式

利用 Euler 公式：

$$
f(x)\sim\sum_{n\in\mathbb Z}c_ne^{inx},
$$

$$
c_n=\frac1{2\pi}
\int_{-\pi}^{\pi}f(x)e^{-inx}\,dx.
$$

$n$ 同时取正整数、零和负整数。对实函数，系数满足：

$$
c_{-n}=\overline{c_n}.
$$

## 一般周期

周期为 $L$ 时，允许波数是：

$$
k_n=\frac{2\pi n}{L}.
$$

展开写成：

$$
f(x)=\sum_{n\in\mathbb Z}c_ne^{i2\pi nx/L}.
$$

周期边界条件 $f(x+L)=f(x)$ 导致频率离散化。

## 固定端正弦级数

若区间 $[0,L]$ 两端要求函数为零，适合使用：

$$
f(x)=\sum_{n=1}^{\infty}b_n
\sin\frac{n\pi x}{L}.
$$

这些基函数自动满足端点条件，是固定端弦的正规模。

## 收敛与 Gibbs 现象

对分段光滑的周期函数，Fourier 级数在连续点通常收敛到函数值，在跳跃点收敛到左右极限平均值：

$$
\frac{f(x^-)+f(x^+)}2.
$$

跳跃附近的有限项近似会出现振铃和过冲，称为 Gibbs 现象；增加项数会让振荡区域变窄，但最大相对过冲不会简单消失。

## Parseval 关系

在一种标准归一化下：

$$
\frac1{2\pi}\int_{-\pi}^{\pi}|f(x)|^2dx
=
\sum_{n\in\mathbb Z}|c_n|^2.
$$

它表示函数的总平方大小等于各频率系数平方之和，类似勾股定理在无限维函数空间中的版本。

## 弦的模式展开

弦坐标沿 $\sigma$ 的依赖由边界条件选择相应 Fourier 基。每个系数再随 $\tau$ 做简谐运动。这样一个偏微分方程被拆成无限多个独立常微分方程。

## 常见误区

1. **任何函数的 Fourier 级数都处处等于它。** 错，要检查函数空间与收敛意义。
2. **负频率是多余错误。** 在复指数表示中，它与正频率共同重建实函数。
3. **Fourier 系数由肉眼读取。** 它们通过正交投影积分得到。
4. **边界条件不影响基函数。** 错，周期、固定端和自由端选择不同模式。
5. **有限项近似在跳跃处无振铃。** 会有 Gibbs 现象。

## 练习

1. 周期为 $L$ 时允许波数 $k_n$ 是什么？
2. 偶函数的正弦系数通常为何为零？
3. 固定端条件为何适合正弦基？
4. 实函数的复 Fourier 系数满足什么关系？
5. Fourier 展开如何把波动方程解耦？

## 答案与提示

1. $2\pi n/L$。
2. 偶函数乘奇函数为奇函数，对称区间积分为零。
3. $\sin(n\pi x/L)$ 在 $0,L$ 都为零。
4. $c_{-n}=\bar c_n$。
5. 每个正交模式独立满足一个时间常微分方程。

## 与其他概念的关系

- Fourier 级数是 [[级数]] 在正交函数基上的应用；
- 系数由 [[内积空间]] 的投影提取；
- [[Fourier 变换]] 是周期趋于无限大时的连续频率版本；
- [[弦的模展开]] 根据边界条件采用相应 Fourier 模式；
- [[位置编码|位置编码]] 中的固定正弦编码和 RoPE 也使用多频率正弦、余弦或二维旋转结构。它们借用了 Fourier 模式的频率与相位语言，但不是把任意 token 序列做 Fourier 分解。

## 参考资料

- [MIT OCW 18.03SC, Fourier Series](https://ocw.mit.edu/courses/18-03sc-differential-equations-fall-2011/)
- [MIT OCW 8.03SC, Vibrations and Waves](https://ocw.mit.edu/courses/8-03sc-physics-iii-vibrations-and-waves-fall-2016/)
