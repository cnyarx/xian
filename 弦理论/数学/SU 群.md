---
aliases:
  - Special Unitary Group
  - SU(n)
  - 特殊酉群
english_name: Special Unitary Group
tags:
  - 数学
  - 群论
  - 量子力学
  - 弦理论先修
prerequisites:
  - "[[弦理论/数学/Lie 群]]"
  - "[[弦理论/数学/Lie 代数]]"
  - "[[弦理论/数学/矩阵]]"
  - "[[弦理论/数学/内积空间]]"
  - "[[弦理论/数学/复数]]"
used_by:
  - "[[弦理论/数学/SU(2) 与 SO(3) 的双覆盖]]"
  - "[[弦理论/数学/旋量]]"
  - "[[弦理论/物理学/自旋]]"
  - "[[弦理论/物理学/Yang-Mills 理论]]"
  - "[[弦理论/物理学/规范对称性]]"
evidence_status: 教材事实
---

# SU 群（Special Unitary Group）

## 一句话解释

$SU(n)$ 是所有保持 $n$ 维复向量内积且行列式为 $1$ 的线性变换组成的 Lie 群。

## 为什么要学它

量子态由复向量描述，保持总概率的线性变换必须保持复内积，因此自然出现酉矩阵。再把整体复相位对应的行列式自由度去掉，就得到 $SU(n)$。

$SU(2)$ 描述自旋与三维旋转的双覆盖，$SU(3)$ 是量子色动力学的规范群。超弦理论、D-brane 和紧致化中也会频繁出现 $SU(n)$ 及其表示。

## 复共轭转置

对复矩阵 $U$，先转置再把每个元素取复共轭，得到 Hermitian 共轭：

$$
U^\dagger=(U^*)^T.
$$

例如：

$$
U=
\begin{pmatrix}
a&b\\c&d
\end{pmatrix}
\quad\Longrightarrow\quad
U^\dagger=
\begin{pmatrix}
a^*&c^*\\b^*&d^*
\end{pmatrix}.
$$

实矩阵没有非平凡复共轭时，$U^\dagger$ 就退化为普通转置 $U^T$。

## 酉矩阵

若复矩阵 $U$ 满足：

$$
U^\dagger U=I,
$$

则称 $U$ 为酉矩阵。这等价于：

$$
U^{-1}=U^\dagger.
$$

所有 $n\times n$ 酉矩阵组成酉群：

$$
U(n)=\{U\in GL(n,\mathbb C)\mid U^\dagger U=I\}.
$$

## 为什么酉矩阵保持复内积

复向量的标准内积为：

$$
\langle x,y\rangle=x^\dagger y.
$$

变换 $x\mapsto Ux$、$y\mapsto Uy$ 后：

$$
\langle Ux,Uy\rangle
=(Ux)^\dagger(Uy)
=x^\dagger U^\dagger Uy
=x^\dagger y.
$$

所以长度、夹角和量子概率归一化都保持不变。

## 从 $U(n)$ 到 $SU(n)$

特殊酉群定义为：

$$
SU(n)=\{U\in U(n)\mid\det U=1\}.
$$

字母含义是：

- $U$：unitary，酉；
- $S$：special，特殊，即行列式被限制为 $1$；
- $n$：复向量空间的复维数，也是矩阵行数。

## 酉矩阵的行列式模长

对 $U^\dagger U=I$ 取行列式：

$$
\det(U^\dagger)\det U=1.
$$

又因为：

$$
\det(U^\dagger)=(\det U)^*,
$$

所以：

$$
|\det U|^2=1,
$$

即：

$$
|\det U|=1.
$$

因此 $U(n)$ 元素的行列式是单位复数；$SU(n)$ 进一步只保留行列式恰好为 $1$ 的元素。

## 为什么 $SU(n)$ 是群

若 $U,V\in SU(n)$，则：

$$
(UV)^\dagger(UV)
=V^\dagger U^\dagger UV
=I,
$$

且：

$$
\det(UV)=\det U\det V=1.
$$

