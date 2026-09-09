---
aliases:
  - Klein-Gordon Field
  - Klein-Gordon 方程
  - Klein-Gordon Equation
english_name: Klein-Gordon Field
tags:
  - 物理学
  - 量子场论
  - 经典场论
  - 弦理论先修
prerequisites:
  - "[[弦理论/物理学/作用量]]"
  - "[[弦理论/物理学/经典场论]]"
  - "[[弦理论/物理学/场的 Euler-Lagrange 方程]]"
  - "[[弦理论/物理学/狭义相对论]]"
  - "[[弦理论/物理学/Minkowski 时空]]"
  - "[[弦理论/数学/偏导数]]"
  - "[[弦理论/数学/积分]]"
  - "[[弦理论/数学/Fourier 变换]]"
  - "[[弦理论/物理学/量子算符]]"
used_by:
  - "[[弦理论/物理学/Dirac 场]]"
  - "[[弦理论/物理学/场的正则量子化]]"
  - "[[弦理论/物理学/传播子]]"
  - "[[弦理论/物理学/生成泛函]]"
  - "[[弦理论/数学/复坐标与全纯分解]]"
  - "[[弦理论/物理学/二维自由玻色子]]"
  - "[[弦理论/物理学/弦的模展开]]"
evidence_status: 教材事实
---

# Klein-Gordon 场（Klein-Gordon Field）

## 一句话解释

Klein-Gordon 场是满足相对论能量—动量—质量关系 $E^2=\mathbf p^2+m^2$ 的自由标量场；其运动方程 $(\Box+m^2)\phi=0$ 是 Lorentz 协变的二阶波动方程，但不可作为单粒子 Schrödinger 方程使用。

## 为什么要学它

自由 Klein-Gordon 场是量子场论中最简单的相对论场，也是理解更复杂场论的起点。它用最少的自由度示范了：

- 怎样从 Lorentz 不变的作用量推出协变运动方程；
- 平面波解怎样通过 Fourier 变换构成场的完备基；
- 能量、动量和电荷怎样由 Noether 定理产生；
- 二次量子化怎样把经典场变成产生和湮灭粒子的算符。

在弦理论中，平直背景共形规范下的世界面标量场 $X^\mu(\tau,\sigma)$ 正好是二维 Klein-Gordon 方程 $\partial_z\partial_{\bar z}X^\mu=0$ 的解，因此 Klein-Gordon 场的结构直接出现在弦的模展开中。

## 直观图景

想象一个布满空间的弹性薄膜，但没有任何钉子和边界。每个点的膜面高度是一个数 $\phi(t,\mathbf x)$。

薄膜的每个小区域都有惯性，倾向于保持当前高度；同时又有弹性，被周围区域拉扯。这两种效应竞争的结果就是波动：局部的扰动会沿薄膜传播。

如果薄膜在真空中完全自由，没有任何外力或摩擦，那么高度函数 $\phi$ 满足的就是 Klein-Gordon 方程。其中的质量参数 $m$ 控制薄膜“回到平衡位置”的倾向大小：$m$ 越大，局部扰动越难向远处传播。

## 自由实标量场的作用量

本篇采用 mostly-minus 度规：

$$
\eta_{\mu\nu}
=\operatorname{diag}(1,-1,-1,\ldots,-1),
$$

自然单位 $c=1,\hbar=1$，时空维数 $D$。

自由实标量场 $\phi(x)$ 是 Lorentz 变换下的标量：$\phi'(x')=\phi(x)$。它的作用量为：

$$
S[\phi]
=\int d^Dx\,
\biggl[
\frac12\partial_\mu\phi\partial^\mu\phi
-\frac12m^2\phi^2
\biggr].
$$

各项含义：

- $\frac12\partial_\mu\phi\partial^\mu\phi$：动能项，描述场随时间和空间变化所需的“能量”；
- $-\frac12m^2\phi^2$：质量项，$m$ 是质量参数，写为负号是因为 mostly-minus 约定下动能项中时间导数前为正号；
- 两个 $\frac12$ 是归一化，使得运动方程中的系数最简洁；
- 积分号 $\int d^Dx$ 表示每个时空点贡献相加。

