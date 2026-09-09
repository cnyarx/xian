---
aliases:
  - SU(2) Double Cover of SO(3)
  - SU(2) 与三维旋转
english_name: SU(2) Double Cover of SO(3)
tags:
  - 数学
  - 群论
  - 关系页
  - 量子力学
  - 弦理论先修
  - 弦理论
prerequisites:
  - "[[SU 群]]"
  - "[[SO 群]]"
  - "[[Lie 群与 Lie 代数的对应]]"
  - "[[群表示]]"
used_by:
  - "[[Clifford 代数]]"
  - "[[旋量]]"
  - "[[自旋]]"
  - "[[角动量]]"
evidence_status: 教材事实
---

# SU(2) 与 SO(3) 的双覆盖（SU(2) Double Cover of SO(3)）

## 一句话解释

每个三维旋转都对应 $SU(2)$ 中恰好两个相反的元素 $U$ 和 $-U$，所以 $SU(2)$ 像一张双层地图覆盖整个 $SO(3)$。

## 为什么要学它

经典三维向量由 $SO(3)$ 旋转，但自旋 $1/2$ 态由 $SU(2)$ 变换。一个 $2\pi$ 旋转在普通空间中已经回到原朝向，却会让自旋量态矢量乘以 $-1$；到 $4\pi$ 才回到原态矢量。

这一关系是理解半整数自旋、Spin 群、Clifford 代数、Gamma 矩阵和超弦时空旋量的入口。

## 什么叫覆盖映射

覆盖映射 $p:\widetilde X\to X$ 的直观含义是：目标空间中每个足够小的区域，其原像由若干互不相交的区域组成，并且每一片都与目标小区域同胚。

若目标中每个点恰有两个原像，就称为双覆盖。

这里存在 Lie 群同态：

$$
\pi:SU(2)\to SO(3),
$$

使每个 $R\in SO(3)$ 恰有两个原像：

$$
U\quad\text{和}\quad -U.
$$

## 两个群的全局形状

$SU(2)$ 作为流形同胚于三维球面：

$$
SU(2)\cong S^3.
$$

$SO(3)$ 可看成把 $S^3$ 上每对对径点识别：

$$
SO(3)\cong SU(2)/\{\pm I\}
\cong S^3/(x\sim -x)
\cong\mathbb{RP}^3.
$$

所以 $SU(2)$ 单连通，而 $SO(3)$ 的基本群为：

$$
\pi_1(SO(3))\cong\mathbb Z_2.
$$

## Pauli 矩阵把三维向量写成矩阵

对三维实向量：

$$
\mathbf x=(x_1,x_2,x_3),
$$

定义 Hermitian 无迹矩阵：

$$
X=\mathbf x\cdot\boldsymbol\sigma
=x_1\sigma_1+x_2\sigma_2+x_3\sigma_3.
$$

展开为：

$$
X=
\begin{pmatrix}
x_3&x_1-ix_2\\
x_1+ix_2&-x_3
\end{pmatrix}.
$$

这个对应把 $\mathbb R^3$ 与所有 $2\times2$ Hermitian 无迹矩阵组成的三维实向量空间联系起来。

## 长度怎样写成行列式

上述矩阵满足：

$$
X^2=|\mathbf x|^2I,
$$

并且：

$$
\det X=-|\mathbf x|^2.
$$

因此保持 $X$ 的行列式，就等于保持三维向量长度。

## 用共轭作用构造旋转

对任意 $U\in SU(2)$，定义：

$$
X\longmapsto X'=UXU^\dagger.
$$

$X'$ 仍然 Hermitian、无迹，而且：

$$
\det X'=\det X.
$$

所以存在一个保持长度的三维线性变换 $R_U$，满足：

$$
UXU^\dagger
=(R_U\mathbf x)\cdot\boldsymbol\sigma.
$$

连续性与 $U=I$ 时 $R_U=I$ 保证 $R_U$ 保持定向，因此：

$$
R_U\in SO(3).
$$

这定义了覆盖同态：

$$
\pi(U)=R_U.
$$

## 为什么它是群同态

先施加 $V$，再施加 $U$：

$$
X\mapsto VXV^\dagger
\mapsto U(VXV^\dagger)U^\dagger
=(UV)X(UV)^\dagger.
$$

因此：

$$
R_{UV}=R_UR_V,
$$

也就是：

$$
\pi(UV)=\pi(U)\pi(V).
$$

## 为什么 $U$ 与 $-U$ 给出同一旋转

把 $U$ 替换为 $-U$：

$$
(-U)X(-U)^\dagger
=(-U)X(-U^\dagger)
=UXU^\dagger.
$$

两个负号抵消，所以：

$$
R_{-U}=R_U.
$$

因此覆盖至少是二对一。

## 覆盖映射的核

