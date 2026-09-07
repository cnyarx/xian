---
aliases:
  - Special Orthogonal Group
  - SO(n)
  - 特殊正交群
english_name: Special Orthogonal Group
tags:
  - 数学
  - 群论
  - 几何
  - 弦理论先修
prerequisites:
  - "[[弦理论/数学/Lie 群]]"
  - "[[弦理论/数学/Lie 代数]]"
  - "[[弦理论/数学/矩阵]]"
  - "[[弦理论/数学/内积空间]]"
used_by:
  - "[[弦理论/数学/SU(2) 与 SO(3) 的双覆盖]]"
  - "[[弦理论/数学/Clifford 代数]]"
  - "[[弦理论/数学/旋量]]"
  - "[[弦理论/物理学/角动量]]"
  - "[[弦理论/物理学/Lorentz 变换]]"
evidence_status: 教材事实
---

# SO 群（Special Orthogonal Group）

## 一句话解释

$SO(n)$ 是所有保持 $n$ 维实空间长度、角度和定向不变的线性旋转组成的 Lie 群。

## 为什么要学它

物理规律通常不应依赖实验装置朝向。把整个实验旋转后，长度、角度和内积不变；这种连续旋转由 $SO(n)$ 描述。

三维角动量、自旋、旋量、相对论中的空间旋转，以及高维弦理论中的旋转对称，都需要区分 $SO(n)$、它的 Lie 代数 $\mathfrak{so}(n)$ 和它的双覆盖 $Spin(n)$。

## 正交矩阵

设 $R$ 是 $n\times n$ 实矩阵。若：

$$
R^TR=I,
$$

则 $R$ 叫正交矩阵。

这里：

- $R^T$：$R$ 的转置；
- $I$：单位矩阵；
- 等式表示 $R^{-1}=R^T$。

所有正交矩阵组成正交群：

$$
O(n)=\{R\in GL(n,\mathbb R)\mid R^TR=I\}.
$$

## 为什么正交矩阵保持长度

对向量 $x\in\mathbb R^n$，变换后为 $Rx$。其长度平方为：

$$
(Rx)^T(Rx)
=x^TR^TRx
=x^Tx.
$$

所以：

$$
\|Rx\|=\|x\|.
$$

同理，对任意向量 $x,y$：

$$
(Rx)\cdot(Ry)=x\cdot y.
$$

因此夹角也保持不变。

## 从 $O(n)$ 到 $SO(n)$

对正交矩阵取行列式：

$$
\det(R^TR)=\det I=1.
$$

又因为 $\det(R^T)=\det R$，所以：

$$
(\det R)^2=1,
$$

即：

$$
\det R=+1\quad\text{或}\quad -1.
$$

特殊正交群定义为：

$$
SO(n)=\{R\in O(n)\mid\det R=1\}.
$$

“特殊”指行列式被限制为 $+1$。

## 行列式在这里表示什么

行列式描述线性变换对有向体积的缩放倍数。

正交变换只可能有行列式 $+1$ 或 $-1$：

- $+1$：保持定向，属于 $SO(n)$；
- $-1$：翻转定向，通常包含反射，不属于 $SO(n)$。

所以 $SO(n)$ 描述纯旋转，而 $O(n)$ 还包含反射类变换。

## 为什么 $SO(n)$ 是群

若 $R_1,R_2\in SO(n)$，则：

$$
(R_1R_2)^T(R_1R_2)
=R_2^TR_1^TR_1R_2
=I,
$$

且：

$$
\det(R_1R_2)=\det R_1\det R_2=1.
$$

单位矩阵 $I$ 属于 $SO(n)$，而逆矩阵 $R^{-1}=R^T$ 也满足相同条件。矩阵乘法具有结合律，因此 $SO(n)$ 满足群公理。

## 为什么 $SO(n)$ 是 Lie 群

$SO(n)$ 是实矩阵空间中的光滑子流形，矩阵乘法和取逆在其上都是光滑映射，因此它是矩阵 Lie 群。

