---
aliases:
  - Faddeev-Popov Ghost
  - FP Ghost
  - FP 鬼场
  - 鬼场
english_name: Faddeev-Popov Ghost
tags:
  - 物理学
  - 量子场论
  - 规范理论
  - 弦理论先修
prerequisites:
  - "[[弦理论/物理学/Faddeev-Popov 行列式]]"
  - "[[弦理论/物理学/规范固定]]"
  - "[[弦理论/物理学/Yang-Mills 理论]]"
  - "[[弦理论/数学/Grassmann 变量]]"
  - "[[弦理论/物理学/Maxwell 场量子化]]"
used_by:
  - "[[弦理论/物理学/路径积分]]"
  - "[[弦理论/物理学/Yang-Mills 理论]]"
  - "[[弦理论/物理学/Feynman 图]]"
  - "[[弦理论/物理学/圈展开]]"
  - "[[弦理论/弦理论完整学习路线图]]"
evidence_status: 教材事实
---

# Faddeev-Popov 鬼场（Faddeev-Popov Ghost）

## 学习导航

- 上一页：[[弦理论/物理学/Faddeev-Popov 行列式]]
- 下一页：[[弦理论/物理学/BRST 对称性]]
- 总路线：[[弦理论/弦理论完整学习路线图]]

## 一句话解释

Faddeev-Popov 鬼场是 Grassmann 奇的 Lorentz 标量场，用于把规范固定路径积分中的功能行列式 $\det M[A]$ 改写为局域场作用量；它们携带规范群伴随指标，不作为物理外态，但在非 Abelian 圈图中补偿非物理规范自由度的贡献。

## 为什么要学它

[[弦理论/物理学/Faddeev-Popov 行列式]] 已给出规范固定后路径积分中的行列式 $\Delta_{\mathrm{FP}}[A]=\det M[A]$。但功能行列式是非局域对象，难以直接用于微扰展开和 Feynman 规则推导。

引入鬼场后，可以把行列式改写为 Grassmann 场的 Gaussian 积分，从而得到局域鬼作用量。这使得：

1. 规范固定后的完整作用量 $\mathcal L_{\mathrm{YM}}+\mathcal L_{\mathrm{gf}}+\mathcal L_{\mathrm{gh}}$ 可以统一处理；
2. 鬼传播子和 ghost–gauge 顶点可以纳入标准 Feynman 规则；
3. 非 Abelian 圈图中鬼场的贡献可以系统计算；
4. 后续 BRST 对称性可以用鬼场构造幂零微分，组织物理态条件。

## 本篇约定

继承前序页面的约定：

- 自然单位，mostly-minus Minkowski 度规 $\eta_{\mu\nu}=\mathrm{diag}(+1,-1,-1,-1)$；
- Hermitian 生成元 $T^a$，$[T^a,T^b]=if^{abc}T^c$；
- 协变导数 $D_\mu=\partial_\mu-igA_\mu$；
- 有限规范变换 $U=e^{ig\alpha}$，无穷小变换 $\delta_\alpha A_\mu^a=\partial_\mu\alpha^a+gf^{acb}A_\mu^c\alpha^b$；
- 伴随表示协变导数 $(D_\mu^{\mathrm{adj}})^{ab}=\delta^{ab}\partial_\mu+gf^{acb}A_\mu^c$。

[[弦理论/物理学/Faddeev-Popov 行列式]] 定义 FP 算符为

$$
M^{ab}=\partial^\mu(D_\mu^{\mathrm{adj}})^{ab}.
$$

本页将说明：在 Minkowski 路径积分 $e^{iS}$ 中，鬼作用量直接使用该算符；在 Euclidean 路径积分 $e^{-S_E}$ 中，通常定义 $\mathcal M_E=-\partial_\mu(D_\mu^{\mathrm{adj}})$ 以避免额外负号。两种约定在各自框架下自洽，不能跨框架比较孤立符号。

