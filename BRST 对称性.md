---
aliases:
  - Becchi-Rouet-Stora-Tyutin Symmetry
  - BRST Symmetry
  - BRST 对称
english_name: BRST Symmetry
tags:
  - 物理学
  - 量子场论
  - 规范理论
  - 弦理论先修
  - 弦理论
prerequisites:
  - "[[Faddeev-Popov 鬼场]]"
  - "[[规范固定]]"
  - "[[Yang-Mills 理论]]"
  - "[[Grassmann 变量]]"
  - "[[Lie 代数]]"
  - "[[Noether 定理]]"
used_by:
  - "[[Poisson 括号]]"
  - "[[Maxwell 场量子化]]"
  - "[[Grassmann 变量]]"
  - "[[Lie 代数]]"
  - "[[群作用]]"
  - "[[模空间]]"
  - "[[弦理论完整学习路线图]]"
  - "[[量子反常]]"
  - "[[Weyl 反常]]"
evidence_status: 教材事实
---

# BRST 对称性（BRST Symmetry）

## 学习导航

- 上一页：[[Faddeev-Popov 鬼场]]
- 下一页：[[BRST 上同调]]
- 总路线：[[弦理论完整学习路线图]]

## 一句话解释

BRST 对称性把规范变换、Faddeev-Popov 鬼场和规范固定项统一为一个 Grassmann 奇的幂零微分；它用 $s^2=0$ 和对应的守恒荷 $Q$ 区分物理态与规范固定引入的非物理自由度。

## 为什么要学它

[[规范固定]] 消除了路径积分对规范轨道的重复计数，[[Faddeev-Popov 鬼场]] 又把功能行列式改写成局域作用量。但规范固定后的拉氏量不再显式保持原来的局域规范不变性，因此还需要一种新的对称结构回答：

1. 规范固定项和鬼项为什么不是任意添加的；
2. 规范参数变化为什么不改变物理可观测量；
3. 鬼场和非物理规范场极化怎样从物理态空间中排除；
4. 量子理论中何时仍可使用规范对称性，何时会因反常而失效；
5. 弦理论中世界面鬼场、Virasoro 约束和物理弦态怎样被统一组织。

BRST 对称性给出的核心工具是幂零微分 $s$。下一页 [[BRST 上同调]] 将研究 $s$ 或 $Q$ 的闭对象模去恰当对象，本页先建立这一代数结构和作用量实现。

## 本篇约定

继承前序页面：

- 自然单位，mostly-minus Minkowski 度规；
- Hermitian 生成元 $T^a$，$[T^a,T^b]=if^{abc}T^c$；
- $D_\mu=\partial_\mu-igA_\mu$；
- 伴随协变导数
  $$
  (D_\mu^{\mathrm{adj}})^{ab}
  =\delta^{ab}\partial_\mu+g f^{acb}A_\mu^c;
  $$
- 无穷小规范变换
  $$
  \delta_\alpha A_\mu^a=(D_\mu^{\mathrm{adj}}\alpha)^a;
  $$
- Lorenz 型规范条件 $G^a[A]=\partial^\mu A_\mu^a$；
- FP 算符 $M^{ab}=\partial^\mu(D_\mu^{\mathrm{adj}})^{ab}$；
- Minkowski 鬼拉氏量
  $$
  \mathcal L_{\mathrm{gh}}
  =\bar c^a M^{ab}c^b.
  $$

BRST 微分记为 $s$，它是 Grassmann 奇导子。带全局 Grassmann 奇常数 $\varepsilon$ 的无穷小变换写成

$$
\delta_{\mathrm{BRST}}=\varepsilon s.
$$

鬼数约定为

$$
\operatorname{gh}(c)=+1,
\qquad
\operatorname{gh}(\bar c)=-1,
\qquad
\operatorname{gh}(A)=\operatorname{gh}(B)=0,
\qquad
\operatorname{gh}(s)=+1.
$$

## 从规范变换到 BRST 变换

普通无穷小规范变换使用 Grassmann 偶参数 $\alpha^a(x)$：

$$
\delta_\alpha A_\mu^a=(D_\mu^{\mathrm{adj}}\alpha)^a.
$$

BRST 构造把 $\alpha^a(x)$ 的角色交给动态鬼场 $c^a(x)$，并把变换扩展到鬼场、反鬼场和辅助场。这里 $c^a$ 不是全局 BRST 变换参数；真正的全局参数是 $\varepsilon$，而 $c^a(x)$ 是参与变换的局域动态场。