其元素可连续变化。例如二维旋转由角度 $\theta$ 连续参数化。

## $SO(2)$：平面旋转

二维旋转矩阵为：

$$
R(\theta)=
\begin{pmatrix}
\cos\theta&-\sin\theta\\
\sin\theta&\cos\theta
\end{pmatrix}.
$$

它满足：

$$
R(\theta)^TR(\theta)=I,
\qquad
\det R(\theta)=1.
$$

旋转合成满足：

$$
R(\theta_1)R(\theta_2)
=R(\theta_1+\theta_2).
$$

因为 $\theta$ 与 $\theta+2\pi$ 表示同一旋转，$SO(2)$ 的群流形同胚于圆周 $S^1$。

## $SO(2)$ 是 Abel 群

二维旋转只有一个旋转平面，因此：

$$
R(\theta_1)R(\theta_2)
=R(\theta_2)R(\theta_1).
$$

所以 $SO(2)$ 是 Abel Lie 群。

但从三维开始，绕不同轴旋转的先后顺序通常会影响结果，因此 $SO(n)$ 在 $n\ge3$ 时一般非 Abel。

## $SO(3)$：三维旋转

$SO(3)$ 描述三维 Euclidean 空间中保持长度、角度和定向的旋转。

绕 $z$ 轴旋转角度 $\theta$ 的矩阵为：

$$
R_z(\theta)=
\begin{pmatrix}
\cos\theta&-\sin\theta&0\\
\sin\theta&\cos\theta&0\\
0&0&1
\end{pmatrix}.
$$

类似地可写出绕 $x$、$y$ 轴的旋转。绕不同轴的旋转通常不对易。

## 旋转轴与角度

任意 $SO(3)$ 元素都可表示为绕某条通过原点的轴旋转某个角度。这是三维旋转的轴—角表示。

但轴—角参数并非全局唯一：

- 旋转角 $0$ 时轴任意；
- 绕轴 $\hat n$ 转 $\theta$ 与绕 $-\hat n$ 转 $-\theta$ 相同；
- 角度 $\pi$ 时还出现边界识别。

因此参数冗余反映了 $SO(3)$ 的非平凡全局拓扑。

## $SO(n)$ 的维数

$n\times n$ 实矩阵最初有 $n^2$ 个实参数。条件：

$$
R^TR=I
$$

给出 $n(n+1)/2$ 个独立约束，因为 $R^TR$ 是对称矩阵。

所以：

$$
\dim SO(n)
=n^2-\frac{n(n+1)}2
=\frac{n(n-1)}2.
$$

这也等于在 $n$ 维空间中选择一个二维旋转平面的独立方式数。

例如：

- $\dim SO(2)=1$；
- $\dim SO(3)=3$；
- $\dim SO(4)=6$。

## Lie 代数 $\mathfrak{so}(n)$

单位元附近写：

$$
R(t)=I+tX+O(t^2).
$$

代入正交条件：

$$
R(t)^TR(t)=I
$$

并保留 $t$ 的一阶项，得到：

$$
X^T+X=0.
$$

所以：

$$
\mathfrak{so}(n)
=\{X\in M_n(\mathbb R)\mid X^T=-X\}.
$$

即 $\mathfrak{so}(n)$ 由所有实反对称矩阵组成。

## 为什么反对称矩阵有 $n(n-1)/2$ 个参数

反对称条件：

$$
X_{ij}=-X_{ji}
$$

要求对角元为零：

$$
X_{ii}=0.
$$

矩阵上三角的每个元素决定下三角对应元素，所以独立参数数目是：

$$
\frac{n(n-1)}2.
$$

这与 $SO(n)$ 的流形维数一致。

## 二维生成元

$\mathfrak{so}(2)$ 的一个生成元可取：

$$
J=
\begin{pmatrix}
0&-1\\
1&0
\end{pmatrix}.
$$