## 为什么引入鬼场

规范固定路径积分中出现

$$
Z_{\mathrm{gf}}\propto\int\mathcal DA\,\det M[A]\,\delta(G[A])\,e^{iS[A]}.
$$

功能行列式 $\det M[A]$ 难以直接处理。但 [[弦理论/数学/Grassmann 变量]] 已说明：复 Grassmann 场的 Gaussian 积分产生行列式。

引入一对 Grassmann 奇场 $c^a(x),\bar c^a(x)$，其中：

- $a$ 是规范群伴随指标；
- $c,\bar c$ 是 Lorentz 标量（不是旋量）；
- $c,\bar c$ 彼此独立（不是复共轭关系，而是 Grassmann 积分中的独立变量）。

则形式上有

$$
\det M[A]=\int\mathcal D\bar c\,\mathcal Dc\,\exp\left(i\int d^dx\,\bar c^a M^{ab}c^b\right).
$$

代入 $Z_{\mathrm{gf}}$ 后，行列式被鬼场作用量替代，整个被积函数变为局域场的指数。

## 鬼场的性质

Faddeev-Popov 鬼场具有以下关键性质：

1. **Grassmann 奇**：$c^a(x)c^b(y)=-c^b(y)c^a(x)$，因此 $(c^a)^2=0$；
2. **Lorentz 标量**：不携带 Lorentz 指标，不是旋量；
3. **伴随表示**：携带规范群指标 $a$，在规范变换下按伴随表示变换；
4. **不作为物理外态**：不进入渐近态空间，不出现在 S 矩阵的外部腿；
5. **统计符号来自 Grassmann 性质**：闭合鬼圈带额外负号，但这来自 Grassmann 积分，不是来自半整数自旋。

因此不能把鬼场解释为"自旋 1/2 的费米子"。它们的反对易统计来自行列式表示的数学需求，不是来自自旋—统计定理。

## 局域鬼作用量

### Minkowski 形式

在 Minkowski 路径积分 $e^{iS}$ 中，使用 FP 行列式页定义的算符 $M^{ab}=\partial^\mu(D_\mu^{\mathrm{adj}})^{ab}$，鬼作用量为

$$
\boxed{
S_{\mathrm{gh}}=\int d^dx\,\bar c^a\,\partial^\mu(D_\mu^{\mathrm{adj}}c)^a.
}
$$

展开协变导数：

$$
S_{\mathrm{gh}}=\int d^dx\,\bar c^a\left(\Box c^a+gf^{acb}\partial^\mu(A_\mu^c c^b)\right).
$$

在 Lorenz 规范 $\partial^\mu A_\mu^c=0$ 下，第二项简化为

$$
S_{\mathrm{gh}}=\int d^dx\,\bar c^a\left(\Box c^a+gf^{acb}A_\mu^c\partial^\mu c^b\right).
$$

分部积分（忽略边界项）可改写为

$$
S_{\mathrm{gh}}=-\int d^dx\,(\partial^\mu\bar c^a)(D_\mu^{\mathrm{adj}}c)^a.
$$

展开后包含两部分：

$$
S_{\mathrm{gh}}=S_{\mathrm{gh}}^{(0)}+S_{\mathrm{gh}}^{\mathrm{int}},
$$

其中自由部分为

$$
S_{\mathrm{gh}}^{(0)}=-\int d^dx\,(\partial^\mu\bar c^a)(\partial_\mu c^a),
$$

相互作用部分为

$$
S_{\mathrm{gh}}^{\mathrm{int}}=-g\int d^dx\,f^{abc}(\partial^\mu\bar c^a)A_\mu^b c^c.
$$

### Euclidean 形式

在 Euclidean 路径积分 $e^{-S_E}$ 中，通常定义

$$
\mathcal M_E^{ab}=-\partial_\mu(D_\mu^{\mathrm{adj}})^{ab},
$$

使得鬼作用量为