为使幂零性在不使用运动方程时成立，引入 Grassmann 偶的 Nakanishi-Lautrup 辅助场 $B^a$。

## Off-shell BRST 变换

与本页约定一致的一组变换是

$$
\boxed{
\begin{aligned}
sA_\mu^a
&=(D_\mu^{\mathrm{adj}}c)^a
=\partial_\mu c^a+g f^{acb}A_\mu^c c^b,\\[4pt]
sc^a
&=-\frac g2 f^{abc}c^b c^c,\\[4pt]
s\bar c^a
&=B^a,\\[4pt]
sB^a
&=0.
\end{aligned}
}
$$

由于 $f^{abc}$ 完全反对称，鬼变换也可按本仓库的指标排列写成

$$
sc^a=\frac g2 f^{acb}c^b c^c.
$$

两式相同，不是两套不同理论。

BRST 微分满足分次 Leibniz 法则：对齐次对象 $X,Y$，

$$
s(XY)=(sX)Y+(-1)^{|X|}X(sY),
$$

其中 $|X|=0,1$ 分别表示 Grassmann 偶、奇。

## 为什么 $sc$ 不是零

如果只做替换 $\alpha\to c$ 却令 $sc=0$，那么 non-Abelian 理论中 $s^2A_\mu$ 不会消失。原因是两次规范变换的交换子仍是规范变换，参数由 Lie 括号给出。

鬼场既 Grassmann 奇又取值于 Lie 代数，因此

$$
sc^a=-\frac g2 f^{abc}c^b c^c
$$

正好编码规范代数的闭合性。Abelian 理论中 $f^{abc}=0$，于是 $sc=0$。

## 幂零性 $s^2=0$

### 对反鬼场和辅助场

由定义立即得到

$$
s^2\bar c^a=sB^a=0,
\qquad
s^2B^a=0.
$$

### 对鬼场

利用分次 Leibniz 法则：

$$
\begin{aligned}
s^2c^a
&=-\frac g2 f^{abc}s(c^bc^c)\\
&=-\frac g2 f^{abc}\left[(sc^b)c^c-c^b(sc^c)\right].
\end{aligned}
$$

代入 $sc$ 后，结果与

$$
f^{abe}f^{ecd}+f^{ace}f^{edb}+f^{ade}f^{ebc}=0
$$

成正比，因此由 [[Lie 代数]] 的 Jacobi 恒等式得到

$$
\boxed{s^2c^a=0.}
$$

### 对规范场

从 $sA_\mu=D_\mu^{\mathrm{adj}}c$ 出发：

$$
s^2A_\mu^a
=s(D_\mu^{\mathrm{adj}}c)^a.
$$

其中一组项来自 $D_\mu(sc)$，另一组来自 $sA_\mu$ 对协变导数中 $A_\mu$ 的变化。代入 $sc=-\frac g2[c,c]$ 的分量形式后，导数项因 Grassmann 反对易性抵消，剩余项由 Jacobi 恒等式消失：

$$
\boxed{s^2A_\mu^a=0.}
$$

因此含 $B^a$ 的变换在不使用运动方程时已经幂零，称为 off-shell nilpotent。

## Yang-Mills 作用量为什么 BRST 不变

Yang-Mills 作用量在普通规范变换下不变。BRST 对 $A_\mu$ 的作用就是把规范参数替换为鬼场，因此

$$
sS_{\mathrm{YM}}=0.
$$

更具体地，场强按伴随表示变换：

$$
sF_{\mu\nu}^a
=g f^{abc}F_{\mu\nu}^b c^c,
$$

而 $F_{\mu\nu}^aF^{a\mu\nu}$ 中的颜色指标收缩与反对称结构常数相乘后为零。

## Gauge-fixing fermion

规范固定项和鬼项可由一个 ghost number 为 $-1$ 的 Grassmann 奇泛函统一生成。为匹配本仓库

$$
\mathcal L_{\mathrm{gf}}
=-\frac1{2\xi}(\partial^\mu A_\mu^a)^2,
\qquad
\mathcal L_{\mathrm{gh}}
=+\bar c^a\partial^\mu(D_\mu^{\mathrm{adj}}c)^a,
$$

定义 gauge-fixing fermion

