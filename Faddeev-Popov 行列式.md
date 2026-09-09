---
aliases:
  - Faddeev-Popov Determinant
  - FP Determinant
  - FP 行列式
english_name: Faddeev-Popov Determinant
tags:
  - 物理学
  - 量子场论
  - 规范理论
  - 弦理论先修
  - 弦理论
prerequisites:
  - "[[规范固定]]"
  - "[[路径积分]]"
  - "[[Yang-Mills 理论]]"
  - "[[群作用]]"
used_by:
  - "[[圈展开]]"
  - "[[弦理论完整学习路线图]]"
evidence_status: 教材事实
---

# Faddeev-Popov 行列式（Faddeev-Popov Determinant）

## 学习导航

- 上一页：[[规范固定]]
- 下一页：[[Faddeev-Popov 鬼场]]
- 总路线：[[弦理论完整学习路线图]]

## 一句话解释

Faddeev-Popov 行列式是规范条件对规范参数的功能行列式，作为 Jacobian 补偿规范轨道坐标到规范切片的变量变换；它把规范群体积从路径积分中分离出来，并决定非 Abelian 理论中鬼场与规范场的相互作用强度。

## 为什么要学它

[[规范固定]] 解释了为什么需要选择规范切片，并给出了插入恒等式的思想。但未回答以下问题：

1. 从功能变量变换出发，Jacobian 为什么是行列式，行列式为什么在分子而不是分母；
2. 如何从具体规范条件推导出 FP 算符的显式形式；
3. 为什么 Abelian determinant 与场无关，而 non-Abelian 行列式依赖规范场；
4. 什么时候可以省略绝对值，什么时候必须保留；
5. 零模和 Gribov copies 怎样限制局部 FP 构造的适用范围。

本页完成这些推导，把 FP 算符和行列式建立为可独立使用的对象。下一页 [[Faddeev-Popov 鬼场]] 用 Grassmann 场把这个行列式指数化并写出鬼作用量。

## 本篇约定

继承 [[规范固定]] 的约定：

- 自然单位、mostly-minus Minkowski 度规；
- Hermitian 生成元，\(D_\mu=\partial_\mu-igA_\mu\)；
- 有限规范变换 \(U=e^{ig\alpha}\)，其中 \(\alpha=\alpha^aT^a\)；
- 无穷小规范变换：

\[
\delta_\alpha A_\mu^a
=
\partial_\mu\alpha^a
+
g f^{acb}A_\mu^c\alpha^b.
\]

等价地，伴随表示协变导数分量形式为：

\[
\boxed{
(D_\mu^{\mathrm{adj}})^{ab}
=
\delta^{ab}\partial_\mu+g f^{acb}A_\mu^c.
}
\]

若 \(f^{abc}\) 完全反对称，也可写成 \(\delta^{ab}\partial_\mu-g f^{abc}A_\mu^c\)，两式相同。不要误写成 \(\delta^{ab}\partial_\mu+g f^{abc}A_\mu^c\)，那对应不同的指标排列或规范变换约定。

## FP 算符的一般定义

设规范条件为

\[
G^a[A](x)=0.
\]

以参数 \(\alpha^b(y)\) 做无穷小规范变换。FP 算符定义为规范条件沿规范轨道切方向的变化率：

\[
\boxed{
M^{ab}(x,y;A)
=
\left.
\frac{\delta G^a[A^\alpha](x)}
{\delta\alpha^b(y)}
\right|_{\alpha=0}.
}
\]

等价地，

\[
\delta_\alpha G^a[A](x)
=
\int d^dy\,
M^{ab}(x,y;A)\alpha^b(y).
\]

\(M^{ab}\) 的指标 \(a\) 标记规范条件，指标 \(b\) 标记规范参数。它是从"规范轨道切空间"到"规范条件空间"的线性映射。

## Abelian Lorenz 规范

取 \(G[A]=\partial^\mu A_\mu\)。在 Abelian 变换

\[
A_\mu^\alpha
=
A_\mu+\partial_\mu\alpha
\]

下：

\[
G[A^\alpha]
=
\partial^\mu A_\mu+\Box\alpha.
\]

因此

\[
\boxed{
M(x,y)=\Box_x\delta^{(d)}(x-y).
}
\]

算符简写为

\[
\boxed{M=\Box.}
\]

这个算符只依赖时空背景和边界条件，不依赖 \(A_\mu\)。因此 \(\det M\) 是场无关的因子。

## Non-Abelian Lorenz 规范

