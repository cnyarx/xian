---
aliases:
  - Quantization of the Maxwell Field
  - Quantum Electromagnetic Field
english_name: Quantization of the Maxwell Field
tags:
  - 物理学
  - 量子场论
  - 规范场
  - 弦理论先修
  - 弦理论
prerequisites:
  - "[[Maxwell 方程]]"
  - "[[规范对称性]]"
  - "[[经典场论]]"
  - "[[Minkowski 时空]]"
  - "[[量子算符]]"
  - "[[对易关系]]"
  - "[[Fock 空间]]"
  - "[[Fourier 变换]]"
used_by:
  - "[[光子]]"
  - "[[场的正则量子化]]"
  - "[[传播子]]"
  - "[[规范固定]]"
  - "[[Faddeev-Popov 鬼场]]"
  - "[[Yang-Mills 理论]]"
  - "[[Wilson 线与 Wilson 圈]]"
evidence_status: 教材事实
---

# Maxwell 场量子化（Quantization of the Maxwell Field）

## 一句话解释

Maxwell 场量子化把经典电磁场的每个横向波模式变成量子谐振子；其能量量子就是光子，而规范冗余和 Gauss 约束保证四维势最终只留下两个物理偏振。

## 为什么要学它

标量场量子化没有规范冗余，Maxwell 场却有四个势分量、约束方程和规范等价。它是学习以下内容的最简单入口：

- 怎样量子化带约束的场；
- 为什么变量分量数不等于物理自由度数；
- 光子为何只有两个 helicity；
- Coulomb 规范与 Lorenz 规范各自解决什么问题；
- 传播子为何依赖规范，但可观测量不依赖规范；
- Faddeev–Popov 与 BRST 为什么会在一般规范理论中出现。

弦理论中的世界面微分同胚和 Weyl 对称更复杂，但“先识别冗余、再量子化物理自由度”的逻辑与 Maxwell 场相同。

## 本篇约定

采用自然单位 $c=\hbar=1$ 和 mostly-minus 度规：

$$
\eta_{\mu\nu}=\operatorname{diag}(+1,-1,-1,-1).
$$

电磁四维势记为 $A_\mu$。本文用 $A_i$ 表示它的协变空间分量，并在三维公式中用 Euclidean $\delta_{ij}$ 识别空间分量。定义：

$$
E_i\equiv F_{0i}=F^{i0}
=\partial_0A_i-\partial_iA_0,
$$

$$
B_i\equiv\frac12\epsilon_{ijk}F_{jk}.
$$

因此本文三维记号 $\mathbf A=(A_1,A_2,A_3)$、$\mathbf E=(E_1,E_2,E_3)$、$\mathbf B=(B_1,B_2,B_3)$ 与后文正则动量约定一致。

场强为：

$$
F_{\mu\nu}=\partial_\mu A_\nu-\partial_\nu A_\mu.
$$

规范变换取：

$$
A_\mu\longmapsto A_\mu+\partial_\mu\Lambda.
$$

不同教材可能改变 $A_0$、$\mathbf E$ 或 Fourier 指数的符号；必须依据场强定义整套比较。

## 每个符号是什么意思

- $A_\mu$：电磁四维势；
- $F_{\mu\nu}$：规范不变场强；
- $\mathbf E$、$\mathbf B$：电场和磁场；
- $\Lambda(x)$：任意足够光滑的规范参数；
- $\Pi^\mu$：与 $A_\mu$ 共轭的正则动量；
- $a_\lambda(\mathbf k)$、$a_\lambda^\dagger(\mathbf k)$：光子湮灭与产生算符；
- $\lambda=1,2$：两个物理横向偏振；
- $\boldsymbol\epsilon_\lambda(\mathbf k)$：偏振向量；
- $\omega_{\mathbf k}=|\mathbf k|$：无质量光子的频率；
- $\delta^T_{ij}$：横向 delta 分布；
- $\Box=\partial_t^2-\nabla^2$：d'Alembert 算符。

## Maxwell 作用量

无源 Maxwell 作用量为：

