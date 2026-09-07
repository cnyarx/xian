---
aliases: [Hamilton's Principle, Principle of Stationary Action]
english_name: Hamilton's Principle
tags: [物理学, 分析力学, 弦理论先修]
prerequisites:
  - "[[弦理论/物理学/作用量]]"
  - "[[弦理论/物理学/Lagrangian]]"
  - "[[弦理论/数学/变分法]]"
used_by:
  - "[[弦理论/物理学/Noether 定理]]"
  - "[[弦理论/物理学/相对论点粒子]]"
  - "[[弦理论/物理学/Nambu-Goto 作用量]]"
evidence_status: 教材事实
---

# Hamilton 原理（Hamilton's Principle）

## 一句话解释

Hamilton 原理说：在固定端点之间，真实经典运动使作用量对任意允许小路径变化的一阶变化为零。

## 为什么要学它

它用一个统一原则取代针对每个方向逐个列力。相对论粒子、场和弦的运动都能通过同一种变分语言得到。

## 数学表述

对：

$$
S[q]=\int_{t_1}^{t_2}L(q,\dot q,t)dt,
$$

取满足端点固定的变化：

$$
\delta q(t_1)=\delta q(t_2)=0.
$$

真实路径满足：

$$
\delta S=0.
$$

这表示作用量的一阶变化消失。

## 为什么叫驻定而不是最小

在简单 Euclidean 几何最短路问题中，驻定路径可能确实最短。但一般动力学中的作用量可以在真实路径处是：

- 局部最小；
- 局部最大；
- 鞍点。

因此“驻定作用量原理”比“最小作用量原理”准确。

## 与 Euler–Lagrange 方程等价

在适当光滑性和边界条件下，Hamilton 原理推出：

$$
\frac d{dt}
\left(\frac{\partial L}{\partial\dot q^i}\right)
-
\frac{\partial L}{\partial q^i}=0.
$$

反过来，满足方程的路径对固定端点允许变化具有零一阶变分。

## 它不是自然界预先比较未来路线

该原理是对整条运动的紧凑数学表述，不意味着粒子具有意识、先试遍未来所有路线再选择。局部微分方程和整体变分原则在适当条件下是等价描述。

## 边界条件

固定端点是一种常用选择。如果端点可变，变分会留下边界项并产生额外边界条件。场和弦的边界处理尤其重要。

闭弦世界面没有空间端点；开弦世界面有边界，因此 Hamilton 原理会限制弦端点怎样运动。

## 相对论粒子

自由相对论粒子作用量：

$$
S=-mc\int ds.
$$

Hamilton 原理给出平直时空中的惯性世界线。该形式直接使用固有长度，保持重新参数化和 Lorentz 对称性。

## 场论推广

场作用量：

$$
S[\phi]=\int d^Dx\,\mathcal L.
$$

对整个场配置变分：

$$
\delta S=0
$$

得到场的 Euler–Lagrange 方程。

## 弦论推广

弦坐标 $X^\mu(\tau,\sigma)$ 的作用量在二维世界面积分。对 $X^\mu$ 变分得到内部运动方程；对开弦还得到边界项。对辅助世界面度量变分则产生能动张量约束。

## 量子理论中的地位

经典 Hamilton 原理不是完整量子运动规则。路径积分形式上让所有路径按 $e^{iS/\hbar}$ 加权；经典驻定路径在半经典极限中因相位抵消机制占主导。

## 常见误区

1. **真实路径总使作用量全局最小。** 错，原则是驻定。
2. **粒子会试走所有路线再选择。** 这是拟人化误解。
3. **整体原理与局部运动方程互相矛盾。** 在适当条件下它们等价。
4. **边界条件与变分无关。** 错，它决定允许变化和边界项。
5. **Hamilton 原理本身就是完整量子理论。** 错，量子理论需额外结构。

## 练习

1. 写出 Hamilton 原理的公式。
2. 为什么固定端点要求 $\delta q(t_1)=\delta q(t_2)=0$？
3. 驻定是否等于最小？
4. 为什么该原理不表示粒子预知未来？
5. 开弦与闭弦的边界分析为何不同？

## 答案与提示

1. $\delta S=0$。
2. 所比较的所有候选路径必须连接同一对端点。
3. 不等于，还可能是最大或鞍点。
4. 它与局部 Euler–Lagrange 方程是等价数学表述。
5. 开弦世界面有空间边界，闭弦沿空间方向周期闭合。

## 与其他概念的关系

- 原理作用于 [[弦理论/物理学/作用量]]；
- [[弦理论/数学/变分法]] 给出计算方法；
- [[弦理论/物理学/Noether 定理]] 研究作用量对称性；
- 相对论粒子和弦作用量都服从驻定原理。

## 参考资料

- [MIT OCW 8.09, Classical Mechanics III](https://ocw.mit.edu/courses/8-09-classical-mechanics-iii-fall-2014/)
- Herbert Goldstein, Charles Poole, John Safko, *Classical Mechanics*, 3rd ed.
- [David Tong, Lectures on Dynamics and Relativity](https://www.damtp.cam.ac.uk/user/tong/dynamics.html)
