---
aliases:
  - 2D Euclidean Field Theory
  - Euclidean 场论
  - 二维欧几里得场论
english_name: 2D Euclidean Field Theory
tags:
  - 物理学
  - 量子场论
  - 二维场论
  - 共形场论先修
  - 弦理论先修
prerequisites:
  - "[[弦理论/物理学/Wick 旋转]]"
  - "[[弦理论/物理学/路径积分]]"
  - "[[弦理论/物理学/能动张量]]"
  - "[[弦理论/数学/度量]]"
  - "[[弦理论/数学/复分析]]"
  - "[[弦理论/数学/Green 函数]]"
used_by:
  - "[[弦理论/数学/复坐标与全纯分解]]"
  - "[[弦理论/物理学/二维自由玻色子]]"
  - "[[弦理论/弦理论完整学习路线图]]"
  - "[[弦理论与大模型跨学科关系图谱]]"
evidence_status: 教材事实
---

# 二维 Euclidean 场论（2D Euclidean Field Theory）

## 学习导航

- 上一页：[[弦理论/物理学/反常消除]]
- 下一页：[[弦理论/数学/复坐标与全纯分解]]
- 总路线：[[弦理论/弦理论完整学习路线图]]

## 一句话解释

二维 Euclidean 场论是在正定二维几何上，以 $e^{-S_E}$ 路径积分和 Euclidean 关联函数描述量子或统计涨落的框架；它是二维共形场论与弦世界面计算的直接入口，但只有满足解析性、反射正性等条件的 Euclidean 数据才能重构为一致的 Lorentz 量子理论。

## 为什么要学它

前面的 [[弦理论/物理学/Weyl 反常]] 与 [[弦理论/物理学/反常消除]] 已经说明：经典对称性、量子测度、正规化和完整一致性条件必须分开检查。接下来需要进入弦世界面真正使用的计算语言。

二维 Euclidean 场论把以下内容连接起来：

1. [[弦理论/物理学/Wick 旋转]] 把 Lorentz 振荡权重变为 Euclidean 衰减权重；
2. [[弦理论/物理学/路径积分]] 和 [[弦理论/物理学/生成泛函]] 定义关联函数；
3. [[弦理论/数学/复分析]] 把两个实坐标组织成 $z,\bar z$；
4. [[弦理论/数学/Green 函数]] 给出二维自由场的对数二点函数；
5. [[弦理论/物理学/能动张量]]、Weyl 变换和二维共形结构组织守恒律；
6. [[弦理论/数学/共形映射]] 的指数映射把圆柱 Euclidean 时间变成平面半径；
7. [[弦理论/数学/黎曼曲面]] 提供高亏格弦世界面的全局几何。

本页只建立共同约定和计算入口。复坐标下的系统全纯分解由 [[弦理论/数学/复坐标与全纯分解]] 展开，量子自由场计算由 [[弦理论/物理学/二维自由玻色子]] 展开；一般 OPE、共形权、径向量子化、态—算符对应以及 Virasoro 代数留给后续独立节点。

## 从 Lorentz 理论到 Euclidean 理论

考虑一个 $1+1$ 维 Lorentz 理论，采用 mostly-minus 度量：

$$
ds_M^2=dt^2-dx^2.
$$

在满足解析条件并结合正确极点处方时，令

$$
t=-i\tau,
\qquad
dt=-i\,d\tau.
$$

则 Euclidean 线元为

$$
ds_E^2=d\tau^2+dx^2.
$$

Lorentz 路径积分权重

$$
e^{iS_M}
$$

相应变为

$$
e^{-S_E}
$$

，这里采用 $\hbar=1$。因此 Euclidean 配分函数形式为

$$
\boxed{
Z_E=\int\mathcal D\Phi\,e^{-S_E[\Phi]}
}.
$$

这一步不是把公式中的字母 $t$ 机械替换成 $-i\tau$。必须同时追踪：

- 时间导数和积分测度；
- 传播子的 $i\varepsilon$ 极点处方；
- 真空与边界条件；
- 费米场和张量分量的延拓；
- 返回 Lorentz 运动学区域的解析路径。

因此 Euclidean 场论通常由 Lorentz 理论的解析延拓得到，也可以先作为满足适当公理的 Euclidean 理论定义，再尝试重构 Lorentz 理论；两种叙述都不能省略一致性条件。

## 二维实坐标和复坐标

把两个 Euclidean 实坐标记为

$$
(x,y),
$$

其中在 Wick 旋转语境中可把 $y$ 视为 Euclidean 时间 $\tau$。定义

$$
\boxed{
z=x+iy,
\qquad
\bar z=x-iy
}.
$$