单位矩阵属于 $SU(n)$，逆矩阵 $U^{-1}=U^\dagger$ 也属于 $SU(n)$。结合律来自矩阵乘法，因此 $SU(n)$ 满足群公理。

## 为什么 $SU(n)$ 是 Lie 群

$SU(n)$ 是复矩阵空间中的实光滑子流形，矩阵乘法和取逆均光滑，因此是矩阵 Lie 群。

这里“实光滑流形”很重要：虽然矩阵元素是复数，Lie 群维数通常按独立实参数计数。

## $U(1)$ 与 $SU(1)$

$U(1)$ 是所有单位复数：

$$
U(1)=\{e^{i\theta}\mid\theta\in\mathbb R\}.
$$

而 $1\times1$ 矩阵的行列式就是它自身。要求行列式为 $1$ 后只剩：

$$
SU(1)=\{1\}.
$$

所以 $SU(1)$ 是平凡群，不等于 $U(1)$。

## $SU(2)$ 的一般形式

任意 $SU(2)$ 元素可写为：

$$
U=
\begin{pmatrix}
\alpha&\beta\\
-\beta^*&\alpha^*
\end{pmatrix},
$$

并满足：

$$
|\alpha|^2+|\beta|^2=1.
$$

令：

$$
\alpha=a+ib,\qquad\beta=c+id,
$$

则约束变成：

$$
a^2+b^2+c^2+d^2=1.
$$

因此 $SU(2)$ 作为流形与三维球面 $S^3$ 同胚，并且是单连通的。

## Pauli 矩阵

$SU(2)$ 的常用 Hermitian 生成元由 Pauli 矩阵给出：

$$
\sigma_1=
\begin{pmatrix}0&1\\1&0\end{pmatrix},
\quad
\sigma_2=
\begin{pmatrix}0&-i\\i&0\end{pmatrix},
\quad
\sigma_3=
\begin{pmatrix}1&0\\0&-1\end{pmatrix}.
$$

常取：

$$
T_a=\frac{\sigma_a}{2}.
$$

它们满足：

$$
[T_a,T_b]=i\varepsilon_{abc}T_c.
$$

## $SU(2)$ 元素的指数形式

单位向量 $\hat n$ 和实参数 $\theta$ 给出：

$$
U(\theta,\hat n)
=\exp\left(-i\frac\theta2\hat n\cdot\boldsymbol\sigma\right).
$$

利用 $(\hat n\cdot\boldsymbol\sigma)^2=I$，可展开为：

$$
U(\theta,\hat n)
=I\cos\frac\theta2
-i(\hat n\cdot\boldsymbol\sigma)\sin\frac\theta2.
$$

半角 $\theta/2$ 是 $SU(2)$ 双覆盖 $SO(3)$ 的关键。

## $2\pi$ 与 $4\pi$ 旋转

代入 $\theta=2\pi$：

$$
U(2\pi,\hat n)=-I.
$$

代入 $\theta=4\pi$：

$$
U(4\pi,\hat n)=I.
$$

在 $SO(3)$ 中，$2\pi$ 旋转已是单位元；在 $SU(2)$ 中，对应的元素是 $-I$。$I$ 与 $-I$ 映到同一个三维旋转，这就是二对一覆盖。

## $SU(n)$ 的实维数

一般复 $n\times n$ 矩阵有 $2n^2$ 个实参数。

酉条件 $U^\dagger U=I$ 给出 $n^2$ 个独立实约束，因此：

$$
\dim_{\mathbb R}U(n)=n^2.
$$

再要求 $\det U=1$ 去掉一个连续实相位参数，所以：

$$
\dim_{\mathbb R}SU(n)=n^2-1.
$$

例如：

- $\dim SU(2)=3$；
- $\dim SU(3)=8$。

## Lie 代数 $\mathfrak{u}(n)$

单位元附近写：

$$
U(t)=I+tX+O(t^2).
$$

代入：

$$
U(t)^\dagger U(t)=I
$$

并保留一阶项，得到：

$$
X^\dagger+X=0.
$$