$$
\boxed{
S_{E,\mathrm{gh}}=\int d^dx_E\,\bar c^a\,\mathcal M_E^{ab}c^b=-\int d^dx_E\,\bar c^a\,\partial_\mu(D_\mu^{\mathrm{adj}}c)^a.
}
$$

这样自由部分为

$$
S_{E,\mathrm{gh}}^{(0)}=\int d^dx_E\,(\partial_\mu\bar c^a)(\partial_\mu c^a),
$$

与 Euclidean 标量场作用量符号一致。

**重要**：Minkowski 的 $M=\partial D$ 与 Euclidean 的 $\mathcal M_E=-\partial D$ 是不同约定。不能在前页使用 $M=\partial D$ 后，直接抄写以 $\mathcal M_E=-\partial D$ 推导的鬼传播子符号，却不说明 Wick 旋转和约定差异。

## 自由鬼传播子

### Minkowski 传播子

从自由作用量

$$
S_{\mathrm{gh}}^{(0)}
=-\int d^dx\,(\partial^\mu\bar c^a)(\partial_\mu c^a)
=\int d^dx\,\bar c^a\Box c^a,
$$

并采用 $e^{-ik\cdot x}$ Fourier 约定，自由二次核为 $M_0^{ab}(k)=-\delta^{ab}k^2$。因此按有向收缩 $\langle c^a(k)\bar c^b(-k)\rangle$ 定义的传播子为

$$
\boxed{
\Delta^{ab}(k)=-\frac{i\delta^{ab}}{k^2+i0}.
}
$$

这个负号来自本页继承的 Minkowski 定义 $M=\partial D$。许多教材改用 $M=-\partial D$ 或把鬼拉氏量整体写成相反符号，此时会得到常见的 $+i\delta^{ab}/(k^2+i0)$；比较公式时必须同时比较 FP 算符、鬼作用量和鬼线方向的约定，不能只比较传播子的孤立符号。

### Euclidean 传播子

从 $S_{E,\mathrm{gh}}^{(0)}=\int d^dx_E\,(\partial_\mu\bar c^a)(\partial_\mu c^a)$，动量空间传播子为

$$
\Delta_E^{ab}(k)=\frac{\delta^{ab}}{k^2}.
$$

## ghost–gauge 顶点

从相互作用作用量

$$
S_{\mathrm{gh}}^{\mathrm{int}}=-g\int d^dx\,f^{abc}(\partial^\mu\bar c^a)A_\mu^b c^c,
$$

可读出 ghost–antighost–gauge-boson 三点顶点。顶点的整体符号和是否显式带 $i$ 取决于 Fourier 变换、全部动量流向以及从 $iS_{\mathrm{int}}$ 提取顶点因子的约定；不说明这些约定时，稳定不变的结论是：顶点与反鬼腿的动量成正比，并携带结构常数。

例如，采用

$$
\phi(x)=\int\frac{d^dp}{(2\pi)^d}e^{-ip\cdot x}\phi(p),
$$

并令反鬼、规范场和鬼的动量 $q,k,p$ 全部流入顶点，满足 $q+k+p=0$。若规范指标依次为 $a,b,c$，则从路径积分权重 $e^{iS}$ 提取的顶点因子为

$$
\boxed{
V_\mu^{abc}(q,k,p)=-g f^{abc}q_\mu.
}
$$

这里 $q_\mu$ 是反鬼腿的流入动量，因为导数作用在 $\bar c^a$ 上。若改用 $e^{+ip\cdot x}$、令反鬼动量流出，或重新排列结构常数的指标，公式会相应变号或改写；使用具体教材的 Feynman 规则时必须整体沿用该教材的约定。

注意：

- 导数作用在反鬼场上，因此顶点依赖反鬼腿动量；
- 结构常数 $f^{abc}$ 完全反对称，指标排列需与鬼线方向和 Feynman 规则一致；
- 该顶点是 non-Abelian 规范理论特有的，Abelian 理论中 $f^{abc}=0$，没有 ghost–gauge 耦合。