有限旋转由指数映射给出：

$$
R(\theta)=e^{\theta J}.
$$

因为 $J^2=-I$，可求得：

$$
e^{\theta J}=I\cos\theta+J\sin\theta.
$$

## 一般旋转平面生成元

对每一对不同坐标方向 $i<j$，可定义生成元 $J_{ij}$，其矩阵只在 $i,j$ 两个方向组成的平面内产生无穷小旋转。

一种常见实反对称约定为：

$$
(J_{ij})_{kl}
=\delta_{ik}\delta_{jl}-\delta_{il}\delta_{jk}.
$$

这里 $\delta_{ij}$ 是 Kronecker delta：指标相等时为 $1$，不等时为 $0$。

## $\mathfrak{so}(n)$ 的对易关系

在上述约定下，生成元满足：

$$
[J_{ij},J_{kl}]
=\delta_{jk}J_{il}-\delta_{ik}J_{jl}
-\delta_{jl}J_{ik}+\delta_{il}J_{jk}.
$$

不同教材可能把生成元乘以 $i$ 或整体负号，因此公式符号会随 Hermitian、anti-Hermitian 约定改变。比较公式时必须先核对约定。

## $\mathfrak{so}(3)$ 与角动量

三维中可把三个独立生成元重新编号为 $J_1,J_2,J_3$，常见 Hermitian 物理约定下：

$$
[J_i,J_j]=i\varepsilon_{ijk}J_k.
$$

$\varepsilon_{ijk}$ 是 Levi-Civita 符号。量子力学中的角动量算符满足同样的 Lie 代数关系。

这说明角动量是旋转的无穷小生成元。

## $SO(3)$ 与 $SU(2)$

存在二对一覆盖同态：

$$
SU(2)\to SO(3).
$$

它的核为：

$$
\{I,-I\}.
$$

因此：

$$
SO(3)\cong SU(2)/\{\pm I\}.
$$

两者 Lie 代数同构，但全局群不同。$SU(2)$ 是单连通的，$SO(3)$ 不是单连通的。

## 为什么半整数自旋需要覆盖群

标量、普通三维向量和整数自旋态可形成 $SO(3)$ 的普通表示。

半整数自旋态在旋转 $2\pi$ 后可能变号，旋转 $4\pi$ 才恢复原值。因此它们不能作为 $SO(3)$ 的普通单值表示，而应视为双覆盖 $SU(2)\cong Spin(3)$ 的表示。

变号不表示物理射线一定改变，但在叠加、干涉和多粒子系统中，这个群表示结构具有可观测后果。

## $SO(n)$ 与 $Spin(n)$

对 $n\ge3$，旋转群 $SO(n)$ 有一个双覆盖群：

$$
Spin(n)\to SO(n).
$$

$Spin(n)$ 可用 Clifford 代数构造，其表示包含旋量表示。

这就是学习 $SO(n)$ 后需要继续学习 Clifford 代数、Gamma 矩阵和旋量的原因。

## $SO(n)$ 的连通性与紧致性

对 $n\ge2$，$SO(n)$ 是连通的紧 Lie 群。

$O(n)$ 则有行列式 $+1$ 与 $-1$ 两个连通分支；$SO(n)$ 是包含单位元的分支。

特别地，$SO(1)=\{1\}$ 是只有一个元素的平凡群。

## Euclidean 旋转与 Lorentz 群的区别

$SO(n)$ 保持正定 Euclidean 内积：

$$
x^Tx.
$$

相对论的 Lorentz 变换保持带一个时间方向负号或正号的非正定二次型，例如：

$$
- (x^0)^2+(x^1)^2+\cdots+(x^{D-1})^2.
$$

对应群记作 $O(1,D-1)$ 或 $O(D-1,1)$，并非普通紧群 $SO(D)$。具体符号取决于度量号差约定。

## 在物理中的作用

$SO(3)$ 描述三维空间旋转，$SO(D-1)$ 描述 $D$ 维 Minkowski 时空中静止有质量粒子的空间小群。

