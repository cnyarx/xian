---
aliases:
  - Gamma Matrices
  - Dirac Matrices
  - γ 矩阵
english_name: Gamma Matrices
tags:
  - 数学
  - Clifford 代数
  - 量子场论
  - 弦理论先修
prerequisites:
  - "[[弦理论/数学/Clifford 代数]]"
  - "[[弦理论/数学/矩阵]]"
  - "[[弦理论/数学/张量积]]"
  - "[[弦理论/数学/复数]]"
  - "[[弦理论/数学/SO 群]]"
used_by:
  - "[[弦理论/数学/旋量]]"
  - "[[弦理论/物理学/Dirac 场]]"
  - "[[弦理论/物理学/Ramond 零模]]"
  - "[[弦理论/物理学/时空旋量]]"
  - "[[弦理论/物理学/超弦临界维数]]"
evidence_status: 教材事实
---

# Gamma 矩阵（Gamma Matrices）

## 一句话解释

Gamma 矩阵是一组满足 Clifford 反对易关系的矩阵，用来让旋转或 Lorentz 变换作用在旋量上。

## 为什么要学它

相对论要求能量和动量满足二次关系，而 Dirac 方程希望使用时间和空间的一阶导数。Gamma 矩阵通过反对易关系，使一个一阶算符的平方变成正确的二阶波动算符。

在超弦理论中，R 扇区零模满足同样的 Clifford 关系，因此其基态自然形成旋量表示。十维手征性、Majorana 条件和时空超对称都离不开 Gamma 矩阵。

## 正式定义

给定带度量 $\eta^{\mu\nu}$ 的 $D$ 维向量空间，一组 Gamma 矩阵 $\Gamma^\mu$ 满足：

$$
\{\Gamma^\mu,\Gamma^\nu\}
=\Gamma^\mu\Gamma^\nu+\Gamma^\nu\Gamma^\mu
=2\eta^{\mu\nu}I.
$$

它们给出相应 Clifford 代数的矩阵表示。

## 每个符号是什么意思

- $D$：时空或向量空间维数；
- $\mu,\nu=0,1,\ldots,D-1$：方向指标；
- $\Gamma^\mu$：与第 $\mu$ 个方向对应的 Gamma 矩阵；
- $\{A,B\}=AB+BA$：反对易子；
- $\eta^{\mu\nu}$：度量的逆矩阵分量；
- $I$：作用在旋量空间上的单位矩阵。

## 平方与反对易

当 $\mu=\nu$ 时：

$$
(\Gamma^\mu)^2=\eta^{\mu\mu}I
$$

在正交坐标基下成立。

当 $\mu\ne\nu$ 且 $\eta^{\mu\nu}=0$ 时：

$$
\Gamma^\mu\Gamma^\nu=-\Gamma^\nu\Gamma^\mu.
$$

所以不同正交方向的 Gamma 矩阵彼此反对易。

## 号差约定

若 Minkowski 度量采用 mostly plus：

$$
\eta=\operatorname{diag}(-1,+1,\ldots,+1),
$$

则：

$$
(\Gamma^0)^2=-I,
\qquad
(\Gamma^i)^2=+I.
$$

若采用 mostly minus：

$$
\eta=\operatorname{diag}(+1,-1,\ldots,-1),
$$

相应平方符号反过来。

一些教材还把 Clifford 定义整体乘以负号。因此比较两套 Gamma 矩阵前，必须先核对度量号差和反对易关系。

## Gamma 矩阵不是普通向量

指标 $\mu$ 表示 Gamma 矩阵与时空基方向的对应关系，但每个 $\Gamma^\mu$ 本身是作用在旋量分量上的矩阵。

它既不是时空中的坐标，也不是普通向量分量。它在“时空向量指标”和“旋量矩阵指标”之间搭桥。

若显式写旋量指标，可记为：

$$
(\Gamma^\mu)^\alpha{}_{\beta}.
$$

其中 $\alpha,\beta$ 是旋量分量指标。

## Pauli 矩阵是低维例子

三个 Pauli 矩阵满足：

$$
\{\sigma_i,\sigma_j\}=2\delta_{ij}I.
$$

所以它们给出三维 Euclidean Clifford 关系的一种复矩阵表示。

但 Pauli 矩阵只有三个，不能直接充当任意维数的全部 Gamma 矩阵；更高维需构造更大的矩阵。

## 四维 Dirac 矩阵

四维 Minkowski 时空需要四个 Gamma 矩阵：

