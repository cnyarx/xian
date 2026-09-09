---
aliases:
  - Weyl Anomaly
  - Conformal Anomaly
  - Trace Anomaly
  - 共形反常
  - 迹反常
  - 缩放反常
  - 世界面缩放对称性失效
english_name: Weyl Anomaly
tags:
  - 物理学
  - 量子场论
  - 共形场论
  - 弦理论先修
  - 弦理论
prerequisites:
  - "[[手征反常]]"
  - "[[量子反常]]"
  - "[[规范对称性]]"
  - "[[能动张量]]"
  - "[[Faddeev-Popov 鬼场]]"
  - "[[beta 函数]]"
used_by:
  - "[[手征反常]]"
  - "[[量子反常]]"
  - "[[BRST 对称性]]"
  - "[[beta 函数]]"
  - "[[反常消除]]"
  - "[[二维 Euclidean 场论]]"
  - "[[算符乘积展开]]"
  - "[[正规序]]"
  - "[[弦理论完整学习路线图]]"
  - "[[弦理论与大模型跨学科关系图谱]]"
evidence_status: 教材事实
---

# Weyl 反常（Weyl Anomaly）

## 学习导航

- 上一页：[[手征反常]]
- 下一页：[[反常消除]]
- 总路线：[[弦理论完整学习路线图]]

## 一句话解释

Weyl 反常是经典局部度量缩放对称性在量子有效作用量中无法保持的现象；在二维共形场论中，它由中心荷控制，在弦世界面上则直接检验 Diff$\times$Weyl 规范冗余能否在量子层面保持。

## 为什么要学它

[[量子反常]] 已说明：经典作用量的对称性不保证量子测度、正规化和重整化后的有效作用量仍满足同一恒等式。[[手征反常]] 展示了轴流 Ward 恒等式怎样被量子效应修正；本页研究另一种对象——度量局部缩放和能动张量的迹。

Weyl 反常把以下知识线连在一起：

1. [[度量]] 与 [[规范对称性]] 中的局部尺度变换；
2. [[能动张量]] 的迹和背景度量变分；
3. 二维共形场论的中心荷、OPE 与 Virasoro 中心扩张；
4. Polyakov 非局域有效作用量和二维曲率；
5. 玻色弦、RNS 超弦的物质场与鬼场中心荷账本；
6. [[BRST 对称性]] 的量子幂零条件；
7. [[beta 函数]]、sigma 模型背景场和目标时空运动方程；
8. 非临界弦、linear dilaton、Liouville 场和内部 CFT。

## 先区分四个容易混淆的名称

### Weyl 反常

直观上，同一张 [[世界面]] 上可以画不同的坐标网格，改变网格疏密不应该改变物理结果；经典 Polyakov 理论中这种局部缩放对称性成立。形式上，把量子场论耦合到背景度量 $h_{ab}$，若经典理论在

$$
h_{ab}(\sigma)\longmapsto e^{2\omega(\sigma)}h_{ab}(\sigma)
$$

下不变，而量子有效作用量不再不变，就出现 Weyl 反常。

### 迹反常

对背景度量作无穷小 Weyl 变换时，有效作用量的响应可写成能动张量迹。因此 Weyl 反常常表现为

$$
\langle T^a{}_a\rangle\ne0.
$$

在明确背景、边界条件和能动张量定义后，Weyl anomaly 与 trace anomaly 常被当作同一现象的两种表述。

### 共形反常

二维局部共形变换可由微分同胚和 Weyl 变换组合描述。平直背景上的共形代数具有 Virasoro 中心扩张，曲背景上则出现迹反常。二者由同一个中心荷联系，但“共形反常”在不同教材中可能强调其中任一侧，使用时应说明语境。

### 尺度反常

全局尺度变换只对应常数缩放，Weyl 变换允许 $\omega(\sigma)$ 随位置变化。平直空间的尺度异常、运行耦合和曲背景的 Weyl 反常彼此相关，但不能在任意维数、任意背景和任意改进能动张量下不加条件地视为同一定义。

