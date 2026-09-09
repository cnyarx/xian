---
aliases:
  - Euler's Formula
  - Euler Formula
english_name: Euler's Formula
tags:
  - 数学
  - 高中基础
  - 弦理论先修
  - 弦理论
prerequisites:
  - "[[指数函数]]"
  - "[[三角函数]]"
  - "[[复数]]"
used_by:
  - "[[Fourier 级数]]"
  - "[[简谐振动]]"
  - "[[行波]]"
  - "[[弦的模展开]]"
evidence_status: 教材事实
---

# Euler 公式（Euler's Formula）

## 一句话解释

Euler 公式说明：复指数 $e^{i\theta}$ 正好代表复平面上转过角度 $\theta$ 的单位向量。

## 核心公式

$$
e^{i\theta}=\cos\theta+i\sin\theta.
$$

其中：

- $e$ 是自然指数函数的底数；
- $i$ 是满足 $i^2=-1$ 的虚数单位；
- $\theta$ 是用弧度表示的实数角；
- $\cos\theta$ 是复数的实部；
- $\sin\theta$ 是虚部的系数。

公式右边在复平面上的坐标是 $(\cos\theta,\sin\theta)$，它位于单位圆上。

## 为什么要学它

它把三类看似不同的对象连在一起：

1. [[指数函数]]；
2. [[三角函数]]；
3. [[复数]]。

借助它，正弦与余弦的计算可以转化为指数运算，波、振动和弦的模展开会变得更紧凑。

## 从幂级数看出公式

指数、正弦、余弦可以展开为无穷级数：

$$
e^x=1+x+\frac{x^2}{2!}+\frac{x^3}{3!}+\cdots,
$$

$$
\cos x=1-\frac{x^2}{2!}+\frac{x^4}{4!}-\cdots,
$$

$$
\sin x=x-\frac{x^3}{3!}+\frac{x^5}{5!}-\cdots.
$$

把 $x=i\theta$ 代入指数级数：

$$
e^{i\theta}
=1+i\theta+\frac{(i\theta)^2}{2!}
+\frac{(i\theta)^3}{3!}+\cdots.
$$

利用：

$$
i^2=-1,\quad i^3=-i,\quad i^4=1,
$$

把实数项与含 $i$ 的项分开：

$$
e^{i\theta}
=\left(1-\frac{\theta^2}{2!}+\frac{\theta^4}{4!}-\cdots\right)
+i\left(\theta-\frac{\theta^3}{3!}+\frac{\theta^5}{5!}-\cdots\right).
$$

第一组括号正是 $\cos\theta$，第二组括号正是 $\sin\theta$，所以得到 Euler 公式。

这里的推导依赖无穷级数的收敛性，后续会在 [[级数]] 中系统说明。

## 几何意义

因为：

$$
|e^{i\theta}|
=\sqrt{\cos^2\theta+\sin^2\theta}
=1,
$$

所以 $e^{i\theta}$ 始终位于单位圆上。改变 $\theta$ 只改变方向，不改变长度。

特别地：

$$
e^{i0}=1,
$$

$$
e^{i\pi/2}=i,
$$

$$
e^{i\pi}=-1,
$$

$$
e^{i2\pi}=1.
$$

角度增加 $2\pi$ 后回到原点位，因此：

$$
e^{i(\theta+2\pi)}=e^{i\theta}.
$$

## Euler 恒等式

令 $\theta=\pi$：

$$
e^{i\pi}=\cos\pi+i\sin\pi=-1.
$$

移项得到：

$$
e^{i\pi}+1=0.
$$

它把 $e$、$i$、$\pi$、$1$ 和 $0$ 联系在一个式子里，但它只是 Euler 公式的一个特殊取值。

## 用复指数表示正弦和余弦

把 $\theta$ 换成 $-\theta$：

$$
e^{-i\theta}=\cos\theta-i\sin\theta.
$$

两式相加：

$$
\cos\theta=\frac{e^{i\theta}+e^{-i\theta}}2.
$$

两式相减：

$$
\sin\theta=\frac{e^{i\theta}-e^{-i\theta}}{2i}.
$$

这两条公式让振动和波可以直接写成复指数。

## 为什么复指数便于描述波

实数振动

$$
x(t)=A\cos(\omega t+\phi)
$$

可以看成复数表达式

$$
Ae^{i(\omega t+\phi)}
$$

的实部：

$$
x(t)=\operatorname{Re}\left[Ae^{i(\omega t+\phi)}\right].
$$

实际可观测位移仍是实数。使用复数只是让加法、微分和相位运算更简单，最后取实部即可。

## 乘法等于角度相加

$$
e^{i\alpha}e^{i\beta}=e^{i(\alpha+\beta)}.
$$

几何上，这表示先旋转 $\alpha$，再旋转 $\beta$，总效果是旋转 $\alpha+\beta$。三角函数加法公式也能由此推出。

## 常见误区

1. **$e^{i\theta}$ 会像 $e^x$ 那样随 $\theta$ 越来越大。** 错；它的模恒为 $1$，只沿单位圆旋转。
2. **复指数表示不可观测的虚假运动。** 错；它是编码实数振动的高效工具，最终可取实部或模平方。
3. **Euler 恒等式就是 Euler 公式的全部。** 错；它只是 $\theta=\pi$ 的特例。
4. **角度可以直接以度数代入分析公式。** 理论推导默认使用弧度。
5. **级数比较只是形式拼凑。** 严格处理需要证明级数收敛；这些标准幂级数在所有复数输入处都收敛。

## 练习

1. 用 Euler 公式求 $e^{i\pi/2}$。
2. 求 $e^{-i\pi}$。
3. 用指数形式写出 $\cos\theta$。
4. 求 $|3e^{i\theta}|$。
5. 解释为什么乘以 $e^{i\alpha}$ 表示旋转 $\alpha$。
6. 把 $2\cos(3t)$ 写成两个复指数之和。

## 答案与提示

1. $i$。
2. $-1$。
3. $(e^{i\theta}+e^{-i\theta})/2$。
4. $3$。
5. 它的模为 $1$，相乘时复数角度增加 $\alpha$。
6. $e^{i3t}+e^{-i3t}$。

## 与其他概念的关系

- 公式由 [[指数函数]]、[[三角函数]] 和 [[复数]] 汇合而成；
- [[简谐振动]] 和 [[行波]] 可用复指数简写；
- [[Fourier 级数]] 用不同频率的复指数分解周期函数；
- [[弦的模展开]] 本质上也使用许多不同频率的振动模式。

## 参考资料

- [MIT OCW 18.03SC, Complex Numbers and Exponentials](https://ocw.mit.edu/courses/18-03sc-differential-equations-fall-2011/)
- [OpenStax, Calculus Volume 2, Power Series](https://openstax.org/details/books/calculus-volume-2)
- Leonhard Euler, *Introductio in analysin infinitorum* (1748)