$$
\gamma^0,\gamma^1,\gamma^2,\gamma^3.
$$

在 mostly minus 约定下，它们满足：

$$
\{\gamma^\mu,\gamma^\nu\}=2\eta^{\mu\nu}I,
\qquad
\eta=\operatorname{diag}(+1,-1,-1,-1).
$$

一种 Dirac 表示为：

$$
\gamma^0=
\begin{pmatrix}
I_2&0\\
0&-I_2
\end{pmatrix},
$$

$$
\gamma^i=
\begin{pmatrix}
0&\sigma_i\\
-\sigma_i&0
\end{pmatrix}.
$$

这里每个区块是 $2\times2$ 矩阵，因此 $\gamma^\mu$ 是 $4\times4$ 矩阵。

## 表示不是唯一的

若 $S$ 是可逆矩阵，则：

$$
\Gamma'^\mu=S\Gamma^\mu S^{-1}
$$

满足同样的 Clifford 关系。

因此 Dirac 表示、Weyl 表示和 Majorana 表示只是不同基底选择。可观测物理结论不应依赖具体矩阵表示。

并非每种维数和号差都能选择所有矩阵元素为实数；“Majorana 表示”是否存在取决于具体 Clifford 代数。

## 偶数维中的矩阵大小

对复 Clifford 代数，在偶数维：

$$
D=2m,
$$

不可约复表示空间的维数为：

$$
2^m=2^{D/2}.
$$

因此 Gamma 矩阵可取为：

$$
2^{D/2}\times2^{D/2}
$$

矩阵。

例如：

- $D=2$：$2\times2$；
- $D=4$：$4\times4$；
- $D=10$：$32\times32$。

这是 Dirac 旋量的复分量数。施加 Weyl 或 Majorana 条件后，独立实自由度会减少。

## 奇数维的说明

在奇数维 $D=2m+1$，复 Clifford 代数的不可约表示可由 $2^m\times2^m$ 矩阵实现，但完整复 Clifford 代数会有两个不可约成分，具体表述取决于是否讨论完整代数或偶子代数。

因此不能只套用偶数维公式而忽略奇偶差别。

## 用张量积递归构造

已知 $D$ 维 Euclidean Gamma 矩阵后，可用 Pauli 矩阵张量积构造 $D+2$ 维表示。例如可取：

$$
\Gamma'^i=\sigma_1\otimes\Gamma^i,
$$

$$
\Gamma'^{D+1}=\sigma_2\otimes I,
\qquad
\Gamma'^{D+2}=\sigma_3\otimes I.
$$

在一致编号和号差下，这些矩阵满足新的 Clifford 关系。每增加两个维度，矩阵边长加倍。

## Dirac 算符平方

定义平直时空 Dirac 算符：

$$
\slashed\partial=\Gamma^\mu\partial_\mu.
$$

平方为：

$$
\slashed\partial^2
=\Gamma^\mu\Gamma^\nu\partial_\mu\partial_\nu.
$$

因为普通偏导数彼此对易，反对称的矩阵部分不贡献，得到：

$$
\slashed\partial^2
=\frac12\{\Gamma^\mu,\Gamma^\nu\}
\partial_\mu\partial_\nu
=\eta^{\mu\nu}\partial_\mu\partial_\nu.
$$

这就是 d'Alembert 算符，整体符号随号差约定而变化。

## Dirac 方程如何导出质量壳条件

一种约定下自由 Dirac 方程写为：

$$
(i\Gamma^\mu\partial_\mu-m)\psi=0.
$$

左乘共轭因子：

$$
(i\Gamma^\nu\partial_\nu+m),
$$

利用 Clifford 关系可得到 Klein–Gordon 型方程。具体写成 $\Box+m^2$ 还是 $\Box-m^2$，取决于度量和 $\Box$ 定义；核心是每个 Dirac 分量满足相对论质量壳二次关系。

## 斜线记号

对向量 $v_\mu$，定义：

$$
\slashed v=\Gamma^\mu v_\mu.
$$

于是 Clifford 关系给出：

$$
\slashed v^2=v^2I,
$$

其中：

$$
v^2=\eta^{\mu\nu}v_\mu v_\nu.
$$

Feynman 斜线记号把向量与 Gamma 矩阵收缩写得更紧凑。

## 反对称 Gamma 乘积

定义反对称乘积：