## Abelian 与 Non-Abelian 鬼的区别

### Abelian 鬼（Maxwell 理论）

在 Abelian Lorenz 规范中，FP 算符为

$$
M=\Box,
$$

与 $A_\mu$ 无关。因此：

- 鬼作用量只有自由部分 $S_{\mathrm{gh}}^{(0)}$，没有 $S_{\mathrm{gh}}^{\mathrm{int}}$；
- 鬼场是自由的无质量标量（Grassmann 奇）；
- 鬼传播子存在，但没有 ghost–photon 顶点；
- 在普通散射振幅中，鬼场从圈图中解耦；
- 鬼的行列式 $\det\Box$ 是场无关因子，通常吸收到归一化中。

**边界**：Abelian 鬼解耦不代表所有规范问题消失。$\Box c=0$ 的零模仍依赖边界条件，残余规范和全局拓扑问题需要单独处理。

### Non-Abelian 鬼（Yang-Mills 理论）

在非 Abelian Lorenz 规范中，FP 算符为

$$
M^{ab}
=
\partial^\mu(D_\mu^{\mathrm{adj}})^{ab}
=
\Box\delta^{ab}
+g f^{acb}\left[(\partial^\mu A_\mu^c)+A_\mu^c\partial^\mu\right],
$$

其中方括号内第一项是乘法算符，第二项的导数作用在其右侧的测试场上。等价地，

$$
(Mc)^a
=
\Box c^a
+g f^{acb}(\partial^\mu A_\mu^c)c^b
+g f^{acb}A_\mu^c\partial^\mu c^b.
$$

这显式依赖 $A_\mu$。因此：

- 鬼作用量包含 $S_{\mathrm{gh}}^{\mathrm{int}}$，产生 ghost–gauge 顶点；
- 鬼场与规范玻色子相互作用；
- 鬼场出现在内部传播线和闭合圈中；
- 每个闭合鬼圈带 Grassmann 统计负号；
- 鬼场对圈图贡献不可忽略，是微扰一致性的重要组成部分。

## 鬼场在圈图中的作用

在 non-Abelian 规范理论微扰展开中，鬼场通过内部线和闭合圈参与消除规范固定引入的非物理自由度对物理量的污染。

具体来说：

1. 协变规范下的规范场传播子包含非物理极化方向；
2. 单独的规范玻色子圈通常不能满足 non-Abelian 规范恒等式；
3. 闭合鬼圈带 Grassmann 负号，并与规范玻色子及其他图共同组成满足 Slavnov–Taylor 恒等式的完整结果；
4. 这种组织发生在一组图和重整化恒等式层面，不是每张鬼图与某张规范玻色子图逐项一一抵消。

因此鬼场的作用是协助保证规范固定微扰论的 Slavnov–Taylor 恒等式和物理 S 矩阵在物理子空间上的幺正性。Abelian 线性规范中的鬼场解耦，普通 Ward 恒等式不需要鬼圈贡献。

## 鬼场不是物理粒子

Faddeev-Popov 鬼场：

- **不作为渐近态**：不进入物理 Hilbert 空间的外部态；
- **不构成物理自旋—统计定理的违反**：它们是 Grassmann 奇的 Lorentz 标量，但规范固定辅助场不属于该定理所约束的正定度规物理粒子态空间；
- **具有辅助量子数**：它们携带颜色伴随指标和 ghost number；通常约定 $\operatorname{gh}(c)=+1$、$\operatorname{gh}(\bar c)=-1$，但这些量子数不对应可探测的物理渐近粒子；
- **只在内部线出现**：在通常的微扰 Feynman 规则中作为内部传播线和闭合圈的辅助场。

"ghost" 名称来自它们的路径积分起源（行列式的 Grassmann 表示），不能解释为实验可探测的"负能量粒子"或"负概率粒子"。