这里 $z$ 与 $\bar z$ 在真实 Euclidean 截面上互为复共轭。在解析延拓或复化场论中，它们也常暂时作为形式独立变量处理。

定义 Wirtinger 导数：

$$
\boxed{
\partial
\equiv\partial_z
=\frac12(\partial_x-i\partial_y),
\qquad
\bar\partial
\equiv\partial_{\bar z}
=\frac12(\partial_x+i\partial_y)
}.
$$

反解为

$$
\partial_x=\partial+\bar\partial,
\qquad
\partial_y=i(\partial-\bar\partial).
$$

因此二维 Laplace 算符满足

$$
\boxed{
\Delta
=\partial_x^2+\partial_y^2
=4\partial\bar\partial
}.
$$

这个因子 $4$ 与后续 Green 函数和二点函数的归一化直接相关，不能单独更改。

## 面积元、微分形式与度量约定

本页固定

$$
\boxed{
d^2z\equiv dx\,dy
}.
$$

由

$$
dz=dx+i\,dy,
\qquad
d\bar z=dx-i\,dy
$$

可得微分形式恒等式

$$
dz\wedge d\bar z=-2i\,dx\wedge dy,
$$

所以在标准定向下

$$
\boxed{
d^2z=\frac{i}{2}\,dz\wedge d\bar z
}.
$$

这里必须区分：

- $dz\wedge d\bar z$ 是反对称微分形式；
- 线元中的 $dz\,d\bar z$ 是对称张量乘积的简写。

平直 Euclidean 度量写成

$$
\boxed{
ds^2=dx^2+dy^2=dz\,d\bar z
}.
$$

若按

$$
ds^2
=g_{zz}dz^2
+2g_{z\bar z}dz\,d\bar z
+g_{\bar z\bar z}d\bar z^2
$$

展开，则本页约定为

$$
\boxed{
g_{z\bar z}=g_{\bar z z}=\frac12,
\qquad
g^{z\bar z}=g^{\bar z z}=2
}.
$$

有些教材把因子 $2$ 吸收到复坐标度量分量中，使用 $g_{z\bar z}=1$。跨教材比较时必须连同线元、面积元、delta 函数和作用量整体转换，不能只替换一个分量。

一般二维 Riemannian 度量在每一点附近都可选取等温坐标，使其写成

$$
\boxed{
ds^2=e^{2\omega(z,\bar z)}dz\,d\bar z
}.
$$

这是局部共形平坦性，不表示曲率、拓扑或模参数可被全局消除。

## 普通自由实标量场

在平直二维 Euclidean 空间上，普通规范化的自由实标量作用量为

$$
\boxed{
S_E[\phi]
=
\frac12\int d^2z\,
\left[
\partial_a\phi\,\partial_a\phi
+m^2\phi^2
\right]
}.
$$

利用

$$
\partial_a\phi\,\partial_a\phi
=(\partial_x\phi)^2+(\partial_y\phi)^2
=4\partial\phi\,\bar\partial\phi,
$$

可写为

$$
S_E[\phi]
=
2\int d^2z\,
\partial\phi\,\bar\partial\phi
+
\frac{m^2}{2}\int d^2z\,\phi^2.
$$

在边界项消失或边界条件适当时，分部积分得到

$$
S_E[\phi]
=
\frac12\int d^2z\,
\phi(-\Delta+m^2)\phi.
$$

Euler–Lagrange 方程为

$$
\boxed{
(-\Delta+m^2)\phi=0
}.
$$

质量为零时：

$$
\partial\bar\partial\phi=0.
$$

局部上这提示解可拆成只依赖 $z$ 和只依赖 $\bar z$ 的部分，但全局单值性、边界条件、零模和量子算符结构仍需额外处理。本页不把局部微分方程直接升级为完整量子全纯分解。

## 曲背景上的标量场

在带正定度量 $h_{ab}$ 的二维曲面 $\Sigma$ 上：

$$
\boxed{
S_E[\phi;h]
=
\frac12\int_\Sigma d^2\sigma\sqrt h\,
\left(
h^{ab}\partial_a\phi\partial_b\phi
+m^2\phi^2
\right)
}.
$$

Laplace–Beltrami 算符为

$$
\Delta_h\phi
=
\frac1{\sqrt h}
\partial_a\left(
\sqrt h\,h^{ab}\partial_b\phi
\right).
$$

运动方程为

$$
(-\Delta_h+m^2)\phi=0.
$$

在二维，质量为零的最小耦合标量动能项在经典 Weyl 变换

$$
h_{ab}\longmapsto e^{2\omega}h_{ab}
$$

下不变，因为

$$
\sqrt h\longmapsto e^{2\omega}\sqrt h,
\qquad
h^{ab}\longmapsto e^{-2\omega}h^{ab}.
$$