$$
\Gamma^{\mu_1\cdots\mu_p}
=\Gamma^{[\mu_1}\Gamma^{\mu_2}\cdots
\Gamma^{\mu_p]}.
$$

方括号表示对指标完全反对称化。是否包含 $1/p!$ 因子取决于约定。

这些矩阵与微分 $p$ 形式、费米双线性和超引力中的 Ramond–Ramond 场耦合密切相关。

## Lorentz 生成元

Gamma 矩阵的对易子给出旋量表示中的 Lorentz Lie 代数生成元。一种常见约定是：

$$
\Sigma^{\mu\nu}
=\frac14[\Gamma^\mu,\Gamma^\nu].
$$

若使用 Hermitian 物理生成元，也常写成：

$$
S^{\mu\nu}=\frac{i}{4}[\Gamma^\mu,\Gamma^\nu].
$$

两者只差因子 $i$ 的约定。有限 Spin 变换局部写成这些生成元的指数。

## Gamma 矩阵怎样随 Spin 变换

若 $S(\Lambda)$ 是 Lorentz 变换 $\Lambda$ 在旋量空间上的提升，则：

$$
S(\Lambda)^{-1}\Gamma^\mu S(\Lambda)
=\Lambda^\mu{}_{\nu}\Gamma^\nu
$$

在一种常见约定下成立。

这个关系保证旋量双线性：

$$
\bar\psi\Gamma^\mu\psi
$$

像普通 Lorentz 向量一样变换。

## 偶数维的手征矩阵

在偶数维 $D=2m$，可按约定定义所有 Gamma 矩阵的乘积：

$$
\Gamma_*=c\,\Gamma^0\Gamma^1\cdots\Gamma^{D-1},
$$

其中常数 $c$ 被选择为使：

$$
\Gamma_*^2=I.
$$

它满足：

$$
\{\Gamma_*,\Gamma^\mu\}=0.
$$

具体相位 $c$ 依赖维数与度量号差，不能脱离约定固定成同一个公式。

## Weyl 投影

利用 $\Gamma_*$ 定义投影算符：

$$
P_\pm=\frac12(I\pm\Gamma_*).
$$

它们满足：

$$
P_\pm^2=P_\pm,
\qquad
P_+P_-=0.
$$

Dirac 旋量可分解为：

$$
\psi=\psi_++\psi_-,
\qquad
\psi_\pm=P_\pm\psi.
$$

$\psi_+$ 与 $\psi_-$ 是相反手征的 Weyl 旋量。

## Dirac 共轭

在常见四维 mostly minus 约定中，Dirac 共轭定义为：

$$
\bar\psi=\psi^\dagger\gamma^0.
$$

这使 $\bar\psi\psi$ 成为 Lorentz 标量，并使 $\bar\psi\gamma^\mu\psi$ 成为 Lorentz 向量。

在其他号差和 Gamma Hermiticity 约定下，定义可能带额外符号或矩阵，不能机械照搬。

## 电荷共轭矩阵

在适当维数和号差下，可引入电荷共轭矩阵 $C$，满足形如：

$$
C\Gamma^\mu C^{-1}=-(\Gamma^\mu)^T.
$$

正负号与转置关系依赖约定。$C$ 用于定义电荷共轭旋量、Majorana 条件和旋量双线性的对称性。

是否能施加 Majorana 条件由实 Clifford 代数结构决定，不是任意维数都可以。

## 十维 Gamma 矩阵

十维 Dirac Gamma 矩阵可取为 $32\times32$ 复矩阵：

$$
\{\Gamma^\mu,\Gamma^\nu\}=2\eta^{\mu\nu}I_{32},
\qquad \mu,\nu=0,\ldots,9.
$$

十维 Dirac 旋量有 $32$ 个复分量。Weyl 投影将其减半为 $16$ 个复分量；适当的 Majorana 实性条件再把独立自由度限制为 $16$ 个实分量。

这里说的是代数分量计数；对壳运动方程和规范对称还会进一步减少传播自由度。

## 十维 Majorana–Weyl 旋量

在十维 Minkowski 号差中，Majorana 与 Weyl 条件可以相容，因此存在 $16$ 实分量的 Majorana–Weyl 旋量。

Type IIA 的两个时空超荷手征性相反，Type IIB 的两个时空超荷手征性相同。完整结论还依赖 GSO 投影和具体超弦理论，不能只由 Gamma 矩阵单独推出。

## RNS 超弦中的 Ramond 零模

R 扇区世界面费米子零模满足：

