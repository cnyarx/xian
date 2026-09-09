---
aliases:
  - Lie Algebra
  - 李代数
english_name: Lie Algebra
tags:
  - 数学
  - 群论
  - 代数
  - 对称性
  - 弦理论先修
prerequisites:
  - "[[弦理论/数学/向量空间]]"
  - "[[弦理论/数学/线性映射]]"
  - "[[弦理论/物理学/对易关系]]"
  - "[[弦理论/数学/群表示]]"
used_by:
  - "[[弦理论/数学/Lie 群]]"
  - "[[弦理论/数学/Lie 群与 Lie 代数的对应]]"
  - "[[弦理论/数学/SO 群]]"
  - "[[弦理论/数学/SU 群]]"
  - "[[弦理论/物理学/Yang-Mills 理论]]"
  - "[[弦理论/物理学/beta 函数]]"
  - "[[弦理论/物理学/BRST 对称性]]"
evidence_status: 教材事实
---

# Lie 代数（Lie Algebra）

## 一句话解释

Lie 代数是带有一种反对称括号运算的向量空间，用来描述连续对称变换在单位元附近的无穷小组合规律。

## 为什么要学它

连续旋转、Lorentz 变换和规范变换往往由矩阵指数表示。直接处理所有有限变换可能很复杂，而单位元附近的无穷小生成元满足更简单的线性关系和对易关系。

Lie 代数用于：

- 推导角动量对易关系；
- 分类旋转群和 Lorentz 群表示；
- 定义规范场的生成元与结构常数；
- 描述世界面 current algebra；
- 组织超对称、BRST 和弦态的对称结构。

## 直观图景

想象所有有限旋转组成一张弯曲的连续空间。单位元是“旋转零度”的点。

在单位元附近，小旋转可以用切向量近似。所有这样的无穷小方向构成一个向量空间。

先做两个不同方向的小变换再反向比较，其不交换部分产生另一个无穷小方向。这个“交换次序留下的差”就是 Lie 括号的直观来源。

## 正式定义

数域 $\mathbb F$ 上的 Lie 代数 $\mathfrak g$ 是一个向量空间，并带有双线性运算：

$$
[\cdot,\cdot]:
\mathfrak g\times\mathfrak g\to\mathfrak g,
$$

称为 Lie 括号，满足：

1. 双线性；
2. 反对称性；
3. Jacobi 恒等式。

对任意 $X,Y,Z\in\mathfrak g$ 和标量 $a,b\in\mathbb F$，下面逐条说明。

## 双线性

Lie 括号对两个输入分别线性：

$$
[aX+bY,Z]
=a[X,Z]+b[Y,Z],
$$

$$
[Z,aX+bY]
=a[Z,X]+b[Z,Y].
$$

这保证可以先在一组基底生成元上定义括号，再线性推广到整个空间。

## 反对称性

$$
[X,Y]=-[Y,X].
$$

令 $X=Y$，在特征不为 $2$ 的数域上有：

$$
[X,X]=0.
$$

这表示一个无穷小变换与自身交换时没有不对易残差。

## Jacobi 恒等式

$$
[X,[Y,Z]]
+[Y,[Z,X]]
+[Z,[X,Y]]=0.
$$

Jacobi 恒等式约束三种嵌套括号的关系，保证这些无穷小生成元能以一致方式组合。

它不是普通结合律。Lie 括号通常不满足：

$$
[X,[Y,Z]]=[[X,Y],Z].
$$

## 最重要的例子：矩阵对易子

设 $X,Y$ 是同样大小的矩阵，定义：

$$
[X,Y]=XY-YX.
$$

它满足双线性、反对称性和 Jacobi 恒等式，因此一组对这种括号封闭的矩阵构成 Lie 代数。

例如所有 $n\times n$ 复矩阵构成：

$$
\mathfrak{gl}(n,\mathbb C).
$$

这里 Lie 括号是矩阵对易子，不是矩阵乘法本身。

## 为什么对易子满足 Jacobi 恒等式

展开：

$$
[X,[Y,Z]]
=X(YZ-ZY)-(YZ-ZY)X,
$$

以及循环的另外两项。把所有三矩阵乘积展开后，每一项都出现一次正号和一次负号，最终完全抵消。

这个证明依赖底层矩阵乘法的结合律。

## 基底与结构常数

选取 Lie 代数基底：

