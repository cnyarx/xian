---
aliases: [Lorentz Transformation]
english_name: Lorentz Transformation
tags: [物理学, 相对论, 弦理论先修]
prerequisites:
  - "[[弦理论/物理学/狭义相对论]]"
  - "[[弦理论/物理学/Minkowski 时空]]"
  - "[[弦理论/数学/矩阵]]"
used_by:
  - "[[弦理论/物理学/四动量]]"
  - "[[弦理论/物理学/相对论点粒子]]"
  - "[[弦理论/物理学/目标时空]]"
evidence_status: 教材事实
---

# Lorentz 变换（Lorentz Transformation）

## 一句话解释

Lorentz 变换连接不同惯性观察者的时空坐标，并保持光速和 Minkowski 时空间隔不变。

## 为什么要学它

相对论理论的方程必须在 Lorentz 变换下保持正确形式。弦的目标时空谱必须组成 Lorentz 群表示，临界维数推导也要求量子 Lorentz 对称性成立。

## 一维 boost

若参考系 $S'$ 以速度 $v$ 沿 $x$ 方向相对 $S$ 运动：

$$
t'=\gamma\left(t-
\frac{vx}{c^2}\right),
$$

$$
x'=\gamma(x-vt),
$$

$$
y'=y,\qquad z'=z,
$$

其中：

$$
\gamma=\frac1{\sqrt{1-v^2/c^2}}.
$$

时间与空间坐标发生混合。

## 逆变换

把 $v$ 换成 $-v$：

$$
t=\gamma\left(t'+
\frac{vx'}{c^2}\right),
$$

$$
x=\gamma(x'+vt').
$$

这反映两个惯性系彼此等价，没有绝对静止系。

## 保持时空间隔

直接代入可验证：

$$
c^2t'^2-x'^2
=c^2t^2-x^2.
$$

三维推广保持：

$$
\eta_{\mu\nu}x'^\mu x'^\nu
=
\eta_{\mu\nu}x^\mu x^\nu.
$$

矩阵条件是：

$$
\Lambda^T\eta\Lambda=
\eta.
$$

## 与旋转的类比

普通旋转保持 $x^2+y^2$；Lorentz boost 保持 $c^2t^2-x^2$。它可看成不定号几何中的“时空旋转”，但双曲函数而非普通圆函数更自然。

定义快度 $\varphi$：

$$
\tanh\varphi=\frac vc.
$$

则：

$$
\gamma=\cosh\varphi,
\qquad
\gamma v/c=\sinh\varphi.
$$

连续同方向 boost 的快度直接相加。

## 同时性、时间与长度

Lorentz 变换中的 $vx/c^2$ 项导致同时性相对；由同一变换可推导时间膨胀和长度收缩。它们不是互相独立的额外假设。

## 四向量变换

四向量满足：

$$
V'^\mu=\Lambda^\mu{}_{\nu}V^\nu.
$$

时空位置、四速度、四动量和四电流都按同一类规则变换。它们的 Minkowski 内积是 Lorentz 标量。

## Lorentz 群组成

完整 Lorentz 群包括空间旋转、boost，以及可能的宇称和时间反演离散分支。与恒等变换连续相连、保持空间和时间定向的部分常记为 $SO^+(1,3)$。

旋量并非 Lorentz 群的普通向量表示，而与其双覆盖群有关，后续单独讲解。

## 主动与被动观点

- 被动：同一事件改用另一惯性坐标描述；
- 主动：在固定坐标系中对物理配置施加 Lorentz 变换。

两种观点公式互为相关逆变换，必须明确约定。

## 常见误区

1. **Lorentz 变换只改变空间，不改变时间。** 错，二者混合。
2. **它不保持任何东西，所以一切相对。** 它严格保持时空间隔。
3. **时间膨胀和长度收缩是独立补丁。** 都来自同一变换。
4. **boost 速度可以超过 $c$。** 标准惯性系相对速度满足 $|v|<c$。
5. **Lorentz 群只有 boost。** 还包括空间旋转及离散分支。

## 练习

1. 写出沿 $x$ 方向 boost 的 $t',x'$。
2. 逆变换如何从正变换得到？
3. Lorentz 变换保持什么二次型？
4. 为什么时间与空间不能彼此独立变换？
5. 快度相较速度有什么组合优势？

## 答案与提示

1. 见核心公式。
2. 将 $v$ 换成 $-v$。
3. $c^2t^2-x^2-y^2-z^2$。
4. 保持光速要求它们按 Lorentz 公式混合。
5. 同方向 boost 的快度相加。

## 与其他概念的关系

- Lorentz 变换保持 [[弦理论/物理学/Minkowski 时空]] 度量；
- [[弦理论/物理学/四动量]] 按四向量规则变换；
- [[弦理论/物理学/相对论点粒子]] 的作用量保持 Lorentz 不变；
- 弦谱必须实现目标时空 Lorentz 对称性。

## 参考资料

- [MIT OCW 8.20, Introduction to Special Relativity](https://ocw.mit.edu/courses/8-20-introduction-to-special-relativity-january-iap-2021/)
- Edwin F. Taylor and John Archibald Wheeler, *Spacetime Physics*
