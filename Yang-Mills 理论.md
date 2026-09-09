---
aliases:
  - Yang-Mills Theory
  - 杨-米尔斯理论
  - 非 Abelian 规范场
english_name: Yang-Mills Theory
tags:
  - 物理学
  - 量子场论
  - 规范理论
  - 弦理论先修
  - 弦理论
prerequisites:
  - "[[经典场论]]"
  - "[[Maxwell 方程]]"
  - "[[规范对称性]]"
  - "[[Lie 群]]"
  - "[[Lie 代数]]"
  - "[[群表示]]"
  - "[[Maxwell 场量子化]]"
used_by:
  - "[[规范协变导数]]"
  - "[[Wilson 线与 Wilson 圈]]"
  - "[[弦理论完整学习路线图]]"
evidence_status: 教材事实
---

# Yang-Mills 理论（Yang-Mills Theory）

## 学习导航

- 上一页：[[有效场论]]
- 下一页：[[规范协变导数]]
- 总路线：[[弦理论完整学习路线图]]

## 一句话解释

Yang-Mills 理论是把 Maxwell 电磁场从交换群 $U(1)$ 推广到非交换 Lie 群的规范场论，其核心对象是 Lie 代数值规范势 $A_\mu$ 和作为联络曲率的场强 $F_{\mu\nu}$。

## 为什么要学它

[[Maxwell 方程|Maxwell 理论]] 描述 $U(1)$ 规范场，即光子。但自然界还有弱相互作用和强相互作用，它们分别由 $SU(2)$ 和 $SU(3)$ 规范群描述。Yang-Mills 理论提供统一的数学框架：

- 规范势是 Lie 代数值的一形式，不是普通向量场；
- 场强包含非线性交换子项，导致规范玻色子自相互作用；
- 物质场处于规范群的某个表示，规范场处于伴随表示；
- 量子化需要规范固定、鬼场和 BRST 对称性。

标准模型的电弱统一和量子色动力学都是 Yang-Mills 理论的具体实现。弦理论中，开弦低能极限和 D-brane 上的规范场也由 Yang-Mills 作用量描述。

## 直观图景

Maxwell 电磁场可以想象成空间每一点有一个箭头（向量势 $A_\mu$），场强 $F_{\mu\nu}$ 描述箭头的旋度。

Yang-Mills 场则是空间每一点有一个**矩阵** $A_\mu = A_\mu^a T^a$，其中 $T^a$ 是 Lie 代数生成元。场强不仅包含普通旋度，还包含矩阵交换子 $[A_\mu, A_\nu]$，这使得不同"颜色"方向的场会相互耦合。

这种自相互作用是非 Abelian 规范理论的核心特征：光子不带电荷所以不直接相互作用，但胶子带色荷所以会相互耦合。

## 本篇约定

采用自然单位 $\hbar=c=1$ 和 mostly-minus 度规 $\eta_{\mu\nu}=\mathrm{diag}(+1,-1,-1,-1)$。

Lie 代数采用 Hermitian 生成元约定：

$$
[T^a, T^b] = i f^{ab}{}_{c} T^c.
$$

对紧致群可选择关于不变正定内积正交归一的生成元；在这种基下，把第三个指标也升起后，$f^{abc}$ 完全反对称。本页讨论 $SU(N)$ 时采用基本表示归一化

$$
\mathrm{tr}_{F}(T^a T^b) = \frac{1}{2} \delta^{ab}.
$$

一般表示 $R$ 中定义 Dynkin 指数 $T(R)$：

$$
\mathrm{tr}_R(T_R^a T_R^b) = T(R) \delta^{ab}.
$$

对 $SU(N)$ 基本表示，$T(F) = 1/2$；伴随表示的二次 Casimir 为 $C_A = N$。这些数值依赖群、表示和生成元归一化，不能无条件推广到任意 Lie 代数。

## 规范势

Yang-Mills 规范势是 Lie 代数值的一形式：

$$
\boxed{
A_\mu(x) = A_\mu^a(x) T^a.
}
$$

其中：