$$
T_1,T_2,\ldots,T_n.
$$

任意括号仍在 Lie 代数内，因此可展开为：

$$
[T_a,T_b]
=f_{ab}{}^cT_c.
$$

重复指标 $c$ 表示求和。

$f_{ab}{}^c$ 叫结构常数。反对称性给出：

$$
f_{ab}{}^c=-f_{ba}{}^c.
$$

它们的具体数值依赖基底选择，但编码的抽象 Lie 代数结构不依赖某个特定基底。

## 物理中的 $i$ 约定

物理教材常选 Hermitian 生成元，并写成：

$$
[T_a,T_b]
=if_{ab}{}^cT_c.
$$

数学教材可能选 anti-Hermitian 生成元，公式中没有显式 $i$。

这通常是基底和约定差异，不表示两个 Lie 代数物理内容不同。比较公式时必须先核对生成元是否 Hermitian。

## Jacobi 恒等式对结构常数的约束

把基底括号代入 Jacobi 恒等式，可得：

$$
f_{ab}{}^d f_{dc}{}^e
+f_{bc}{}^d f_{da}{}^e
+f_{ca}{}^d f_{db}{}^e
=0
$$

在不显式写 $i$ 的约定下成立。

这说明结构常数不能任意指定；它们必须满足非线性一致性条件。

## Abel Lie 代数

若所有括号都为零：

$$
[X,Y]=0
$$

对所有 $X,Y$ 成立，就称 Abel Lie 代数。

例如一维 Lie 代数只有一个生成元 $T$，必有：

$$
[T,T]=0.
$$

$U(1)$ 的 Lie 代数是典型一维 Abel Lie 代数。

连续群是否全局 Abel 与其 Lie 代数是否 Abel 密切相关，但 Lie 代数只控制单位元连通分支的局部结构，不能看见所有离散全局信息。

## $\mathfrak{so}(3)$ 例子

三维旋转的生成元 $J_i$ 满足：

$$
[J_i,J_j]
=i\hbar\epsilon_{ijk}J_k.
$$

若定义无量纲生成元：

$$
T_i=\frac{J_i}{\hbar},
$$

则：

$$
[T_i,T_j]
=i\epsilon_{ijk}T_k.
$$

这就是物理常用的 $\mathfrak{so}(3)$ 或等价局部结构 $\mathfrak{su}(2)$ 的对易关系。

## $\epsilon_{ijk}$ 是什么

$\epsilon_{ijk}$ 是 Levi-Civita 符号：

- $(i,j,k)$ 为 $(1,2,3)$ 的偶排列时取 $+1$；
- 为奇排列时取 $-1$；
- 任意两个指标相同时取 $0$。

例如：

$$
[J_x,J_y]=i\hbar J_z,
$$

$$
[J_y,J_x]=-i\hbar J_z.
$$

这体现旋转生成元不交换。

## $\mathfrak{su}(2)$ 的 Pauli 矩阵表示

取：

$$
T_i=\frac{\sigma_i}{2},
$$

其中 $\sigma_i$ 是 Pauli 矩阵。它们满足：

$$
[\sigma_i,\sigma_j]
=2i\epsilon_{ijk}\sigma_k.
$$

所以：

$$
[T_i,T_j]
=i\epsilon_{ijk}T_k.
$$

这是 $\mathfrak{su}(2)$ 的二维基本表示。

## Lie 代数不等于矩阵集合本身

抽象 Lie 代数只要求向量空间和 Lie 括号。矩阵对易子是实现它的一种表示。

同一个抽象 Lie 代数可以用不同大小的矩阵表示。例如 $\mathfrak{su}(2)$ 有二维、三维以及更高维表示。

因此不应把抽象生成元 $T_a$ 与某个特定表示中的矩阵永久绑定。

## Lie 代数同态

两个 Lie 代数之间的线性映射：

$$
\varphi:\mathfrak g\to\mathfrak h
$$

若满足：

$$
\varphi([X,Y])
=[\varphi(X),\varphi(Y)],
$$

就称为 Lie 代数同态。

若它是双射，就得到 Lie 代数同构。

## Lie 代数表示

Lie 代数表示是线性映射：

$$
\rho:\mathfrak g\to\mathfrak{gl}(V)
$$

并保持括号：

$$
\rho([X,Y])
=[\rho(X),\rho(Y)].
$$

右边是线性算符对易子。

在基底中，若：