取

\[
G^a[A]=\partial^\mu A_\mu^a.
\]

利用无穷小变换：

\[
\delta_\alpha G^a
=
\partial^\mu(D_\mu^{\mathrm{adj}}\alpha)^a.
\]

因此

\[
\boxed{
M^{ab}
=
\partial^\mu(D_\mu^{\mathrm{adj}})^{ab}.
}
\]

显式 kernel 为

\[
M^{ab}(x,y;A)
=
\partial_x^\mu
\left[
\left(
\delta^{ab}\partial_\mu^x
+
g f^{acb}A_\mu^c(x)
\right)
\delta^{(d)}(x-y)
\right].
\]

作用到测试函数上：

\[
(M\alpha)^a
=
\Box\alpha^a
+
g f^{acb}
\partial^\mu(A_\mu^c\alpha^b).
\]

展开第二项：

\[
(M\alpha)^a
=
\Box\alpha^a
+
g f^{acb}(\partial^\mu A_\mu^c)\alpha^b
+
g f^{acb}A_\mu^c\partial^\mu\alpha^b.
\]

在 Lorenz 规范切片 \(\partial^\mu A_\mu^c=0\) 上，中间项消失：

\[
(M\alpha)^a
=
\Box\alpha^a
+
g f^{acb}A_\mu^c\partial^\mu\alpha^b.
\]

有些教材定义正 Euclidean 算符 \(\mathcal M=-\partial^\mu D_\mu^{\mathrm{adj}}\)。这是另一个定义约定；不能一边定义 \(M=\partial D\)，一边直接抄用以 \(-\partial D\) 写出的鬼作用量符号。

## 行列式为什么在分子

### 有限维原型

设群轨道参数为 \(\alpha^i\)，规范条件 \(F^a(\alpha)=G^a(A^\alpha)\) 在考察邻域中只有一个简单零点。变量变换公式给出

\[
\boxed{
\int d^n\alpha\,
\delta^{(n)}(F(\alpha))
=
\frac{1}
{\left|\det\!\left(
\frac{\partial F^a}{\partial\alpha^i}
\right)_{\alpha=0}\right|}.
}
\]

为了得到 \(1\)，必须乘上行列式：

\[
\boxed{
1
=
|\det M[A]|
\int d^n\alpha\,
\delta^{(n)}(G[A^\alpha]).
}
\]

因此行列式在分子，而不是 \(1/\det M\)。这是因为 delta 泛函做变量变换时，行列式出现在分母，而构建恒等式把它移到了分子。

### 绝对值与有向行列式

严格有限维 delta 变量变换给出 \(|\det M|\)。标准微扰 FP 处理中常写成

\[
\Delta_{\mathrm{FP}}[A]=\det M[A],
\]

其成立条件是：

- 在选定的局部规范切片和连通区域内工作；
- \(M\) 不经过零特征值；
- 固定规范群坐标和局部取向；
- 行列式的符号或相位在该局部区域连续选定。

跨过 \(\det M=0\) 的位置时，取向可能改变，不能继续无条件省略绝对值。Grassmann 积分自然表示有向行列式，不自动生成 \(|\det M|\)。

### 多重交点

若一条轨道有多个配置满足相同规范条件，每个交点都是积分贡献点。此时

\[
\int\mathcal Dg\,\delta(G[A^g])
\]

成为所有交点的逆 Jacobian 之和，单个交点的 \(\det M\) 不能独立代表整条轨道的权重。

## 规范群体积的分离

形式上，未规范固定的生成泛函为

\[
Z
=
\int\mathcal DA\,e^{iS[A]}.
\]

插入局部 FP 恒等式：

\[
Z
=
\int\mathcal DA\,
\Delta_{\mathrm{FP}}[A]
\int\mathcal Dg\,
\delta(G[A^g])e^{iS[A]}.
\]

若

- \(S[A^g]=S[A]\)；
- \(\mathcal DA\) 规范不变；
- \(\mathcal Dg\) 是相应 Haar 型测度；
- 没有反常；
- 局部切片假设成立，

则作 \(A\mapsto A^{g^{-1}}\) 可得

\[
\boxed{
Z
=
\operatorname{Vol}(\mathcal G)
\int\mathcal DA\,
\Delta_{\mathrm{FP}}[A]\,
\delta(G[A])e^{iS[A]}.
}
\]

物理上使用除去公共群体积后的规范固定泛函：

