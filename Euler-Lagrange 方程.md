---
aliases: [Euler-Lagrange Equation, Euler–Lagrange Equation]
english_name: Euler-Lagrange Equation
tags: [数学, 变分法, 弦理论先修, 弦理论]
prerequisites:
  - "[[变分法]]"
  - "[[偏导数]]"
used_by:
  - "[[Lagrangian]]"
  - "[[Hamilton 原理]]"
  - "[[场的 Euler-Lagrange 方程]]"
evidence_status: 教材事实
---

# Euler-Lagrange 方程（Euler-Lagrange Equation）

## 一句话解释

Euler–Lagrange 方程是作用量对所有允许路径的一阶变化为零时，路径必须满足的局部运动方程。

## 为什么要学它

Newton 方法从力开始，Lagrangian 方法从作用量开始。后者更容易保持相对论和对称性结构，并能直接推广到场和弦。

## 单自由度形式

对泛函：

$$
S[q]=\int_{t_1}^{t_2}L(q,\dot q,t)\,dt,
$$

驻定条件 $\delta S=0$ 给出：

$$
\frac d{dt}
\left(\frac{\partial L}{\partial\dot q}\right)
-
\frac{\partial L}{\partial q}=0.
$$

其中：

- $q(t)$ 是广义坐标；
- $\dot q=dq/dt$ 是广义速度；
- $L$ 是 Lagrangian；
- 第一个偏导先把 $q,t$ 固定、对 $\dot q$ 求偏导，再对时间求全导数。

## 推导

令：

$$
q(t)\to q(t)+\varepsilon\eta(t),
\qquad
\eta(t_1)=\eta(t_2)=0.
$$

一阶变分为：

$$
\delta S=
\int_{t_1}^{t_2}
\left[
\frac{\partial L}{\partial q}\eta
+
\frac{\partial L}{\partial\dot q}\dot\eta
\right]dt.
$$

对第二项分部积分：

$$
\delta S=
\left[
\frac{\partial L}{\partial\dot q}\eta
\right]_{t_1}^{t_2}
+
\int_{t_1}^{t_2}
\left[
\frac{\partial L}{\partial q}
-
\frac d{dt}
\left(\frac{\partial L}{\partial\dot q}\right)
\right]
\eta\,dt.
$$

固定端点使边界项为零。由于内部的 $\eta(t)$ 任意，方括号必须为零，得到 Euler–Lagrange 方程。

## 自由粒子例子

一维自由粒子的 Lagrangian：

$$
L=\frac12m\dot x^2.
$$

有：

$$
\frac{\partial L}{\partial x}=0,
\qquad
\frac{\partial L}{\partial\dot x}=m\dot x.
$$

因此：

$$
\frac d{dt}(m\dot x)=0.
$$

质量恒定时：

$$
m\ddot x=0,
$$

即自由粒子速度恒定。

## 势能中的粒子

若：

$$
L=\frac12m\dot x^2-U(x),
$$

则：

$$
\frac{\partial L}{\partial x}=-\frac{dU}{dx},
\qquad
\frac{\partial L}{\partial\dot x}=m\dot x.
$$

Euler–Lagrange 方程给出：

$$
m\ddot x=-\frac{dU}{dx}=F(x).
$$

这正是 Newton 第二定律。

## 多个广义坐标

若有 $q^i(t)$，每个坐标都满足：

$$
\frac d{dt}
\left(\frac{\partial L}{\partial\dot q^i}\right)
-
\frac{\partial L}{\partial q^i}=0.
$$

上标 $i$ 只是不同自由度的标签，不表示幂。

## 共轭动量

定义：

$$
p_i=\frac{\partial L}{\partial\dot q^i}.
$$

Euler–Lagrange 方程变为：

$$
\dot p_i=\frac{\partial L}{\partial q^i}.
$$

若 $L$ 不显含某个 $q^i$，则 $\partial L/\partial q^i=0$，对应共轭动量守恒。该坐标称为循环坐标。

## 场的推广

场 $\phi(x)$ 的 Lagrangian 密度为 $\mathcal L(\phi,\partial_\mu\phi,x)$，场方程为：

$$
\partial_\mu
\left(
\frac{\partial\mathcal L}
{\partial(\partial_\mu\phi)}
\right)
-
\frac{\partial\mathcal L}{\partial\phi}=0.
$$

它把时间轨迹推广为时空中的函数。

## 弦坐标的推广

对世界面场 $X^\mu(\tau,\sigma)$，需要分别处理 $\partial_\tau X^\mu$ 与 $\partial_\sigma X^\mu$。自由 Polyakov 作用量的变分会给出二维波动方程，同时产生必须单独处理的边界项。

## 总导数不改变内部方程

若把 Lagrangian 改为：

$$
L'=L+\frac d{dt}F(q,t),
$$

作用量只增加端点项。在固定端点且条件适当时，内部 Euler–Lagrange 方程不变。这说明不同 Lagrangian 可能描述相同经典运动。

## 常见误区

1. **Euler–Lagrange 方程只适用于最小作用量。** 它来自驻定作用量。
2. **$\partial L/\partial\dot q$ 求完后不用再对时间求导。** 错。
3. **推导中边界项可以无条件删除。** 必须由边界条件处理。
4. **上标 $i$ 总表示幂。** 在 $q^i$ 中通常是分量标签。
5. **不同 Lagrangian 必定给出不同运动。** 相差总导数时可给出相同内部方程。

## 练习

1. 对 $L=m\dot x^2/2$ 推导运动方程。
2. 对 $L=m\dot x^2/2-kx^2/2$ 推导运动方程。
3. 若 $L$ 不显含坐标 $q$，哪个量守恒？
4. 为什么固定端点变化能消除边界项？
5. 场的 Euler–Lagrange 方程与粒子版本有何主要区别？

## 答案与提示

1. $m\ddot x=0$。
2. $m\ddot x+kx=0$。
3. $p=\partial L/\partial\dot q$。
4. 边界处 $\eta=0$。
5. 独立变量从时间推广到多个时空坐标，并使用 $\partial_\mu$。

## 与其他概念的关系

- 方程由 [[变分法]] 推导；
- [[Lagrangian]] 是方程中的核心输入；
- [[Hamilton 原理]] 规定真实路径使作用量驻定；
- [[场的 Euler-Lagrange 方程]] 与弦方程是其多变量推广。

## 参考资料

- [MIT OCW 8.09, Classical Mechanics III](https://ocw.mit.edu/courses/8-09-classical-mechanics-iii-fall-2014/)
- Herbert Goldstein, Charles Poole, John Safko, *Classical Mechanics*, 3rd ed.
- I. M. Gelfand and S. V. Fomin, *Calculus of Variations*