## 每个符号是什么意思

- $\phi(x)$：实数值标量场，$x=(t,\mathbf x)$ 是时空点；
- $\partial_\mu=\partial/\partial x^\mu$：对第 $\mu$ 个时空坐标的偏导数；
- $\partial^\mu=\eta^{\mu\nu}\partial_\nu$：用 Minkowski 度量升指标后的导数；
- $\partial_\mu\phi\partial^\mu\phi$ 展开为 $(\partial_t\phi)^2-(\nabla\phi)^2$，在 mostly-minus 约定下成立；
- $m$：质量参数，在经典理论中决定场激发的特征频率，在量子理论中对应粒子的质量；
- $D$：时空维数，常见取 $D=4$，但公式对一般 $D$ 也成立；
- $\eta_{\mu\nu}$：Minkowski 度量矩阵；
- $d^Dx$：$D$ 维时空体积元。

## Klein-Gordon 方程

对作用量做变分并取边界项为零，由场的 Euler-Lagrange 方程得到：

$$
\boxed{(\Box+m^2)\phi=0},
$$

其中 d'Alembert 算符在 mostly-minus 约定和 $x^0=t$ 下为：

$$
\Box
=\partial_\mu\partial^\mu
=\partial_t^2-\nabla^2.
$$

推导步骤：

1. 动能项对 $\partial_\mu\phi$ 的偏导给出 $\partial^\mu\phi$，再取 $\partial_\mu$ 得到 $\Box\phi$；
2. 质量项对 $\phi$ 的偏导给出 $-m^2\phi$；
3. 两项代入场方程 $\partial_\mu(\partial\mathcal L/\partial(\partial_\mu\phi))-\partial\mathcal L/\partial\phi=0$ 即得 $(\Box+m^2)\phi=0$。

若采用 mostly-plus 度规，方程会写成 $(\Box-m^2)\phi=0$，只是符号约定不同，物理内容一致。

## 为什么这是相对论协变方程

Lorentz 变换下：

$$
x^\mu\to x'^\mu
=\Lambda^\mu{}_\nu x^\nu,
$$

标量场按 $\phi'(x')=\phi(x)$ 变换。

d'Alembert 算符 $\Box=\partial_\mu\partial^\mu$ 是 Lorentz 标量算符：它在所有惯性系中形式相同。因此若 $\phi$ 在一个惯性系中满足 $(\Box+m^2)\phi=0$，则在所有惯性系中成立。

这是相对论量子力学早期尝试的关键：Schrödinger 方程 $i\partial_t\psi=-\frac{1}{2m}\nabla^2\psi$ 有一阶时间导数但二阶空间导数，不是 Lorentz 协变的。Klein-Gordon 方程时间和空间导数都是二阶，因此自然满足 Lorentz 协变性。

## 为什么 Schrödinger 方程不能用于相对论

Schrödinger 方程：

$$
i\partial_t\psi
=-\frac{1}{2m}\nabla^2\psi
$$

来源于非相对论能量—动量关系 $E=\mathbf p^2/(2m)$。

在相对论中，正确的关系是：

$$
E^2=\mathbf p^2+m^2.
$$

做量子力学替换 $E\to i\partial_t$、$\mathbf p\to-i\nabla$ 后，得到：

$$
-\partial_t^2\phi
=(-\nabla^2+m^2)\phi.
$$

整理即得 $(\Box+m^2)\phi=0$。因为现在能量是平方形式，所以波函数满足二阶方程。

## 平面波解

寻找形式为：

$$
\phi(x)=Ae^{-ik\cdot x}
$$

的解，其中 $k\cdot x=k_\mu x^\mu$。代入方程：

$$
(-k^2+m^2)Ae^{-ik\cdot x}=0,
$$

其中 $k^2=k_\mu k^\mu$。对非零振幅，必须：

$$
\boxed{k^2-m^2=0}.
$$

这就是质量壳条件。在 mostly-minus 约定下：

$$
k^2
=(k^0)^2-|\mathbf k|^2
=m^2.
$$

因此频率与波矢的关系为：