因此数学中常用的约定是：

$$
\mathfrak u(n)
=\{X\in M_n(\mathbb C)\mid X^\dagger=-X\},
$$

即 anti-Hermitian 矩阵。

## Lie 代数 $\mathfrak{su}(n)$

行列式条件在无穷小层面给出无迹条件：

$$
\operatorname{tr}X=0.
$$

所以数学约定下：

$$
\mathfrak{su}(n)
=\{X\in M_n(\mathbb C)
\mid X^\dagger=-X,\ \operatorname{tr}X=0\}.
$$

它是 traceless anti-Hermitian 矩阵组成的实向量空间。

## 为什么出现无迹条件

对任意方阵 $X$，有：

$$
\det(e^{tX})=e^{t\operatorname{tr}X}.
$$

若 $e^{tX}$ 对所有足够小 $t$ 都属于 $SU(n)$，则行列式恒为 $1$，因此：

$$
\operatorname{tr}X=0.
$$

所以“特殊”在 Lie 代数层面表现为无迹。

## 物理学常用的 Hermitian 约定

物理中常把 anti-Hermitian 元素写成：

$$
X=i\theta^aT_a,
$$

其中 $T_a$ 取 Hermitian 且无迹：

$$
T_a^\dagger=T_a,
\qquad
\operatorname{tr}T_a=0.
$$

有限变换写成：

$$
U=e^{i\theta^aT_a}
$$

或因主动、被动变换约定写成 $e^{-i\theta^aT_a}$。

数学与物理约定描述同一结构，只是把因子 $i$ 放在不同位置。

## 结构常数

在 Hermitian 基下通常写：

$$
[T_a,T_b]=if_{ab}{}^cT_c.
$$

$SU(2)$ 的结构常数可取 $\varepsilon_{abc}$。$SU(3)$ 有八个生成元，常用 Gell-Mann 矩阵的一半作为基。

结构常数依赖生成元归一化；比较不同资料时必须同时核对基和迹归一化。

## $SU(n)$ 的中心

$SU(n)$ 中与所有群元素对易的标量矩阵组成中心：

$$
Z(SU(n))
=\left\{e^{2\pi ik/n}I\mid k=0,1,\ldots,n-1\right\}.
$$

它同构于有限循环群：

$$
Z(SU(n))\cong\mathbb Z_n.
$$

对中心取商可得到：

$$
PSU(n)=SU(n)/\mathbb Z_n.
$$

$SU(n)$ 与 $PSU(n)$ 有同一个 Lie 代数，但全局群和允许表示不同。

## $SU(2)$ 与 $SO(3)$

$SU(2)$ 的中心为：

$$
\{I,-I\}\cong\mathbb Z_2.
$$

并且：

$$
SO(3)\cong SU(2)/\mathbb Z_2.
$$

它们 Lie 代数同构：

$$
\mathfrak{su}(2)\cong\mathfrak{so}(3),
$$

但群的全局拓扑和表示内容不同。

## 基本表示与伴随表示

$SU(n)$ 直接作用在 $\mathbb C^n$ 上的表示叫基本表示，维数为 $n$。

Lie 代数对自身通过对易子作用：

$$
\operatorname{ad}_X(Y)=[X,Y],
$$

得到伴随表示，其维数为：

$$
n^2-1.
$$

例如 $SU(3)$ 的伴随表示是八维，对应八个胶子所携带的规范代数指标。

## 紧致性与单连通性

$SU(n)$ 是紧、连通 Lie 群。对 $n\ge2$，$SU(n)$ 还是单连通的。

这些是全局拓扑事实，不能只从局部 Lie 代数结构直接推出。它们影响群表示、拓扑缺陷和规范理论中的全局问题。

## 在量子力学中的作用

二能级量子系统的纯态变换与 $SU(2)$ 密切相关。忽略不可观测整体相位后，Bloch 球上的旋转由 $SO(3)$ 描述，而作用在二分量态矢量上的变换由 $SU(2)$ 描述。