若 $U$ 映到恒等旋转，则对所有 Hermitian 无迹矩阵 $X$ 有：

$$
UXU^\dagger=X.
$$

这意味着 $U$ 与所有 Pauli 矩阵对易。满足这一点的 $SU(2)$ 元素只有：

$$
U=I\quad\text{或}\quad U=-I.
$$

所以：

$$
\ker\pi=\{I,-I\}\cong\mathbb Z_2.
$$

由第一同构定理：

$$
SO(3)\cong SU(2)/\mathbb Z_2.
$$

这里还使用了映射 $\pi$ 对 $SO(3)$ 的满射性。

## 轴—角参数

任意 $SU(2)$ 元素可写成：

$$
U(\theta,\hat n)
=\exp\left(-i\frac\theta2\hat n\cdot\boldsymbol\sigma\right),
$$

其中：

- $\hat n$：三维单位向量，表示旋转轴；
- $\theta$：对应 $SO(3)$ 旋转角；
- $\boldsymbol\sigma=(\sigma_1,\sigma_2,\sigma_3)$：Pauli 矩阵组；
- 半角 $\theta/2$：双覆盖的关键。

展开后：

$$
U(\theta,\hat n)
=I\cos\frac\theta2
-i(\hat n\cdot\boldsymbol\sigma)\sin\frac\theta2.
$$

## 它确实产生绕 $\hat n$ 的旋转

利用 Pauli 矩阵恒等式：

$$
(\mathbf a\cdot\boldsymbol\sigma)
(\mathbf b\cdot\boldsymbol\sigma)
=(\mathbf a\cdot\mathbf b)I
+i(\mathbf a\times\mathbf b)\cdot\boldsymbol\sigma,
$$

可推出：

$$
U(\theta,\hat n)
(\mathbf x\cdot\boldsymbol\sigma)
U(\theta,\hat n)^\dagger
=(R_{\hat n}(\theta)\mathbf x)\cdot\boldsymbol\sigma,
$$

其中 $R_{\hat n}(\theta)$ 正是绕轴 $\hat n$ 旋转角 $\theta$ 的三维旋转。

## Rodrigues 旋转公式

对应的三维向量变换为：

$$
R_{\hat n}(\theta)\mathbf x
=\mathbf x\cos\theta
+(\hat n\times\mathbf x)\sin\theta
+\hat n(\hat n\cdot\mathbf x)(1-\cos\theta).
$$

三项分别表示：

1. 原向量按 $\cos\theta$ 保留；
2. 垂直旋转方向贡献 $\sin\theta$；
3. 沿旋转轴的分量保持不变。

## 为什么出现半角

$SU(2)$ 元素使用 $\theta/2$，但它对三维向量的共轭作用产生角度 $\theta$。因此：

$$
U(\theta+2\pi,\hat n)=-U(\theta,\hat n),
$$

而：

$$
R_{\hat n}(\theta+2\pi)=R_{\hat n}(\theta).
$$

群元素要到 $4\pi$ 才完全重复：

$$
U(\theta+4\pi,\hat n)=U(\theta,\hat n).
$$

## 绕 $z$ 轴的例子

取：

$$
\hat n=(0,0,1).
$$

则：

$$
U_z(\theta)
=e^{-i\theta\sigma_3/2}
=
\begin{pmatrix}
e^{-i\theta/2}&0\\
0&e^{i\theta/2}
\end{pmatrix}.
$$

它对应三维旋转：

$$
R_z(\theta)=
\begin{pmatrix}
\cos\theta&-\sin\theta&0\\
\sin\theta&\cos\theta&0\\
0&0&1
\end{pmatrix}.
$$

当 $\theta=2\pi$ 时，$R_z=I_3$，但 $U_z=-I_2$。

## Lie 代数为何相同

$SU(2)$ 与 $SO(3)$ 的覆盖映射在单位元处求微分，得到 Lie 代数同构：

$$
d\pi_I:\mathfrak{su}(2)\to\mathfrak{so}(3).
$$

所以：

$$
\mathfrak{su}(2)\cong\mathfrak{so}(3).
$$

两边都有三个生成元，并可采用相同形式的对易关系：

$$
[J_i,J_j]=i\varepsilon_{ijk}J_k.
$$

局部无穷小旋转相同，差异只在全局拓扑和允许的群表示。

## 整数自旋与半整数自旋

$SU(2)$ 的有限维不可约复表示由：

$$
j=0,\frac12,1,\frac32,\ldots
$$

标记，维数为：

$$
2j+1.
$$

中心元素 $-I$ 在自旋 $j$ 表示中作用为：

$$
(-1)^{2j}I.
$$

因此：