$$
k^0
=\pm\omega_{\mathbf k},
\qquad
\omega_{\mathbf k}
=\sqrt{|\mathbf k|^2+m^2}.
$$

符号含义：

- $k$：四维波矢，$k^\mu=(k^0,\mathbf k)$；
- $k^0$：频率，等于能量（在 $\hbar=1$ 下）；
- $\mathbf k$：三维波矢；
- $\omega_{\mathbf k}$：角频率；
- $k\cdot x=k^0t-\mathbf k\cdot\mathbf x$：四维内积；
- 正频解 $e^{-i\omega_{\mathbf k}t+i\mathbf k\cdot\mathbf x}$ 在量子化后与湮灭算符相乘；
- 负频解 $e^{+i\omega_{\mathbf k}t-i\mathbf k\cdot\mathbf x}$ 在量子化后与产生算符相乘。

对实标量场，粒子与反粒子是同一种中性粒子，正负频部分由实场条件联系；对带守恒 $U(1)$ 电荷的复标量场，两套独立模才分别描述粒子与反粒子。

## 质量壳条件是什么意思

在 mostly-minus 约定下，质量壳条件 $k^2=m^2$ 展开为：

$$
(k^0)^2-|\mathbf k|^2=m^2.
$$

这是相对论能量—动量关系 $E^2=\mathbf p^2+m^2$ 在 $E=k^0$、$\mathbf p=\mathbf k$（$\hbar=1$）下的直接翻译。

之所以叫“壳”，是因为在四维动量空间中，所有满足 $k^2=m^2$ 的点构成一个三维双曲面，形状像一个壳。每个在壳且满足正能条件的 $k$ 都可标记一个自由单粒子动量态。

不在壳上的动量 $k$，即 $k^2\ne m^2$，会出现在微扰量子场论的 Feynman 图内线和相关积分中。这类贡献常被口语化地称为“虚拟粒子”，但它不是可以被探测器单独捕获、只短暂存在一下的真实粒子。

## 一般解与 Fourier 表示

Klein-Gordon 方程是线性的，任何解的叠加仍是解。一般实解可写成正负频平面波的叠加：

$$
\phi(x)
=\int\frac{d^{D-1}k}{(2\pi)^{D-1}2\omega_{\mathbf k}}
\bigl[
a(\mathbf k)e^{-ik\cdot x}
+a^*(\mathbf k)e^{+ik\cdot x}
\bigr],
$$

其中积分中的 $k^0$ 取正频支 $k^0=\omega_{\mathbf k}$。

各项含义：

- $\int d^{D-1}k$：对所有三维波矢积分；
- $1/(2\omega_{\mathbf k})$：Lorentz 不变的相空间测度因子；
- $a(\mathbf k)$：复振幅，携带每个平面波的强度和相位；
- $a^*(\mathbf k)$：$a(\mathbf k)$ 的复共轭，保证 $\phi$ 为实场；
- $e^{-ik\cdot x}$：正频平面波；
- $e^{+ik\cdot x}$：负频平面波。

量子化后，$a(\mathbf k)$ 和 $a^*(\mathbf k)$ 分别变成湮灭算符和产生算符。

## Lorentz 不变的积分测度

因子：

$$
\frac{d^{D-1}k}{(2\pi)^{D-1}2\omega_{\mathbf k}}
$$

是 Lorentz 不变的。可以把 $D$ 维壳上积分与 $D$ 维动量空间积分联系起来：

$$
\frac{d^{D-1}k}{(2\pi)^{D-1}2\omega_{\mathbf k}}
=
\frac{d^Dk}{(2\pi)^{D-1}}
\,\delta(k^2-m^2)\,\theta(k^0),
$$

其中 $\delta(k^2-m^2)$ 限制在质量壳上，$\theta(k^0)$ 只取正能分支。这个测度在量子场论的散射截面和衰变率计算中反复出现。

## 因果传播

Klein-Gordon 方程是双曲型偏微分方程，在 $t=0$ 时刻的初始数据会影响未来光锥内的事件并受过去光锥内的数据影响，但不会影响类空分离的事件。