## 与世界面鬼场的关系

弦理论中还存在世界面鬼场，但它们与目标时空 FP 鬼场不是同一对象：

| 性质 | 目标时空 FP 鬼 | 世界面 $bc$ 鬼 | RNS $\beta\gamma$ 超鬼 |
|------|----------------|----------------|------------------------|
| 来源 | 目标时空内部规范群的规范固定 | 世界面 Diff×Weyl 的规范固定 | 世界面局部超对称（世界面超引力）的规范固定 |
| 对应的规范自由度 | 规范场 $A_\mu^a(x)$ 的规范轨道方向 | 世界面度量 $h_{ab}(\sigma)$ 的 Diff×Weyl 冗余 | 世界面超引力伴侣 gravitino 的局部超对称冗余 |
| 场系统 | Grassmann 奇 Lorentz 标量 | anticommuting 一阶系统 | commuting/bosonic 一阶系统 |
| 共形权（全纯部分） | 不适用 | $h_b=2,\ h_c=-1$ | $h_\beta=3/2,\ h_\gamma=-1/2$ |
| 物理作用 | 局域化目标时空规范固定的 FP 行列式 | 局域化世界面 Diff×Weyl 的 FP 行列式 | 局域化局部世界面超对称产生的逆行列式/Berezinian 因子 |

共同结构是：它们都把相应规范固定产生的 determinant 或 Berezinian 因子改写为局域一阶场系统。但统计并不相同：目标时空 FP 鬼和世界面 $bc$ 鬼是 Grassmann 奇的，RNS $\beta\gamma$ 超鬼则是 commuting/bosonic 的。三者的规范对称性、场内容、维度和物理角色不同，不能机械等同。

## 与大模型路径的边界

Faddeev-Popov 鬼场与大模型学习路径之间没有直接物理或算法对应。明确禁止：

- 鬼场 $\ne$ 隐变量或辅助 token；
- 鬼场 $\ne$ 负样本权重或辅助损失；
- 鬼圈负号 $\ne$ 损失函数中的惩罚项；
- BRST 微分 $\ne$ 反向传播。

[[弦理论与大模型跨学科关系图谱]] 只记录这些禁止误连，不建立强关系。

## 鬼场与 BRST 的预告

鬼场为后续 BRST 对称性提供了基础。在无穷小规范变换中，普通 Grassmann 偶规范参数被鬼场 $c^a(x)$ 所替代并提升为动态场；BRST 变换本身则由 Grassmann 奇的全局参数乘以幂零 BRST 微分 $s$ 表示，而不是把 $c^a$ 本身称为 BRST 变换参数。

BRST 微分满足 $s^2=0$，并组织以下结构：

- 规范固定项与鬼项可以共同写成 BRST-exact 形式；
- 量子态语言中，BRST 荷 $Q$ 满足 $Q^2=0$，物理态条件可写成 $Q|\mathrm{phys}\rangle=0$；
- [[弦理论/物理学/BRST 上同调]] 给出物理态空间，排除 BRST-exact 的非物理态。

完整 BRST 变换、辅助场和幂零结构见下一节点 [[弦理论/物理学/BRST 对称性]]；上同调类的系统分类再由后续独立页面展开。

## 适用条件与事实边界

1. 鬼场是 Grassmann 奇的 Lorentz 标量，不是自旋 1/2 费米子。
2. 鬼场携带规范群伴随指标，不作为物理外态。
3. Abelian 鬼场自由且解耦；non-Abelian 鬼场与规范玻色子相互作用。
4. 鬼场作用量的符号依赖 Minkowski/Euclidean 约定和算符定义，不能跨约定比较孤立负号。
5. 闭合鬼圈带 Grassmann 统计负号，但鬼不作为外态。
6. 鬼场补偿非物理规范自由度的贡献，在完整图之和和恒等式结构中实现，不是逐图简单抵消。
7. 鬼场指数化表示有向行列式 $\det M$，不自动处理 $|\det M|$、Gribov copies 和全局规范固定。
8. 目标时空 FP 鬼与世界面 $bc$ 鬼不是同一场系统。
9. 鬼场不进入物理渐近态，不违反自旋—统计定理。
10. 鬼场为 BRST 对称性提供基础，但完整 BRST 结构属于后续节点。