## 本页约定

### Euclidean 生成泛函

本页讨论二维 Euclidean 世界面，定义

$$
Z_E[h]
=
\int\mathcal D\Psi\,e^{-S_E[\Psi,h]},
\qquad
W_E[h]=-\log Z_E[h].
$$

这里 $h_{ab}$ 是正定世界面度量，$h=\det h_{ab}$。能动张量期望值定义为

$$
\boxed{
\langle T_{ab}\rangle
=
-\frac{2}{\sqrt h}
\frac{\delta W_E}{\delta h^{ab}}
}.
$$

无穷小 Weyl 变换取

$$
\delta_\omega h_{ab}=2\omega h_{ab},
\qquad
\delta_\omega h^{ab}=-2\omega h^{ab}.
$$

由这些定义得到

$$
\boxed{
\delta_\omega W_E
=
\int d^2\sigma\sqrt h\,
\omega\,\langle T^a{}_a\rangle
}.
$$

若改变 $W_E$、能动张量或 Euclidean 延拓的定义，整体符号可能改变。

### 曲率和 Laplacian

本页使用

$$
[\nabla_a,\nabla_b]V^c
=R^c{}_{dab}V^d,
\qquad
R_{db}=R^c{}_{dcb},
$$

以及

$$
\Box=\nabla^a\nabla_a.
$$

在正定紧致流形上，$-\Box$ 的非零本征值非负。若文献定义 $\Delta=-\Box$，Polyakov 作用量的显示整体号会相应改写。

### 左右中心荷

允许左右移动扇区中心荷不同，记为 $c_L,c_R$。对非手征理论常有

$$
c_L=c_R=c.
$$

本页写“中心荷 $c$”时，默认指每个手征扇区的共同值，而曲背景迹反常使用左右和。

## 从经典 Weyl 对称到量子迹反常

若经典作用量满足

$$
\delta_\omega S_E=0,
$$

则经典能动张量在壳上可满足

$$
T^a{}_a=0.
$$

量子理论必须定义测度、调节短距离发散并重整化复合算符。这些步骤可能引入无法由允许的局域反项同时消除的 Weyl 响应。于是

$$
\delta_\omega W_E\ne0.
$$

对无边界二维背景，局域性、维数和微分同胚不变性把非平凡曲率项限制为

$$
\boxed{
\langle T^a{}_a\rangle_E
=
-\frac{c_L+c_R}{48\pi}R^{(2)}
}.
$$

非手征理论 $c_L=c_R=c$ 时化为

$$
\boxed{
\langle T^a{}_a\rangle_E
=
-\frac{c}{24\pi}R^{(2)}
}.
$$

这里的负号依赖前述 $W_E$、$T_{ab}$ 和曲率约定；不同教材出现相反号时，应先比较定义，而不是只比较公式表面。

## 有限 Weyl 变换

在二维令

$$
\widetilde h_{ab}=e^{2\omega}h_{ab}.
$$

曲率变换为

$$
\boxed{
\widetilde R^{(2)}
=e^{-2\omega}
\left(R^{(2)}-2\Box\omega\right)
}.
$$

与迹反常积分后，对非手征中心荷 $c$ 可写 Wess–Zumino 泛函

$$
\boxed{
W_E[e^{2\omega}h]-W_E[h]
=
-\frac{c}{24\pi}
\int d^2\sigma\sqrt h\,
\left[(\nabla\omega)^2+\omega R^{(2)}\right]
}.
$$

该表达满足连续 Weyl 变换的组合一致性。它不是说 $W_E$ 本身是局域泛函；局域的是两个共形相关度量之间的差。

## Polyakov 非局域有效作用量

二维迹反常可由 Polyakov induced-gravity 作用量积分得到。在本页 $\Box=\nabla^2$ 的约定下，可写