这是经典层面的因果性保证。量子化后，由 $\phi(x)$ 和 $\phi(y)$ 的对易子在类空间隔为零来表达微观因果性。

## 复标量场

若 $\phi$ 取复数值，作用量推广为：

$$
S[\phi,\phi^*]
=\int d^Dx\,
\bigl[
\partial_\mu\phi^*\partial^\mu\phi
-m^2|\phi|^2
\bigr].
$$

这里 $\phi^*$ 是 $\phi$ 的复共轭，$|\phi|^2=\phi^*\phi$。

把 $\phi$ 和 $\phi^*$ 当作独立变量变分，分别得到：

$$
(\Box+m^2)\phi=0,
\qquad
(\Box+m^2)\phi^*=0.
$$

复标量场引入了一个自由实场没有的结构：整体的 $U(1)$ 相位对称性。

## 整体 $U(1)$ 对称性与守恒流

复标量场的作用量在变换：

$$
\phi\to e^{-i\alpha}\phi,
\qquad
\phi^*\to e^{+i\alpha}\phi^*
$$

下不变，其中 $\alpha$ 是实常数。

由 Noether 定理，对应的守恒流为：

$$
j^\mu
=i\bigl[
\phi^*\partial^\mu\phi
-(\partial^\mu\phi^*)\phi
\bigr].
$$

它满足：

$$
\partial_\mu j^\mu=0.
$$

守恒荷为：

$$
Q
=\int d^{D-1}x\,j^0.
$$

量子化后，$Q$ 成为粒子数减反粒子数的算符。本节只讨论经典守恒流；正则量子化后还需考虑正规排序和真空荷。

## 能动张量

由时空平移不变性，Noether 定理给出正则能动张量。对实标量场：

$$
T^{\mu\nu}
=\partial^\mu\phi\partial^\nu\phi
-\eta^{\mu\nu}\mathcal L.
$$

代入 Lagrangian 密度后：

$$
T^{\mu\nu}
=\partial^\mu\phi\partial^\nu\phi
-\eta^{\mu\nu}
\left(
\frac12\partial_\rho\phi\partial^\rho\phi
-\frac12m^2\phi^2
\right).
$$

能量密度和动量密度为：

$$
\mathcal H
=T^{00}
=\frac12(\partial_t\phi)^2
+\frac12|\nabla\phi|^2
+\frac12m^2\phi^2,
$$

$$
\mathcal P^i
=T^{0i}
=\partial_t\phi\,\partial^i\phi.
$$

在 mostly-minus 约定和自然单位下，$\partial^0\phi=\partial_t\phi$，$\partial^i\phi=-\partial_i\phi$。总能量为：

$$
H
=\int d^{D-1}x\,\mathcal H.
$$

这里的 $\mathcal H$ 是 Hamiltonian 密度，$H$ 是总 Hamiltonian。正则能动张量 $T^{\mu\nu}$ 未必对称；在广义相对论中通常使用对称化的 Belinfante 能动张量。

## Hamiltonian 形式

通过 Legendre 变换，定义共轭动量：

$$
\pi(x)
=\frac{\partial\mathcal L}
{\partial(\partial_t\phi)}
=\partial_t\phi.
$$

Hamiltonian 密度为：

$$
\mathcal H
=\pi\partial_t\phi-\mathcal L
=\frac12\pi^2
+\frac12|\nabla\phi|^2
+\frac12m^2\phi^2.
$$

三项分别对应场的“动能”、空间梯度的“弹性能”和质量带来的“势能”。

这是量子化起点：$\phi$ 和 $\pi$ 在量子理论中变成算符，并满足等时对易关系。

## 从经典到量子的边界

经典 Klein-Gordon 场理论中：

- $\phi(x)$ 和 $\pi(x)$ 是普通函数；
- 方程是确定性的偏微分方程；
- 参数 $m$ 只是方程中的系数。

二次量子化后：