## 常见误区

1. **鬼场是自旋 1/2 费米子。** 它们是 Grassmann 奇的 Lorentz 标量，反对易统计来自行列式表示，不是来自自旋。
2. **鬼场是物理粒子。** 它们不作为渐近态，只在内部线和圈图中出现。
3. **Abelian 理论没有鬼场。** Abelian 鬼场存在但自由且解耦，不等于"没有鬼"。
4. **鬼场抵消非物理偏振是逐图成立的。** 抵消在完整图之和和恒等式结构中实现。
5. **引入鬼场后规范冗余完全解决。** 鬼场指数化不自动处理 Gribov copies 和全局规范固定。
6. **目标时空鬼场与世界面 $bc$ 鬼场相同。** 它们来自不同的规范群和场内容。
7. **Minkowski 和 Euclidean 鬼作用量符号相同。** 两者约定不同，不能跨框架比较。
8. **鬼场是负概率粒子。** "ghost" 名称来自路径积分起源，不是物理可观测的负能量或负概率。

## 练习

1. 写出 Minkowski 和 Euclidean 鬼作用量的表达式，并说明两者的约定差异。
2. 从自由鬼作用量推导 Minkowski 和 Euclidean 鬼传播子。
3. 从相互作用鬼作用量推导 ghost–gauge 顶点因子。
4. 解释为什么 Abelian 鬼场解耦，而 non-Abelian 鬼场不解耦。
5. 说明鬼场在圈图中的作用，以及为什么闭合鬼圈带负号。
6. 解释为什么鬼场不是自旋 1/2 费米子，尽管它们是 Grassmann 奇的。
7. 比较目标时空 FP 鬼与世界面 $bc$ 鬼的来源、张量类型和物理作用。
8. 说明为什么鬼场指数化不能自动处理 Gribov copies。
9. 从鬼作用量出发，说明鬼场如何为 BRST 对称性提供基础。
10. 解释为什么鬼场不作为物理外态，以及这如何与 S 矩阵幺正性相容。

## 答案与提示