$$
[T_a,T_b]=if_{ab}{}^cT_c,
$$

表示矩阵 $t_a=\rho(T_a)$ 必须满足：

$$
[t_a,t_b]=if_{ab}{}^ct_c.
$$

## 伴随表示

Lie 代数通过括号作用在自身上：

$$
\operatorname{ad}_X(Y)=[X,Y].
$$

这定义伴随表示：

$$
\operatorname{ad}:\mathfrak g
\to\mathfrak{gl}(\mathfrak g).
$$

在基底中：

$$
(\operatorname{ad}_{T_a})_b{}^c
=f_{ab}{}^c
$$

在无显式 $i$ 的约定下成立。

规范场通常携带 Lie 代数的伴随指标。

## 理想

子空间 $\mathfrak h\subseteq\mathfrak g$ 若满足：

$$
[X,Y]\in\mathfrak h
$$

对所有 $X\in\mathfrak g$、$Y\in\mathfrak h$ 成立，就称 $\mathfrak h$ 是理想。

理想是 Lie 代数中对应正规子群的结构。只有理想才能自然构造商 Lie 代数：

$$
\mathfrak g/\mathfrak h.
$$

## 中心

Lie 代数的中心是：

$$
Z(\mathfrak g)
=\{X\in\mathfrak g:[X,Y]=0
\text{ 对所有 }Y\in\mathfrak g\}.
$$

中心中的元素与所有生成元对易。

中心扩张在量子理论中很重要，例如 Virasoro 代数是 Witt 代数的中心扩张。

## 子代数

若向量子空间 $\mathfrak h\subseteq\mathfrak g$ 对 Lie 括号封闭：

$$
[X,Y]\in\mathfrak h
$$

对所有 $X,Y\in\mathfrak h$ 成立，则它是 Lie 子代数。

子代数只要求内部括号封闭；理想还要求与整个 $\mathfrak g$ 中任意元素做括号后仍留在 $\mathfrak h$。

## 指数映射预告

矩阵 Lie 代数元素 $X$ 可通过矩阵指数产生群元素：

$$
\exp X
=I+X+\frac{X^2}{2!}+\frac{X^3}{3!}+\cdots.
$$

若参数很小：

$$
e^{\varepsilon X}
=I+\varepsilon X+O(\varepsilon^2).
$$

所以 $X$ 是有限变换 $e^{\varepsilon X}$ 在单位元处的切向方向。

指数映射通常能描述单位元附近的群元素，但不保证对任意 Lie 群都是全局一一或满射。

## 对易子如何测量不交换性

取小参数 $\varepsilon$，考虑群交换子：

$$
e^{\varepsilon X}
e^{\varepsilon Y}
e^{-\varepsilon X}
e^{-\varepsilon Y}.
$$

展开到最低非平凡阶：

$$
=I+\varepsilon^2[X,Y]+O(\varepsilon^3).
$$

如果 $[X,Y]=0$，两种小变换在这一阶交换；若不为零，交换次序会留下新的无穷小变换。

## Baker–Campbell–Hausdorff 公式预告

两个指数乘积可形式上写成一个指数：

$$
e^Xe^Y
=\exp\left(
X+Y+\frac12[X,Y]
+\frac1{12}[X,[X,Y]]
+\frac1{12}[Y,[Y,X]]
+\cdots
\right).
$$

它说明有限群乘法在单位元附近由 Lie 括号及其嵌套结构控制。

该级数的收敛和全局使用需要条件；入门阶段主要把它作为局部形式公式。

## Casimir 算符预告

Lie 代数表示中，若某个由生成元构造的算符与所有生成元对易，就称 Casimir 算符。

例如 $\mathfrak{su}(2)$ 中：

$$
\mathbf J^2
=J_x^2+J_y^2+J_z^2
$$

满足：

$$
[\mathbf J^2,J_i]=0.
$$

在不可约表示中，Casimir 通常作用成常数倍单位算符，可用于标记表示。

## Lie 代数与角动量

量子角动量满足：

$$
[J_i,J_j]
=i\hbar\epsilon_{ijk}J_k.
$$

这套关系决定：

- 不能同时精确测量三个角动量分量；
- 可选 $J^2$ 与一个分量 $J_z$ 同时对角化；
- 升降算符改变磁量子数；
- 不可约表示由 $j=0,1/2,1,\ldots$ 分类。

