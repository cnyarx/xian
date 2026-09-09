---
aliases:
  - Beta Function
  - β 函数
  - beta function
english_name: Beta Function
tags:
  - 物理学
  - 量子场论
  - 重整化群
  - 弦理论先修
prerequisites:
  - "[[弦理论/物理学/正规化与重整化]]"
  - "[[弦理论/物理学/重整化群]]"
  - "[[弦理论/数学/曲率]]"
  - "[[弦理论/数学/群表示]]"
  - "[[弦理论/数学/Lie 代数]]"
used_by:
  - "[[弦理论/物理学/有效场论]]"
  - "[[弦理论/物理学/Yang-Mills 理论]]"
  - "[[弦理论/物理学/Weyl 反常]]"
  - "[[弦理论/弦理论完整学习路线图]]"
evidence_status: 教材事实
---

# beta 函数（Beta Function）

## 一句话解释

beta 函数（beta function）描述：在裸参数固定时，重整化耦合怎样随重整化尺度变化。它是耦合空间中的向量场，控制耦合的尺度演化；结合场与复合算符的反常维数和算符混合矩阵，才能描述完整的 RG 演化。

## 为什么要学它

[[弦理论/物理学/重整化群]] 把尺度流写成常微分方程，并解释了运行耦合、固定点和 RG 改善。但没回答三个更具体的问题：

- 怎么从给定的重整化方案和反项中定量提取 beta 函数？
- 不同理论（标量、量子电动力学、量子色动力学、弦世界面）的 beta 函数具体是哪些系数？
- 哪些系数在不同方案之间不变，哪些会变？

本页补充这些内容，会自包含地给出 $\lambda\phi^4$、QED、QCD 和世界面 sigma 模型的一圈例子，并解释方案依赖的边界，不重复运行耦合积分、Landau 极点和 Wilsonian 教学。

QED、QCD 和非线性 sigma 模型的独立教程尚未建立，因此本页仍以自包含“实例”方式给出它们的 beta 函数。[[弦理论/物理学/Yang-Mills 理论]] 已建立，负责非 Abelian 规范场的定义、生成元归一化、作用量和自相互作用；本页只负责一圈系数、方案边界和渐近自由判据。

## 本篇约定

采用自然单位 $\hbar=c=1$ 和 mostly-minus 度规。重整化尺度记为 $\mu$，导数约定为

$$
\beta(g)\equiv\mu\frac{d g}{d\mu}\bigg|_{\text{裸参数固定}}.
$$

若文献使用 $\mu^2 d/d\mu^2$ 或 $d/d\ln\mu^2$，所得结果乘 $1/2$ 才能与本页比较。在 $d=4-2\varepsilon$ 维中，通常把经典工程量纲项与四维量子 beta 分开：

$$
\beta_d(g,\varepsilon)
=-\kappa\varepsilon g+\beta(g),
$$

其中 $\lambda\phi^4$ 耦合 $\kappa=2$，QED 或 Yang-Mills 规范耦合 $\kappa=1$。

## 正式定义

对一组重整化耦合 $g^i$，beta 函数定义为

$$
\boxed{
\beta^i(g)
\equiv
\mu\frac{d g^i}{d\mu}
\bigg|_{\text{裸参数固定}}
}.
$$

它是耦合空间中的向量场。[[弦理论/物理学/重整化群]] 解释了它怎样驱动运行耦合和固定点，本页聚焦提取方法。

## 从 MS 和 MS-bar 的极点提取 beta

在 $d=4-2\varepsilon$ 维的 MS 或 $\overline{\mathrm{MS}}$ 方案中，裸耦合通常含 $1/\varepsilon$ 极点：

$$
g_0
=
\mu^{\kappa\varepsilon}
\left[
g
+
\frac{a_1(g)}{\varepsilon}
+
\frac{a_2(g)}{\varepsilon^2}
+\cdots
\right].
$$

由裸耦合不依赖 $\mu$，令

$$
F(g,\varepsilon)
=
g
+
\frac{a_1(g)}{\varepsilon}
+
\frac{a_2(g)}{\varepsilon^2}
+\cdots.
$$