- $\mu = 0,1,2,3$ 是时空指标；
- $a = 1, \ldots, \dim G$ 是 Lie 代数或伴随指标；
- $A_\mu^a(x)$ 是实值场分量；
- $T^a$ 是规范群 $G$ 的 Lie 代数生成元。

$A_\mu$ 不是普通向量场，而是矩阵值场。它在局域规范变换下不是张量，而是包含非齐次导数项。

## 物质场与表示

物质场 $\psi(x)$ 处于规范群 $G$ 的某个表示 $R$ 中。在无穷小规范变换下：

$$
\psi(x) \to \psi'(x) = \left(1 + i \alpha^a(x) T_R^a\right) \psi(x),
$$

其中 $\alpha^a(x)$ 是局域规范参数，$T_R^a$ 是表示 $R$ 中的生成元矩阵。

有限规范变换写成矩阵形式：

$$
\psi'(x) = U(x) \psi(x), \qquad U(x) = \exp\left(i \alpha^a(x) T_R^a\right).
$$

不同表示的物质场与规范场的耦合方式不同。例如 QCD 中夸克处于 $SU(3)$ 基本表示，而规范玻色子（胶子）处于伴随表示。

## 规范协变导数

普通导数 $\partial_\mu \psi$ 在局域规范变换下不是协变的，因为 $\partial_\mu U(x)$ 会贡献额外项。为此引入**规范协变导数**：

$$
\boxed{
D_\mu = \partial_\mu - i g A_\mu,
}
$$

其中 $g$ 是规范耦合常数。作用于表示 $R$ 中的物质场：

$$
D_\mu \psi = \left(\partial_\mu - i g A_\mu^a T_R^a\right) \psi.
$$

要求协变导数在规范变换下满足：

$$
(D_\mu \psi)' = U (D_\mu \psi),
$$

可以推导出规范势的变换律：

$$
\boxed{
A_\mu' = U A_\mu U^{-1} + \frac{i}{g} U (\partial_\mu U^{-1}).
}
$$

等价写法是：

$$
A_\mu' = U A_\mu U^{-1} - \frac{i}{g} (\partial_\mu U) U^{-1}.
$$

第二项是非齐次导数项，使得 $A_\mu$ 本身不是规范张量。

路线图下一节点 [[规范协变导数]] 详细展开不同表示中的协变导数、Leibniz 法则和与联络的关系。

## 场强

场强定义为协变导数的对易子：

$$
\boxed{
F_{\mu\nu} = \frac{i}{g} [D_\mu, D_\nu].
}
$$

直接计算得到：

$$
\boxed{
F_{\mu\nu} = \partial_\mu A_\nu - \partial_\nu A_\mu - i g [A_\mu, A_\nu].
}
$$

分量形式为：

$$
F_{\mu\nu}^a = \partial_\mu A_\nu^a - \partial_\nu A_\mu^a + g f^{abc} A_\mu^b A_\nu^c.
$$

第三项是非 Abelian 交换子贡献，在 $U(1)$ 情形消失。

场强在规范变换下按伴随表示协变：

$$
F_{\mu\nu}' = U F_{\mu\nu} U^{-1}.
$$

因此 $F_{\mu\nu}^a$ 本身不是规范不变量，但迹 $\mathrm{tr}(F_{\mu\nu} F^{\mu\nu})$ 是局域规范不变量。

## Yang-Mills 作用量

纯 Yang-Mills 作用量为：

$$
\boxed{
S_{\mathrm{YM}} = -\frac{1}{4} \int d^d x \, F_{\mu\nu}^a F^{a\mu\nu}.
}
$$

等价矩阵形式：

$$
S_{\mathrm{YM}} = -\frac{1}{2} \int d^d x \, \mathrm{tr}\left(F_{\mu\nu} F^{\mu\nu}\right).
$$

在 Minkowski 时空中，作用量的整体符号依赖度规约定。Euclidean 作用量通常写成正定形式：

$$
S_E = \frac{1}{4} \int d^d x \, F_{\mu\nu}^a F_{\mu\nu}^a.
$$

展开 $F_{\mu\nu}^a F^{a\mu\nu}$ 会出现：