$$
\boxed{
W_P[h]
=
\frac{c}{96\pi}
\int d^2\sigma\sqrt h\,
R^{(2)}\Box^{-1}R^{(2)}
}.
$$

它是非局域的，因为 $\Box^{-1}$ 是 Green 函数。对紧致无边界曲面，常数是 $\Box$ 的零模，所以 $\Box^{-1}$ 只能在与零模正交的子空间上定义。等价地，需要明确投影掉常数模，并单独处理 Euler 特征相关部分。

不能把 $R\Box^{-1}R$ 当作普通点乘，也不能忽略 Green 函数的边界条件。若使用 $\Delta=-\Box$，同一物理泛函会显示为相反整体号。

## 中心荷为何同时出现在三个地方

### 能动张量 OPE

二维 CFT 的 holomorphic 能动张量满足

$$
T(z)T(w)
\sim
\frac{c/2}{(z-w)^4}
+
\frac{2T(w)}{(z-w)^2}
+
\frac{\partial T(w)}{z-w}.
$$

最高阶极点的系数定义中心荷。

### Virasoro 中心扩张

把 $T(z)$ 展开成模 $L_n$，得到

$$
\boxed{
[L_m,L_n]
=
(m-n)L_{m+n}
+
\frac{c}{12}(m^3-m)\delta_{m+n,0}
}.
$$

中心项不是经典 Witt 代数的一部分，而是量子算符乘积的短距离奇点留下的中心扩张。

### 曲背景迹反常

同一个 $c$ 决定

$$
\langle T^a{}_a\rangle_E
=-\frac{c}{24\pi}R^{(2)}
$$

对非手征理论的系数。OPE 中的 $T(z)$ 与物理分量 $T_{zz}$ 之间可能含 $2\pi$ 等归一化因子，所以跨教材比较时应整套比较 OPE、模展开和能动张量定义。

## Weyl 反常与引力反常不同

二维手征理论可有 $c_L\ne c_R$。此时两种组合控制不同现象：

$$
\boxed{
\text{Weyl anomaly}\propto c_L+c_R
},
\qquad
\boxed{
\text{gravitational anomaly}\propto c_L-c_R
}.
$$

Weyl 反常涉及能动张量迹；微分同胚或局域 Lorentz 引力反常涉及相应守恒恒等式。二者不能因为都含中心荷就混为一谈。

## 一阶系统的中心荷

### 反对易 $bc$ 系统

若 $b$ 的共形权为 $\lambda$，$c$ 的权为 $1-\lambda$，反对易 $bc$ 系统中心荷为

$$
\boxed{
c_{bc}=1-3(2\lambda-1)^2
}.
$$

弦世界面 Diff$\times$Weyl 规范固定产生权重 $(2,-1)$ 的 $bc$ 鬼，因此

$$
c_{bc}=1-3(3)^2=-26.
$$

### 对易 $\beta\gamma$ 系统

若 $\beta$ 的权为 $\lambda$，$\gamma$ 的权为 $1-\lambda$，对易系统中心荷为

$$
\boxed{
c_{\beta\gamma}
=-1+3(2\lambda-1)^2
}.
$$

RNS 超弦的 superghost 权重为 $(3/2,-1/2)$，所以

$$
c_{\beta\gamma}=-1+3(2)^2=11.
$$

这里 $\beta\gamma$ 是 commuting 或 bosonic superghost，不是优化器中的 $\beta_1,\beta_2$。

## 玻色弦中心荷账本

在平直 $D$ 维目标时空，每个自由坐标标量 $X^\mu$ 贡献 $1$，所以

$$
c_X=D.
$$

规范固定的 $bc$ 鬼贡献

$$
c_{bc}=-26.
$$

总中心荷为

$$
\boxed{
c_{\mathrm{tot}}=D-26
}.
$$

标准平直临界玻色弦要求