$$
S[A]=-\frac14\int d^4x\,F_{\mu\nu}F^{\mu\nu}.
$$

Lagrangian 密度可写成：

$$
\mathcal L
=-\frac14F_{\mu\nu}F^{\mu\nu}
=\frac12(\mathbf E^2-\mathbf B^2).
$$

对 $A_\nu$ 变分得到：

$$
\partial_\mu F^{\mu\nu}=0.
$$

另一组 Maxwell 方程来自定义恒等式：

$$
\partial_{[\rho}F_{\mu\nu]}=0.
$$

## 为什么不能直接量子化四个独立分量

四维势有四个分量，但规范变换不改变 $F_{\mu\nu}$。此外，$A_0$ 在 Maxwell Lagrangian 中没有独立的平方时间导数。

正则动量为：

$$
\Pi^\mu
=\frac{\partial\mathcal L}{\partial(\partial_0A_\mu)}
=F^{\mu0}
$$

在本篇指标约定下成立。于是：

$$
\Pi^0=F^{00}=0.
$$

这不是运动后偶然得到的方程，而是初级约束。$A_0$ 更像实施 Gauss 定律的 Lagrange 乘子，不是独立传播的光子模式。

若无视约束，把四个分量都当普通标量场量子化，会引入非物理纵向、时间样偏振和不定范数问题。

## Gauss 约束

无源 Maxwell 方程的 $\nu=0$ 分量给出：

$$
\nabla\cdot\mathbf E=0.
$$

在正则语言中，它约束允许的初始数据。含电荷密度时变为：

$$
\nabla\cdot\mathbf E=\rho.
$$

Gauss 定律没有独立二阶时间演化，而是必须在每个时刻满足的约束。运动方程会保持已经满足的 Gauss 约束。

## 自由度怎样从四个变成两个

配置空间中的直观计数如下：

1. $A_\mu$ 有四个实分量；
2. 一个局域规范函数代表一个冗余配置方向；
3. Gauss 定律限制一个配置方向的共轭数据；
4. 最终每个非零动量只剩两个传播偏振。

更严格的 Hamiltonian 计数从八维相空间开始。$\Pi^0=0$ 与 Gauss 约束都是一级（first-class）约束；每个一级约束连同其生成的一个规范方向去掉两维相空间。因此二者共去掉四维，留下四维物理相空间，即两个配置自由度。

## Coulomb 规范

Coulomb 规范取：

$$
\nabla\cdot\mathbf A=0.
$$

在无源自由理论并配合适当边界条件时，还可选择：

$$
A_0=0.
$$

于是只剩横向向量势：

$$
\mathbf A=\mathbf A^T,
\qquad
\nabla\cdot\mathbf A^T=0.
$$

运动方程成为：

$$
\Box\mathbf A^T=0.
$$

每个横向分量像质量为零的标量场，但两者要共同满足横向条件。

有电荷源时，$A_0$ 一般不能简单设为零；它由 Poisson 方程决定并产生瞬时 Coulomb 势。这里的“瞬时”是规范描述的一部分，不导致可观测超光速信号。

## 横向分解

空间向量场可形式分解为：

$$
\mathbf A=\mathbf A^T+\nabla\chi,
$$

其中：

$$
\nabla\cdot\mathbf A^T=0.
$$

纵向部分 $\nabla\chi$ 可由规范变换改变，横向部分承载自由辐射。

这种 Helmholtz 分解需要合适的空间拓扑和边界或衰减条件。紧致空间和非平凡拓扑还可能有不能归入普通梯度或横向波的调和零模。

## 偏振向量

对非零动量 $\mathbf k$，选择两个实或复偏振向量：

$$
\boldsymbol\epsilon_\lambda(\mathbf k),
\qquad \lambda=1,2,
$$

满足：

$$
\mathbf k\cdot\boldsymbol\epsilon_\lambda(\mathbf k)=0,
$$