- 二次项 $(\partial A)^2$：自由传播；
- 三次项 $g (\partial A) A^2$：三规范玻色子顶点；
- 四次项 $g^2 A^4$：四规范玻色子顶点。

这是非 Abelian 规范理论与自由 Maxwell 理论的核心动力学差异。

## 运动方程

对 $A_\mu^a$ 变分作用量，得到 Yang-Mills 运动方程：

$$
\boxed{
D_\mu F^{\mu\nu} = 0.
}
$$

分量形式为：

$$
(D_\mu F^{\mu\nu})^a = \partial_\mu F^{a\mu\nu} + g f^{abc} A_\mu^b F^{c\mu\nu} = 0.
$$

若作用量还含物质部分 $S_{\mathrm m}[A,\psi]$，定义伴随表示电流的归一化为

$$
gJ^{a\nu}
\equiv
-\frac{\delta S_{\mathrm m}}{\delta A_\nu^a},
$$

则场方程写成

$$
(D_\mu F^{\mu\nu})^a = gJ^{a\nu}.
$$

这个定义同时固定了 $J$ 的符号和是否包含耦合 $g$；若文献对 $D_\mu$ 或物质相互作用项采用不同符号，方程右端也会相应改变。由规范不变性和物质场方程可得协变守恒条件 $(D_\nu J^\nu)^a=0$。注意这里是**协变散度** $D_\mu$，不是普通散度 $\partial_\mu$。

## Bianchi 恒等式

场强定义隐含 Bianchi 恒等式：

$$
\boxed{
D_{[\mu} F_{\nu\rho]} = 0,
}
$$

即：

$$
D_\mu F_{\nu\rho} + D_\nu F_{\rho\mu} + D_\rho F_{\mu\nu} = 0.
$$

它来自协变导数的 Jacobi 恒等式，不是独立的动力学方程。在 Abelian 情形退化为 $\partial_{[\mu} F_{\nu\rho]} = 0$，即 Maxwell 方程中的 $\nabla \cdot \mathbf{B} = 0$ 和 $\nabla \times \mathbf{E} + \partial_t \mathbf{B} = 0$。

## 非线性和自相互作用

将 $F_{\mu\nu}^a F^{a\mu\nu}$ 展开后，作用量包含：

$$
S_{\mathrm{YM}} = \int d^d x \left[ -\frac{1}{4} (\partial_\mu A_\nu^a - \partial_\nu A_\mu^a)^2 - g f^{abc} (\partial_\mu A_\nu^a) A^{b\mu} A^{c\nu} - \frac{g^2}{4} f^{abc} f^{ade} A_\mu^b A_\nu^c A^{d\mu} A^{e\nu} \right].
$$

第二项给出三规范玻色子顶点，第三项给出四规范玻色子顶点。这些自相互作用顶点是非 Abelian 规范理论的特征，在微扰量子化时产生额外的 Feynman 图。

不能因此断言"所有非 Abelian 规范理论都强耦合"。耦合强弱依能标和理论内容而变；例如 QCD 在高能时渐近自由，耦合变小。

## Abelian 极限

当规范群为 Abelian（如 $U(1)$）时，结构常数 $f^{abc} = 0$，场强退化为：

$$
F_{\mu\nu} = \partial_\mu A_\nu - \partial_\nu A_\mu.
$$

三顶点和四顶点消失，作用量变为多个独立 Maxwell 场的叠加。

注意区分两个极限：

- 令 $g \to 0$：得到自由理论，无相互作用；
- 令群为 Abelian：交换子恒为零，但 $g$ 仍可非零。

两者都能使非线性项消失，但物理含义不同。

## 自由度

在 $d$ 维平直时空中，无质量规范玻色子的物理偏振数为 $d-2$。例如四维中光子有两个横偏振。

规范势 $A_\mu$ 有 $d$ 个分量，但其中：

- 一个时间分量 $A_0$ 是非动力学的（约束方程）；
- 一个纵向分量可通过规范选择消除。

因此物理自由度为 $d - 2$。

规范冗余不是物理对称性，而是描述中的多余自由度。[[规范固定]] 展开如何选择规范条件和处理冗余；Elitzur 定理通过局域规范对称性无法自发破缺这一事实制约了“物理对称性”的日常语言，但完备的量子化还需要 [[Faddeev-Popov 行列式]] 和后续 BRST 对称性一并建立。