$$
\boxed{
\Psi
=\bar c^a\left(G^a[A]-\frac\xi2 B^a\right),
\qquad
G^a[A]=\partial^\mu A_\mu^a.
}
$$

“fermion” 指 $\Psi$ 是 Grassmann 奇泛函，不表示它是可观测自旋 $1/2$ 粒子。

取

$$
\boxed{
\mathcal L_{\mathrm{gf+gh}}=-s\Psi.
}
$$

由于 $\bar c$ 为奇，分次 Leibniz 法则给出

$$
\begin{aligned}
s\Psi
&=(s\bar c^a)\left(G^a-\frac\xi2B^a\right)
-\bar c^a\left(sG^a-\frac\xi2sB^a\right)\\
&=B^aG^a-\frac\xi2B^aB^a-\bar c^aM^{ab}c^b.
\end{aligned}
$$

因此

$$
\boxed{
\mathcal L_{\mathrm{gf+gh}}
=-B^aG^a+\frac\xi2B^aB^a+\bar c^aM^{ab}c^b.
}
$$

这一式同时固定了 $B$ 项、规范固定项和鬼项的相对符号。

## 消去辅助场 $B^a$

$B^a$ 没有导数，是代数辅助场。其运动方程为

$$
-G^a+\xi B^a=0,
$$

所以

$$
B^a=\frac1\xi G^a
=\frac1\xi\partial^\mu A_\mu^a.
$$

代回得到

$$
-B^aG^a+\frac\xi2B^aB^a
=-\frac1{2\xi}G^aG^a.
$$

因此

$$
\boxed{
\mathcal L_{\mathrm{gf+gh}}
=-\frac1{2\xi}(\partial^\mu A_\mu^a)^2
+\bar c^a\partial^\mu(D_\mu^{\mathrm{adj}}c)^a,
}
$$

与前序两页的符号完全一致。

### Off-shell 与 on-shell 的区别

保留 $B^a$ 时，$s^2\bar c=sB=0$ 无需运动方程，幂零性是 off-shell 的。消去 $B^a$ 后，

$$
s\bar c^a=\frac1\xi\partial^\mu A_\mu^a,
$$

再作用一次 $s$ 会得到与鬼场运动方程相关的项。因此消去 $B$ 后，反鬼场上的幂零性通常只在使用运动方程时成立。

这不表示物理理论改变；$B$ 只是把代数闭合写得更透明。

## BRST-exact 为什么自动 BRST 不变

由于 $s^2=0$，

$$
s\mathcal L_{\mathrm{gf+gh}}
=-s^2\Psi=0.
$$

于是完整作用量

$$
S_{\mathrm{tot}}
=S_{\mathrm{YM}}+\int d^dx\,\mathcal L_{\mathrm{gf+gh}}
$$

满足

$$
\boxed{sS_{\mathrm{tot}}=0.}
$$

这说明规范固定虽然破坏了原局域规范不变性的显式形式，却留下了统一组织规范场、鬼场和辅助场的全局 Grassmann 奇对称性。

## 规范固定参数与物理量

当规范固定变化可写成 gauge-fixing fermion 的变化 $\Psi\to\Psi+\delta\Psi$ 时，作用量变化为

$$
\delta S_{\mathrm{tot}}
=-s(\delta\Psi).
$$

对 BRST-closed 的物理插入，在测度也保持 BRST 不变、边界项消失且没有反常的条件下，BRST-exact 变化不改变其期望值。

因此“物理量与规范参数无关”不是无条件口号，它依赖：

- 路径积分测度 BRST 不变；
- 正规化和重整化保持 BRST/Slavnov-Taylor 恒等式；
- 不存在 BRST 反常；
- 边界条件、零模和 Gribov 等全局问题得到适当处理。

## Noether BRST 荷

BRST 变换的参数 $\varepsilon$ 是时空常数，因此它是一种全局连续对称性。由 [[Noether 定理]] 可构造守恒流

$$
\partial_\mu j_{\mathrm{BRST}}^\mu=0
$$

和守恒荷

$$
\boxed{
Q=\int d^{d-1}x\,j_{\mathrm{BRST}}^0.
}
$$

量子理论中，$Q$ 生成 BRST 变换。省略依赖 Grassmann 奇偶的约定因子时，可概括写为

$$
s\Phi\sim[Q,\Phi\}_{\mathrm{gr}},
$$