$$
c_{\mathrm{tot}}=0,
$$

因此

$$
\boxed{D=26}.
$$

这不是说任意中心荷非零的二维 CFT 都不一致。普通二维 CFT 可以有非零中心荷；特殊之处在于弦世界面的 Weyl 变换是被规范化的冗余，未处理的总反常会破坏规范独立性和 BRST 构造。

## RNS 超弦中心荷账本

RNS 物质坐标贡献

$$
c_X=D,
$$

$D$ 个 Majorana 世界面费米子贡献

$$
c_\psi=\frac D2.
$$

鬼系统贡献

$$
c_{bc}=-26,
\qquad
c_{\beta\gamma}=11.
$$

因此

$$
\boxed{
c_{\mathrm{tot}}
=D+\frac D2-26+11
=\frac{3D}{2}-15
}.
$$

令其为零得到

$$
\boxed{D=10}.
$$

$D=10$ 来自世界面超共形物质与鬼系统的中心荷平衡，不是 GSO 投影直接推出。GSO 投影负责谱的手征性、模不变性和时空超对称等结构，不能与中心荷账本互相替代。

## BRST 幂零与正规序截距

在玻色弦中，量子 BRST 荷平方包含由总中心荷和正规序常数产生的项。标准表述下，一致条件包括

$$
\boxed{
c_{\mathrm{tot}}=0,
\qquad
a=1
}.
$$

因此只写 $c_{\mathrm{tot}}=0$ 还没有完整说明物理态条件中的正规序截距。

RNS 常见的物质扇区截距是

$$
a_{\mathrm{NS}}=\frac12,
\qquad
a_{\mathrm R}=0.
$$

这些数值来自 NS/R 边界条件与零点能。superghost picture 会改变 ghost vacuum、ghost contribution 以及完整 $L_0$ 物理态条件的记账方式；因此讨论总 Hilbert 空间的截距时，仍须固定 picture、ghost vacuum 和 $L_0$ 定义，不能把裸数值脱离语境搬用。

## 一般 sigma 模型背景

弦在背景 $G_{\mu\nu}(X)$、$B_{\mu\nu}(X)$ 和 dilaton $\Phi(X)$ 中传播时，世界面理论具有一组位置依赖耦合。量子 Weyl 不变性不再只是平直自由场的一个总中心荷数字，而要求相应 Weyl anomaly coefficients 消失，模去冗余变换。

令

$$
H_{\mu\nu\rho}=3\partial_{[\mu}B_{\nu\rho]}.
$$

在常用玻色弦最低阶约定中，度量和 $B$ 场的 Weyl 系数可写为