- $\phi(x)$ 和 $\pi(x)$ 变成 Hilbert 空间上的算符；
- 满足等时对易关系 $[\phi(t,\mathbf x),\pi(t,\mathbf y)]=i\delta^{(D-1)}(\mathbf x-\mathbf y)$；
- 平面波系数 $a(\mathbf k)$ 和 $a^*(\mathbf k)$ 变成产生和湮灭算符；
- 质量参数 $m$ 对应单粒子态的能量下限。

经典理论中的 Noether 荷 $Q$ 和 Hamiltonian $H$ 在量子化后需要正规排序来处理真空零点能。

## 与弦世界面的关系

在平直目标时空中，共形规范下取 Lorentzian 世界面度规：

$$
\eta_{ab}=\operatorname{diag}(-1,+1),
$$

Polyakov 作用量可写成：

$$
S
=-\frac{T}{2}
\int d^2\sigma\,
\eta^{ab}
\partial_aX^\mu\partial_bX_\mu.
$$

其中 $T$ 是弦张力。若改变世界面度规号差或作用量整体符号，公式外观会相应变化，但在约定保持一致时运动方程相同。

运动方程为：

$$
\partial_a\partial^a X^\mu=0.
$$

在 Euclidean 世界面使用复坐标 $z,\bar z$ 后，这变为：

$$
\partial_z\partial_{\bar z}X^\mu=0.
$$

这正好是二维质量为零的 Klein-Gordon 方程。因此每个 $X^\mu$ 在经典层面都是自由二维标量场。

例如采用 $\sigma\in[0,\pi]$、两端 Neumann 边界条件，并定义：