质量项不具有这个抵消，因此显式引入尺度并破坏经典 Weyl 对称性。

## 弦世界面标量的不同规范化

弦坐标场 $X^\mu$ 不是按上一节普通标量的 $1/2$ 系数规范化。平直 Euclidean 世界面上的 Polyakov 物质作用量为

$$
\boxed{
S_E[X]
=
\frac{1}{4\pi\alpha'}
\int d^2z\,
\partial_aX^\mu\partial_aX_\mu
}.
$$

在本页的复坐标约定下：

$$
\boxed{
S_E[X]
=
\frac{1}{\pi\alpha'}
\int d^2z\,
\partial X^\mu\bar\partial X_\mu
}.
$$

普通标量与弦坐标场的作用量系数不同，所以二点函数前因子也不同。不能先采用普通标量 Green 函数，再遗漏 $\alpha'$ 规范化直接写成弦传播子。

## Euclidean 生成泛函和关联函数

加入外源 $J$ 后定义

$$
\boxed{
Z_E[J]
=
\int\mathcal D\phi\,
\exp\left[
-S_E[\phi]
+\int d^2z\,J(z)\phi(z)
\right]
}.
$$

归一化生成泛函为

$$
\mathcal Z_E[J]
=
\frac{Z_E[J]}{Z_E[0]}.
$$

于是

$$
\left.
\frac{\delta^n\mathcal Z_E[J]}
{\delta J(z_1)\cdots\delta J(z_n)}
\right|_{J=0}
=
\langle
\phi(z_1)\cdots\phi(z_n)
\rangle_E.
$$

一般局域算符的归一化关联函数写成

$$
\boxed{
\langle\mathcal O_1\cdots\mathcal O_n\rangle_E
=
\frac1{Z_E[0]}
\int\mathcal D\phi\,
\mathcal O_1\cdots\mathcal O_n
\,e^{-S_E[\phi]}
}.
$$

自由二次理论中，形式 Gaussian 积分给出

$$
Z_E[J]
=
Z_E[0]
\exp\left[
\frac12
\int d^2z\,d^2w\,
J(z)G(z,w)J(w)
\right].
$$

这个公式要求二次算符在指定边界条件下可逆，或者所有零模已被分离和单独积分；行列式与泛函测度也必须经过正规化。

## 二维 Green 函数的分布归一化

定义二维 delta 函数：

$$
\int d^2z\,
\delta^{(2)}(z-w)f(z,\bar z)
=f(w,\bar w).
$$

本页约定下的基本分布恒等式是

$$
\boxed{
\Delta\ln|z|^2
=4\pi\delta^{(2)}(z)
}.
$$

由于 $\Delta=4\partial\bar\partial$，等价地

$$
\boxed{
\partial\bar\partial\ln|z|^2
=\pi\delta^{(2)}(z)
}.
$$

这些等式只在分布意义下成立。对 $z\ne0$，$\ln|z|^2$ 是调和函数；delta 函数来自原点奇点的边界通量。

若无质量 Green 函数定义为

$$
-\Delta G_0(z)=\delta^{(2)}(z),
$$

则可取

$$
\boxed{
G_0(z)
=-\frac1{4\pi}
\ln\left(\mu^2|z|^2\right)
}.
$$

也可写成

$$
G_0(r)
=-\frac1{2\pi}\ln(\mu r),
\qquad r=|z|.
$$

$\mu$ 是使对数自变量无量纲的红外参考尺度。改变 $\mu$ 只给 $G_0$ 增加常数，这正反映二维无质量 Laplace 算符的常数零模和红外歧义。

## 有质量 Green 函数与无质量极限

二维平面上的有质量 Green 函数为

$$
\boxed{
G_m(r)=\frac1{2\pi}K_0(mr)
},
$$

满足

$$
(-\Delta+m^2)G_m(z)=\delta^{(2)}(z).
$$

这里 $K_0$ 是第二类修正 Bessel 函数。小参数展开为

$$
K_0(mr)
=-\ln\frac{mr}{2}-\gamma
+O\!\left(m^2r^2\ln(mr)\right).
$$

因此 $m\to0$ 时恢复对数的空间依赖，同时产生发散的加法常数。质量 $m$ 可以作为红外调节器，但调节后的有质量理论并不具有原无质量理论的全部尺度或共形性质；必须说明在哪些观测量中以及怎样取无质量极限。

## 弦坐标场的二点函数

由弦世界面作用量的系数得到

$$
\boxed{
\langle
X^\mu(z,\bar z)X^\nu(w,\bar w)
\rangle
=
-\frac{\alpha'}2
\eta^{\mu\nu}
\ln\left(\mu^2|z-w|^2\right)
}.
$$

这里目标时空指标由 $\eta^{\mu\nu}$ 收缩，而 $z,\bar z$ 描述的是 Euclidean 世界面。不能因世界面采用 Euclidean 签名就推断目标时空也必须 Euclidean 化。

若保留 Lorentz 目标度量，timelike 分量 $X^0$ 的世界面二次型具有与 spacelike 分量不同的符号。此时二点函数应理解为从适当轮廓或目标时间解析延拓得到的形式 CFT 关联函数，不能把每个 $X^\mu$ 都当作具有普通正定 Gaussian 测度和逐场 OS 反射正性的标量。完整规范固定弦世界面还包含鬼场，物理幺正性最终在约束或 BRST 物理态空间中检验。

教材常把公式简写为

$$
-\frac{\alpha'}2\eta^{\mu\nu}\ln|z-w|^2.
$$

这省略了一个加法常数。对导数场或满足总动量中性条件的顶点算符关联函数，该常数通常不影响结果；但它不能消除 $X^\mu$ 本身的红外零模问题。

## 紧致曲面上的常数零模

无质量作用量只依赖导数：

$$
S_E[\phi]
=
\frac12\int d^2z\,(\partial_a\phi)^2.
$$

因此它在常数平移

$$
\phi(z)\longmapsto\phi(z)+c
$$

下不变。常数函数满足

$$
-\Delta_h1=0.
$$

在体积有限、无边界的紧致曲面 $\Sigma$ 上，先定义相对于不变量测度归一化的协变 delta 分布：

$$
\boxed{
\int_\Sigma d^2x\sqrt{h(x)}\,
\delta_h(x,y)f(x)=f(y)
}.
$$

它在局部坐标中可写为

$$
\delta_h(x,y)
=\frac{\delta^{(2)}(x-y)}{\sqrt{h(x)}}.
$$

不可能存在满足

$$
-\Delta_{h,x}G(x,y)=\delta_h(x,y)
$$

的普通全局逆，因为对 $x$ 使用不变量测度积分后左边为零、右边为一。

正确做法是把常数模投影掉：

$$
\boxed{
-\Delta_{h,x}G(x,y)
=
\delta_h(x,y)-\frac1V
},
$$

其中

$$
V=\int_\Sigma d^2x\sqrt h.
$$

还可选择归一化条件

$$
\int_\Sigma d^2x\sqrt h\,G(x,y)=0.
$$

常见处理方式包括：

1. 分解 $\phi=\phi_0+\phi'$，单独积分常数模；
2. 固定 $\phi'$ 的平均值为零；
3. 使用投影 Green 函数；
4. 暂时加入质量调节器，再控制 $m\to0$；
5. 计算对常数平移不敏感的导数字段；
6. 对指数算符要求总电荷或总动量中性。

弦世界面上，$X^\mu$ 的零模积分通常产生目标时空动量守恒 delta 函数：

$$
(2\pi)^D
\delta^{(D)}\!\left(\sum_i k_i\right).
$$

所以“处理零模”不等于随意删除它；零模可能编码重要的全局守恒律。

## 反射正性与 Lorentz 理论重构

Euclidean 作用量是实数或非负，并不足以单独证明理论对应一个幺正 Lorentz 量子场论。设 Euclidean 时间反射为

$$
\theta:(\tau,x)\longmapsto(-\tau,x).
$$

若泛函 $F$ 只依赖 $\tau>0$ 半空间内的场，Osterwalder–Schrader 反射正性形式上要求

$$
\boxed{
\langle(\Theta F)F\rangle_E\ge0
}.
$$

$\Theta$ 除了反射坐标，还包含复共轭以及场分量所需的变换。反射正性是 Lorentz 理论中正定 Hilbert 空间和幺正时间演化在 Euclidean 表述中的遗迹。

完整重构还需要 Euclidean 不变性、置换对称性、适当正则性与增长条件、聚类等结构。因此：

- 任意写下的 Euclidean 关联函数不一定来自一致的 Lorentz QFT；
- 错误符号动能项和某些高阶导数理论可能违反反射正性；
- 格点或数值 Euclidean 数据恢复实时谱通常是病态解析延拓问题；
- 规范固定后的规范势与鬼场不必各自具有普通正定 Hilbert 空间解释，物理正定性需在约束或 BRST 物理子空间中判断。

## Euclidean 能动张量

本页沿用 [[弦理论/物理学/Weyl 反常]] 的 Euclidean 变分约定。经典能动张量定义为

$$
\boxed{
T_{ab}
=-\frac2{\sqrt h}
\frac{\delta S_E}{\delta h^{ab}}
}.
$$

量子期望值则由

$$
W_E[h]=-\ln Z_E[h]
$$

定义：

$$
\boxed{
\langle T_{ab}\rangle
=-\frac2{\sqrt h}
\frac{\delta W_E}{\delta h^{ab}}
}.
$$

按这套对逆度量变分的符号约定，普通标量给出

$$
T_{ab}
=-\partial_a\phi\partial_b\phi
+\frac12h_{ab}
\left[(\nabla\phi)^2+m^2\phi^2\right].
$$

二维中的经典迹为

$$
\boxed{
T^a{}_a=m^2\phi^2
}.
$$

所以无质量时经典迹消失，质量项则显式破坏尺度和 Weyl 对称性。其他教材可能对 $h_{ab}$ 变分或采用相反的 $T_{ab}$ 定义，导致所有分量整体反号；比较时必须先核对定义。

## 二维为什么在共形问题中特殊

### 每个二维度量局部共形平坦

在足够小的邻域内，可写

$$
h_{ab}=e^{2\omega}\delta_{ab}.
$$

这使二维几何天然适合用复坐标和 Weyl 因子描述。但局部形式不能消除全局亏格、边界、曲率积分和模参数。

### 无质量标量的经典动能项 Weyl 不变

二维中 $\sqrt h$ 和 $h^{ab}$ 的 Weyl 因子恰好抵消。因此自由无质量标量提供最基本的二维经典共形场论候选。

然而“无质量”不是量子共形不变的充分条件。耦合常数的 beta 函数、正规化、改进能动张量和 [[弦理论/物理学/Weyl 反常]] 都可能改变量子结论。

### 局部共形映射具有全纯结构

保持定向的局部二维 Euclidean 共形变换可写为

$$
z\longmapsto f(z),
\qquad
\bar z\longmapsto\bar f(\bar z).
$$

这使二维局部共形变换候选形成远比高维丰富的结构。本页只给入口，不在尚未建立 OPE 和径向量子化前推导 Witt 或 Virasoro 代数。

## 经典迹为零与量子 Weyl 反常

经典无质量作用量满足

$$
T^a{}_a=0
$$

并不保证量子期望值仍为零。在非手征二维 CFT 和 [[弦理论/物理学/Weyl 反常]] 所采用的 Euclidean 约定下：

$$
\boxed{
\langle T^a{}_a\rangle_E
=-\frac{c}{24\pi}R^{(2)}
}.
$$

这里 $c$ 是相应二维系统的中心荷，$R^{(2)}$ 是世界面标量曲率。该公式描述量子测度和正规化对局部 Weyl 变换的响应，不应被解释为普通质量项。

因此需要分开判断：

1. 经典作用量是否 Weyl 不变；
2. 量子 beta 函数或 Weyl anomaly coefficients 是否消失；
3. 总物质、鬼和其他扇区的中心荷是否满足完整世界面一致性条件。

## 圆柱到平面的指数映射

令 Euclidean 圆柱坐标为

$$
w=\tau+i\sigma,
\qquad
\sigma\sim\sigma+2\pi.
$$

指数映射

$$
\boxed{
z=e^w=e^{\tau+i\sigma}
}
$$

把无限圆柱映到穿孔复平面 $\mathbb C^\times$。因为

$$
|z|=e^\tau,
\qquad
\arg z=\sigma,
$$

所以

$$
\tau_1>\tau_2
\quad\Longleftrightarrow\quad
|z_1|>|z_2|.
$$

圆柱上较晚的 Euclidean 时间对应平面上更大的半径。于是时间排序的几何角色转化为径向排序：较大 $|z|$ 的算符放在较小 $|z|$ 的算符外侧。

极限关系为：

$$
\tau\to-\infty
\Longleftrightarrow z\to0,
$$

$$
\tau\to+\infty
\Longleftrightarrow z\to\infty.
$$

这是径向量子化的入口，但不是完整定义。从这张几何图到 Hilbert 空间、态—算符对应、共形 Hamiltonian 和 Casimir 能位移，还需要后续独立构造。

## 与统计物理的关系

经典统计系统的配分函数具有 Boltzmann 形式

$$
Z_{\mathrm{stat}}
=\sum_{\{\text{configurations}\}}e^{-\beta H}.
$$

Euclidean 场论则形式上写为

$$
Z_E=\int\mathcal D\phi\,e^{-S_E[\phi]}.
$$

共同的衰减权重使两者建立精确而受条件约束的联系：

1. 二维经典晶格模型在连续极限中可由二维 Euclidean 场论描述；
2. $1+1$ 维量子系统的 Euclidean 时间路径积分可离散为二维经典统计模型；
3. 临界点附近相关长度 $\xi$ 发散，连续极限常由重整化群固定点控制；
4. 在适当的二维局域、旋转不变、幺正等条件下，尺度不变固定点常进一步具有共形对称性。

但以下边界不能省略：

- Euclidean 场论不等于统计力学本身；
- 含复作用量、拓扑相位或费米行列式符号时，$e^{-S_E}$ 不一定是非负概率权重；
- CFT 描述的是临界连续极限，不是统计模型在所有温度和耦合下的完整行为；
- 形式上都出现指数权重，不代表两个理论的变量、测度和观测量相同。

## 与弦世界面的关系

弦的 Lorentz 世界面经 Wick 旋转后成为二维 Euclidean 曲面。局部上可选择复坐标，固定到共形规范后，物质场、鬼场和其他内部自由度构成二维 Euclidean 场论。

这带来三层必须分开的结构：

1. **局部场论**：作用量、方程、关联函数和 OPE；
2. **局部共形几何**：复坐标、全纯变换、能动张量与 Weyl 因子；
3. **全局世界面几何**：亏格、模空间、自同构、边界和穿孔。

只在平面上求出自由二点函数，不等于已经定义了任意黎曼曲面上的完整弦振幅。后者还需规范固定、鬼场行列式、零模、模空间积分、顶点算符和全局一致性条件。

## 与大模型的真实关系和禁止误连

二维 Euclidean 场论与大模型训练没有已知的一般物理等价关系。可复用的只是在明确变量、测度和边界条件后检查归一化、零模、局部与全局结构的方法论。

以下等价化必须禁止：

- Euclidean 作用量 $S_E$ $\ne$ 大模型训练损失；
- $e^{-S_E}$ $\ne$ softmax、token 概率或语言模型概率；
- 场构型的泛函积分 $\ne$ 参数优化轨迹或 SGD 路径；
- Wick 旋转 $\ne$ 复值训练或参数空间旋转；
- Euclidean 时间 $\ne$ 训练步数；
- 圆柱—平面映射 $\ne$ 位置编码或上下文窗口变换；
- 径向量子化的半径 $\ne$ 网络深度；
- Green 函数或场二点函数 $\ne$ attention matrix、kernel matrix 或 embedding 相似度；
- 反射正性 $\ne$ 损失非负、概率归一化或安全对齐；
- 红外零模 $\ne$ 零梯度、死亡神经元、零奇异值或未训练参数；
- 质量调节器 $\ne$ weight decay 或普通正则化；
- 二维共形不变性 $\ne$ 大模型 scaling law；
- 共形映射 $\ne$ LayerNorm、特征缩放或表示空间旋转。

## 适用条件与事实边界

1. 本页采用 $d^2z=dx\,dy$、$\Delta=4\partial\bar\partial$ 和 $g_{z\bar z}=1/2$；换约定时必须整套转换。
2. $\Delta\ln|z|^2=4\pi\delta^{(2)}(z)$ 是分布恒等式，不是原点处的普通函数等式。
3. $G_0=-(4\pi)^{-1}\ln(\mu^2|z|^2)$ 对应 $-\Delta G_0=\delta^{(2)}$。
4. 普通标量与弦坐标场的作用量归一化不同，二点函数前因子不能混用。
5. 二维无质量标量在非紧平面上仍有红外尺度歧义，在紧致曲面上还有显式常数零模。
6. 紧致无边界曲面的 Green 函数应使用相对于 $\sqrt h\,d^2x$ 归一化的协变分布 $\delta_h$，并把常数模投影掉，使右边成为 $\delta_h-1/V$。
7. 零模不能一概删除；弦坐标零模积分会产生目标时空动量守恒。
8. Euclidean 权重只有在适当条件下才能解释为概率测度；费米或拓扑系统可能有符号问题。
9. Wick 旋转必须结合解析性、边界条件和 $i\varepsilon$ 处方。
10. 反射正性不是“作用量为正”的同义词，也不是 OS 重构的唯一条件。
11. 无质量不自动推出量子共形不变，还需检查 beta 函数、迹和量子反常。
12. 每个二维度量局部共形平坦，不表示曲率、拓扑和模参数全局平凡。
13. 圆柱到平面的指数映射只提供径向量子化的几何入口，不替代 Hilbert 空间构造。
14. 世界面采用 Euclidean 复坐标，不表示目标时空必定二维或 Euclidean。
15. 后继 [[弦理论/数学/复坐标与全纯分解]] 系统推导向量、一形式、张量分量和局部全纯分解，[[弦理论/物理学/二维自由玻色子]] 则在同一约定下计算量子二点函数与能动张量短距离奇异项。

## 常见误区

1. **Euclidean 时间是真实存在的第二种物理时间。** 它是解析延拓或 Euclidean 定义中的坐标，物理实时解释需重构回 Lorentz 理论。
2. **把 $t$ 换成 $-i\tau$ 就完成 Wick 旋转。** 还需同步处理测度、导数、极点、边界条件和场分量。
3. **$e^{-S_E}$ 总是普通概率。** 权重可能为负或复数，且形式泛函测度本身也需定义。
4. **$d^2z$ 在所有教材中都有同一含义。** 不同资料可能把 $2$ 或 $i$ 吸收到面积元中。
5. **$dz\,d\bar z$ 与 $dz\wedge d\bar z$ 相同。** 前者在度量中表示对称乘积，后者是反对称二形式。
6. **二维无质量标量 Green 函数没有红外问题。** 对数需要参考尺度，紧致曲面还必须处理常数零模。
7. **Green 函数可在紧致曲面上直接反演整个 Laplacian。** 常数模使其不可逆，必须投影。
8. **无质量理论必然是量子 CFT。** 量子 beta 函数、反常和改进项仍需检查。
9. **经典迹为零说明中心荷为零。** 中心荷控制量子 Weyl 反常和能动张量代数，不等于经典质量项。
10. **任意 Euclidean 关联函数都能对应幺正实时理论。** 还需反射正性等 OS 条件。
11. **圆柱到平面的映射已证明态—算符对应。** 它只给出几何动机，正式对应还需量子化构造。
12. **世界面复坐标是目标时空坐标。** $z,\bar z$ 标记世界面点，$X^\mu$ 才描述到目标时空的映射。
13. **二维场论就是二维共形场论。** 有质量理论、离开固定点的理论和有尺度边界条件都可不是 CFT。
14. **质量调节器与原无质量理论完全相同。** 它显式改变红外和共形性质，只能在受控极限中移除。
15. **二维统计系统与大模型概率分布形式相似，所以两者物理等价。** 变量、测度、动力学和可观测量均不同。

## 练习

1. 从 $z=x+iy$ 推出 $\partial_z$、$\partial_{\bar z}$ 和 $\Delta=4\partial\bar\partial$。
2. 验证 $dz\wedge d\bar z=-2i\,dx\wedge dy$。
3. 在本页线元约定下，为什么 $g_{z\bar z}=1/2$ 而不是 $1$？
4. 把普通二维标量作用量从实坐标改写成复坐标形式。
5. 使用 $\Delta\ln|z|^2=4\pi\delta^{(2)}(z)$ 验证 $-\Delta G_0=\delta^{(2)}$。
6. 为什么无质量 Green 函数需要尺度 $\mu$？改变 $\mu$ 会怎样？
7. 比较普通标量和弦坐标场二点函数的归一化。
8. 定义曲面协变 delta 分布 $\delta_h(x,y)$，并证明紧致无边界曲面上不能有 $-\Delta_hG=\delta_h$ 的普通全局解。
9. 写出投影掉常数零模后的协变 Green 函数方程。
10. 反射正性为何比“Euclidean 作用量非负”更强？
11. 解释无质量标量经典 Weyl 不变为何不自动排除量子 Weyl 反常。
12. 由 $z=e^{\tau+i\sigma}$ 说明 Euclidean 时间排序为什么变成径向排序。
13. 圆柱到平面映射覆盖的是 $\mathbb C$ 还是 $\mathbb C^\times$？
14. 二维 Euclidean 场论与二维经典统计系统的联系有哪些适用边界？
15. 为什么世界面 Euclidean 化不要求目标时空同时 Euclidean 化？

## 答案与提示

1. 用链式法则得到 $\partial_z=(\partial_x-i\partial_y)/2$、$\partial_{\bar z}=(\partial_x+i\partial_y)/2$，相乘后交叉项抵消。
2. 展开 $(dx+i\,dy)\wedge(dx-i\,dy)$，利用 $dx\wedge dx=dy\wedge dy=0$ 和 $dy\wedge dx=-dx\wedge dy$。
3. 因为线元展开包含 $2g_{z\bar z}dz\,d\bar z$，而 $ds^2=dz\,d\bar z$，所以 $2g_{z\bar z}=1$。
4. $(\partial_x\phi)^2+(\partial_y\phi)^2=4\partial\phi\bar\partial\phi$，因此动能项为 $2\int d^2z\,\partial\phi\bar\partial\phi$。
5. $G_0=-(4\pi)^{-1}\ln(\mu^2|z|^2)$；常数 $\ln\mu^2$ 被 Laplacian 消去，剩余正好给 $\delta^{(2)}$。
6. 对数自变量必须无量纲，且二维无质量 Laplacian 的逆只确定到加法常数；改变 $\mu$ 只改变该常数。
7. 普通标量二点函数为相应 $(-\Delta)^{-1}$；弦作用量含 $1/(4\pi\alpha')$，所以 $\langle XX\rangle=-(\alpha'/2)\ln|z-w|^2$。
8. 协变 delta 由 $\int_\Sigma d^2x\sqrt h\,\delta_h(x,y)f(x)=f(y)$ 定义。对 $-\Delta_{h,x}G=\delta_h$ 使用不变量测度积分：左边由无边界分部积分为零，右边为一，矛盾来自常数零模。
9. $-\Delta_{h,x}G(x,y)=\delta_h(x,y)-1/V$，并可附加 $\int_\Sigma d^2x\sqrt h\,G(x,y)=0$。
10. 反射正性约束所有正半空间泛函的相关函数矩阵，关系到重构后内积正定；单个经典作用量的点态符号不足以保证它。
11. 量子测度和正规化可产生非零 $\langle T^a{}_a\rangle$；还需检查 beta 函数和总中心荷。
12. $|z|=e^\tau$，所以较大的 $\tau$ 对应较大的半径，时间先后次序转为内外半径次序。
13. 有限圆柱坐标映到 $z\ne0$ 的穿孔平面 $\mathbb C^\times$；原点和无穷远分别来自 $\tau\to\mp\infty$。
14. 联系依赖连续极限、边界条件和正权重等；不是所有 Euclidean 场论都能当作普通概率模型，也不是所有统计状态都由 CFT 描述。
15. $z,\bar z$ 是世界面坐标，$X^\mu$ 是到目标时空的场；两者是不同几何层次，可分别选择签名和解析延拓。

## 与其他概念的关系

- [[弦理论/物理学/反常消除]] 是上一路线节点，说明进入世界面场论前必须区分不同一致性条件；
- [[弦理论/物理学/Wick 旋转]] 连接 Lorentz 权重 $e^{iS_M}$ 与 Euclidean 权重 $e^{-S_E}$；
- [[弦理论/物理学/路径积分]] 和 [[弦理论/物理学/生成泛函]] 定义 Euclidean 配分函数与关联函数；
- [[弦理论/数学/复分析]] 提供 $z,\bar z$、Wirtinger 导数和全纯函数语言；
- [[弦理论/数学/度量]] 定义二维面积元、Laplace–Beltrami 算符和 Weyl 变换；
- [[弦理论/数学/Green 函数]] 解释自由场二点函数为何是动力学算符的逆；
- [[弦理论/数学/Dirac delta]] 给出对数 Green 函数的分布归一化；
- [[弦理论/物理学/传播子]] 连接 Euclidean 二点函数、极点处方和 Lorentz 传播；
- [[弦理论/物理学/能动张量]] 定义度量变分、守恒流和迹；
- [[弦理论/物理学/Weyl 反常]] 说明经典迹为零为何可能在量子层面失效；
- [[弦理论/数学/共形映射]] 给出 $z=e^w$ 和二维局部角度保持变换；
- [[弦理论/数学/黎曼曲面]] 把局部复坐标推广到弦世界面的全局几何；
- [[弦理论/物理学/二维自由玻色子]] 继承本页作用量、Green 函数和 timelike 边界，进一步计算导数收缩、正规序和中心荷；
- [[弦理论/物理学/紫外发散与红外发散]] 解释二维无质量标量的红外尺度和调节器；
- [[弦理论/弦理论完整学习路线图]] 把本页放在反常消除与复坐标、自由场、CFT 结构之间；
- [[弦理论与大模型跨学科关系图谱]] 记录受控方法论联系并禁止把 Euclidean 场论误写成大模型训练动力学。

## 参考资料

- Joseph Polchinski, *String Theory, Vol. 1*, Cambridge University Press, 1998, Chapters 2–3.
- Philippe Di Francesco, Pierre Mathieu, and David Sénéchal, *Conformal Field Theory*, Springer, 1997.
- Paul Ginsparg, “Applied Conformal Field Theory,” arXiv:hep-th/9108028.
- David Tong, “Lectures on String Theory,” arXiv:0908.0333.
- John Cardy, *Scaling and Renormalization in Statistical Physics*, Cambridge University Press, 1996.
- Jean Zinn-Justin, *Quantum Field Theory and Critical Phenomena*, Oxford University Press.
- Konrad Osterwalder and Robert Schrader, “Axioms for Euclidean Green's Functions,” *Communications in Mathematical Physics* **31** (1973), 83–112; **42** (1975), 281–305.
- James Glimm and Arthur Jaffe, *Quantum Physics: A Functional Integral Point of View*, Springer, 1987.