无质量粒子的小群结构不同，不能仅用 $SO(D-1)$ 分类。

场和粒子态按照旋转群或其覆盖群的表示变换：标量不变，向量按定义表示变换，旋量按 $Spin(n)$ 表示变换。

## 在弦理论中的作用

弦理论中 $SO(n)$ 出现在：

- 目标空间的 Euclidean 旋转；
- 光锥规范下横向方向的旋转群；
- 弦态按小群表示分类；
- 紧致化空间的切空间结构群；
- 旋量、超对称和 R 扇区零模的表示理论。

在十维 Minkowski 时空中，无质量态的物理横向旋转小群与 $SO(8)$ 密切相关；其旋量表示和 triality 是超弦谱的重要结构。但这需要结合 Lorentz 小群与光锥量子化的具体条件理解。

## 一个计算例子：绕 $z$ 轴旋转

取向量：

$$
x=
\begin{pmatrix}
1\\0\\0
\end{pmatrix}.
$$

施加 $R_z(\theta)$：

$$
R_z(\theta)x
=
\begin{pmatrix}
\cos\theta\\
\sin\theta\\
0
\end{pmatrix}.
$$

长度仍为：

$$
\sqrt{\cos^2\theta+\sin^2\theta}=1.
$$

当 $\theta=\pi/2$ 时，向量从 $x$ 轴正方向转到 $y$ 轴正方向。

## 适用条件与事实边界

1. $O(n)$ 由保持标准实内积的正交矩阵组成；$SO(n)$ 还要求行列式为 $+1$。
2. $SO(n)$ 保持长度、角度和定向；$O(n)$ 中行列式为 $-1$ 的分支包含定向翻转。
3. $SO(n)$ 的实流形维数是 $n(n-1)/2$，不是 $n$。
4. $\mathfrak{so}(n)$ 由实反对称矩阵组成。
5. 生成元及对易关系中的因子 $i$ 和整体符号依赖约定。
6. $SO(2)$ 是 Abel 群；$SO(n)$ 在 $n\ge3$ 时一般非 Abel。
7. 对 $n\ge2$，$SO(n)$ 连通且紧；$O(n)$ 有两个行列式不同的连通分支。
8. $SO(3)$ 与 $SU(2)$ 具有同构 Lie 代数，但不是同一个全局群。
9. 半整数自旋是 $Spin(n)$ 等覆盖群的表示，不能仅靠 $SO(n)$ 的普通表示完整描述。
10. Euclidean 旋转群 $SO(n)$ 与非紧 Lorentz 群 $SO(1,n-1)$ 不同。
11. 十维超弦中的 $SO(8)$ 结论依赖无质量小群和光锥规范语境，不能直接当作完整十维 Lorentz 群。

## 常见误区

1. **$SO(n)$ 中的 $S$ 表示对称。** $S$ 表示 special，即行列式为 $+1$。
2. **所有正交矩阵都是旋转。** 行列式为 $-1$ 的正交矩阵会翻转定向，通常含反射。
3. **$SO(n)$ 的维数是 $n$。** 正确维数是 $n(n-1)/2$。
4. **三维绕不同轴旋转可以任意交换顺序。** $SO(3)$ 非 Abel，顺序通常重要。
5. **$SO(3)$ 和 $SU(2)$ 完全相同。** 它们局部代数相同，但 $SU(2)$ 双覆盖 $SO(3)$。
6. **$2\pi$ 旋转对任何量子态都等于恒等。** 半整数自旋态在 $2\pi$ 旋转下可变号。
7. **$SO(n)$ 就是 Lorentz 群。** 前者保持正定 Euclidean 内积，后者保持非正定时空度量。
8. **旋量是 $SO(n)$ 的普通向量表示。** 旋量属于覆盖群 $Spin(n)$ 的表示。
9. **某个坐标矩阵看起来复杂，长度就会改变。** 是否保长应检查 $R^TR=I$，而不是凭外观判断。