$$
\ell_s=\sqrt{2\alpha'},
$$

开弦模展开的一种常见写法是：

$$
X^\mu(\tau,\sigma)
=x^\mu
+\ell_s^2 p^\mu\tau
+i\ell_s
\sum_{n\ne0}
\frac{1}{n}
\alpha_n^\mu e^{-in\tau}\cos(n\sigma).
$$

不同资料对 $\ell_s$、$\alpha'$ 和振子归一化使用不同约定，整体系数必须与相应对易关系一起核对。这里的 $\cos(n\sigma)$ 来自开弦 Neumann 边界条件；闭弦应有左右两组独立振子 $\alpha_n^\mu$ 与 $\widetilde\alpha_n^\mu$，不能把上式标成闭弦展开。

振荡系数正是二维质量为零 Klein-Gordon 场正规模的振幅。

## 适用条件与事实边界

1. 自由 Klein-Gordon 场没有自相互作用，运动方程是线性偏微分方程。
2. 本篇采用 mostly-minus 度规，$\Box=\partial_t^2-\nabla^2$。若改用 mostly-plus，方程和符号需要整体调整。
3. 质量参数 $m$ 在经典理论中只是场方程的特征参数；在量子理论中通过 $E^2=\mathbf p^2+m^2$ 与粒子质量对应。
4. 经典能量密度对所有物理场配置非负，因为 $m^2\ge0$ 时每一项都是平方。
5. 若 $m^2<0$，则 $\phi=0$ 不是势能极小值；在存在稳定化高阶项（如 $\phi^4$ 且耦合为正）时，这表示系统具有自发对称破缺。
6. 复标量场的 $U(1)$ 守恒荷 $Q$ 在经典层面可取任意实数；量子化后 $Q$ 的取值与粒子数算符相关。
7. 平面波解 $e^{\pm ik\cdot x}$ 在无限空间中是广义函数，需要积分构造波包才得到平方可积的初始数据。
8. Lorentz 不变测度 $d^{D-1}k/(2\omega_{\mathbf k})$ 来自质量壳约束和阶梯函数的协变写法。
9. 正则能动张量 $T^{\mu\nu}$ 在存在自旋或规范场时需要对称化或改进。
10. 弦世界面标量场 $X^\mu$ 的二维 Klein-Gordon 方程是 $m=0$ 的特例，且带 Virasoro 约束。

## 常见误区

1. **Klein-Gordon 方程是单一粒子的 Schrödinger 方程。** 它是经典场方程；作为单粒子波动方程使用时，负能解和负概率密度是早期难题，量子场论通过二次量子化解决这些问题。
2. **$(\Box+m^2)\phi=0$ 和 $(\Box-m^2)\phi=0$ 是不同物理。** 差异完全来自度规号差约定，物理内容相同。
3. **质量 $m$ 在经典和量子理论中意义完全相同。** 经典中 $m$ 只是方程参数；量子中 $m$ 是单粒子态的能量下限，且会受到相互作用和重整化修正。
4. **平面波解是物理粒子。** 经典平面波是无限延展的理想化解；量子化后，波包态的叠加才对应位置有一定局域性的物理粒子。
5. **Klein-Gordon 场只能描述自旋零的粒子。** 标量场确实只描述自旋零，但多个标量场可以通过内部对称性构成更丰富的结构。
6. **复标量场的 $U(1)$ 守恒荷必定是电荷。** 它只是全局对称性对应的守恒量；是否对应电磁荷取决于是否与规范场耦合。
7. **自由场没有可研究的量子结构。** 自由量子场仍有真空涨落、传播子和零点能；Casimir 效应还依赖边界条件。Lamb 移位则需要与电磁场的相互作用，不能归因于纯自由场本身。
8. **弦世界面标量场 $X^\mu$ 就是普通的 Klein-Gordon 场。** $X^\mu$ 是二维零质量标量场，但带 Virasoro 约束，这些约束把多余的振动模式排除在物理态之外。

## 练习

1. 写出自由实标量场在 mostly-minus 约定下的作用量。
2. 由作用量推导 Klein-Gordon 方程。
3. 写出 mostly-minus 约定下 d'Alembert 算符 $\Box$ 的显式。
4. 求平面波解 $e^{-ik\cdot x}$ 代入 KG 方程后得到什么条件。
5. 写出质量壳条件 $k^2=m^2$ 在 mostly-minus 约定下的分量形式。
6. 写出实标量场一般解的 Fourier 表示。
7. 为什么积分测度 $d^{D-1}k/(2\omega_{\mathbf k})$ 是 Lorentz 不变的？
8. 复标量场的作用量是什么？
9. 复标量场的 $U(1)$ 守恒流和守恒荷的表达式是什么？
10. 写出实标量场 Hamiltonian 密度的表达式。
11. 共轭动量 $\pi(x)$ 是怎样定义的？
12. 为什么经典 KG 场不能直接作为单粒子波函数理论？
13. 弦世界面标量场 $X^\mu$ 满足的方程是什么？
14. 若 $m^2<0$，$\phi=0$ 是否稳定？还需要什么条件才能得到稳定的自发对称破缺势？
15. 经典 KG 场和量子化后的 KG 场在哪些方面有本质不同？

## 答案与提示

1. $S=\int d^Dx\,[\frac12\partial_\mu\phi\partial^\mu\phi-\frac12m^2\phi^2]$。
2. $\partial_\mu\partial^\mu\phi+m^2\phi=0$，即 $(\Box+m^2)\phi=0$。
3. 在 mostly-minus 约定和 $x^0=t$ 下，$\Box=\partial_t^2-\nabla^2$。
4. $(-k^2+m^2)Ae^{-ik\cdot x}=0$，所以 $k^2=m^2$。
5. $(k^0)^2-|\mathbf k|^2=m^2$，即 $k^0=\pm\sqrt{|\mathbf k|^2+m^2}$。
6. $\phi(x)=\int\frac{d^{D-1}k}{(2\pi)^{D-1}2\omega_{\mathbf k}}[a(\mathbf k)e^{-ik\cdot x}+a^*(\mathbf k)e^{+ik\cdot x}]$，其中 $k^0=\omega_{\mathbf k}$。
7. 可写成 $\frac{d^Dk}{(2\pi)^{D-1}}\delta(k^2-m^2)\theta(k^0)$，其中 $d^Dk$、$\delta(k^2-m^2)$ 和 $\theta(k^0)$ 在固有正时 Lorentz 变换下不变。
8. $S=\int d^Dx\,[\partial_\mu\phi^*\partial^\mu\phi-m^2|\phi|^2]$。
9. $j^\mu=i[\phi^*\partial^\mu\phi-(\partial^\mu\phi^*)\phi]$，$Q=\int d^{D-1}x\,j^0$。
10. $\mathcal H=\frac12\pi^2+\frac12|\nabla\phi|^2+\frac12m^2\phi^2$，其中 $\pi=\partial_t\phi$。
11. $\pi(x)=\partial\mathcal L/\partial(\partial_t\phi)=\partial_t\phi$。
12. 负频解使 KG 内积不是正定概率密度；量子场论把正负频部分解释为产生和湮灭算符，而不是单粒子位置概率波函数。
13. 二维零质量 KG 方程：$\partial_a\partial^aX^\mu=0$，在复坐标下为 $\partial_z\partial_{\bar z}X^\mu=0$。
14. $\phi=0$ 不稳定。纯二次负质量平方势无下界；还需正的高阶项，如 $+\lambda\phi^4$，才能形成有界且在非零场值处取极小值的自发对称破缺势。
15. $\phi$ 和 $\pi$ 变成算符；$a,a^*$ 变成产生湮灭算符；需要正规排序处理真空能；守恒荷变成算符；场对易关系替换经典 Poisson 括号。

## 与其他概念的关系

- [[弦理论/物理学/作用量]] 与 [[弦理论/物理学/经典场论]] 给出 KG 作用量的构造和场论框架；
- [[弦理论/物理学/场的 Euler-Lagrange 方程]] 从作用量变分推出 $(\Box+m^2)\phi=0$；
- [[弦理论/物理学/狭义相对论]] 与 [[弦理论/物理学/Minkowski 时空]] 保证方程的 Lorentz 协变性；
- [[弦理论/数学/偏导数]] 与 [[弦理论/数学/积分]] 构建微分方程和 Fourier 解；
- [[弦理论/数学/Fourier 变换]] 提供平面波基和动量空间表示；
- [[弦理论/物理学/量子算符]] 是二次量子化时 $\phi$ 和 $\pi$ 提升为算符的基础；
- [[弦理论/物理学/Dirac 场]] 用旋量和 Gamma 矩阵构造自旋 $\frac12$ 场的一阶相对论方程；其每个分量进一步满足 Klein-Gordon 型二阶方程；
- [[弦理论/物理学/场的正则量子化]] 把经典 KG 场提升为量子场；
- [[弦理论/物理学/传播子]] 是 KG 场的 Green 函数，描述粒子在两点间传播的振幅；
- [[弦理论/物理学/生成泛函]] 通过 KG 场引入路径积分和相关函数；
- [[弦理论/数学/复坐标与全纯分解]] 将二维无质量 KG 方程改写为 $\partial\bar\partial X=0$，并区分局部两扇区解与周期、现实性、动量和绕数等全局约束；
- [[弦理论/物理学/弦的模展开]] 中的 $X^\mu$ 节是二维自由 KG 场的直接应用；
- [[弦理论/物理学/二维自由玻色子]] 是在弦世界面上定义的二维 $m=0$ 标量场 CFT；
- [[弦理论/物理学/能动张量]] 从 KG 场的时空平移不变性得到能量和动量密度；
- [[弦理论/物理学/Noether 定理]] 从 $U(1)$ 对称性推导复 KG 场的守恒流。

## 参考资料

- Michael E. Peskin and Daniel V. Schroeder, *An Introduction to Quantum Field Theory*, Westview Press, 1995, Chapter 2.
- Mark Srednicki, *Quantum Field Theory*, Cambridge University Press, 2007, Chapters 2–3.
- Steven Weinberg, *The Quantum Theory of Fields, Vol. 1*, Cambridge University Press, 1995, Chapter 1.
- Walter Greiner and Joachim Reinhardt, *Field Quantization*, Springer, 1996.
- Ashok Das, *Lectures on Quantum Field Theory*, 2nd ed., World Scientific, 2020.
- Joseph Polchinski, *String Theory, Vol. 1*, Cambridge University Press, 1998, Chapter 2.
- David Tong, *String Theory*, arXiv:0908.0333, [arXiv](https://arxiv.org/abs/0908.0333)
- Barton Zwiebach, *A First Course in String Theory*, 2nd ed., Cambridge University Press, 2009.