$$
\{\psi_0^\mu,\psi_0^\nu\}
=\eta^{\mu\nu}
$$

在一种常见归一化下成立。

可令：

$$
\psi_0^\mu=\frac1{\sqrt2}\Gamma^\mu,
$$

于是 Gamma 矩阵关系给出所需零模反对易关系。其他教材可能把 $\sqrt2$ 放在不同位置。

因此 Ramond 基态必须承载 Gamma 矩阵作用，即形成目标时空旋量。

## Gamma 矩阵恒等式

由 Clifford 关系可以系统化简 Gamma 矩阵乘积。例如：

$$
\Gamma^\mu\Gamma^\nu
=\eta^{\mu\nu}I+\Gamma^{\mu\nu},
$$

其中：

$$
\Gamma^{\mu\nu}
=\frac12[\Gamma^\mu,\Gamma^\nu].
$$

更高阶乘积可分解为完全反对称 Gamma 乘积与度量收缩。不同维数还存在 Hodge 对偶型恒等式。

## 迹恒等式

在偶数维不可约复表示中，单个 Gamma 矩阵以及奇数个不同 Gamma 矩阵乘积的迹通常为零。四维常见公式包括：

$$
\operatorname{tr}(\gamma^\mu\gamma^\nu)
=4\eta^{\mu\nu}.
$$

更高维系数由旋量表示维数决定。含手征矩阵的迹还会产生 Levi-Civita 张量。

这些公式高度依赖维数和归一化，必须在具体语境中使用。

## Fierz 恒等式

Gamma 矩阵的完整基可用于重新排列旋量双线性的指标收缩，这类关系称为 Fierz 恒等式。

它在超对称、超引力、κ 对称和超弦振幅中非常重要。其具体系数依赖维数、旋量类型和电荷共轭约定，本篇不把某一维公式误写成普遍公式。

## 一个四维检查

在 mostly minus 的 Dirac 表示中：

$$
(\gamma^0)^2=I_4,
$$

而：

$$
(\gamma^i)^2=-I_4.
$$

对 $i\ne j$：

$$
\gamma^i\gamma^j=-\gamma^j\gamma^i.
$$

这正对应：

$$
\eta=\operatorname{diag}(+1,-1,-1,-1).
$$

## 适用条件与事实边界

1. Gamma 矩阵是 Clifford 代数的矩阵表示，不是抽象 Clifford 代数或旋量本身。
2. 反对易关系的整体符号和各矩阵平方取决于度量号差与 Clifford 约定。
3. 不同 Gamma 矩阵表示可由相似变换联系；具体矩阵形式不是物理可观测量。
4. 偶数维 $D$ 的不可约复 Dirac 表示维数为 $2^{D/2}$；奇数维需单独区分完整 Clifford 代数和偶子代数。
5. 手征矩阵只在偶数维按通常方式把 Dirac 旋量分成两个手征子空间。
6. $\Gamma_*$ 的相位、Dirac 共轭和电荷共轭矩阵均依赖维数与约定。
7. Majorana 条件、Weyl 条件及二者兼容性取决于维数和号差。
8. 十维 $32$、$16$ 的计数是代数分量数；对壳传播自由度还需运动方程等约束。
9. Lorentz 生成元写成 $[\Gamma^\mu,\Gamma^\nu]/4$ 或带 $i/4$，取决于生成元约定。
10. Ramond 零模与 Gamma 矩阵之间的 $\sqrt2$ 因子依赖世界面费米子的归一化。
11. 迹恒等式和 Fierz 恒等式不能脱离具体维数、表示大小与旋量类型直接套用。
12. Type IIA/IIB 手征性还依赖 GSO 投影和理论构造，不是仅由 Clifford 代数决定。

## 常见误区

1. **Gamma 矩阵就是时空中的普通向量。** 它们是带时空指标、作用在旋量空间上的矩阵。
2. **Gamma 矩阵有唯一标准形式。** 不同基可给出不同但等价的矩阵表示。
3. **所有维数都使用 $4\times4$ Gamma 矩阵。** 矩阵大小随维数增加。
4. **反对易关系中时间矩阵一定平方为 $+I$。** 这取决于度量号差。
5. **$2^{D/2}$ 是 Clifford 代数自身维数。** 它是偶数维不可约复旋量表示维数；代数维数是 $2^D$。
6. **手征矩阵在任意维数都能把旋量一分为二。** 通常的手征分解针对偶数维。
7. **Majorana 表示意味着任意维数都能取实旋量。** 实结构依赖维数和号差。
8. **Ramond 零模等于 Gamma 矩阵且没有归一化差异。** 两者常差一个约定相关因子。
9. **Fierz 恒等式在所有维数系数相同。** 系数取决于维数和旋量类型。