\[
Z_{\mathrm{gf}}
\propto
\int\mathcal DA\,
\Delta_{\mathrm{FP}}[A]\,
\delta(G[A])e^{iS[A]}.
\]

注意：

- 对非规范不变源 \(J\cdot A\)，integrand 不沿轨道恒定，上述分离需另行论证；
- 无限维 \(\operatorname{Vol}(\mathcal G)\) 通常只是形式量；
- 稳定子、零模和大规范变换需要单独因子或进一步约化。

## 行列式的轨道性质

更稳健的出发点是将 FP 行列式定义为

\[
\Delta_{\mathrm{FP}}[A]^{-1}
=
\int\mathcal Dg\,\delta(G[A^g]).
\]

在 Haar 测度可重参数化且局部唯一的条件下，右边只依赖规范轨道，因此

\[
\Delta_{\mathrm{FP}}[A^h]
=
\Delta_{\mathrm{FP}}[A].
\]

但应限定：

- 这是局部 FP factor 的轨道不变性；
- 原始矩阵 \(M^{ab}\) 本身依赖规范条件、群坐标和基；
- 其行列式在群参数重定义下会带相应 Jacobian；
- 多重交点或稳定子存在时，单个交点处的 \(\det M\) 不能独立代表完整轨道权重。

## 零模与残余规范

若存在非零 \(\alpha\) 满足

\[
M[A]\alpha=0,
\]

则

- 无穷小规范变换保持规范条件：\(\delta_\alpha G[A]=0\)；
- 切片与规范轨道不横截；
- \(\det M[A]=0\)；
- 插入恒等式的普通局部变量变换公式失效。

Abelian Lorenz 规范中，\(\Box\alpha=0\) 就是残余规范条件。是否存在允许的非平凡解取决于边界条件、紧致性和函数空间。non-Abelian 情形中，FP 算符的零模还可标记规范切片失去横截性的 Gribov horizon。

## Gribov horizon 与 copies

非 Abelian 理论中，同一规范轨道可能有多个配置满足同一个规范条件。这些不同交点称为 Gribov copies。

更一般地，局部规范切片在 FP 算符出现零模、$\det M=0$ 时失去横截性。在 Euclidean Landau 或 Coulomb 规范等 FP 算符可取适当 Hermitian 形式的常见设定中，第一 Gribov horizon 可具体描述为最低相关特征值到达零的边界；跨越该边界时有向行列式的符号可能改变。这个特征值图景不能无条件套用到任意 Minkowski 规范。

综上：

- 局部 FP 构造适用于微扰真空附近等可选取横截切片的区域；
- 不应声称单一 Lorenz/Landau 条件在整个 non-Abelian 配置空间中给出全局唯一代表；
- Abelian 理论也可有零模和残余规范，但不能无条件把它们等同于典型 non-Abelian Gribov copies。

本页不展开 Gribov region、Gribov-Zwanziger 理论或 fundamental modular region。

## Abelian 与 Non-Abelian 行列式

### Abelian 场无关

Lorenz 规范下 \(M=\Box\) 仅依赖时空背景，不依赖 \(A_\mu\)。因此

\[
\det M=\det\Box
\]

是场无关因子，通常被吸收入归一化或 \(Z[J]/Z[0]\)。但"场无关"不等于"没有零模"：\(\Box\) 的零模仍需依边界条件单独去除或处理。

### Non-Abelian 场依赖

\[
M^{ab}
=
\partial^\mu
\left(
\delta^{ab}\partial_\mu
+
g f^{acb}A_\mu^c
\right)
\]

含 \(A_\mu\)。因此 \(\det M[A]\) 依赖规范场配置。这正是后续用 Grassmann 鬼场指数化后，产生 ghost–gauge 相互作用顶点的来源。

## Minkowski 与 Euclidean 行列式边界

FP 行列式首先是规范条件对规范参数的 Jacobian。它本身不会仅因路径积分权重从 \(e^{iS}\) 换成 \(e^{-S_E}\) 就自动多一个负号。

会变化的是：

1. Wick 旋转后的微分算符：Minkowski 的 \(\Box_M\) 与 Euclidean Laplacian 的关系；
2. 对算符采用 \(M=\partial D\) 还是 \(\mathcal M=-\partial D\) 的定义；
3. 行列式的无限维正规化、相位和零模处理；
4. 用 Grassmann 场指数化时，Minkowski 与 Euclidean 作用量中的显式 \(i\) 和符号。

本页只说明这些边界；鬼作用量的完整符号固定见 [[Faddeev-Popov 鬼场]]。