其中 $[\cdot,\cdot\}_{\mathrm{gr}}$ 是分次交换子。$s^2=0$ 对应

$$
\boxed{Q^2=0}
$$

在没有 BRST 反常且算符定义良好的条件下成立。

本页不写依赖正则变量、边界项和规范选择的 $Q$ 的完整分量表达式，避免把某一特殊规范的公式误当成普适定义。

## 物理态条件

规范固定后的扩展状态空间含有纵向/时间样规范场自由度、鬼和反鬼。物理态要求 BRST-closed：

$$
\boxed{Q|\mathrm{phys}\rangle=0.}
$$

但仅满足闭条件还不够。若

$$
|\psi\rangle=Q|\chi\rangle,
$$

则它是 BRST-exact，代表应从物理态中商去的冗余方向。于是物理态空间的核心结构是

$$
\mathcal H_{\mathrm{phys}}
=\frac{\ker Q}{\operatorname{im}Q}.
$$

这一商空间的系统计算、闭态与恰当态的分类，以及 quartet mechanism 见下一节点 [[BRST 上同调]]。

## Abelian 与 Non-Abelian BRST

### Abelian 理论

Abelian 情形 $f^{abc}=0$：

$$
sA_\mu=\partial_\mu c,
\qquad
sc=0,
\qquad
s\bar c=B,
\qquad
sB=0.
$$

鬼场自由并从普通散射中解耦，但 BRST 结构仍可统一表达规范固定和物理态条件。

### Non-Abelian 理论

non-Abelian 情形必须有

$$
sc^a=-\frac g2f^{abc}c^bc^c.
$$

这一非线性项编码 Lie 代数闭合，也是 $s^2A=0$ 的必要组成。鬼场与规范场耦合，Slavnov-Taylor 恒等式取代 Abelian Ward 恒等式成为主要约束。

## 与约束和 Poisson 括号的关系

在 Hamilton 约束系统中，一阶约束的括号代数编码规范变换闭合。[[Poisson 括号]] 提供经典括号结构，BRST 方法则扩展相空间、加入鬼变量，并把约束和结构常数组织进一个幂零荷。

本页采用拉氏量和路径积分语言，不展开 BFV-BRST 的扩展相空间构造。不能把本页的 $Q$ 直接当作普通 Hamiltonian，也不能把 ghost number 当作能量或粒子数。

## 与世界面 BRST 的关系

目标时空 Yang-Mills BRST 与弦世界面 BRST 共享：

- 规范固定后引入鬼系统；
- 用 Grassmann 奇幂零算符组织规范冗余；
- 物理态由 $Q$ 的上同调给出；
- 反常可能破坏量子幂零性和一致性。

但必须区分：

1. Yang-Mills BRST 固定目标时空内部规范群，鬼场 $c^a,\bar c^a$ 是 Lorentz 标量并带伴随指标；
2. Polyakov 世界面 BRST 固定二维 Diff×Weyl，使用具有共形权的 $bc$ 鬼系统；
3. RNS 理论还包含 commuting/bosonic 的 $\beta\gamma$ 超鬼；
4. Yang-Mills 的经典 $s^2=0$ 由 Lie 代数 Jacobi 恒等式保证；世界面量子 BRST 荷的 $Q^2=0$ 还要求总中心荷反常消失；
5. 临界维数条件属于世界面共形反常消除，不是任意 Yang-Mills BRST 的成立条件。

具体的玻色弦和 RNS BRST 荷留给路线图后续弦量子化节点。

## 与量子反常的边界

经典作用量 BRST 不变，不自动保证量子理论也 BRST 不变。如果路径积分测度或正规化方案不保持该对称性，可能出现

$$
s\Gamma\ne0,
$$

其中 $\Gamma$ 是量子有效作用量。可否用局域反项恢复恒等式，需要满足 Wess-Zumino 一致性等条件。

本页只给出反常会破坏 Slavnov-Taylor 恒等式和量子 BRST 幂零性的入口。[[量子反常]] 给出总框架；手征反常、Weyl 反常和反常消除属于后续独立节点。

## 与大模型路径的边界

BRST 对称性与大模型训练没有直接物理或算法对应。明确禁止：