## 练习

1. 写出 $O(n)$ 和 $SO(n)$ 的定义。
2. 用 $R^TR=I$ 证明正交变换保持向量长度。
3. 为什么正交矩阵的行列式只能是 $\pm1$？
4. 写出二维旋转矩阵 $R(\theta)$。
5. $SO(2)$ 为什么是 Abel 群？
6. 推导 $\dim SO(n)=n(n-1)/2$。
7. 从 $R(t)=I+tX+O(t^2)$ 推导 $X^T=-X$。
8. $SO(3)$ 与 $SU(2)$ 的覆盖映射是几对一？核是什么？
9. 为什么半整数自旋不能成为 $SO(3)$ 的普通单值表示？
10. Euclidean 旋转群和 Lorentz 群保持的二次型有何不同？

## 答案与提示

1. $O(n)=\{R\mid R^TR=I\}$；$SO(n)=\{R\in O(n)\mid\det R=1\}$。
2. $(Rx)^T(Rx)=x^TR^TRx=x^Tx$。
3. 对 $R^TR=I$ 取行列式得 $(\det R)^2=1$。
4. $R(\theta)=\begin{pmatrix}\cos\theta&-\sin\theta\\\sin\theta&\cos\theta\end{pmatrix}$。
5. 旋转合成等于角度相加，而实数加法可交换。
6. $n^2$ 个矩阵分量减去对称矩阵方程提供的 $n(n+1)/2$ 个独立约束。
7. 展开得 $(I+tX^T)(I+tX)=I+t(X^T+X)+O(t^2)$，故一阶系数为零。
8. 二对一，核为 $\{I,-I\}$。
9. 半整数自旋表示中 $2\pi$ 旋转可作用为 $-I$，而在 $SO(3)$ 中 $2\pi$ 旋转就是单位元。
10. $SO(n)$ 保持正定 $x^Tx$；Lorentz 群保持含时间与空间不同符号的非正定二次型。

## 与其他概念的关系

- [[弦理论/数学/Lie 群]] 提供连续矩阵群的总体框架；
- [[弦理论/数学/Lie 代数]] 描述 $SO(n)$ 的无穷小生成元；
- [[弦理论/数学/矩阵]] 提供转置、逆矩阵、乘法和行列式语言；
- [[弦理论/数学/内积空间]] 解释正交变换为何保持长度和角度；
- [[弦理论/数学/SU(2) 与 SO(3) 的双覆盖]] 详细解释三维旋转与半整数自旋；
- [[弦理论/数学/Clifford 代数]] 用于构造 $Spin(n)$；
- [[弦理论/数学/Gamma 矩阵]] 给出 Clifford 代数的矩阵表示；
- [[弦理论/数学/旋量]] 是旋转覆盖群的表示对象；
- [[弦理论/物理学/角动量]] 是三维旋转的量子生成元；
- [[弦理论/物理学/Lorentz 变换]] 使用保持 Minkowski 度量的伪正交群。

## 参考资料

- Brian C. Hall, *Lie Groups, Lie Algebras, and Representations*, 2nd ed., Springer, 2015.
- Howard Georgi, *Lie Algebras in Particle Physics*, 2nd ed., Westview Press, 1999.
- John F. Cornwell, *Group Theory in Physics, Vol. 1*, Academic Press, 1984.
- Michael Tinkham, *Group Theory and Quantum Mechanics*, Dover, 2003.
- Mikio Nakahara, *Geometry, Topology and Physics*, 2nd ed., CRC Press, 2003.
- Steven Weinberg, *The Quantum Theory of Fields, Vol. 1*, Cambridge University Press, 1995.
- Joseph Polchinski, *String Theory, Vol. 1*, Cambridge University Press, 1998.
- [MIT OpenCourseWare 18.701, Algebra I](https://ocw.mit.edu/courses/18-701-algebra-i-fall-2010/)