## 与弦世界面 FP 行列式的关系

目标时空 Yang-Mills 与 Polyakov 世界面都执行相同逻辑：

1. 配置空间上有局部群作用；
2. 选择规范条件/局部切片；
3. 线性化规范条件得到 FP 算符；
4. 行列式补偿变量变换的 Jacobian；
5. 零模和稳定子需要单独处理。

但必须区分：

- Yang-Mills FP 行列式来自目标时空内部规范群，作用于规范场 \(A_\mu^a\)；
- Polyakov 世界面 FP 行列式来自二维 Diff×Weyl，作用于世界面度量 \(h_{ab}\)；
- 世界面共形规范的行列式导向 \(bc\) 鬼系统，这些鬼场具有特定二维张量类型和共形权；
- 目标时空 FP 鬼与世界面 \(bc\) 鬼不是同一个场系统；
- RNS 的 \(\beta\gamma\) 超鬼来自局部世界面超对称，更不是本页的 Yang-Mills FP 行列式。

## 与大模型路径的边界

FP 行列式与大模型学习路径之间没有直接物理或算法对应。明确禁止：

- FP 行列式 \(\ne\) 神经网络 Jacobian 行列式；
- 规范群体积 \(\operatorname{Vol}(\mathcal G)\ne\) 参数空间体积；
- Gribov horizon \(\ne\) 损失景观鞍点或局部极小值；
- 鬼行列式 \(\ne\) 负样本权重或辅助损失。

[[弦理论与大模型跨学科关系图谱]] 只记录这些禁止误连，不建立强关系。

## 适用条件与事实边界

1. FP 行列式是局部对象；其构造依赖规范条件、群坐标和所选切片。
2. 严格有限维变量变换给出 \(|\det M|\)；微扰处理中在合适区域可写成 \(\det M\)。
3. \(\det M=0\) 时局部 FP 构造失效，对应残余规范或 Gribov horizon。
4. 行列式在分子来自 delta 泛函变量变换，不是 \(1/\det M\)。
5. 规范群体积分离依赖作用量、测度和插入对象的规范不变性；有非规范不变源时需另行论证。
6. Abelian Lorenz 行列式场无关，但零模仍需依边界条件和拓扑处理。
7. Non-Abelian 行列式依赖规范场，是后续鬼-规范玻色子相互作用的起源。
8. 非 Abelian Lorenz 规范 FP 算符 \(M^{ab}=\partial^\mu(D_\mu^{\mathrm{adj}})^{ab}\) 与某些教材使用的 \(\mathcal M=-\partial^\mu D_\mu^{\mathrm{adj}}\) 不是同一约定。
9. 本页不展开 Grassmann 指数化、鬼作用量、鬼顶点、鬼数或 BRST 结构。
10. 目标时空 FP 行列式与世界面 FP 行列式不是同一对象。

## 常见误区

1. **行列式应该在分母。** delta 泛函变量变换使行列式进入分母，但构建恒等式时把它移到了分子。
2. **\(\det M\) 无条件等于 \(|\det M|\)。** 只在局部取向固定、无零特征值且行列式符号连续的区域内成立。
3. **Abelian 行列式场无关，所以没有零模。** \(\Box\) 的零模取决于边界条件，场无关不等于零模自动消失。
4. **Non-Abelian 行列式可在任何区域使用单一 Lorenz 条件。** Gribov copies 和 horizon 限制其适用范围。
5. **\(\operatorname{Vol}(\mathcal G)\) 分离对于所有规范理论都成立。** 依赖作用量、测度和插入对象的规范不变性。
6. **FP 行列式就是世界面鬼场的行列式。** 两者来自不同的规范群和场内容。
7. **行列式中的 \(M\) 与共形场论中的 Virasoro 算符相同。** 前者是规范条件对规范参数的功能导数，后者是能动张量生成元。

## 练习

1. 从有限维 delta 泛函变量变换出发，推导行列式为什么在分子。
2. 写出一般 FP 算符的 kernel 定义 \(M^{ab}(x,y;A)\)。
3. 在 Abelian Lorenz 规范下推导 \(M(x,y)\)。
4. 在本页约定下推导伴随协变导数的分量形式 \((D_\mu^{\mathrm{adj}})^{ab}\)。
5. 推导 non-Abelian Lorenz 规范的 FP 算符 \(M^{ab}\)，并写出 \((M\alpha)^a\) 的展开式。
6. 解释为什么 Abelian 行列式场无关但可能仍有零模。
7. 说明 \(M\alpha=0\) 的几何意义。
8. 在什么条件下可把 \(|\det M|\) 写成 \(\det M\)？
9. 推导规范群体积的分离，并说明分离所需的条件。
10. 比较目标时空 Yang-Mills FP 行列式与 Polyakov 世界面 FP 行列式的共同结构和关键区别。

