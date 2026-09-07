---
aliases: [Noether's Theorem]
english_name: Noether's Theorem
tags: [物理学, 对称性, 弦理论先修]
prerequisites:
  - "[[弦理论/物理学/Lagrangian]]"
  - "[[弦理论/物理学/Hamilton 原理]]"
  - "[[弦理论/数学/变分法]]"
used_by:
  - "[[弦理论/物理学/规范对称性]]"
  - "[[弦理论/物理学/经典场论]]"
  - "[[弦理论/物理学/世界面微分同胚]]"
evidence_status: 教材事实
---

# Noether 定理（Noether's Theorem）

## 一句话解释

Noether 定理把作用量的每个连续对称性与一个守恒量或守恒流联系起来。

## 为什么要学它

动量、能量和角动量守恒不是互不相关的巧合，它们分别来自空间平移、时间平移和旋转对称性。弦理论的世界面对称性、时空对称性和规范结构都用 Noether 方法分析。

## 什么是连续对称性

若变换由连续小参数 $\varepsilon$ 控制，并使作用量不变或只改变边界项，就是连续对称性：

$$
q^i\to q^i+
\varepsilon\Delta q^i.
$$

“连续”表示可以从恒等变换逐渐变化过去。镜像反射等离散对称性通常不直接对应 Noether 守恒流。

## 粒子系统的核心推导

在满足运动方程时，Lagrangian 变化可整理为总时间导数。若对称变换使 $\delta L=dF/dt$，则：

$$
Q=
\sum_i
\frac{\partial L}{\partial\dot q^i}
\Delta q^i-F
$$

满足：

$$
\frac{dQ}{dt}=0.
$$

$Q$ 就是 Noether 守恒量。

## 空间平移与动量

若系统在：

$$
\mathbf r\to\mathbf r+
\varepsilon\mathbf a
$$

下不变，说明空间没有特殊绝对位置，对应总动量守恒。

## 时间平移与能量

若 Lagrangian 不显含时间：

$$
\frac{\partial L}{\partial t}=0,
$$

则：

$$
E=
\sum_i p_i\dot q^i-L
$$

守恒。对普通保守粒子系统，它等于机械总能量。

## 旋转与角动量

若作用量在空间旋转下不变，对应角动量守恒。旋转对称性越大，通常对应更多独立守恒分量。

## 场论中的守恒流

连续变换 $\delta\phi$ 对应 Noether 流 $j^\mu$，在运动方程成立时满足：

$$
\partial_\mu j^\mu=0.
$$

对应守恒荷：

$$
Q=\int d^{D-1}x\,j^0.
$$

若边界通量消失，则 $dQ/dt=0$。

## 全局对称与规范冗余

全局连续对称通常对应物理守恒荷。局域规范对称更微妙：它往往表示描述冗余，并通过 Noether 第二定理产生运动方程之间的恒等关系和约束。

不能简单地把每个规范参数都当成独立可观测守恒量。

## 边界与反常

经典 Noether 流是否产生真正守恒荷，还要检查：

- 边界通量；
- 对称性是否只差边界项；
- 量子化后对称性是否发生反常；
- 荷是否良好定义。

经典对称性可能在量子理论中被反常破坏。

## 弦理论中的作用

目标时空平移给出弦的时空动量；世界面平移和共形变换给出能动张量与相应守恒流。世界面局域对称性还产生约束，量子层面是否保持这些对称性决定临界维数。

## 常见误区

1. **所有守恒定律都只来自 Newton 第三定律。** 更普遍结构来自连续对称性。
2. **任何对称性都对应普通守恒量。** Noether 第一定理针对连续全局对称，规范对称更微妙。
3. **Lagrangian 必须逐点完全不变。** 改变总导数仍可保持作用量对称。
4. **经典守恒量在量子理论中自动守恒。** 可能出现反常。
5. **局部守恒方程自动保证总荷守恒。** 还要检查边界通量。

## 练习

1. 空间平移、时间平移、旋转分别对应什么守恒量？
2. 场论守恒流满足什么局部方程？
3. 为什么边界通量会影响总荷守恒？
4. 离散对称是否直接由 Noether 第一定理给出连续流？
5. 量子反常意味着什么？

## 答案与提示

1. 动量、能量、角动量。
2. $\partial_\mu j^\mu=0$。
3. 守恒量可以通过边界流出研究区域。
4. 通常不直接给出。
5. 经典对称性在量子化后无法保持。

## 与其他概念的关系

- 定理依赖 [[弦理论/物理学/Hamilton 原理]] 与 [[弦理论/物理学/Lagrangian]]；
- [[弦理论/物理学/经典场论]] 使用守恒流；
- [[弦理论/物理学/规范对称性]] 需要 Noether 第二定理和约束观点；
- 弦的量子一致性要求关键世界面对称性不发生致命反常。

## 参考资料

- Emmy Noether, “Invariante Variationsprobleme” (1918), [English translation](https://arxiv.org/abs/physics/0503066)
- [MIT OCW 8.09, Classical Mechanics III](https://ocw.mit.edu/courses/8-09-classical-mechanics-iii-fall-2014/)
- [David Tong, Lectures on Dynamics and Relativity](https://www.damtp.cam.ac.uk/user/tong/dynamics.html)