- 整数 $j$：$-I$ 作用为 $+I$，表示能下降到 $SO(3)$；
- 半整数 $j$：$-I$ 作用为 $-I$，表示不能下降为 $SO(3)$ 的普通表示。

## 态矢量变号是否可观测

孤立态矢量 $|\psi\rangle$ 与 $-|\psi\rangle$ 代表同一量子射线，因此单看最终孤立态，整体负号不改变普通概率。

但不能因此说双覆盖没有物理意义。在不同旋转路径的相干叠加、干涉实验、复合系统和场的变换规律中，相对相位可产生可观测效应。中子干涉实验等已检验自旋 $1/2$ 的 $4\pi$ 周期结构。

## 旋转群的基本群

$SU(2)\cong S^3$ 是 $SO(3)$ 的普适覆盖空间。覆盖核是 $\mathbb Z_2$，因此：

$$
\pi_1(SO(3))\cong\mathbb Z_2.
$$

这意味着 $SO(3)$ 中闭合旋转路径分为两类：

- 可收缩为一点的偶类；
- 不能在 $SO(3)$ 内收缩为一点的奇类。

连续做两遍奇类路径后，会落入可收缩类。这是“皮带把戏”与“盘子把戏”的拓扑基础。

## 四元数图景

$SU(2)$ 也同构于单位四元数群。单位四元数：

$$
q=a+b\mathbf i+c\mathbf j+d\mathbf k,
\qquad a^2+b^2+c^2+d^2=1
$$

组成 $S^3$。

三维向量可写成纯虚四元数 $\mathbf v$，旋转由：

$$
\mathbf v\mapsto q\mathbf vq^{-1}
$$

给出。$q$ 与 $-q$ 产生同一旋转，与 Pauli 矩阵共轭作用完全平行。

## 从 $Spin(3)$ 看双覆盖

利用三维 Euclidean Clifford 代数可构造旋转群的双覆盖 $Spin(3)$，并有：

$$
Spin(3)\cong SU(2).
$$

因此三维旋量是 $SU(2)$ 的表示。更高维中，$Spin(n)$ 双覆盖 $SO(n)$，但通常不再等同于简单的 $SU(2)$。

## 在量子力学中的作用

三维角动量算符满足：

$$
[J_i,J_j]=i\hbar\varepsilon_{ijk}J_k.
$$

有限旋转作用在量子态上：

$$
U(R)=\exp\left(-\frac{i}{\hbar}\theta\hat n\cdot\mathbf J\right).
$$

对自旋 $1/2$：

$$
\mathbf J=\frac\hbar2\boldsymbol\sigma,
$$

于是恢复 $SU(2)$ 的半角公式。

## 在弦理论中的作用

超弦理论需要时空旋量和世界面费米子。旋量不是 $SO(n)$ 的普通张量表示，而是其覆盖群 $Spin(n)$ 的表示。

$SU(2)\to SO(3)$ 是最容易直观计算的低维模型，它展示了：

- 为什么旋量在 $2\pi$ 旋转后可变号；
- 为什么必须区分旋转群与其覆盖群；
- 为什么 Lie 代数信息不足以决定允许的全局表示；
- Clifford 代数如何通向 Spin 群和旋量。

十维超弦使用的是更高维 Lorentz 群的 Spin 覆盖与 Majorana–Weyl 旋量，不能直接把三维 $SU(2)$ 公式原样搬过去，但核心覆盖思想相同。

## 适用条件与事实边界

1. $\pi:SU(2)\to SO(3)$ 是满射 Lie 群同态，核为 $\{I,-I\}$。
2. 每个 $SO(3)$ 元素在 $SU(2)$ 中恰有两个原像 $U$ 与 $-U$。
3. $SU(2)\cong S^3$ 单连通；$SO(3)\cong\mathbb{RP}^3$ 且基本群为 $\mathbb Z_2$。
4. 两群 Lie 代数同构，但全局群不相同。
5. 半整数自旋表示是 $SU(2)$ 的表示，不能下降为 $SO(3)$ 的普通单值表示。
6. 态矢量整体负号单独不改变量子射线，但相对相位和旋转路径干涉可体现双覆盖结构。
7. $2\pi$ 旋转在 $SO(3)$ 中为单位元，在自旋 $1/2$ 的 $SU(2)$ 表示中作用为 $-I$；$4\pi$ 才作用为 $I$。
8. Pauli 矩阵共轭构造描述 Euclidean 三维旋转；更高维或 Lorentzian 情形需要相应 Clifford 与 Spin 群。
9. $Spin(3)\cong SU(2)$ 是低维特殊同构，不应推广成任意 $Spin(n)\cong SU(2)$。
10. 文中的指数符号正负依赖主动旋转、被动旋转与生成元约定，但双覆盖结论不变。

## 常见误区

