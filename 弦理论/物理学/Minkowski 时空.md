---
aliases: [Minkowski Spacetime]
english_name: Minkowski Spacetime
tags: [物理学, 相对论, 弦理论先修]
prerequisites:
  - "[[弦理论/物理学/狭义相对论]]"
  - "[[弦理论/数学/坐标系]]"
  - "[[弦理论/数学/点积]]"
used_by:
  - "[[弦理论/物理学/Lorentz 变换]]"
  - "[[弦理论/物理学/四动量]]"
  - "[[弦理论/物理学/目标时空]]"
evidence_status: 教材事实
---

# Minkowski 时空（Minkowski Spacetime）

## 一句话解释

Minkowski 时空是狭义相对论的平直四维几何，其中时间和空间统一，但时间方向在度量中具有不同符号。

## 为什么要学它

弦理论首先常在 $D$ 维平直 Minkowski 目标时空中建立。Lorentz 对称性、质量壳条件和负范数问题都来自这种不定号几何。

## 事件与坐标

一个事件用时空坐标表示：

$$
x^\mu=(ct,x,y,z).
$$

$\mu=0,1,2,3$，其中 $x^0=ct$。乘 $c$ 后，四个坐标具有相同长度量纲。

## 时空间隔

采用 mostly-minus 约定：

$$
ds^2=c^2dt^2-dx^2-dy^2-dz^2.
$$

也可写成：

$$
ds^2=\eta_{\mu\nu}dx^\mu dx^\nu,
$$

$$
\eta_{\mu\nu}=\operatorname{diag}(1,-1,-1,-1).
$$

有些教材使用相反符号 $(-,+,+,+)$。两种约定都可，但必须全程一致。

## 不定号与普通距离的区别

Euclidean 距离平方对非零向量总为正；Minkowski 间隔可为：

- $ds^2>0$：类时；
- $ds^2=0$：类光；
- $ds^2<0$：类空。

非零向量可以有零“长度”，这是光状向量，不是普通 Euclidean 内积空间中的情况。

## Lorentz 不变量

不同惯性观察者对 $dt,dx,dy,dz$ 的数值不同，但都得到相同 $ds^2$。保持 Minkowski 度量的线性变换就是 Lorentz 变换：

$$
\Lambda^T\eta\Lambda=
\eta.
$$

## 光锥

从某事件发出的光满足：

$$
ds^2=0.
$$

在一维空间中为 $x=\pm ct$。它把时空分成未来光锥、过去光锥和类空区域，并定义因果结构。

## 固有时间

对类时世界线：

$$
c^2d\tau^2=ds^2.
$$

因此：

$$
d\tau=dt\sqrt{1-
\frac{v^2}{c^2}}.
$$

固有时间是随粒子一起运动的钟沿世界线测得的时间。

## 指标升降

向量 $V^\mu$ 可通过度量降指标：

$$
V_\mu=\eta_{\mu\nu}V^\nu.
$$

在 mostly-minus 约定中：

$$
V_0=V^0,
\qquad
V_i=-V^i.
$$

上、下指标不是纯排版区别，空间分量符号会改变。

## $D$ 维推广

弦理论常写：

$$
\eta_{\mu\nu}=
\operatorname{diag}(1,-1,\ldots,-1),
\qquad
\mu=0,1,\ldots,D-1.
$$

一个时间维和 $D-1$ 个空间维。临界维数问题问的是保持量子一致性时 $D$ 必须取何值。

## 目标时空与世界面

Minkowski 时空通常是弦嵌入的目标时空；弦自身扫出的世界面是二维的。$X^\mu(\tau,\sigma)$ 把世界面点映射到目标时空事件。

## 常见误区

1. **四维时空就是四个普通 Euclidean 空间方向。** 时间符号不同，因果结构也不同。
2. **非零向量平方为零说明向量本身为零。** 在不定度量中错误。
3. **度量符号约定只有一种。** 常见有两种相反约定。
4. **上、下指标可以随意交换。** 必须用度量升降。
5. **世界面二维等于目标时空只有二维。** 错，它们是不同空间。

## 练习

1. 写出 mostly-minus 度量矩阵。
2. 光沿 $x$ 方向传播时 $ds^2$ 是多少？
3. 类时、类光、类空怎样按本篇约定分类？
4. Lorentz 变换保持什么量？
5. $D$ 维目标时空有几个空间维？

## 答案与提示

1. $\operatorname{diag}(1,-1,-1,-1)$。
2. 零，因为 $dx=cdt$。
3. 分别为正、零、负。
4. Minkowski 时空间隔或度量。
5. $D-1$ 个。

## 与其他概念的关系

- Minkowski 时空实现 [[弦理论/物理学/狭义相对论]] 的几何；
- [[弦理论/物理学/Lorentz 变换]] 保持其度量；
- [[弦理论/物理学/四动量]] 是时空向量；
- 弦的 [[弦理论/物理学/目标时空]] 常先取 $D$ 维 Minkowski 时空。

## 参考资料

- [MIT OCW 8.20, Introduction to Special Relativity](https://ocw.mit.edu/courses/8-20-introduction-to-special-relativity-january-iap-2021/)
- Edwin F. Taylor and John Archibald Wheeler, *Spacetime Physics*
- Hermann Minkowski, “Space and Time” (1908)