对 $g_0=\mu^{\kappa\varepsilon}F(g,\varepsilon)$ 展开链式法则，得到

$$
0
=
\mu^{-\kappa\varepsilon}
\mu\frac{d g_0}{d\mu}
=
\kappa\varepsilon F(g,\varepsilon)
+
\beta_d(g,\varepsilon)\,\partial_gF(g,\varepsilon).
$$

因此可导出精确关系

$$
\boxed{
\beta_d(g,\varepsilon)
=
-\kappa\varepsilon\,
\frac{F(g,\varepsilon)}{\partial_gF(g,\varepsilon)}
=
-\kappa\varepsilon\,
\frac{g+\dfrac{a_1(g)}{\varepsilon}+\cdots}
{1+\dfrac{a_1'(g)}{\varepsilon}+\cdots}
}.
$$

要求 $\beta_d$ 在 $\varepsilon\to0$ 时有限，则四维 beta 只由简单极点 $a_1$ 决定：

$$
\boxed{
\beta(g)
=
\kappa\bigl[
g\,a_1'(g)-a_1(g)
\bigr]
}.
$$

若采用乘法形式

$$
g_0
=
\mu^{\kappa\varepsilon}g Z_g,
\qquad
Z_g
=
1+\frac{z_1(g)}{\varepsilon}
+\frac{z_2(g)}{\varepsilon^2}+\cdots,
$$

则 $a_1(g)=g z_1(g)$，代入得到

$$
\boxed{
\beta(g)=\kappa g^2 z_1'(g)
}.
$$

这里的 $a_1$ 是裸耦合整体加法展开中的简单极点系数，不是任意一个图或任意一个 $Z$ 因子的极点。$\overline{\mathrm{MS}}$ 方案把 $1/\bar\varepsilon=1/\varepsilon-\gamma+\ln4\pi$ 的有限常数吸收到尺度定义中，不改变“简单极点决定 beta”的结构。

## 单实标量 $\lambda\phi^4$ 理论

采用

$$
\mathcal L_{\mathrm{int}}
=-\frac{\lambda}{4!}\phi^4
$$

和 $\overline{\mathrm{MS}}$ 方案。已有结果：

$$
\boxed{
\beta_\lambda(\lambda)
=
\frac{3\lambda^2}{16\pi^2}
-
\frac{17\lambda^3}{3(16\pi^2)^2}
+
O(\lambda^4)
}.
$$

在 $d=4-2\varepsilon$ 中：

$$
\beta_{\lambda,d}
=
-2\varepsilon\lambda
+
\frac{3\lambda^2}{16\pi^2}
-
\frac{17\lambda^3}{3(16\pi^2)^2}
+
O(\lambda^4).
$$

若定义 $u=\lambda/(16\pi^2)$，则

$$
\beta_u
=
-2\varepsilon u
+3u^2
-\frac{17}{3}u^3
+\cdots.
$$

[[弦理论/物理学/正规化与重整化]] 已从一圈反项推导出 $\beta=3\lambda^2/(16\pi^2)$；两圈系数需要两圈反项才能完整推导，这里直接列出已知结果。不能把这些系数套到 $-g\phi^4/4$、$-g\phi^4$ 或 $O(N)$ 对称归一化上。

## 量子电动力学（QED）一圈

对一个电荷 $Q=1$ 的 Dirac 费米子，在 $\overline{\mathrm{MS}}$ 方案中，裸电荷整体加法展开的简单极点为

$$
a_1(e)=\frac{e^3}{24\pi^2}+O(e^5).
$$

由 $\kappa=1$ 和简单极点公式得到：

$$
\boxed{
\beta_e(e)
=
\mu\frac{d e}{d\mu}
=
\frac{e^3}{12\pi^2}
+
O(e^5)
}.
$$

令 $\alpha=e^2/(4\pi)$，则

$$
\boxed{
\beta_\alpha(\alpha)
=
\mu\frac{d\alpha}{d\mu}
=
\frac{2}{3\pi}\alpha^2
+
O(\alpha^3)
}.
$$

多个 Dirac 费米子时，一圈结果乘以 $\sum_f Q_f^2$。正号表示电磁耦合向紫外增强，QED 不是渐近自由理论。

## 量子色动力学（QCD）一圈与渐近自由

考虑 $SU(N_c)$，有 $n_f$ 个基本表示 Dirac 费米子。采用

$$
\operatorname{tr}(T^a T^b)=T_F\delta^{ab},
\qquad
T_F=\frac12,
\qquad
C_A=N_c.
$$

定义

$$
\beta_0
=
\frac{11}{3}C_A-\frac{4}{3}T_F n_f
=
\boxed{
\frac{11}{3}N_c-\frac{2}{3}n_f
}.
$$

则一圈 beta 函数为

$$
\boxed{
\mu\frac{d g_s}{d\mu}
=
-\frac{\beta_0}{16\pi^2}g_s^3
+
O(g_s^5)
}.
$$

对 $\alpha_s=g_s^2/(4\pi)$：

$$
\boxed{
\mu\frac{d\alpha_s}{d\mu}
=
-\frac{\beta_0}{2\pi}\alpha_s^2
+
O(\alpha_s^3)
}.
$$

渐近自由条件为

$$
\boxed{
\beta_0>0
\iff
n_f<\frac{11}{2}N_c
}.
$$

对 $SU(3)$，$N_c=3$，条件为 $n_f\le16$。质量无关方案中的 $n_f$ 表示当前有效理论包含的活跃味数；跨过重夸克阈值时需 EFT 匹配，不能简单从公式中删去一个味。

## 方案变换下的普适系数

### 单耦合

设单个无量纲耦合展开为

$$
\beta(a)=b_0 a^2+b_1 a^3+b_2 a^4+\cdots,
$$

并作有限解析方案变换

$$
a'=a+c_1 a^2+c_2 a^3+\cdots.
$$

由于 $\beta'(a')=(da'/da)\beta(a)$，可得

$$
\boxed{
b_0'=b_0,\qquad b_1'=b_1
}.
$$

而 $b_2$ 及更高系数一般依赖方案。这一结论要求：

1. 单一无量纲耦合；
2. 变换在高斯点附近解析、局部可逆；
3. 保持树级归一化 $a'=a+O(a^2)$；
4. 变换没有显式 $\mu$ 或 $m/\mu$ 依赖；
5. 没有改变场内容或跨越阈值。

若允许 $a'=c a+O(a^2)$，则 $b_0'=b_0/c$、$b_1'=b_1/c^2$。因此“前两个系数数值普适”隐含了相同树级耦合归一化。

### 多耦合

对多耦合向量场 $g^i$，有限耦合重定义

$$
g'^i=f^i(g)
$$

下，

$$
\beta'^i(g')
=
\frac{\partial f^i}{\partial g^j}\beta^j(g).
$$

固定点位置在正规、可逆方案变换下映射到固定点；稳定矩阵 $M^i{}_j=\partial\beta^i/\partial g^j|_{g_*}$ 的特征值在正规坐标变换下不变。多耦合理论不能简单说“每个 beta 的前两项都普适”。

## 世界面非线性 sigma 模型

采用欧氏世界面作用量

$$
S
=
\frac{1}{4\pi\alpha'}
\int d^2\sigma\sqrt{h}\,
h^{ab}G_{\mu\nu}(X)
\partial_a X^\mu\partial_b X^\nu.
$$

在 $B_{\mu\nu}=0$、常数 dilaton 且定义

$$
\beta^G_{\mu\nu}
\equiv
\mu\frac{d G_{\mu\nu}}{d\mu}
$$

时，最低阶结果为

$$
\boxed{
\beta^G_{\mu\nu}
=
\alpha'R_{\mu\nu}
+
O(\alpha'^2)
}.
$$

对应的尺度流方向为 $dG_{\mu\nu}/d\ln\mu=+\alpha'R_{\mu\nu}+\cdots$。若改用长度尺度 $L\sim\mu^{-1}$，则 $dG_{\mu\nu}/d\ln L=-\alpha'R_{\mu\nu}+\cdots$，因此不能简单把正负号与数学 Ricci flow 的比较结论当作普适公式。

### 世界面 beta 与 Weyl 反常系数的区别

世界面普通 RG beta 与 Weyl anomaly coefficient 一般不应直接等同：

$$
\beta^G_{\mu\nu}\neq\bar\beta^G_{\mu\nu},
$$

它们可能相差：

- dilaton 对应力张量的改进项；
- 靶空间微分同胚产生的 Lie 导数；
- $B$ 场规范变换；
- 局域场重定义与方案变换。

若 $\beta^G$ 沿冗余方向（如 $\beta^G=\mathcal L_V G$），流动可能不代表物理背景发生非平凡尺度演化。[[弦理论/数学/曲率]] 已解释了最低阶 Ricci 条件与 sigma 模型 beta 的关系，并指出更高阶有 $\alpha'$ 修正和场重定义边界。

$\beta^G_{\mu\nu}=\alpha'R_{\mu\nu}$ 只适用于玻色弦最低阶、无 $B$ 场、常数 dilaton、弱曲率 $\alpha'|R|\ll1$ 且忽略 $O(\alpha'^2)$ 修正的情况。不能把“一圈要求 Ricci-flat”表述为完整、所有阶的弦背景方程。

## 适用条件与事实边界

1. 本篇所有 beta 函数均使用 $\mu d/d\mu$ 约定；改写为 $\mu^2 d/d\mu^2$ 或 $d/d\ln\mu^2$ 时，右端需乘 $1/2$。
2. 从 MS/$\overline{\mathrm{MS}}$ 简单极点提取 beta 的公式要求裸耦合按 $g_0=\mu^{\kappa\varepsilon}(g+a_1/\varepsilon+\cdots)$ 展开。
3. $\lambda\phi^4$ 两圈、QED 和 QCD 系数均在 $\overline{\mathrm{MS}}$ 方案中列出；在正文所列解析、局部可逆、无显式尺度或质量依赖且保持树级归一化的单耦合方案变换下，前两个系数仍不变，超出这些条件时才可能改变。
4. 单耦合前两阶普适条件要求树级归一化一致、变换在高斯点附近解析且无显式尺度或质量依赖。
5. 多耦合理论中，beta 向量在坐标变换下按向量场变换，固定点位置和稳定矩阵特征值在正规坐标变换下不变。
6. 世界面 sigma 模型从 $\alpha'R_{\mu\nu}$ 出发，更高阶修正和场重定义边界已在正文中说明。

## 常见误区

1. **beta 函数就是 $\beta(\lambda)=\mu d\lambda/d\mu$ 且不管什么导数约定都一样。** 若用 $\mu^2 d/d\mu^2$，结果差因子 $1/2$。
2. **$\lambda\phi^4$ 的 $3/(16\pi^2)$ 可以套到任何 $\phi^4$ 归一化。** 不同归一化（$-g\phi^4/4$、$-\lambda\phi^4/4!$、$O(N)$ 对称）会改变系数。
3. **QED 的 beta 函数与 QCD 的 beta 函数符号相同，所以 QED 也渐近自由。** QED 的 $\beta>0$，耦合向紫外增强。
4. **两圈系数总是方案无关。** 只有单耦合、解析有限重参数化且保持树级归一化时，$b_0$ 和 $b_1$ 才不变。
5. **多耦合理论中“每个 beta 的前两项都普适”。** 多耦合坐标变换可以混合各 beta 函数的高阶系数。
6. **$\beta^G_{\mu\nu}=\alpha'R_{\mu\nu}$ 就是所有阶的完整弦背景方程。** 它仅适用于玻色弦最低阶、弱曲率、无 $B$ 场和常数 dilaton。
7. **世界面 beta 函数就是 Weyl 反常系数。** 两者可能相差场重定义、Lie 导数和改进项。
8. **从 MS-bar 简单极点提取 beta 的公式是 $\beta=\kappa g a_1'$。** 正确是 $\kappa(g a_1'-a_1)$，漏掉 $-a_1$ 会得到错误系数。
9. **$d=4-2\varepsilon$ 和 $d=4-\epsilon$ 的经典工程量纲项可以互换。** 前者的 $\lambda\phi^4$ 项是 $-2\varepsilon\lambda$，后者是 $-\varepsilon\lambda$。
10. **QCD 的 $n_f$ 可以随便加减。** 它表示当前有效理论包含的活跃味数；跨阈值时需 EFT 匹配。

## 练习

1. 写出 $\beta(g)$ 的定义，并说明为什么导数在裸参数固定时取。
2. 在最低非平凡微扰阶，从 $g_0=\mu^{\kappa\varepsilon}(g+a_1(g)/\varepsilon)$ 推导 $\beta(g)=\kappa(g a_1'(g)-a_1(g))$，并说明被略去项的阶数。
3. 对 $\lambda\phi^4/4!$ 的一圈结果 $a_1(\lambda)=3\lambda^2/(32\pi^2)$，验证 $\beta=3\lambda^2/(16\pi^2)$。
4. 对 QED 一个 Dirac 费米子，用 $a_1(e)$ 推导 $\beta_e=e^3/(12\pi^2)$。
5. 写出 $SU(3)$ 的 $\beta_0$，并判断 $n_f=6$ 时是否渐近自由。
6. 若 $d/d\ln\mu^2$ 约定下 $\beta^{(\mu^2)}(\alpha)=b\alpha^2$，本页 $\mu d/d\mu$ 约定下的 $\beta$ 是多少？
7. 方案变换 $a'=a+2a^2$ 下，$b_0$ 和 $b_1$ 是否改变？
8. 为什么多耦合理论不能简单说“每个 beta 的前两项都普适”？
9. 写出玻色弦 sigma 模型最低阶的 $\beta^G_{\mu\nu}$，并说明符号依赖的流向约定。
10. 解释世界面 beta 函数与 Weyl 反常系数的区别。
11. 为什么 $a_1(g)$ 必须是整体裸耦合加法展开中的极点系数，而不是任意一个 $Z$ 因子的极点？
12. 为什么跨过重夸克阈值时不能直接从 $n_f$ 中删去一个味？

## 答案与提示

1. $\beta(g)=\mu dg/d\mu$ 在裸参数固定时取。因为裸参数是 Lagrangian 中最初写下的参数，它的定义不含 $\mu$，所以 $d g_0/d\mu=0$ 是推导 beta 的起点。
2. 写 $\beta_d=-\kappa\varepsilon g+\beta(g)$，则
   $$
   0
   =
   \kappa\varepsilon\left(g+\frac{a_1}{\varepsilon}\right)
   +
   \left(-\kappa\varepsilon g+\beta\right)
   \left(1+\frac{a_1'}{\varepsilon}\right).
   $$
   $\kappa\varepsilon g$ 与 $-\kappa\varepsilon g$ 抵消。在最低非平凡耦合阶，若 $a_1=O(g^p)$，则 $\beta=O(g^p)$，所以 $\beta a_1'/\varepsilon=O(g^{2p-1})/\varepsilon$ 属于更高耦合阶，本阶不保留。比较剩余的有限 $O(\varepsilon^0)$ 项 $\kappa a_1+\beta-\kappa g a_1'=0$，得到 $\beta=\kappa(g a_1'-a_1)$。若要求全阶精确推导，必须恢复正文中的完整极点塔；更高极点通过极点递推关系抵消相应发散项。
3. $\kappa=2$，$a_1(\lambda)=3\lambda^2/(32\pi^2)$，$a_1'(\lambda)=3\lambda/(16\pi^2)$。代入：$\beta=2[\lambda\cdot3\lambda/(16\pi^2)-3\lambda^2/(32\pi^2)]=2[3\lambda^2/(16\pi^2)-3\lambda^2/(32\pi^2)]=3\lambda^2/(16\pi^2)$。
4. 对 QED 一个 Dirac 费米子，$a_1(e)=e^3/(24\pi^2)$，$a_1'(e)=e^2/(8\pi^2)$。$\kappa=1$，所以 $\beta_e=e\cdot e^2/(8\pi^2)-e^3/(24\pi^2)=e^3/(12\pi^2)$。
5. $\beta_0=11\cdot3/3-2\cdot6/3=11-4=7>0$，所以渐近自由。
6. $\beta^{(\mu^2)}=\mu^2 d\alpha/d\mu^2=b\alpha^2$，则 $\beta=\mu d\alpha/d\mu=2\mu^2 d\alpha/d\mu^2=2b\alpha^2$。
7. $b_0$ 和 $b_1$ 不变。因为 $b_0'=b_0$ 且 $b_1'=b_1$ 在保持树级归一化的解析变换下成立；$a'=a+2a^2$ 满足 $a'=a+O(a^2)$。
8. 多耦合坐标变换 $g'^i=f^i(g)$ 可以混合各 beta 函数的系数，不再有“每个 beta 各自的前两项不变”的简单结论。
9. $\beta^G_{\mu\nu}=\alpha'R_{\mu\nu}+O(\alpha'^2)$。在 $\mu d/d\mu$ 约定下为正号；若改用长度尺度 $L\sim\mu^{-1}$，则 $dG/d\ln L=-\alpha'R$。
10. 世界面普通 RG beta 描述度量耦合随世界面尺度变化；Weyl 反常系数是共形反常的度量。两者可能相差场重定义、Lie 导数、改进项和方案变换。
11. 只有 $a_1(g)$ 是整体裸耦合加法展开中的简单极点系数时，$0=\mu d g_0/d\mu$ 才能导出“简单极点决定 beta”的精确关系；单独某个 $Z$ 因子的极点可能与其他因子相互抵消。
12. 质量无关方案不会自动让重费米子在阈值下退耦；跨阈值必须构造少一个活跃味的低能有效理论，并用 EFT 匹配把阈值两侧的耦合和低能可观测量一致地对应起来。

## 与其他概念的关系

- [[弦理论/物理学/正规化与重整化]] 用 MS/$\overline{\mathrm{MS}}$ 方案定义反项和 $1/\bar\varepsilon$ 极点，是提取 beta 函数的直接起点；
- [[弦理论/物理学/重整化群]] 从 $\mu$ 独立性引出 RG 方程，并解释运行耦合、固定点和 RG 改善；本页聚焦系数提取与方案依赖；
- [[弦理论/数学/曲率]] 解释 Ricci 张量，并说明 sigma 模型最低阶 beta 与目标时空曲率的关系；
- [[弦理论/数学/群表示]] 提供 Lie 代数表示和 Casimir 算子，QCD 的 $\beta_0$ 依赖 $C_A$ 和 $T_F$；
- [[弦理论/数学/Lie 代数]] 提供非 Abel 规范群的结构常数和迹约定；
- [[弦理论/物理学/Yang-Mills 理论]] 定义非 Abelian 规范势、场强、作用量和生成元归一化；本页在这些约定上给出一圈 beta 系数和渐近自由条件；
- [[弦理论/物理学/有效场论]] 使用 beta 函数和反常维数矩阵运行 Wilson 系数，并在重粒子阈值两侧重新 matching；
- [[弦理论/物理学/Weyl 反常]] 说明普通 RG beta 与世界面 Weyl anomaly coefficient 的区别，并给出含 dilaton 改进的一般背景条件；
- [[弦理论/弦理论完整学习路线图]] 将本节点放在重整化群之后、有效场论之前。

## 参考资料

- J. C. Collins, *Renormalization*, Cambridge University Press, 1984.
- G. 't Hooft, "Dimensional Regularization and the Renormalization Group," *Nuclear Physics B* 61 (1973), 455–468. https://doi.org/10.1016/0550-3213(73)90376-3
- M. E. Peskin and D. V. Schroeder, *An Introduction to Quantum Field Theory*, Westview Press, 1995, Chapters 12 and 16.
- Particle Data Group, "Quantum Chromodynamics," *Review of Particle Physics*. https://pdg.lbl.gov/2024/reviews/rpp2024-rev-qcd.pdf
- D. Friedan, "Nonlinear Models in $2+\epsilon$ Dimensions," *Physical Review Letters* 45 (1980), 1057. https://doi.org/10.1103/PhysRevLett.45.1057
- C. G. Callan, D. Friedan, E. J. Martinec and M. J. Perry, "Strings in Background Fields," *Nuclear Physics B* 262 (1985), 593–609. https://doi.org/10.1016/0550-3213(85)90506-1
- J. Polchinski, *String Theory*, Vol. 1, Cambridge University Press, 1998, Chapter 3.