- BRST 微分 $s\ne$ 反向传播；
- $s^2=0\ne$ 梯度消失、梯度裁剪或二阶导数为零；
- BRST 荷 $Q\ne$ 优化器、损失函数或模型算子；
- $Q|\mathrm{phys}\rangle=0\ne$ 分类器输出、停止条件或束搜索；
- BRST 上同调 $\ne$ 聚类、降维或表征学习；
- gauge-fixing fermion $\Psi\ne$ 正则化项或训练损失；
- Nakanishi-Lautrup 场 $B^a\ne$ 神经网络 bias、隐变量或辅助 token。

[[弦理论与大模型跨学科关系图谱]] 只记录这些禁止误连，不建立强关系。

## 适用条件与事实边界

1. BRST 微分是 Grassmann 奇导子，$\delta_{\mathrm{BRST}}=\varepsilon s$；鬼场 $c^a(x)$ 不是全局变换参数。
2. $sc$ 的非线性项编码 non-Abelian Lie 代数闭合，不能任意省略。
3. $s^2=0$ 对 $A,c$ 依赖 Grassmann 反对易性和 Jacobi 恒等式。
4. 引入 $B^a$ 后幂零性 off-shell 成立；消去 $B$ 后反鬼场上的闭合通常需要运动方程。
5. 本仓库采用 $\mathcal L_{\mathrm{gf+gh}}=-s\Psi$，以匹配既有的负规范固定项和正鬼项。
6. BRST-exact 变化不改变物理量需要测度不变、无反常、边界项可控和全局规范问题得到处理。
7. $Q|\mathrm{phys}\rangle=0$ 只给出闭态；还必须模去 $Q$-exact 态。
8. Yang-Mills BRST 与世界面 BRST 共享幂零和上同调结构，但规范群、鬼系统和量子反常条件不同。
9. BRST 不自动解决 Gribov copies 和全局规范固定问题。
10. 本页不展开 BRST 上同调的显式计算、BFV-BRST、BV 形式化或世界面 BRST 荷。

## 常见误区

1. **鬼场 $c$ 就是 BRST 变换参数。** 全局参数是 $\varepsilon$，$c(x)$ 是局域动态场。
2. **令 $sc=0$ 仍适用于 non-Abelian 理论。** 这会破坏 $s^2A=0$；只有 Abelian 情形可令 $sc=0$。
3. **规范固定项和鬼项各自任意选择。** 它们由 gauge-fixing fermion 的 BRST-exact 组合固定相对结构。
4. **消去 $B$ 后幂零性仍无条件 off-shell 成立。** 反鬼场上的闭合通常转为 on-shell。
5. **满足 $Q|\psi\rangle=0$ 的态都彼此不同。** 相差 $Q|\chi\rangle$ 的闭态属于同一物理上同调类。
6. **BRST 自动消除所有全局规范问题。** Gribov copies 等问题不由局部 FP/BRST 构造自动解决。
7. **世界面 BRST 与 Yang-Mills BRST 是同一具体算符。** 它们共享代数结构，但作用对象和反常条件不同。
8. **BRST 上同调就是机器学习降维。** 二者没有算法等价关系。

## 练习

1. 在本页约定下写出 $sA_\mu^a,sc^a,s\bar c^a,sB^a$。
2. 为什么 non-Abelian 理论不能令 $sc=0$？
3. 使用分次 Leibniz 法则说明 $s^2c=0$ 与 Jacobi 恒等式的关系。
4. 说明引入 $B^a$ 后，为什么 $s^2\bar c=0$ 可 off-shell 成立。
5. 从 $\Psi=\bar c^a(G^a-\xi B^a/2)$ 推导 $-s\Psi$。
6. 消去 $B^a$，验证得到 $-G^2/(2\xi)+\bar cMc$。
7. 为什么 BRST-exact 的规范固定变化通常不改变物理可观测量？列出必要条件。
8. 区分 BRST-closed 态与 BRST-exact 态。
9. 比较 Abelian 与 non-Abelian BRST 变换。
10. 比较目标时空 Yang-Mills BRST 与世界面 BRST 的共同结构和关键区别。

## 答案与提示