$$
\boldsymbol\epsilon_\lambda^*(\mathbf k)
\cdot\boldsymbol\epsilon_{\lambda'}(\mathbf k)
=\delta_{\lambda\lambda'}.
$$

完备关系为：

$$
\sum_{\lambda=1}^2
\epsilon_{\lambda i}(\mathbf k)
\epsilon^*_{\lambda j}(\mathbf k)
=\delta_{ij}-\frac{k_i k_j}{|\mathbf k|^2}.
$$

右边是横向投影矩阵，它消去沿 $\mathbf k$ 的纵向分量。

## 模展开

Coulomb 规范下的自由横向势可展开为：

$$
A_i^T(x)
=\sum_{\lambda=1}^2
\int\frac{d^3k}{(2\pi)^3\sqrt{2\omega_{\mathbf k}}}
\left[
\epsilon_{\lambda i}(\mathbf k)
a_\lambda(\mathbf k)e^{-ik\cdot x}
+
\epsilon^*_{\lambda i}(\mathbf k)
a_\lambda^\dagger(\mathbf k)e^{+ik\cdot x}
\right],
$$

其中：

$$
k^0=\omega_{\mathbf k}=|\mathbf k|.
$$

实场条件由正负频系数的 Hermitian 共轭关系保证。

## 正则对易关系

约化到横向自由度后，等时对易关系为：

$$
[A_i^T(t,\mathbf x),
E_j^T(t,\mathbf y)]
=i\delta^T_{ij}(\mathbf x-\mathbf y)
$$

在选定 $E_i$ 与正则动量符号一致的约定下成立。

横向 delta 的 Fourier 表示为：

$$
\delta^T_{ij}(\mathbf x-\mathbf y)
=\int\frac{d^3k}{(2\pi)^3}
\left(\delta_{ij}-\frac{k_i k_j}{|\mathbf k|^2}\right)
e^{i\mathbf k\cdot(\mathbf x-\mathbf y)}.
$$

它只在散度为零的向量场子空间上充当恒等算符。

相应模式算符满足：

$$
[a_\lambda(\mathbf k),
a_{\lambda'}^\dagger(\mathbf q)]
=(2\pi)^3\delta_{\lambda\lambda'}
\delta^{(3)}(\mathbf k-\mathbf q),
$$

其余同类对易子为零。

## 光子 Fock 空间

定义真空：

$$
a_\lambda(\mathbf k)|0\rangle=0.
$$

单光子态为：

$$
|\mathbf k,\lambda\rangle
=a_\lambda^\dagger(\mathbf k)|0\rangle.
$$

在本文连续归一化下：

$$
\langle\mathbf q,\lambda'|\mathbf k,\lambda\rangle
=(2\pi)^3\delta_{\lambda'\lambda}
\delta^{(3)}(\mathbf q-\mathbf k).
$$

多光子态由多个产生算符构造。因为光子是玻色子：

$$
[a_\lambda^\dagger(\mathbf k),
a_{\lambda'}^\dagger(\mathbf q)]=0.
$$

交换两个光子不会让状态变号，同一模式可有任意非负整数占据数。

## Hamiltonian

把模展开代入场能量：

$$
H=\frac12\int d^3x\,
(\mathbf E^2+\mathbf B^2),
$$

得到：

$$
H
=\sum_{\lambda=1}^2
\int\frac{d^3k}{(2\pi)^3}\,
\omega_{\mathbf k}
\left[
a_\lambda^\dagger(\mathbf k)a_\lambda(\mathbf k)
+\frac12(2\pi)^3\delta^{(3)}(0)
\right].
$$

这里 $(2\pi)^3\delta^{(3)}(0)$ 是连续归一化下的形式体积因子；等价地，可先在有限盒中把动量离散化，再取无限体积极限。

正规排序后：

$$
:H:
=\sum_{\lambda=1}^2
\int\frac{d^3k}{(2\pi)^3}\,
\omega_{\mathbf k}
a_\lambda^\dagger(\mathbf k)a_\lambda(\mathbf k).
$$

每次作用 $a_\lambda^\dagger$ 都增加一个能量为 $\omega_{\mathbf k}$ 的光子。真空零点能在无限体积连续模式下发散；正规排序可移除平直时空无引力散射中的常数，但边界、曲率或引力问题需要更谨慎的重整化。

## 动量和 helicity

正规排序后的总动量为：

$$
:\mathbf P:
=\sum_{\lambda=1}^2
\int\frac{d^3k}{(2\pi)^3}\,
\mathbf k\,
a_\lambda^\dagger(\mathbf k)a_\lambda(\mathbf k).
$$

对每个非零 $\mathbf k$，选择右手正交标架 $(\boldsymbol\epsilon_1,\boldsymbol\epsilon_2,\widehat{\mathbf k})$，即
$\boldsymbol\epsilon_1\times\boldsymbol\epsilon_2=\widehat{\mathbf k}$。定义圆偏振基：

$$
\boldsymbol\epsilon_h
=\frac1{\sqrt2}
(\boldsymbol\epsilon_1+i h\boldsymbol\epsilon_2),
\qquad h=\pm1.
$$

它满足：

$$
i\widehat{\mathbf k}\times\boldsymbol\epsilon_h
=h\boldsymbol\epsilon_h.
$$

因此在这一明示的定向和 helicity 算符约定下，$\boldsymbol\epsilon_h$ 对应 helicity $h$。若改变标架定向、Fourier 指数或圆偏振定义，$+$、$-$ 标签可能互换，但两个物理本征值始终是 $+1$ 与 $-1$。无质量光子没有静止系，因此不能照搬有质量自旋 $1$ 粒子的三个自旋投影。

## Lorenz 规范

Lorenz 规范是：

$$
\partial_\mu A^\mu=0.
$$

名称来自 Ludvig Lorenz，不是 Lorentz 变换中的 Hendrik Lorentz；但这个条件本身是 Lorentz 协变的。

在自由理论中，它使方程化为：

$$
\Box A^\mu=0.
$$

它保留了四维协变外观，但若把四个分量都量子化，会出现时间样和纵向非物理态。因此还需对物理态施加条件，或使用 BRST 语言取上同调。

## Gupta–Bleuler 方法

协变量子化中不能把算符恒等式：

$$
\partial_\mu A^\mu=0
$$

强加在整个不定度规 Fock 空间，否则与正则对易关系冲突。Gupta–Bleuler 方法只要求其正频部分湮灭物理态：

$$
(\partial_\mu A^\mu)^{(+)}
|\mathrm{phys}\rangle=0.
$$

物理态空间中仍可能有零范数态；把这些态商去后，只剩两个横向光子偏振并得到正定物理 Hilbert 空间。

该方法最适合自由或 Abelian 电磁场。非 Abelian 规范理论通常使用 Faddeev–Popov 和 BRST 框架。

## 规范固定项与传播子

协变路径积分常加入：

$$
\mathcal L_{\mathrm{gf}}
=-\frac1{2\xi}(\partial_\mu A^\mu)^2.
$$

动量空间传播子可写成：

$$
D_{\mu\nu}(k)
=\frac{-i}{k^2+i\varepsilon}
\left[
\eta_{\mu\nu}
-(1-\xi)\frac{k_\mu k_\nu}{k^2}
\right]
$$

在本篇作用量和 Fourier 约定下成立。

$\xi=1$ 是 Feynman 规范，$\xi\to0$ 对应 Landau 规范的极限。传播子的纵向部分依赖 $\xi$，但与守恒流耦合的物理 S 矩阵元不应依赖规范参数。

## Abelian 鬼场为何解耦

对线性规范条件 $G[A]=\partial_\mu A^\mu$，规范变换后：

$$
\frac{\delta G[A^\Lambda]}{\delta\Lambda}
=\Box
$$

与 $A_\mu$ 无关。因此 Maxwell 理论的 [[Faddeev-Popov 行列式]] 只贡献一个与场无关的常数；相应鬼场是自由的并从普通散射振幅中解耦。

在非 Abelian Yang–Mills 理论中，Faddeev–Popov 算符依赖规范场，鬼场会与规范玻色子相互作用。鬼场不是外部可观测粒子，而是维持规范量子化一致性的辅助 Grassmann 场。

## 与带电物质耦合

加入守恒电流：

$$
\mathcal L
=-\frac14F_{\mu\nu}F^{\mu\nu}
-J_\mu A^\mu.
$$

规范变换下作用量的变化是边界项加上：

$$
\int d^4x\,\Lambda\,\partial_\mu J^\mu.
$$

因此规范不变性要求：

$$
\partial_\mu J^\mu=0.
$$

在量子电动力学中，$J^\mu=q\bar\psi\gamma^\mu\psi$。电磁场和 Dirac 场相互作用后，光子数一般不守恒，但电荷守恒。

## 微观因果性

Coulomb 规范中的横向势是非局域投影后的变量，其等时对易子含 $\delta^T_{ij}$，外观上不是严格局域的。

真正可观测的局域场强满足因果可交换性：类空分离时，$F_{\mu\nu}(x)$ 与 $F_{\rho\sigma}(y)$ 的对易子为零。

因此不能从某个规范势分量的非局域表达直接推断可观测超光速传播。

## 边界、有限体积和零模

在无限平直空间中，常用连续动量积分。若空间装入盒子或取紧致空间，动量变成离散，模展开改为求和。

$\mathbf k=0$ 时横向投影 $k_i k_j/|\mathbf k|^2$ 不定义，零模必须依据边界条件、全局 Gauss 定律和空间拓扑单独处理。

例如紧致无边界空间上的总电荷受积分 Gauss 定律限制。非平凡拓扑还可能支持 Wilson 线、磁通或调和一形式自由度，这些不能从局部平面波偏振计数中看出。

## 与弦理论的关系

开放弦的无质量一级激发可产生目标时空规范玻色子。其偏振向量满足横向条件，并存在：

$$
\epsilon_\mu
\sim\epsilon_\mu+\lambda k_\mu
$$

的等价关系，这与线性化 Maxwell 规范冗余同形。

这里需要区分理论与扇区。单个 D-brane 或一维 Chan–Paton 空间上的定向开弦扇区给出一个 Abelian $U(1)$ 矢量；加入重合的多重 D-brane 或更高维 Chan–Paton 因子后，低能理论通常是非 Abelian Yang–Mills，而不再只是 Maxwell 理论。开玻色弦和开超弦都含无质量矢量候选态，但玻色弦还含 tachyon；具有适当 GSO 投影的超弦可去掉相应 tachyon。具体规范群和物质谱还取决于弦类型、定向投影与 D-brane 构型。

闭弦无质量谱中的引力子、Kalb–Ramond 场和 dilaton 也通过世界面约束去除非物理偏振。理解 Maxwell 场量子化，有助于辨认弦谱中“协变张量分量”与“物理传播自由度”的差别。

但 Maxwell 规范固定与世界面 Diff×Weyl 规范固定不是同一个群作用，不能把两套 ghost 或 BRST 荷机械等同。

## 适用条件与事实边界

1. 本篇主要讨论四维平直时空中的自由 Abelian Maxwell 场。
2. 四维势有四个分量，但规范冗余与 Gauss 约束只留下两个物理传播偏振。
3. Coulomb 规范直接量子化横向自由度，Lorenz 规范保留显式 Lorentz 协变性但需处理非物理态。
4. $A_0=0$ 不能在有任意电荷源和边界条件时无条件采用。
5. 横向分解依赖空间拓扑和边界条件；零模与全局模需单独处理。
6. 规范势和传播子依赖规范，$F_{\mu\nu}$ 与正确计算的物理 S 矩阵元不依赖规范选择。
7. Gupta–Bleuler 条件施加在物理态上，而不是作为全 Hilbert 空间中的强算符恒等式。
8. Abelian Faddeev–Popov 鬼在常见线性协变规范中解耦；非 Abelian 鬼通常不解耦。
9. 正规排序去掉的平直真空常数不等于解决所有背景中的真空能问题。
10. helicity $\pm1$ 是四维无质量光子的两个物理偏振；其他维数的物理偏振数为 $D-2$。
11. 经典 Maxwell 波与单光子态不是同一对象；经典相干场通常对应含不确定光子数的相干态。
12. 弦谱中的规范冗余与 Maxwell 结构相关，但世界面规范对称和目标时空规范对称必须区分。

## 常见误区

1. **量子化 Maxwell 场就是把四个 $A_\mu$ 都当独立标量场。** 这样会重复计算规范方向并引入非物理态。
2. **$A_0$ 是第三种光子偏振。** 它没有独立动能，主要实施 Gauss 约束。
3. **光子自旋为一，所以有三个物理偏振。** 无质量光子没有静止系，四维只有 helicity $\pm1$。
4. **选定 Coulomb 规范后不再有任何边界或零模问题。** 残余规范和全局模仍取决于边界与拓扑。
5. **Lorenz 规范条件可作为严格算符恒等式强加给所有态。** 协变量子化需使用 Gupta–Bleuler 或 BRST 条件。
6. **传播子依赖 $\xi$，所以实验结果依赖规范。** 规范依赖部分在守恒流和完整振幅中抵消。
7. **Faddeev–Popov 鬼是实验可探测的负概率粒子。** 它不作为外态，只是规范固定的辅助场。
8. **Abelian 理论有鬼场，所以光子会与鬼散射。** 常见线性规范下 Abelian 鬼完全解耦。
9. **Coulomb 势的瞬时形式意味着超光速信号。** 规范相关势的瞬时项与横向辐射组合后给出因果可观测场。
10. **经典电磁波就是固定光子数态。** 最接近经典场的是相干态，而不是单一数态。

## 练习

1. 写出无源 Maxwell 作用量和规范变换。
2. 为什么 $\Pi^0=0$ 是约束？
3. Gauss 定律在正则量子化中扮演什么角色？
4. 为什么四个势分量最终只有两个物理自由度？
5. 写出 Coulomb 规范和横向场方程。
6. 偏振向量满足什么正交与完备关系？
7. 写出横向势的模展开结构。
8. 横向等时对易关系与普通 $\delta_{ij}$ 有何不同？
9. 单光子态怎样由真空构造？
10. 正规排序后的自由光子 Hamiltonian 是什么结构？
11. 为什么四维光子只有 helicity $\pm1$？
12. 写出 Lorenz 规范和 Gupta–Bleuler 物理态条件。
13. 协变规范固定项和 Maxwell 传播子的常见形式是什么？
14. 为什么 Abelian Faddeev–Popov 鬼解耦？
15. 为什么传播子可依赖规范而物理振幅不依赖？
16. 有电流时，规范不变性要求电流满足什么条件？
17. 为什么 Coulomb 规范势的非局域性不破坏因果性？
18. 为什么 $\mathbf k=0$ 零模需要单独处理？
19. $D$ 维 Maxwell 场有多少物理偏振？
20. 开弦无质量矢量偏振的等价关系与 Maxwell 规范变换有什么联系？

## 答案与提示

1. $S=-\frac14\int F_{\mu\nu}F^{\mu\nu}d^4x$；$A_\mu\to A_\mu+\partial_\mu\Lambda$。
2. Lagrangian 不含 $\partial_0A_0$ 的平方，故其共轭动量恒为零，不能反解速度。
3. 它限制物理初始数据和物理态，排除纵向电场的无源自由激发。
4. 一个规范配置方向和一个相应约束共去掉一对正则自由度，留下两个配置自由度。
5. $\nabla\cdot\mathbf A=0$；无源并适当选取 $A_0=0$ 后，$\Box\mathbf A^T=0$。
6. $\mathbf k\cdot\boldsymbol\epsilon_\lambda=0$，$\epsilon_\lambda^*\cdot\epsilon_{\lambda'}=\delta_{\lambda\lambda'}$，偏振和给出横向投影。
7. $A_i^T\sim\sum_{\lambda=1}^2\int d^3k\,[\epsilon_{\lambda i}a_\lambda e^{-ikx}+\epsilon^*_{\lambda i}a_\lambda^\dagger e^{ikx}]/\sqrt{2\omega}$。
8. 右边是 $i\delta^T_{ij}$，只投影到散度为零的横向子空间。
9. $|\mathbf k,\lambda\rangle=a_\lambda^\dagger(\mathbf k)|0\rangle$。
10. $:H:=\sum_\lambda\int\frac{d^3k}{(2\pi)^3}\,\omega_{\mathbf k}a_\lambda^\dagger(\mathbf k)a_\lambda(\mathbf k)$，对应正文采用的连续归一化。
11. 无质量小群与规范等价去掉纵向和时间样分量，只剩两个圆偏振；$+$、$-$ 标签需由偏振标架定向和 helicity 算符约定固定。
12. $\partial_\mu A^\mu=0$；$(\partial_\mu A^\mu)^{(+)}|\mathrm{phys}\rangle=0$。
13. $\mathcal L_{\mathrm{gf}}=-(\partial\cdot A)^2/(2\xi)$；传播子见正文，纵向项依 $\xi$。
14. 线性规范下 Faddeev–Popov 算符为与 $A$ 无关的 $\Box$，行列式只是场无关因子。
15. 纵向规范依赖项与守恒流收缩或在完整 Ward 恒等式中抵消。
16. $\partial_\mu J^\mu=0$。
17. 局域可观测场强在类空分离时对易；势本身不是规范不变量。
18. 横向投影含 $1/|\mathbf k|^2$，且全局 Gauss 定律与拓扑会改变零模结构。
19. $D-2$。
20. $\epsilon_\mu\sim\epsilon_\mu+\lambda k_\mu$ 表明沿动量方向的偏振是冗余，对应动量空间规范变换。

## 与其他概念的关系

- [[Maxwell 方程]] 给出经典场方程、Gauss 定律和电磁波；
- [[规范对称性]] 解释四维势的冗余和规范轨道；
- [[经典场论]] 与 [[Minkowski 时空]] 提供作用量和 Lorentz 协变框架；
- [[量子算符]]、[[对易关系]] 与 [[Fock 空间]] 构造光子态；
- [[Fourier 变换]] 将自由 Maxwell 方程分解为动量和偏振模式；
- [[光子]] 是量子化 Maxwell 场的单量子激发；
- [[场的正则量子化]] 系统处理场、共轭动量和约束；
- [[传播子]] 给出规范固定后的电磁传播核；
- [[规范固定]]、[[Faddeev-Popov 鬼场]] 与 [[BRST 对称性]] 给出协变量子化语言；
- [[Yang-Mills 理论]] 把 Abelian Maxwell 规范场推广到非交换群；
- [[Wilson 线与 Wilson 圈]] 说明紧致空间中的 Wilson 线和磁通自由度不包含在局部平面波计数中，并展示全局 holonomy 如何探测 Maxwell 场量子化未能直接看到的拓扑信息；
- [[开弦质量谱]] 的无质量矢量态在低能极限产生规范场。

## 参考资料

- Claude Itzykson and Jean-Bernard Zuber, *Quantum Field Theory*, McGraw-Hill, 1980.
- Michael E. Peskin and Daniel V. Schroeder, *An Introduction to Quantum Field Theory*, Westview Press, 1995, Chapters 9 and 16.
- Steven Weinberg, *The Quantum Theory of Fields, Vol. 1*, Cambridge University Press, 1995, Chapters 5 and 7.
- Lewis H. Ryder, *Quantum Field Theory*, 2nd ed., Cambridge University Press, 1996.
- Michael D. Schwartz, *Quantum Field Theory and the Standard Model*, Cambridge University Press, 2014, Chapters 8 and 14.
- Marc Henneaux and Claudio Teitelboim, *Quantization of Gauge Systems*, Princeton University Press, 1992.
- Paul A. M. Dirac, *Lectures on Quantum Mechanics*, Dover, 2001.
- N. N. Bogoliubov and D. V. Shirkov, *Introduction to the Theory of Quantized Fields*, Wiley, 1980.
- Joseph Polchinski, *String Theory, Vol. 1*, Cambridge University Press, 1998.
- David Tong, *Lectures on Quantum Field Theory*, [course notes](https://www.damtp.cam.ac.uk/user/tong/qft.html)