## 答案与提示

1. 有限维下 \(\int d^n\alpha\,\delta(F(\alpha))=1/|\det(\partial F/\partial\alpha)|\)，因此构建恒等式 \(1=|\det M|\int d^n\alpha\,\delta(G[A^\alpha])\)。行列式在分子来自 delta 泛函变量变换。
2. \(M^{ab}(x,y;A)=\left.\delta G^a[A^\alpha](x)/\delta\alpha^b(y)\right|_{\alpha=0}\)。
3. \(A_\mu^\alpha=A_\mu+\partial_\mu\alpha\)，\(G[A^\alpha]=\partial^\mu A_\mu+\Box\alpha\)，因此 \(M(x,y)=\Box_x\delta(x-y)\)。
4. \(\delta_\alpha A_\mu^a=\partial_\mu\alpha^a+g f^{acb}A_\mu^c\alpha^b\)，因此 \((D_\mu^{\mathrm{adj}})^{ab}=\delta^{ab}\partial_\mu+g f^{acb}A_\mu^c\)。
5. \(M^{ab}=\partial^\mu(D_\mu^{\mathrm{adj}})^{ab}\)。\((M\alpha)^a=\Box\alpha^a+g f^{acb}(\partial^\mu A_\mu^c)\alpha^b+g f^{acb}A_\mu^c\partial^\mu\alpha^b\)。
6. \(M=\Box\) 不含 \(A\)，但 \(\Box\alpha=0\) 可有受边界条件控制的非平凡解，虽然这些解未必在所有边界条件下都允许。
7. 规范轨道切向量落在规范切片切空间中，切片不横截，存在残余规范变换，行列式为零。
8. 在局部选定取向、\(M\) 无零特征值且行列式在该局部区域符号连续的条件下。
9. 插入 FP 恒等式后作 \(A\mapsto A^{g^{-1}}\)，利用 \(S[A^g]=S[A]\)、测度不变性等，得到 \(Z=\operatorname{Vol}(\mathcal G)Z_{\mathrm{gf}}\)。需满足作用量、测度和插入对象的规范不变性，且局部切片假设成立。
10. 共同结构：对群作用取商、选择切片、线性化得到 FP 算符、行列式补偿 Jacobian。区别：Yang-Mills 规范群是目标时空内部规范群，作用于 \(A_\mu^a\)；Polyakov 世界面固定 Diff×Weyl，作用于 \(h_{ab}\)；世界面行列式导向 \(bc\) 鬼，具有特定二维张量类型和共形权。

## 与其他概念的关系

- [[规范固定]] 是本页的直接前驱，给出规范轨道、切片和插入恒等式的思想；
- [[路径积分]] 提供泛函测度、变量变换和 Gaussian 行列式背景；
- [[Yang-Mills 理论]] 给出 non-Abelian 规范场的作用量和约定；
- [[群作用]] 解释轨道、稳定子、商空间和群作用分层；
- [[圈展开]] 在 non-Abelian 一圈计算中需要 FP 行列式及 [[Faddeev-Popov 鬼场]] 的贡献；
- [[弦理论完整学习路线图]] 将本节点放在规范固定与 [[Faddeev-Popov 鬼场]] 之间。

## 参考资料

- L. D. Faddeev and V. N. Popov, "Feynman Diagrams for the Yang-Mills Field," *Physics Letters B* 25 (1967), 29–30.
- Michael E. Peskin and Daniel V. Schroeder, *An Introduction to Quantum Field Theory*, Westview Press, 1995, Chapter 16.
- Steven Weinberg, *The Quantum Theory of Fields, Vol. 2*, Cambridge University Press, 1996, Chapter 15.
- Mark Srednicki, *Quantum Field Theory*, Cambridge University Press, 2007, Chapters 69–71.
- Claude Itzykson and Jean-Bernard Zuber, *Quantum Field Theory*, McGraw-Hill, 1980, Chapter 12.
- V. N. Gribov, "Quantization of Non-Abelian Gauge Theories," *Nuclear Physics B* 139 (1978), 1–19.
- David Tong, *Gauge Theory*, arXiv:1707.07845. https://arxiv.org/abs/1707.07845