这些结论不仅来自某个具体微分算符形式，也来自 Lie 代数结构。

## Lie 代数与规范场

设规范代数生成元满足：

$$
[T_a,T_b]=if_{ab}{}^cT_c.
$$

规范场写成 Lie 代数值形式：

$$
A_\mu(x)=A_\mu^a(x)T_a.
$$

非 Abel 场强包含对易子：

$$
F_{\mu\nu}
=\partial_\mu A_\nu
-\partial_\nu A_\mu
-ig[A_\mu,A_\nu]
$$

在一种常见物理约定下。

若 Lie 代数 Abel，对易子项为零；非 Abel 结构使规范场发生自相互作用。

## Lie 代数与 Poisson 括号

经典力学中，一组生成函数可能在 Poisson 括号下闭合：

$$
\{Q_a,Q_b\}_{\mathrm P}
=f_{ab}{}^cQ_c.
$$

量子化后常对应：

$$
[\hat Q_a,\hat Q_b]
=i\hbar f_{ab}{}^c\hat Q_c
$$

在没有反常和排序修正的理想情形下。

实际量子化可能出现中心项或反常，不能把经典括号到量子对易子的替换当作无条件严格规则。

## Lie 代数与世界面 CFT

二维 CFT 的全纯流可能满足 affine Lie algebra 或 Kac–Moody 代数：

$$
J^a(z)J^b(w)
\sim
\frac{k\delta^{ab}}{(z-w)^2}
+\frac{if^{ab}{}_cJ^c(w)}{z-w}
+\cdots.
$$

这里普通 Lie 代数结构常数出现在简单极点，而双极点给出中心扩张的 level $k$。

因此世界面 current algebra 是有限维 Lie 代数的无限维环代数扩张，而不是简单等同于原 Lie 代数。

## 在弦理论中的作用

Lie 代数用于：

- 描述目标时空 Lorentz 与旋转生成元；
- 描述开放弦 Chan–Paton 规范代数；
- 分类杂化弦的规范结构；
- 构造世界面 current algebra；
- 表达 BRST 变换的闭合关系；
- 检查反常消除中的群论系数；
- 分析紧致化后的规范对称与 holonomy。

全局规范群不能只由 Lie 代数唯一决定。例如 $SU(2)$ 与 $SO(3)$ 具有同构 Lie 代数，却有不同全局拓扑和表示内容。

## 一个计算例子

取 Pauli 矩阵：

$$
\sigma_x=
\begin{pmatrix}0&1\\1&0\end{pmatrix},
\quad
\sigma_y=
\begin{pmatrix}0&-i\\i&0\end{pmatrix},
\quad
\sigma_z=
\begin{pmatrix}1&0\\0&-1\end{pmatrix}.
$$

计算：

$$
\sigma_x\sigma_y=i\sigma_z,
$$

$$
\sigma_y\sigma_x=-i\sigma_z.
$$

所以：

$$
[\sigma_x,\sigma_y]
=2i\sigma_z.
$$

令 $T_i=\sigma_i/2$，得到：

$$
[T_x,T_y]=iT_z.
$$

循环交换指标可得完整 $\mathfrak{su}(2)$ 对易关系。

## 适用条件与事实边界

1. Lie 代数是带 Lie 括号的向量空间，不是只有一张对易关系表。
2. Lie 括号满足 Jacobi 恒等式，但通常不满足结合律。
3. 结构常数依赖基底；抽象 Lie 代数不依赖某一组具体数值表示。
4. 数学与物理教材可能因 Hermitian 或 anti-Hermitian 生成元约定而相差因子 $i$ 和符号。
5. Lie 代数描述 Lie 群单位元附近及其连通分支的局部结构，不能决定全部全局拓扑。
6. 同一个 Lie 代数可有许多不同维数的表示。
7. 指数映射通常是局部工具，不保证全局一一或满射。
8. 经典 Poisson 括号量子化为对易子时可能出现排序、中心项或反常。
9. 世界面 affine Lie algebra 含无限多个模和中心扩张，不等于有限维 Lie 代数本身。
10. 指定规范 Lie 代数仍不足以完整定义量子规范理论，还需全局群、场表示、作用量和量子一致性条件。

## 常见误区