这正体现了 $SU(2)$ 双覆盖 $SO(3)$：两个相差整体负号的 $SU(2)$ 元素诱导同一个 Bloch 球旋转。

## 在粒子物理中的作用

标准模型的局部规范代数通常写成：

$$
\mathfrak{su}(3)_C
\oplus\mathfrak{su}(2)_L
\oplus\mathfrak{u}(1)_Y.
$$

其中：

- $SU(3)_C$ 与强相互作用色对称相关；
- $SU(2)_L$ 与弱同位旋相关；
- $U(1)_Y$ 与弱超荷相关。

精确全局规范群可能涉及离散商，因此仅写局部直积不等于给出全部全局信息。

## 在弦理论中的作用

$SU(n)$ 在弦理论中可出现于：

- D-brane 上规范群的子群或低能有效规范对称；
- 弦态和场的表示分类；
- Calabi–Yau 流形的 $SU(3)$ holonomy；
- 束的结构群与杂化弦紧致化；
- 世界面电流代数和 affine $\mathfrak{su}(n)$；
- 对偶和增强规范对称点。

具体出现 $U(n)$、$SU(n)$ 还是离散商群，取决于整体构型、中心、荷谱和其他一致性条件，不能只由局部 Lie 代数决定。

## 一个计算例子：$SU(2)$ 绕 $z$ 轴

取生成元：

$$
T_3=\frac{\sigma_3}{2}
=\frac12
\begin{pmatrix}1&0\\0&-1\end{pmatrix}.
$$

对应变换：

$$
U_z(\theta)=e^{-i\theta T_3}
=
\begin{pmatrix}
e^{-i\theta/2}&0\\
0&e^{i\theta/2}
\end{pmatrix}.
$$

它是酉矩阵，且：

$$
\det U_z(\theta)
=e^{-i\theta/2}e^{i\theta/2}=1.
$$

当 $\theta=2\pi$ 时 $U_z=-I$；当 $\theta=4\pi$ 时 $U_z=I$。

## 适用条件与事实边界

1. $U(n)$ 保持标准复内积；$SU(n)$ 还要求行列式为 $1$。
2. $SU(n)$ 的维数按实参数计为 $n^2-1$，不是复维数 $n^2-1$。
3. 数学约定下 $\mathfrak{su}(n)$ 由无迹 anti-Hermitian 矩阵组成；物理常改用无迹 Hermitian 生成元并在指数中加入 $i$。
4. 生成元对易关系中的因子 $i$、正负号和结构常数数值依赖约定与归一化。
5. $SU(1)$ 是平凡群；$U(1)$ 是圆群，两者不同。
6. $SU(2)$ 作为流形同胚于 $S^3$，并双覆盖 $SO(3)$。
7. $SU(n)$ 和 $PSU(n)=SU(n)/\mathbb Z_n$ 有同构 Lie 代数，但全局表示与拓扑信息不同。
8. 对 $n\ge2$，$SU(n)$ 紧、连通且单连通。
9. $SU(3)$ 的八个生成元与群的八维伴随表示相关，但不能把生成元本身简单称为粒子。
10. 弦紧致化中出现的 $SU(n)$ 结构必须结合 holonomy、规范束和全局商条件具体判断。

## 常见误区

1. **$SU(n)$ 中的 $S$ 表示对称。** 它表示 special，即行列式为 $1$。
2. **酉矩阵只需满足 $U^TU=I$。** 复矩阵必须使用 Hermitian 共轭 $U^\dagger$。
3. **$SU(n)$ 的维数是 $n$。** 其实维数是 $n^2-1$。
4. **$SU(2)$ 就是 $SO(3)$。** 前者是后者的双覆盖，不是同一个群。
5. **数学和物理给出的 $\mathfrak{su}(n)$ 矩阵条件互相矛盾。** 它们通常只差因子 $i$ 的约定。
6. **$2\pi$ 旋转在 $SU(2)$ 中一定是单位矩阵。** 它对应 $-I$；$4\pi$ 才回到 $I$。
7. **相同 Lie 代数意味着相同允许表示。** 全局中心商可能排除某些表示。
8. **$SU(3)$ 有八个生成元，所以基本表示是八维。** 基本表示是三维，伴随表示才是八维。
9. **所有 D-brane 构型都直接给 $SU(N)$。** 常见重合定向 D-brane 先给 $U(N)$；具体投影和背景可改变群。