$$
\boxed{
\mathcal B^G_{\mu\nu}
=
\alpha'
\left(
R_{\mu\nu}
-\frac14H_{\mu\rho\sigma}H_\nu{}^{\rho\sigma}
+2\nabla_\mu\nabla_\nu\Phi
\right)
+O(\alpha'^2)
},
$$

$$
\boxed{
\mathcal B^B_{\mu\nu}
=
\alpha'
\left(
-\frac12\nabla^\rho H_{\rho\mu\nu}
+\nabla^\rho\Phi\,H_{\rho\mu\nu}
\right)
+O(\alpha'^2)
}.
$$

令这些系数消失，在相应近似和场重定义意义下给出目标时空背景方程。$\mathcal B^\Phi$ 还包含中心荷亏损项，但其常数、归一化和显示符号依维数、作用量与 scheme 定义；不能把未声明约定的孤立 $\mathcal B^\Phi=0$ 直接称为唯一形式的 dilaton 运动方程。

## 普通 RG beta 不等于 Weyl anomaly coefficient

[[beta 函数]] 定义普通 RG beta 为耦合随重整化尺度的流动。对背景度量，最低阶特例可写

$$
\beta^G_{\mu\nu}
=
\alpha'R_{\mu\nu}+O(\alpha'^2)
$$

在无 $B$ 场、常数 dilaton 和相应 scheme 下成立。但一般有

$$
\boxed{
\beta^G_{\mu\nu}\ne\mathcal B^G_{\mu\nu}
}.
$$

两者可能相差：

- 目标空间微分同胚，即沿向量场的 Lie 导数；
- $B$ 场规范变换；
- dilaton 对能动张量的改进；
- 冗余算符方向；
- 局域场重定义；
- 重整化方案变换。

因此“beta 为零”等价于“Weyl 反常消失”只在排除这些冗余并固定定义后才能成立。RG fixed point 也不是优化器损失收敛点。

## 场重定义与时空方程

若背景场作局域可逆重定义，beta 向量和低能有效作用量的显示形式会改变，但物理散射和 Weyl 不变条件的等价类不应改变。因此：

1. 最低阶 $R_{\mu\nu}=0$ 是特定简化背景下的结果；
2. 更高阶有 $\alpha'$ 曲率修正；
3. 含 $B$ 场和 dilaton 时需联立全部系数；
4. 目标空间微分同胚和场重定义方向不代表新的物理背景流；
5. 世界面 Weyl 条件与目标时空有效作用量方程的对应依赖同一阶次和同一 scheme。

## 非临界弦与 Liouville 模式

若物质和鬼场中心荷没有按平直临界账本相消，Weyl 因子不再只是可完全除去的规范自由度。把

$$
h_{ab}=e^{2\varphi}\widehat h_{ab}
$$

代入量子有效作用量后，$\varphi$ 可获得 Liouville 动力学。

玻色 Liouville 理论常写

$$
\boxed{
c_L=1+6Q^2
}.
$$

若物质 CFT 中心荷为 $c_m$，加上 $bc$ 鬼后总账为

$$
c_m+c_L-26=0.
$$

因此

$$
\boxed{
Q^2=\frac{25-c_m}{6}
}.
$$

分子是 $25-c_m$，不是 $26-c_m$，因为 Liouville 场本身的中心荷含常数 $1$。

这说明“只有 $D=26$ 或 $D=10$ 才有任何弦理论”过强。临界维数是标准平直自由世界面场内容的结果；内部 CFT、linear dilaton、Liouville 模式和其他非临界构造可改变中心荷账本，但同时必须重新检查模不变性、谱和幺正性。

## Linear dilaton 与内部 CFT

线性 dilaton 背景

$$
\Phi(X)=V_\mu X^\mu
$$

会改进能动张量并改变中心荷。具体改变量依 $\alpha'$、时空号差和 $V^2$ 约定。

紧化时，若部分自由坐标由内部 CFT 替代，总中心荷条件约束的是

$$
c_{\mathrm{noncompact}}+c_{\mathrm{internal}}+c_{\mathrm{ghost}}=0,
$$

而不是简单把非紧目标空间维数机械设为 $26$ 或 $10$。

## 异质弦必须逐侧计数

heterotic string 的左、右移动扇区使用不同世界面结构，所以中心荷必须逐侧平衡。中心荷条件可以限制内部自由度总量，却不会单独唯一推出完整规范群。

得到特定十维规范群还需要模不变性、偶自对偶晶格或等价的 current algebra 条件。不能只凭“中心荷正好”跳过这些全局一致性要求。

## 世界面与目标时空反常的边界

必须区分：

1. **世界面 Weyl 反常**：二维 Diff$\times$Weyl 规范冗余的量子破缺；
2. **世界面引力反常**：左右手征不平衡导致微分同胚或局域 Lorentz 恒等式异常；
3. **目标时空迹反常**：目标时空 QFT 对背景时空局部缩放的响应；
4. **目标时空规范或引力反常**：目标时空手征谱的规范、微分同胚或局域 Lorentz 一致性问题；
5. **全局轴流反常**：例如 ABJ 反常，它可以是正确理论中的物理效应。

世界面中心荷抵消不能代替目标时空 Green–Schwarz 反常消除；目标时空 anomaly polynomial 的因子化也不能代替世界面 Weyl/BRST 一致性。

## 与大模型的真实交叉点和禁止误连

Weyl 反常与大模型之间没有已知的直接物理等价关系。可复用的是更抽象的方法论：区分冗余表示与物理量、检查正则化是否保持恒等式、追踪局域与全局约束、明确 scheme 和变量重定义下哪些量不变。

以下类比必须禁止：

- Weyl scaling $\ne$ 特征缩放、标准化、LayerNorm 或 RMSNorm；
- 中心荷 $\ne$ 参数量、隐藏维度、注意力头数或模型容量；
- 临界维数 $\ne$ embedding dimension 或 context length；
- $bc$ 鬼 $\ne$ 辅助 token、负样本或 dropout mask；
- $\beta\gamma$ 鬼 $\ne$ Adam 的 $\beta_1,\beta_2$；
- Polyakov 非局域作用量 $\ne$ 全局注意力；
- sigma-model beta $\ne$ 优化器 beta；
- RG fixed point $\ne$ 优化器收敛点；
- Liouville 场 $\ne$ 新增网络层或 scale token；
- anomaly cancellation $\ne$ 梯度裁剪、ensemble 抵消或安全对齐。

## 适用条件与事实边界

1. 本页二维迹反常公式使用明确的 Euclidean $W_E=-\log Z_E$、能动张量和曲率约定；改约定可能翻转整体号。
2. 非手征理论的 $c$ 是每个手征扇区共同中心荷；一般情形应使用 $(c_L+c_R)/2$ 进入迹反常。
3. $c_L+c_R$ 控制 Weyl 反常，$c_L-c_R$ 控制二维引力反常。
4. 单个非零中心荷的二维 CFT 不因此自动不一致；弦世界面要求总账处理，是因为 Weyl 对称是规范冗余。
5. $c_{\mathrm{tot}}=0$ 给出标准平直临界世界面中心荷条件，但完整量子一致性还包括 BRST 截距、模不变性、谱和边界条件。
6. $D=26$ 和 $D=10$ 分别适用于标准平直玻色弦和 RNS 场内容，不是所有弦背景的唯一可能。
7. sigma 模型普通 beta 与 Weyl anomaly coefficient 可能相差微分同胚、规范变换、改进项、冗余算符、场重定义和 scheme。
8. 背景场方程的显示形式只在固定 $\alpha'$ 阶次、作用量和场变量后有意义。
9. Polyakov 作用量中的 $\Box^{-1}$ 需要 Green 函数、边界条件和零模投影。
10. 非临界弦引入 Liouville 或 linear dilaton 后，必须重新检查完整世界面一致性，不能只补一个中心荷数字。
11. 世界面 Weyl 反常、目标时空迹反常和目标时空规范/引力反常属于不同层次。
12. 后续 [[反常消除]] 分别检查表示求和、Green–Schwarz、inflow、中心荷、tadpole 与全局拓扑条件，不能让一种机制替代其他层次。

## 常见误区

1. **每种量子场都会“破坏”Weyl 对称性，所以任何含量子场的理论都不一致。** 各场贡献中心荷；普通 CFT 可有非零中心荷，弦世界面要求处理的是总规范反常。
2. **只要 $c\ne0$ 就存在负概率。** 非零中心荷本身不是普通 CFT 非幺正的判据。
3. **$c_{\mathrm{tot}}=0$ 自动保证完整弦论一致。** 还需 BRST、截距、模不变性、谱和全局条件。
4. **RNS 的 $D=10$ 来自 GSO 投影。** 它来自物质与鬼中心荷平衡；GSO 处理另一组谱和模不变性问题。
5. **普通 beta 函数就是 Weyl 反常系数。** 两者可能相差冗余方向与改进项。
6. **$\beta^G=\alpha'R$ 是完整弦背景方程。** 它只是在简化背景和最低阶下成立。
7. **Polyakov 非局域作用量是局域曲率平方项。** $\Box^{-1}$ 使它非局域，并需处理零模。
8. **Weyl 反常与引力反常相同。** 二者分别由 $c_L+c_R$ 与 $c_L-c_R$ 控制。
9. **Liouville 中 $Q^2=(26-c_m)/6$。** 正确账本给出 $(25-c_m)/6$。
10. **中心荷可以直接解释模型容量。** 两者没有已知物理等价关系。

## 练习

1. 写出本页 $Z_E$、$W_E$ 和 $\langle T_{ab}\rangle$ 的定义。
2. 从 $\delta_\omega h^{ab}=-2\omega h^{ab}$ 推导 $\delta_\omega W_E$ 与能动张量迹的关系。
3. 写出一般二维理论和非手征二维 CFT 的迹反常系数。
4. 有限 Weyl 变换下二维标量曲率怎样变化？
5. 为什么 Polyakov 有效作用量是非局域的？紧致曲面还需处理什么？
6. 说明同一中心荷怎样出现在 $TT$ OPE、Virasoro 代数和迹反常中。
7. 用一阶系统公式计算弦世界面 $bc$ 鬼和 RNS $\beta\gamma$ superghost 的中心荷。
8. 推导玻色弦的 $D=26$ 和 RNS 超弦的 $D=10$。
9. 为什么普通二维 CFT 的 $c\ne0$ 不自动表示理论不一致？
10. 为什么玻色弦 BRST 条件不能只写 $c_{\mathrm{tot}}=0$？
11. 举出普通 RG beta 与 Weyl anomaly coefficient 可能不同的四种来源。
12. 由 $c_L=1+6Q^2$ 和总账推导 $Q^2=(25-c_m)/6$。
13. 比较 Weyl 反常与二维引力反常所依赖的中心荷组合。
14. 解释世界面 Weyl 反常为何不能由目标时空 Green–Schwarz 机制替代处理。

## 答案与提示

1. $Z_E[h]=\int\mathcal D\Psi e^{-S_E}$，$W_E=-\log Z_E$，$\langle T_{ab}\rangle=-2(\delta W_E/\delta h^{ab})/\sqrt h$。
2. 由 $\delta W_E=\int(\delta W_E/\delta h^{ab})\delta h^{ab}$，代入定义和 $\delta h^{ab}=-2\omega h^{ab}$，得到 $\delta_\omega W_E=\int\sqrt h\,\omega\langle T^a{}_a\rangle$。
3. 一般为 $-(c_L+c_R)R^{(2)}/(48\pi)$；若 $c_L=c_R=c$，为 $-cR^{(2)}/(24\pi)$，符号依本页约定。
4. $\widetilde R^{(2)}=e^{-2\omega}(R^{(2)}-2\Box\omega)$。
5. 它含 $\Box^{-1}$ Green 函数；紧致曲面要投影常数零模并指定边界或归一化条件。
6. $TT$ OPE 最高阶极点给出 $c$，模积分产生 Virasoro 中心项，耦合曲背景后同一短距离信息产生迹反常。
7. $bc$ 取 $\lambda=2$，得 $1-3(3)^2=-26$；$\beta\gamma$ 取 $\lambda=3/2$，得 $-1+3(2)^2=11$。
8. 玻色弦：$D-26=0$，故 $D=26$。RNS：$D+D/2-26+11=0$，故 $D=10$。
9. 中心荷是 CFT 的物理数据；只有当对应局部 Weyl 变换是需要除去的规范冗余时，总反常才破坏规范一致性。
10. 标准玻色弦还需正规序截距 $a=1$，并进一步检查模不变性等全局条件。
11. 目标空间微分同胚、$B$ 场规范变换、dilaton 改进、冗余算符、场重定义或 scheme 中任选四种。
12. $c_m+(1+6Q^2)-26=0$，所以 $6Q^2=25-c_m$。
13. Weyl 反常依赖 $c_L+c_R$；引力反常依赖 $c_L-c_R$。
14. 前者属于二维世界面 Diff$\times$Weyl/BRST 结构；后者通过目标时空形式场耦合抵消目标时空 anomaly polynomial，作用空间和恒等式不同。

## 与其他概念的关系

- [[手征反常]] 展示轴流或手征规范 Ward 恒等式的反常，并区分它与世界面迹反常；
- [[量子反常]] 提供 Wess–Zumino 一致性、局域反项和规范反常的一般框架；
- [[度量]] 定义 Weyl 变换作用的几何对象；
- [[规范对称性]] 给出弦世界面微分同胚与经典 Weyl 局部尺度冗余；
- [[能动张量]] 通过背景度量变分定义 $T_{ab}$ 及其迹；
- 二维共形场论提供中心荷、能动张量 OPE 和 Virasoro 代数，本页在对应专题页创建前自包含这些公式；
- [[beta 函数]] 说明世界面 RG 流与 Weyl anomaly coefficient 的联系和边界；
- [[重整化群]] 提供尺度流、固定点和 scheme 变换的语言；
- [[BRST 对称性]] 把总中心荷反常与量子 BRST 荷幂零性联系起来；
- [[Faddeev-Popov 鬼场]] 解释 $bc$ 鬼的来源及其负中心荷；
- Polyakov 作用量中的世界面度量是 Weyl 规范冗余的载体，本页在对应专题页创建前自包含其量子反常结构；
- [[反常消除]] 将局域规范反常、Green–Schwarz、inflow、tadpole 和中心荷条件统一为一致性检查表；
- [[二维 Euclidean 场论]] 固定 $\Delta\ln|z|^2=4\pi\delta^{(2)}$、$G_0=-(4\pi)^{-1}\ln(\mu^2|z|^2)$ 和紧致曲面零模投影，为 Weyl 反常的世界面计算提供完整的二维 Euclidean 约定；
- [[算符乘积展开]] 系统说明 $T(z)T(w)$ 四阶极点如何定义中心荷，并区分平面局部 OPE 与本页曲背景迹反常；
- [[正规序]] 定义自由场量子能动张量，同时说明正规序不能删除 $TT$ 中心项或曲背景 Weyl 反常；
- [[弦理论完整学习路线图]] 将本节点放在手征反常与反常消除之间；
- [[弦理论与大模型跨学科关系图谱]] 记录可复用的方法论关系并阻止伪物理类比；
- 跨学科图谱层的概览页 [[临界维数]]、[[中心荷]] 与 [[对称性与不变量]] 以本页为 Weyl 反常和中心荷账本的正式锚点。

## 参考资料

- Joseph Polchinski, *String Theory, Vol. 1*, Cambridge University Press, 1998, Chapters 2–3.
- Philippe Di Francesco, Pierre Mathieu and David Sénéchal, *Conformal Field Theory*, Springer, 1997.
- Paul Ginsparg, *Applied Conformal Field Theory*, arXiv:hep-th/9108028.
- A. M. Polyakov, “Quantum Geometry of Bosonic Strings,” *Physics Letters B* 103 (1981), 207–210.
- David Friedan, “Nonlinear Models in $2+\epsilon$ Dimensions,” *Physical Review Letters* 45 (1980), 1057.
- C. G. Callan, D. Friedan, E. J. Martinec and M. J. Perry, “Strings in Background Fields,” *Nuclear Physics B* 262 (1985), 593–609.
- David Tong, *Lectures on String Theory*, arXiv:0908.0333.
- Barton Zwiebach, *A First Course in String Theory*, 2nd ed., Cambridge University Press, 2009.
- 库内相关推导：[[为什么标准超弦理论要求十维]]。