1. **Lie 代数就是普通可结合代数。** Lie 括号通常不结合，只满足 Jacobi 恒等式。
2. **Lie 括号一定是矩阵对易子。** 矩阵对易子是重要实现，但定义可以是抽象的。
3. **结构常数在所有基底中数值相同。** 改变基底会改变其分量。
4. **交换生成元顺序不影响结果。** 非 Abel Lie 代数的核心正是不对易。
5. **$SU(2)$ 与 $SO(3)$ Lie 代数同构，所以两个群完全相同。** 它们的全局拓扑和允许表示不同。
6. **知道 Lie 代数就知道完整规范群。** 还需全局群结构及中心取商信息。
7. **指数映射为每个群元素提供唯一生成元。** 一般既不唯一，也不保证覆盖所有元素。
8. **经典对称代数量子化后一定原样保留。** 可能出现中心扩张或反常。
9. **中心元素等于普通群单位元。** Lie 代数中心是与所有元素括号为零的子空间。

## 练习

1. 写出 Lie 代数的三条核心性质。
2. 用矩阵对易子说明反对称性。
3. 结构常数 $f_{ab}{}^c$ 表示什么？
4. Abel Lie 代数的括号有什么特点？
5. 为什么 $[X,[Y,Z]]$ 一般不能改成 $[[X,Y],Z]$？
6. 写出 $\mathfrak{su}(2)$ 的生成元对易关系。
7. 什么是 Lie 代数表示？
8. 伴随表示怎样作用在 Lie 代数自身上？
9. 为什么同构 Lie 代数不保证对应 Lie 群全局相同？

## 答案与提示

1. 括号双线性、反对称，并满足 Jacobi 恒等式。
2. $[Y,X]=YX-XY=-(XY-YX)=-[X,Y]$。
3. 它们是在选定基底中把 $[T_a,T_b]$ 展开为 $T_c$ 线性组合的系数。
4. 所有元素之间的 Lie 括号都为零。
5. Lie 括号通常不满足结合律；正确约束是 Jacobi 恒等式。
6. 常用 Hermitian 约定下 $[T_i,T_j]=i\epsilon_{ijk}T_k$。
7. 保持括号的线性映射 $\rho:\mathfrak g\to\mathfrak{gl}(V)$。
8. $\operatorname{ad}_X(Y)=[X,Y]$。
9. Lie 代数只描述单位元附近的局部结构，不能看见基本群、中心取商等全局信息。

## 与其他概念的关系

- [[弦理论/数学/向量空间]] 是 Lie 代数的底层线性结构；
- [[弦理论/物理学/对易关系]] 的矩阵或算符对易子给出最重要的 Lie 括号实例；
- [[弦理论/数学/群表示]] 为 Lie 代数表示提供向量空间和生成元矩阵背景；
- [[弦理论/数学/Lie 群]] 的单位元切空间带自然 Lie 代数结构；
- [[弦理论/数学/Lie 群与 Lie 代数的对应]] 解释指数映射和局部群乘法；
- [[弦理论/数学/SO 群]] 与 [[弦理论/数学/SU 群]] 具有重要矩阵 Lie 代数；
- [[弦理论/物理学/角动量]] 满足 $\mathfrak{su}(2)$ 型对易关系；
- [[弦理论/物理学/Yang-Mills 理论]] 使用 Lie 代数值规范场和非 Abel 场强；
- [[弦理论/物理学/beta 函数]] 中 QCD 的一圈系数使用 $C_A$、$T_F$ 和生成元迹归一化。

## 参考资料

- Brian C. Hall, *Lie Groups, Lie Algebras, and Representations*, 2nd ed., Springer, 2015.
- Anthony W. Knapp, *Lie Groups Beyond an Introduction*, 2nd ed., Birkhäuser, 2002.
- James E. Humphreys, *Introduction to Lie Algebras and Representation Theory*, Springer, 1972.
- Howard Georgi, *Lie Algebras in Particle Physics*, 2nd ed., Westview Press, 1999.
- [MIT OpenCourseWare 18.755, Introduction to Lie Groups](https://ocw.mit.edu/courses/18-755-introduction-to-lie-groups-fall-2004/)
- J. J. Sakurai and Jim Napolitano, *Modern Quantum Mechanics*, 3rd ed., Cambridge University Press, 2020.
- Michael E. Peskin and Daniel V. Schroeder, *An Introduction to Quantum Field Theory*, Westview Press, 1995.
- Joseph Polchinski, *String Theory, Vol. 1–2*, Cambridge University Press, 1998.