1. Minkowski: $S_{\mathrm{gh}}=\int d^dx\,\bar c^a\partial^\mu(D_\mu^{\mathrm{adj}}c)^a$；Euclidean: $S_{E,\mathrm{gh}}=-\int d^dx_E\,\bar c^a\partial_\mu(D_\mu^{\mathrm{adj}}c)^a$。差异来自 $e^{iS}$ 与 $e^{-S_E}$ 的约定，以及 Euclidean 定义 $\mathcal M_E=-\partial D$ 以避免额外负号。
2. 自由二次核为 $M_0(k)=-\delta^{ab}k^2$，因此 Minkowski $\Delta^{ab}(k)=-i\delta^{ab}/(k^2+i0)$；Euclidean: $\Delta_E^{ab}(k)=\delta^{ab}/k^2$。采用 $M=-\partial D$ 或改变鬼线方向约定的教材会得到相反符号，比较时必须完整核对 FP 算符、鬼作用量和鬼线方向的约定。
3. 采用本页的 $e^{-ip\cdot x}$ Fourier 约定，并令反鬼、规范场、鬼的动量 $q,k,p$ 全部流入，则 $V_\mu^{abc}(q,k,p)=-g f^{abc}q_\mu$，其中 $q$ 是反鬼腿的流入动量。改用其他 Fourier 或动量流向约定时，整体符号应相应调整。
4. Abelian FP 算符 $M=\Box$ 与 $A_\mu$ 无关，鬼作用量只有自由部分；non-Abelian $M^{ab}=\partial^\mu(D_\mu^{\mathrm{adj}})^{ab}$ 依赖 $A_\mu$，产生 ghost–gauge 顶点。
5. 在 non-Abelian 微扰论中，鬼场通过内部线和闭合圈参与消除规范固定引入的非物理自由度对物理量的污染，并与规范玻色子及其他图共同满足 Slavnov–Taylor 恒等式；这种组织不是逐图一一抵消。闭合鬼圈的额外负号来自 Grassmann 积分的统计性质。
6. 鬼场是 Lorentz 标量，不携带旋量指标。Grassmann 奇性质来自行列式表示的数学需求；物理自旋—统计定理的假设不直接适用于被排除出物理态空间的规范固定辅助场。
7. FP 鬼来自目标时空内部规范群，是 Grassmann 奇 Lorentz 标量；$bc$ 鬼来自世界面 Diff×Weyl，是 anticommuting 一阶系统，具有共形权 $h_b=2, h_c=-1$；RNS $\beta\gamma$ 超鬼来自世界面局部超对称，是 commuting/bosonic 一阶系统，具有共形权 $h_\beta=3/2, h_\gamma=-1/2$。三者的统计和来源不同，不可机械等同。
8. Grassmann 积分表示有向行列式 $\det M$，不自动给出 $|\det M|$。当 $M$ 有零模或同一轨道与切片有多个交点时，局部鬼作用量不能解决全局规范固定问题。
9. 鬼场 $c^a(x)$ 替代无穷小规范变换中的 Grassmann 偶规范参数并成为动态场。BRST 微分 $s$ 是 Grassmann 奇幂零算符，$s^2=0$；带全局 Grassmann 奇参数 $\varepsilon$ 的变换写作 $\delta_{\mathrm{BRST}}=\varepsilon s$。规范固定项与鬼项可共同写成 $s(\cdots)$ 形式，物理态条件为 $Q|\mathrm{phys}\rangle=0$。
10. 鬼场不进入渐近态空间，因此不影响 S 矩阵的外部腿。它们通过圈图补偿非物理自由度，保证 S 矩阵在物理子空间上的幺正性。

## 与其他概念的关系

- [[弦理论/物理学/Faddeev-Popov 行列式]] 给出鬼场的起源和功能行列式；
- [[弦理论/物理学/规范固定]] 提供规范轨道、切片和 FP 插入恒等式的背景；
- [[弦理论/物理学/Yang-Mills 理论]] 提供非 Abelian 规范群、结构常数和协变导数约定；
- [[弦理论/数学/Grassmann 变量]] 提供 Grassmann 积分表示行列式的数学基础；
- [[弦理论/物理学/Maxwell 场量子化]] 提供 Abelian 原型和鬼场解耦的对比；
- [[弦理论/物理学/圈展开]] 说明鬼场在圈图中的统计符号和作用；
- [[弦理论/弦理论完整学习路线图]] 将本节点放在 FP 行列式之后、BRST 对称性之前。

## 参考资料

- Michael E. Peskin and Daniel V. Schroeder, *An Introduction to Quantum Field Theory*, Westview Press, 1995, Chapter 16.
- Steven Weinberg, *The Quantum Theory of Fields, Vol. 2*, Cambridge University Press, 1996, Chapter 15.
- Mark Srednicki, *Quantum Field Theory*, Cambridge University Press, 2007, Chapters 71–73.
- Claude Itzykson and Jean-Bernard Zuber, *Quantum Field Theory*, McGraw-Hill, 1980, Chapter 12.
- L. D. Faddeev and V. N. Popov, "Feynman Diagrams for the Yang-Mills Field," *Physics Letters B* 25 (1967), 29–30.
- David Tong, *Gauge Theory*, arXiv:1707.07845. https://arxiv.org/abs/1707.07845