1. $sA_\mu^a=(D_\mu^{\mathrm{adj}}c)^a$，$sc^a=-\frac g2f^{abc}c^bc^c$，$s\bar c^a=B^a$，$sB^a=0$。
2. non-Abelian 规范变换的交换子仍是规范变换。$sc\propto[c,c]$ 编码 Lie 代数闭合，并抵消 $s^2A$ 中由 $sA$ 产生的项；令 $sc=0$ 会使 $s^2A\ne0$。
3. 代入 $sc$ 后得到三个鬼场乘积与两个结构常数的组合；利用鬼场反对易性将其完全反对称化，系数化为 Jacobi 组合 $f^{abe}f^{ecd}+f^{ace}f^{edb}+f^{ade}f^{ebc}=0$，因此 $s^2c^a=0$。
4. 因为 $s\bar c=B$ 且 $sB=0$，无需使用任何运动方程即可得到 $s^2\bar c=0$。
5. $s\Psi=B^aG^a-\frac\xi2B^aB^a-\bar c^aM^{ab}c^b$，所以 $-s\Psi=-B^aG^a+\frac\xi2B^aB^a+\bar c^aM^{ab}c^b$。
6. $B$ 的方程是 $B^a=G^a/\xi$。代回前两项得到 $-G^2/\xi+G^2/(2\xi)=-G^2/(2\xi)$，鬼项保持 $+\bar cMc$。
7. 规范固定变化若是 $-s(\delta\Psi)$，在测度 BRST 不变、无反常、边界项消失、正规化保持恒等式并妥善处理零模和全局规范问题的前提下，BRST-exact 变化不改变 BRST-closed 插入的期望值。
8. closed 态满足 $Q|\psi\rangle=0$；exact 态可写成 $Q|\chi\rangle$。物理态由 closed 态模去 exact 态，即 $\ker Q/\operatorname{im}Q$。
9. Abelian 情形 $sc=0$ 且鬼自由解耦；non-Abelian 情形 $sc=-\frac g2f^{abc}c^bc^c$，鬼与规范场耦合，Jacobi 恒等式保证幂零性。
10. 共同点是鬼系统、Grassmann 奇幂零荷和上同调物理态；区别是 Yang-Mills 固定目标时空内部规范群，而世界面 BRST 固定 Diff×Weyl（RNS 还含局部超对称），鬼场张量类型不同，世界面量子 $Q^2=0$ 还要求总中心荷反常消失。

## 与其他概念的关系

- [[Faddeev-Popov 鬼场]] 提供 $c,\bar c$、鬼作用量和 ghost number 的直接前驱；
- [[规范固定]] 给出 $G[A]$、规范参数 $\xi$ 和规范切片；
- [[Yang-Mills 理论]] 给出规范代数、场强和协变导数；
- [[Grassmann 变量]] 提供奇导子、分次 Leibniz 法则和 Berezin 积分；
- [[Lie 代数]] 的 Jacobi 恒等式保证 non-Abelian BRST 幂零性；
- [[Noether 定理]] 把全局 BRST 对称性对应到守恒荷 $Q$；
- [[Poisson 括号]] 是 Hamilton/BFV-BRST 约束代数的经典前驱；
- [[群作用]] 从轨道与商空间角度解释 BRST 所处理的冗余；
- [[模空间]] 在世界面规范固定中使用 BRST 和鬼场处理测度；
- [[量子反常]] 说明测度或正规化如何破坏量子 Slavnov–Taylor 恒等式，以及何时该破缺不能由局域反项恢复；
- [[Weyl 反常]] 说明世界面总中心荷和正规序条件怎样进入量子 BRST 荷的幂零性；
- [[弦理论完整学习路线图]] 将本节点放在 FP 鬼场与 BRST 上同调之间。

## 参考资料

- C. Becchi, A. Rouet, and R. Stora, "Renormalization of Gauge Theories," *Annals of Physics* 98 (1976), 287–321.
- I. V. Tyutin, "Gauge Invariance in Field Theory and Statistical Physics in Operator Formalism," Lebedev Institute preprint 39 (1975), arXiv:0812.0580.
- Michael E. Peskin and Daniel V. Schroeder, *An Introduction to Quantum Field Theory*, Westview Press, 1995, Chapter 16.
- Steven Weinberg, *The Quantum Theory of Fields, Vol. 2*, Cambridge University Press, 1996, Chapters 15–16.
- Marc Henneaux and Claudio Teitelboim, *Quantization of Gauge Systems*, Princeton University Press, 1992.
- Taichiro Kugo and Izumi Ojima, "Local Covariant Operator Formalism of Non-Abelian Gauge Theories and Quark Confinement Problem," *Progress of Theoretical Physics Supplement* 66 (1979), 1–130.
- Joseph Polchinski, *String Theory, Vol. 1*, Cambridge University Press, 1998, Chapters 3–4.