1. **$SU(2)$ 与 $SO(3)$ 是同一个群。** 它们的 Lie 代数同构，但群之间是二对一覆盖。
2. **一个三维旋转只有一个 $SU(2)$ 原像。** 实际有 $U$ 与 $-U$ 两个。
3. **$2\pi$ 旋转后态矢量变号意味着所有概率都改变。** 孤立整体相位不改变概率，但相对相位可在干涉中显现。
4. **$4\pi$ 才恢复说明物体在普通空间中必须真的转两圈才能朝向复原。** 普通向量朝向在 $2\pi$ 已复原；$4\pi$ 周期属于旋量表示。
5. **两群生成元对易关系相同，所以所有表示相同。** 全局中心决定哪些代数表示能下降到群表示。
6. **双覆盖是把旋转角简单乘二。** 它是群与拓扑层面的覆盖映射，半角只是常用参数表现。
7. **$SU(2)$ 的每个元素都代表不同三维旋转。** $U$ 与 $-U$ 代表同一旋转。
8. **任意维旋量都由 $SU(2)$ 描述。** 一般应使用 $Spin(n)$ 或 Lorentzian Spin 群。

## 练习

1. 写出覆盖同态 $\pi:SU(2)\to SO(3)$ 的核。
2. 为什么 $U$ 与 $-U$ 对矩阵 $X$ 的共轭作用相同？
3. 把三维向量 $\mathbf x$ 写成 Pauli 矩阵组合 $X$。
4. 为什么 $UXU^\dagger$ 保持 $\mathbf x$ 的长度？
5. 写出 $U(\theta,\hat n)$ 的指数形式与展开形式。
6. 当 $\theta=2\pi$、$4\pi$ 时，$U(\theta,\hat n)$ 分别是什么？
7. 哪些 $SU(2)$ 自旋 $j$ 表示能下降为 $SO(3)$ 表示？
8. $SU(2)$ 与 $SO(3)$ 的流形分别同胚于什么空间？
9. 为什么态矢量的整体负号与双覆盖的物理意义不矛盾？
10. $Spin(3)$ 与哪个熟悉群同构？

## 答案与提示

1. $\{I,-I\}\cong\mathbb Z_2$。
2. $(-U)X(-U)^\dagger=UXU^\dagger$，两个负号抵消。
3. $X=x_1\sigma_1+x_2\sigma_2+x_3\sigma_3$。
4. 共轭作用保持行列式，而 $\det X=-|\mathbf x|^2$。
5. $U=e^{-i\theta\hat n\cdot\boldsymbol\sigma/2}=I\cos(\theta/2)-i\hat n\cdot\boldsymbol\sigma\sin(\theta/2)$。
6. 分别为 $-I$ 与 $I$。
7. 整数 $j$；此时中心元素 $-I$ 作用为 $+I$。
8. $SU(2)\cong S^3$；$SO(3)\cong\mathbb{RP}^3$。
9. 孤立整体相位不改变射线，但不同路径或系统分支间的相对相位可产生干涉效应。
10. $Spin(3)\cong SU(2)$。

## 与其他概念的关系

- [[SU 群]] 给出 $SU(2)$ 的矩阵、中心和表示；
- [[SO 群]] 给出三维旋转群 $SO(3)$；
- [[Lie 群与 Lie 代数的对应]] 解释相同局部代数为何可对应不同全局群；
- [[群表示]] 区分整数与半整数自旋表示是否能下降到 $SO(3)$；
- [[Clifford 代数]] 用于构造一般 $Spin(n)$；
- [[Gamma 矩阵]] 是 Clifford 代数的矩阵表示；
- [[旋量]] 是 Spin 群的表示对象；
- [[自旋]] 使用 $SU(2)$ 的不可约表示分类三维旋转下的量子态；
- [[角动量]] 提供旋转生成元及其对易关系。

## 参考资料

- Brian C. Hall, *Lie Groups, Lie Algebras, and Representations*, 2nd ed., Springer, 2015.
- J. J. Sakurai and Jim Napolitano, *Modern Quantum Mechanics*, 3rd ed., Cambridge University Press, 2020.
- Michael Tinkham, *Group Theory and Quantum Mechanics*, Dover, 2003.
- Howard Georgi, *Lie Algebras in Particle Physics*, 2nd ed., Westview Press, 1999.
- H. F. Jones, *Groups, Representations and Physics*, 2nd ed., CRC Press, 1998.
- Mikio Nakahara, *Geometry, Topology and Physics*, 2nd ed., CRC Press, 2003.
- S. A. Werner, R. Colella, A. W. Overhauser, and C. F. Eagen, “Observation of the Phase Shift of a Neutron Due to Precession in a Magnetic Field,” *Physical Review Letters* 35, 1053 (1975), [DOI](https://doi.org/10.1103/PhysRevLett.35.1053)