## 练习

1. 写出 $U(n)$ 与 $SU(n)$ 的定义。
2. 证明酉变换保持复内积。
3. 为什么酉矩阵的行列式模长为 $1$？
4. $SU(1)$ 与 $U(1)$ 分别是什么？
5. 推导 $\dim_{\mathbb R}SU(n)=n^2-1$。
6. 数学约定下，$\mathfrak{su}(n)$ 中的矩阵满足哪两个条件？
7. 物理学为何常使用 Hermitian 生成元？
8. 写出 $SU(2)$ 的三个 Pauli 生成元 $T_a$。
9. $SU(2)\to SO(3)$ 的核是什么？
10. $SU(n)$ 的中心同构于哪个有限群？

## 答案与提示

1. $U(n)=\{U\mid U^\dagger U=I\}$；$SU(n)=\{U\in U(n)\mid\det U=1\}$。
2. $(Ux)^\dagger(Uy)=x^\dagger U^\dagger Uy=x^\dagger y$。
3. 对酉条件取行列式，得到 $(\det U)^*\det U=1$。
4. $SU(1)=\{1\}$；$U(1)=\{e^{i\theta}\}$。
5. $2n^2$ 个实矩阵参数减去 $n^2$ 个酉约束，再减去一个行列式相位参数。
6. $X^\dagger=-X$ 且 $\operatorname{tr}X=0$。
7. 这样可把量子可观测量与生成元写成 Hermitian 矩阵，把因子 $i$ 放入指数。
8. $T_a=\sigma_a/2$，其中 $\sigma_1,\sigma_2,\sigma_3$ 为正文所列 Pauli 矩阵。
9. $\{I,-I\}\cong\mathbb Z_2$。
10. $\mathbb Z_n$。

## 与其他概念的关系

- [[弦理论/数学/Lie 群]] 提供连续群与光滑结构；
- [[弦理论/数学/Lie 代数]] 描述 $SU(n)$ 的无穷小生成元；
- [[弦理论/数学/复数]] 提供复共轭、复相位和单位复数；
- [[弦理论/数学/矩阵]] 提供 Hermitian 共轭、逆矩阵、迹和行列式；
- [[弦理论/数学/内积空间]] 解释酉变换为何保持概率内积；
- [[弦理论/数学/SU(2) 与 SO(3) 的双覆盖]] 详细解释半角、覆盖核和半整数自旋；
- [[弦理论/数学/群表示]] 区分基本表示、伴随表示和其他不可约表示；
- [[弦理论/数学/旋量]] 与 $SU(2)\cong Spin(3)$ 的表示密切相关；
- [[弦理论/物理学/自旋]] 使用 $SU(2)$ 表示分类三维旋转下的量子态；
- [[弦理论/物理学/Yang-Mills 理论]] 常以 $SU(n)$ 作为规范群。

## 参考资料

- Brian C. Hall, *Lie Groups, Lie Algebras, and Representations*, 2nd ed., Springer, 2015.
- Howard Georgi, *Lie Algebras in Particle Physics*, 2nd ed., Westview Press, 1999.
- John F. Cornwell, *Group Theory in Physics, Vol. 1*, Academic Press, 1984.
- Michael Tinkham, *Group Theory and Quantum Mechanics*, Dover, 2003.
- Matthew Robinson, *Symmetry and the Standard Model*, Springer, 2011.
- Mikio Nakahara, *Geometry, Topology and Physics*, 2nd ed., CRC Press, 2003.
- Steven Weinberg, *The Quantum Theory of Fields, Vol. 2*, Cambridge University Press, 1996.
- Joseph Polchinski, *String Theory, Vol. 2*, Cambridge University Press, 1998.