## 练习

1. 写出 Gamma 矩阵的 Clifford 反对易关系。
2. 在正交基下，$\mu\ne\nu$ 时两个 Gamma 矩阵有什么关系？
3. mostly minus 四维约定下，$(\gamma^0)^2$ 和 $(\gamma^i)^2$ 分别是什么？
4. 为什么相似变换后的 Gamma 矩阵仍满足同一 Clifford 关系？
5. 偶数维 $D=2m$ 的不可约复 Dirac 旋量有多少分量？
6. 用 Clifford 关系证明 $(\Gamma^\mu\partial_\mu)^2=\eta^{\mu\nu}\partial_\mu\partial_\nu$。
7. 写出 Lorentz 旋量生成元的一种常见定义。
8. Weyl 投影算符怎样定义？
9. 十维 Dirac、Weyl 和 Majorana–Weyl 旋量分别有多少代数分量？
10. RNS 超弦中 Ramond 零模为什么作用在旋量空间上？

## 答案与提示

1. $\{\Gamma^\mu,\Gamma^\nu\}=2\eta^{\mu\nu}I$。
2. 若 $\eta^{\mu\nu}=0$，则 $\Gamma^\mu\Gamma^\nu=-\Gamma^\nu\Gamma^\mu$。
3. 分别为 $+I$ 与 $-I$。
4. 把 $S\Gamma^\mu S^{-1}$ 代入反对易子，$S^{-1}S$ 抵消，结果为 $2\eta^{\mu\nu}I$。
5. $2^m=2^{D/2}$ 个复分量。
6. 因偏导数对称，只有 Gamma 乘积的反对称子贡献为零，剩下反对易子的一半。
7. $\Sigma^{\mu\nu}=\frac14[\Gamma^\mu,\Gamma^\nu]$，或 Hermitian 约定下乘以 $i$。
8. $P_\pm=(I\pm\Gamma_*)/2$。
9. 十维 Dirac 为 $32$ 复分量，Weyl 为 $16$ 复分量，Majorana–Weyl 为 $16$ 实分量；均为约束前的代数分量计数。
10. 零模满足目标时空 Clifford 反对易关系，所以其基态必须承载该代数的矩阵表示。

## 与其他概念的关系

- [[弦理论/数学/Clifford 代数]] 给出 Gamma 矩阵必须满足的抽象生成关系；
- [[弦理论/数学/矩阵]] 提供相似变换、迹、转置和 Hermitian 共轭；
- [[弦理论/数学/张量积]] 可递归构造更高维 Gamma 矩阵；
- [[弦理论/数学/SO 群]] 的 Spin 覆盖在旋量空间上的生成元由 Gamma 对易子实现；
- [[弦理论/数学/旋量]] 是 Gamma 矩阵作用的向量；
- [[弦理论/物理学/Dirac 场]] 使用 Gamma 矩阵构造相对论一阶波动方程；
- [[弦理论/物理学/Ramond 零模]] 经过归一化后可由 Gamma 矩阵表示；
- [[弦理论/物理学/时空旋量]] 在十维中可施加 Majorana 与 Weyl 条件；
- [[弦理论/物理学/超弦临界维数]] 的谱与时空超对称分析需要十维旋量结构。

## 参考资料

- Pertti Lounesto, *Clifford Algebras and Spinors*, 2nd ed., Cambridge University Press, 2001.
- H. Blaine Lawson and Marie-Louise Michelsohn, *Spin Geometry*, Princeton University Press, 1989.
- Michael E. Peskin and Daniel V. Schroeder, *An Introduction to Quantum Field Theory*, Westview Press, 1995.
- Mark Srednicki, *Quantum Field Theory*, Cambridge University Press, 2007.
- Daniel Z. Freedman and Antoine Van Proeyen, *Supergravity*, Cambridge University Press, 2012.
- Joseph Polchinski, *String Theory, Vol. 1*, Cambridge University Press, 1998.
- Joseph Polchinski, *String Theory, Vol. 2*, Cambridge University Press, 1998.
- David Tong, *Lectures on String Theory*, [arXiv:0908.0333](https://arxiv.org/abs/0908.0333)