## 量子化预告

经典 Yang-Mills 理论的量子化不能直接套用路径积分 $\int \mathcal{D}A \, e^{iS}$，因为规范轨道上的所有场构型给出相同物理态，导致路径积分发散。

解决方法包括：

1. **[[规范固定]]**：选择规范条件 $G(A) = 0$ 处理冗余；
2. **[[Faddeev-Popov 行列式]]**：把规范固定的 Jacobian 写入路径积分；
3. **[[Faddeev-Popov 鬼场]]**：用 Grassmann 奇的标量场 $c^a, \bar{c}^a$ 表示行列式；
4. **[[BRST 对称性]]**：用幂零 BRST 微分组织规范固定作用量、鬼场和物理态条件。

这四个页面已经建立；[[BRST 上同调]] 进一步把物理态定义为闭态模去恰当态。

## 与弦理论的关系

开弦端点可携带 Chan-Paton 标签 $i, j = 1, \ldots, N$，使得质量零开弦态组成 $U(N)$ 伴随表示。低能目标时空场成为矩阵值规范场 $A_\mu = A_\mu^a T^a$。

对单个 D-brane 的 Abelian 场，在平直背景并忽略其他世界体场时，Dirac-Born-Infeld 作用量可写成

$$
S_{\mathrm{DBI}}
=
-T_p\int d^{p+1}x\,
\sqrt{-\det\!\left(\eta_{\mu\nu}+2\pi\alpha' F_{\mu\nu}\right)}.
$$

小场强展开的领先动力学项为

$$
S_{\mathrm{DBI}}
=
-T_p\int d^{p+1}x
-
\frac{1}{4g_{\mathrm{YM}}^2}
\int d^{p+1}x\,F_{\mu\nu}F^{\mu\nu}
+
O\!\left((2\pi\alpha'F)^4\right),
$$

其中 $g_{\mathrm{YM}}$ 由 $T_p$、$\alpha'$ 和弦耦合共同决定。重合 brane 的非 Abelian 低能作用量同样以 Yang-Mills 项为领先项，但完整 non-Abelian DBI 在一般场强下并不存在一个由简单矩阵行列式完全定义的已知闭式；高阶项还包含交换子、迹排序和协变导数修正。

因此 Yang-Mills 是开弦/D-brane 扇区的低能领先理论。就导数展开而言，具体首个非零 $\alpha'$ 修正依弦类型、超对称性、背景和场重定义而变：例如 bosonic open string 可出现与 $\alpha'\,\mathrm{Tr}(F^3)$ 同阶的修正，而超弦有效作用量的首批纯场强修正通常从 $\alpha'^2F^4$ 开始，不能统一写成没有量纲说明的 $O(\alpha')$。

必须说明的边界：

1. 单个 D-brane 给出 $U(1)$，不是非 Abelian 规范群；
2. $N$ 个分离 brane 只保留 $U(1)^N$，连接不同 brane 的弦有质量；
3. brane 重合时这些弦变成质量零，规范对称性增强到 $U(N)$；
4. orientifold 投影可产生 $SO(N)$ 或 $Sp(N)$；
5. 杂化弦的规范场来自世界面 current algebra，不是开弦 Chan-Paton；
6. 目标时空 Yang-Mills 鬼场与世界面 $bc$ 鬼场不是同一系统。

## 与大模型路径的边界

Yang-Mills 理论与大模型学习路径之间没有直接的物理或算法对应。现有跨学科图谱已记录群作用、表示和等变性的共享数学语言，但不建立强等价关系。

明确禁止的误连：

- 局域规范变换 $\ne$ token 位置旋转；
- 规范轨道 $\ne$ 参数优化轨迹；
- 规范固定 $\ne$ 模型正则化；
- 鬼场 $\ne$ 隐变量或辅助损失；
- BRST 幂零算符 $\ne$ 反向传播；
- Yang-Mills 自相互作用 $\ne$ 多头注意力交互；
- 渐近自由 $\ne$ 模型规模越大越容易训练。

[[弦理论与大模型跨学科关系图谱]] 记录这些边界，防止虚假等价。

## 适用条件与事实边界

1. 本页讨论局域、经典和微扰量子场论层面的 Yang-Mills 理论。
2. Lie 代数不足以确定完整量子理论；还需指定全局规范群、物质表示、时空维数、耦合和拓扑项。
3. 局部平凡化中的公式不能替代主丛的全局结构；instantons、磁荷和 Wilson 线可能依赖全局拓扑。
4. 四维纯 Yang-Mills 经典层面无质量参数，但量子理论可通过 dimensional transmutation 产生尺度。
5. 微扰渐近自由是紫外结论；红外禁闭和质量隙属于非微扰问题，不能由一圈 beta 函数直接证明。
6. "规范群未自发破缺"和"规范冗余本身被破坏"不是同一说法。
7. 经典场方程不能代替量子规范固定、鬼场、BRST 和反常分析。
8. 物质场的表示 $R$ 必须明确；不能默认所有物质都处于基本表示。
9. $SU(N)$ 是重要例子，但 Yang-Mills 不限于 $SU(N)$。
10. 目标时空 Yang-Mills 规范对称与弦世界面 Diff×Weyl 冗余不是同一规范群。

## 常见误区

1. **规范势 $A_\mu$ 是向量场。** 它是 Lie 代数值的一形式，在规范变换下含非齐次导数项。
2. **场强分量 $F_{\mu\nu}^a$ 是规范不变量。** 它按伴随表示协变变换；只有迹 $\mathrm{tr}(F_{\mu\nu} F^{\mu\nu})$ 等群不变量才是局域规范不变的。
3. **非 Abelian 规范理论一定强耦合。** 耦合强弱依能标和理论内容而变；QCD 在高能时渐近自由。
4. **Bianchi 恒等式是运动方程。** 它来自场强定义和 Jacobi 恒等式，与由作用量变分得到的 $D_\mu F^{\mu\nu} = 0$ 来源不同。
5. **把规范冗余当作普通全局物理对称性，并用局域规范非不变量作为序参量。** Elitzur 定理说明，在未规范固定的表述中，局域规范非不变量的期望值不能作为自发破缺序参量；这不否认 Higgs 相或残余全局对称性的物理区分。
6. **一圈 beta 函数为负证明禁闭。** 渐近自由是紫外微扰结论；红外禁闭是非微扰问题，需要格点或其他方法。
7. **$g \to 0$ 和群为 Abelian 是同一极限。** 前者得到自由理论，后者使交换子为零但 $g$ 仍可非零。
8. **普通散度 $\partial_\mu F^{\mu\nu}$ 等于协变散度 $D_\mu F^{\mu\nu}$。** 非 Abelian 情形两者相差 $g f^{abc} A_\mu^b F^{c\mu\nu}$。
9. **指定 Lie 代数就确定规范群。** $\mathfrak{su}(2)$ 可对应全局群 $SU(2)$ 或 $SO(3)$，它们有不同拓扑和表示内容。
10. **局部场强公式捕捉所有拓扑信息。** Wilson 线、holonomy 和主丛拓扑需要全局分析。

## 练习

1. 从 $D_\mu = \partial_\mu - ig A_\mu$ 直接计算 $[D_\mu, D_\nu]$，验证得到 $F_{\mu\nu}$。
2. 验证 Abelian 情况下交换子项消失并恢复 Maxwell 场强。
3. 根据 $(D_\mu \psi)' = U (D_\mu \psi)$ 推导 $A_\mu'$ 的变换律。
4. 证明 $F_{\mu\nu}' = U F_{\mu\nu} U^{-1}$。
5. 利用迹的循环性证明 $\mathrm{tr}(F_{\mu\nu} F^{\mu\nu})$ 规范不变。
6. 从 Yang-Mills 作用量变分推导 $D_\mu F^{\mu\nu} = 0$，正确处理分部积分和迹。
7. 用协变导数的 Jacobi 恒等式推导 $D_{[\mu} F_{\nu\rho]} = 0$。
8. 展开 $F_{\mu\nu}^a F^{a\mu\nu}$，辨认二次、三次、四次场项。
9. 对 $SU(2)$ 使用 $T^a = \sigma^a/2$，显式计算一个场强分量中的非 Abelian 项。
10. 说明为什么规范玻色子按伴随表示变换，而物质场不必处于伴随表示。
11. 比较"$g \to 0$"和"规范群变成 Abelian"两个极限的物理差异。
12. 解释为什么指定 Lie 代数 $\mathfrak{su}(2)$ 还不足以区分全局群 $SU(2)$ 和 $SO(3)$。
13. 在 $d$ 维由作用量无量纲条件求 $[A_\mu]$ 和 $[g]$，解释四维 Yang-Mills 耦合为什么无量纲。
14. 给出一个理由说明"一圈 beta 函数为负"不能单独构成禁闭证明。
15. 解释局部场强公式为什么不能捕捉所有 Wilson 线和主丛拓扑信息。

## 答案与提示

1. $[D_\mu, D_\nu] = [\partial_\mu - ig A_\mu, \partial_\nu - ig A_\nu] = -ig(\partial_\mu A_\nu - \partial_\nu A_\mu) - g^2 [A_\mu, A_\nu]$。因此 $\frac{i}{g}[D_\mu, D_\nu] = \partial_\mu A_\nu - \partial_\nu A_\mu - ig[A_\mu, A_\nu] = F_{\mu\nu}$。
2. Abelian 群的对易子 $[A_\mu, A_\nu] = 0$，所以 $F_{\mu\nu} = \partial_\mu A_\nu - \partial_\nu A_\mu$，即 Maxwell 场强。
3. 要求 $(\partial_\mu - ig A_\mu')(U\psi) = U(\partial_\mu - ig A_\mu)\psi$。展开左边并比较，得到 $A_\mu' = U A_\mu U^{-1} + \frac{i}{g} U (\partial_\mu U^{-1})$。
4. 直接计算 $F_{\mu\nu}' = \frac{i}{g}[D_\mu', D_\nu'] = \frac{i}{g}[U D_\mu U^{-1}, U D_\nu U^{-1}] = U \frac{i}{g}[D_\mu, D_\nu] U^{-1} = U F_{\mu\nu} U^{-1}$。
5. $\mathrm{tr}(F_{\mu\nu}' F'^{\mu\nu}) = \mathrm{tr}(U F_{\mu\nu} U^{-1} U F^{\mu\nu} U^{-1}) = \mathrm{tr}(U F_{\mu\nu} F^{\mu\nu} U^{-1}) = \mathrm{tr}(F_{\mu\nu} F^{\mu\nu})$，利用迹的循环性。
6. 变分 $\delta S = -\frac{1}{2} \int d^d x \, F^{a\mu\nu} \delta F_{\mu\nu}^a$。利用 $\delta F_{\mu\nu}^a = (D_\mu \delta A_\nu)^a - (D_\nu \delta A_\mu)^a$，分部积分后得到 $\delta S = \int d^d x \, (D_\mu F^{\mu\nu})^a \delta A_\nu^a$。令 $\delta S = 0$ 对任意 $\delta A_\nu^a$ 成立，得到 $D_\mu F^{\mu\nu} = 0$。
7. Jacobi 恒等式 $[D_\mu, [D_\nu, D_\rho]] + \text{循环} = 0$。代入 $[D_\nu, D_\rho] = -ig F_{\nu\rho}$，得到 $D_{[\mu} F_{\nu\rho]} = 0$。
8. 令 $G_{\mu\nu}^a\equiv\partial_\mu A_\nu^a-\partial_\nu A_\mu^a$。利用 $f^{abc}$ 的反对称性，
   $$
   F_{\mu\nu}^aF^{a\mu\nu}
   =
   G_{\mu\nu}^aG^{a\mu\nu}
   +4g f^{abc}(\partial_\mu A_\nu^a)A^{b\mu}A^{c\nu}
   +g^2f^{abc}f^{ade}A_\mu^bA_\nu^cA^{d\mu}A^{e\nu}.
   $$
   三项分别为二次、三次和四次场项；乘上 Lagrangian 的整体因子 $-1/4$ 后，三次项系数为 $-g$，四次项系数为 $-g^2/4$。
9. 对 $SU(2)$，$f^{abc} = \epsilon^{abc}$。$F_{12}^1 = \partial_1 A_2^1 - \partial_2 A_1^1 + g(A_1^2 A_2^3 - A_1^3 A_2^2)$。
10. 规范玻色子来自规范势 $A_\mu^a$，其指标 $a$ 是伴随表示指标。物质场 $\psi$ 可以处于任意表示 $R$，由物理内容决定。
11. $g \to 0$ 时所有相互作用消失，得到自由理论。群为 Abelian 时交换子为零，三顶点和四顶点消失，但 $g$ 仍可非零，物质场仍与规范场耦合。
12. $SU(2)$ 和 $SO(3)$ 有相同 Lie 代数 $\mathfrak{su}(2)$，但 $SU(2)$ 是单连通覆盖群，$SO(3) = SU(2)/\mathbb{Z}_2$。它们有不同全局拓扑和允许表示（$SO(3)$ 没有半整数自旋表示）。
13. 作用量 $S = \int d^d x \, F^2$ 无量纲，所以 $[F^2] = d$。由 $F \sim \partial A$ 得 $[F] = 1 + [A]$，所以 $2(1 + [A]) = d$，即 $[A] = (d-2)/2$。由 $F \sim g A^2$ 得 $[g] + 2[A] = [F] = 1 + [A]$，所以 $[g] = 1 - [A] = (4-d)/2$。四维中 $[g] = 0$，耦合无量纲。
14. 一圈 beta 函数为负说明耦合在高能时变小（渐近自由），这是微扰紫外结论。红外禁闭涉及强耦合非微扰区域，一圈结果无法外推到低能。需要格点模拟或其他非微扰方法。
15. 局部场强 $F_{\mu\nu}(x)$ 只描述无穷小邻域的曲率。Wilson 线 $W = \mathcal{P} \exp(i \oint A_\mu dx^\mu)$ 依赖沿有限路径的积分，可探测非平凡 holonomy 和主丛拓扑（如 instanton 数）。局部公式无法捕捉这些全局信息。

## 与其他概念的关系

- [[经典场论]] 提供作用量和场变分的基础；
- [[Maxwell 方程]] 是 Abelian $U(1)$ 规范理论的原型；
- [[规范对称性]] 解释规范冗余和局域变换的概念；
- [[Lie 群]] 提供有限规范变换所在的群；
- [[Lie 代数]] 提供生成元、结构常数和伴随表示；
- [[群表示]] 区分物质场和规范场的表示；
- [[Maxwell 场量子化]] 建立 Abelian 规范场的量子化，并预告非 Abelian 鬼不解耦；
- [[有效场论]] 是路线图的上一节点，Yang-Mills 是其低能极限的具体实现；
- [[beta 函数]] 给出非 Abelian 规范理论的一圈 beta 函数和渐近自由条件；
- [[曲率]] 说明规范场强严格就是规范联络的曲率；
- [[Wilson 线与 Wilson 圈]] 把局部规范联络沿有限路径积分为平行输运，并探测 holonomy、全局群结构和非微扰动力学；
- [[弦理论完整学习路线图]] 将本节点放在有效场论之后、规范协变导数之前。

## 参考资料

- Michael E. Peskin and Daniel V. Schroeder, *An Introduction to Quantum Field Theory*, Westview Press, 1995, Chapters 15–16.
- Mark Srednicki, *Quantum Field Theory*, Cambridge University Press, 2007, Chapters 69–74.
- Steven Weinberg, *The Quantum Theory of Fields, Vol. 2*, Cambridge University Press, 1996, Chapters 15–16.
- A. Zee, *Quantum Field Theory in a Nutshell*, 2nd ed., Princeton University Press, 2010, Chapters I.4 and II.6.
- Joseph Polchinski, *String Theory, Vol. 1*, Cambridge University Press, 1998, Chapter 3 and 6.
- David Tong, *Gauge Theory*, arXiv:1707.07845. https://arxiv.org/abs/1707.07845
