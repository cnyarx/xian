---
aliases:
  - BRST Cohomology
  - Becchi-Rouet-Stora-Tyutin Cohomology
  - BRST Cohomological Space
english_name: BRST Cohomology
tags:
  - 物理学
  - 量子场论
  - 规范理论
  - 弦理论先修
prerequisites:
  - "[[弦理论/物理学/BRST 对称性]]"
  - "[[弦理论/数学/上同调]]"
  - "[[弦理论/物理学/Faddeev-Popov 鬼场]]"
  - "[[弦理论/数学/Hilbert 空间]]"
used_by:
  - "[[弦理论/物理学/BRST 对称性]]"
  - "[[弦理论/物理学/场的正则量子化]]"
  - "[[弦理论/物理学/Fock 空间]]"
  - "[[弦理论/物理学/Faddeev-Popov 鬼场]]"
  - "[[弦理论/物理学/Yang-Mills 理论]]"
  - "[[弦理论/数学/Hilbert 空间]]"
  - "[[弦理论/弦理论完整学习路线图]]"
  - "[[弦理论/物理学/量子反常]]"
evidence_status: 教材事实
---

# BRST 上同调（BRST Cohomology）

## 学习导航

- 上一页：[[弦理论/物理学/BRST 对称性]]
- 下一页：[[弦理论/物理学/量子反常]]
- 总路线：[[弦理论/弦理论完整学习路线图]]

## 一句话解释

BRST 上同调把被 BRST 荷 $Q$ 消灭的闭态，按相差一个 $Q$-exact 态视为等价，从规范固定后的较大候选空间中提取真正不同的物理态或物理算符。

## 为什么要学它

[[弦理论/物理学/BRST 对称性]] 建立了 Grassmann 奇的幂零荷

$$
Q^2=0
$$

以及物理态条件

$$
Q|\mathrm{phys}\rangle=0.
$$

但仅有这个条件仍不够。若一个态可写为

$$
|\eta\rangle=Q|\chi\rangle,
$$

它自动满足 $Q|\eta\rangle=0$，却通常只代表规范冗余方向，不应被计作新的物理态。因此还必须把相差 $Q|\chi\rangle$ 的闭态识别为同一个物理状态。

这正是上同调的作用。它回答：

1. 为什么闭态还要模去恰当态；
2. 为什么 $Q^2=0$ 使这个商空间有定义；
3. 非物理规范模式和鬼自由度怎样在适当条件下不贡献上同调；
4. 状态空间上同调、局域算符上同调和反常上同调有何区别；
5. Yang-Mills 与弦世界面如何共享同一代数骨架，却具有不同的具体物理扇区。

## 从一般上同调到 BRST 上同调

[[弦理论/数学/上同调]] 说明：若一个分次空间上有平方为零的微分，就可以研究“闭对象模去恰当对象”。BRST 理论把这一骨架应用到 ghost number 分次的态或算符空间。

设

$$
\mathcal H
=\bigoplus_{n\in\mathbb Z}\mathcal H^n,
$$

其中 $\mathcal H^n$ 是 ghost number 为 $n$ 的子空间。BRST 荷增加一个 ghost number：

$$
Q:\mathcal H^n\longrightarrow\mathcal H^{n+1}.
$$

若 $N_{\mathrm{gh}}$ 是 ghost-number 算符，则常用约定写成

$$
[N_{\mathrm{gh}},Q]=Q.
$$

因为 $N_{\mathrm{gh}}$ 是 Grassmann 偶算符，这里使用普通交换子。

幂零性

$$
Q^2=0
$$

使这些子空间构成上链复形：

$$
\cdots
\xrightarrow{Q}\mathcal H^{n-1}
\xrightarrow{Q}\mathcal H^n
\xrightarrow{Q}\mathcal H^{n+1}
\xrightarrow{Q}\cdots.
$$

## 闭态、恰当态和上同调类

### 闭态

第 $n$ 阶闭态空间定义为

$$
Z^n(Q)
=
\ker\left(Q:\mathcal H^n\to\mathcal H^{n+1}\right).
$$

即

$$
|\psi\rangle\in Z^n(Q)
\quad\Longleftrightarrow\quad
Q|\psi\rangle=0.
$$

BRST-closed 表示该态满足 $Q|\psi\rangle=0$ 这一闭条件，但不保证它处于正确的物理 ghost-number 扇区，也不保证它代表非平凡物理态。

### 恰当态

第 $n$ 阶恰当态空间定义为

$$
B^n(Q)
=
\operatorname{im}\left(Q:\mathcal H^{n-1}\to\mathcal H^n\right).
$$

即

$$
|\eta\rangle\in B^n(Q)
\quad\Longleftrightarrow\quad
|\eta\rangle=Q|\chi\rangle
$$

其中 $|\chi\rangle\in\mathcal H^{n-1}$。

“exact” 在这里译作“恰当”或“正合”；它不表示实验结果“精确”，而表示该对象位于 $Q$ 的像中。

### 为什么像包含于核

若 $|\eta\rangle=Q|\chi\rangle$，则

$$
Q|\eta\rangle
=Q^2|\chi\rangle
=0.
$$

因此

$$
\boxed{B^n(Q)\subseteq Z^n(Q)}
$$

或简写为

$$
\boxed{\operatorname{im}Q\subseteq\ker Q.}
$$

只有因为像是核的子空间，才能对闭态空间取商。

### BRST 上同调

第 $n$ 阶 BRST 上同调定义为

$$
\boxed{
H^n(Q)
=
\frac{
\ker(Q:\mathcal H^n\to\mathcal H^{n+1})
}{
\operatorname{im}(Q:\mathcal H^{n-1}\to\mathcal H^n)
}.
}
$$

若

$$
|\psi'\rangle
=|\psi\rangle+Q|\chi\rangle,
$$

则 $|\psi\rangle$ 与 $|\psi'\rangle$ 代表同一个上同调类：

$$
[|\psi'\rangle]=[|\psi\rangle].
$$

非平凡上同调类是“闭但不恰当”的等价类。

## 一个有限维例子

取分次空间的基

$$
a\in\mathcal H^0,
\qquad
b,c\in\mathcal H^1,
$$

并定义

$$
Qa=b,
\qquad
Qb=0,
\qquad
Qc=0.
$$

显然 $Q^2a=Qb=0$。

在 ghost number 0：

- $a$ 不是闭态，因为 $Qa=b\ne0$；
- 所以 $H^0(Q)=0$。

在 ghost number 1：

- $b,c$ 都是闭态；
- $b=Qa$ 是恰当态；
- $c$ 不是恰当态，因为没有 ghost number 0 的元素可以映到 $c$。

因此

$$
H^1(Q)=\operatorname{span}\{[c]\}.
$$

这个例子说明：闭态 $b$ 虽然满足 $Qb=0$，但因它是恰当态，在上同调中等于零。

## 物理态空间

在常见 Yang-Mills 渐近态约定中，物理态通常由 ghost number 零上同调表示：

$$
\boxed{
\mathcal H_{\mathrm{phys}}
\simeq H^0(Q).
}
$$

展开为

$$
H^0(Q)
=
\frac{
\{|\psi\rangle\in\mathcal H^0\mid Q|\psi\rangle=0\}
}{
\{Q|\chi\rangle\mid |\chi\rangle\in\mathcal H^{-1}\}
}.
$$

这里必须限定：物理扇区位于 ghost number 0 是常见 Yang-Mills/Fock 空间约定，不是所有 BRST 系统中不依赖约定的普遍结论。

在弦世界面理论中，物理态所在 ghost number 还依赖：

- 鬼真空的 ghost-number 归一化；
- 开弦或闭弦；
- 绝对上同调或相对上同调；
- integrated 或 unintegrated 顶点算符；
- RNS 理论中的 picture number。

因此不能把所有弦物理态无条件写成 $H^0(Q_B)$。

## 候选态空间与物理 Hilbert 空间

协变量子化先得到一个包含非物理规范模式和鬼自由度的扩展候选空间。这个空间可能具有不定内积，不能直接当作满足概率解释的物理 [[弦理论/数学/Hilbert 空间]]。

BRST 上同调完成两个步骤：

1. 取核：保留满足 $Q|\psi\rangle=0$ 的闭态；
2. 取商：把相差 $Q|\chi\rangle$ 的闭态视为同一物理态。

但 $Q^2=0$ 本身只保证商空间有定义，不自动证明：

- 上同调非零；
- 取商后的内积正定；
- 所有非物理态都已被消除；
- 物理 S 矩阵自动幺正。

这些结论还需要 BRST 荷的伴随性质、完备性、quartet/no-ghost 结果、边界条件和无反常等附加条件。

## 恰当态的正交性与零范数

协变量子化的扩展空间通常具有不定内积。用 $Q^\ddagger$ 表示相对于该内积和鬼共轭约定的适当伴随。假设：

- $Q^\ddagger=Q$；
- $Q^2=0$ 在量子理论中成立；
- 相关态属于 $Q$ 和 $Q^\ddagger$ 的共同适当定义域；
- 边界项不会破坏伴随关系。

令 $|\eta\rangle=Q|\chi\rangle$ 为恰当态，$Q|\psi\rangle=0$ 为闭态，则

$$
\begin{aligned}
\langle\psi|\eta\rangle
&=\langle\psi|Q|\chi\rangle\\
&=\langle Q^\ddagger\psi|\chi\rangle\\
&=\langle Q\psi|\chi\rangle\\
&=0.
\end{aligned}
$$

因此在这些假设下

$$
\boxed{\operatorname{im}Q\perp\ker Q.}
$$

恰当态本身也是闭态，所以

$$
\langle Q\chi|Q\chi\rangle
=\langle\chi|Q^\ddagger Q|\chi\rangle
=\langle\chi|Q^2|\chi\rangle
=0.
$$

即恰当态可为非零的零范数态。

这依赖不定内积或相应的 Krein/分次伴随结构。在普通正定 Hilbert 空间中，零范数会推出向量为零；若一个处处定义、自伴且幂零的 $Q$ 作用在正定空间上，则对任意 $|\chi\rangle$ 都有 $\|Q|\chi\rangle\|^2=0$，从而直接推出 $Q=0$。因此非平凡 BRST 荷不能按这种朴素的正定、自伴、处处定义框架理解，必须区分扩展候选空间与最终物理 Hilbert 空间。

还不能反推：

- 所有零范数态都是 BRST-exact；
- 取商后内积必然正定；
- $Q^2=0$ 单独保证物理幺正性。

## BRST doublet

若两个变量或态满足

$$
Qu=v,
\qquad
Qv=0,
$$

则称 $(u,v)$ 构成 BRST doublet。仅凭这两式，通常还不足以对整个复杂空间作全局结论。

若进一步存在收缩同伦算符 $K$ 和计数算符 $N$，满足

$$
\{Q,K\}=N,
$$

并且一个闭态 $|\psi\rangle$ 是 $N$ 的正本征值态：

$$
Q|\psi\rangle=0,
\qquad
N|\psi\rangle=n|\psi\rangle,
\qquad
n>0,
$$

则

$$
\begin{aligned}
n|\psi\rangle
&=N|\psi\rangle\\
&=\{Q,K\}|\psi\rangle\\
&=QK|\psi\rangle+KQ|\psi\rangle\\
&=QK|\psi\rangle.
\end{aligned}
$$

所以

$$
\boxed{
|\psi\rangle
=Q\left(\frac1nK|\psi\rangle\right),
}
$$

该闭态是恰当态，不贡献非平凡上同调。

## Quartet mechanism 的边界

在协变规范中，时间样/纵向规范场模式、鬼和反鬼自由度可在适当条件下组织为 BRST doublet 或 quartet。其直观结果是：这些非物理扇区中的闭态成为恰当态，剩余上同调由横向物理自由度表示。

但这个结论需要：

1. $Q^2=0$ 且没有 BRST 反常；
2. doublet/quartet 分解完整；
3. 收缩同伦和计数算符定义良好；
4. 相关正本征值扇区可分解；
5. 不遗漏零模、边界态和拓扑扇区；
6. 全局规范固定和 Gribov 问题不破坏所用局部构造；
7. 相互作用理论中渐近态、完备性和内积性质得到额外证明。

因此本页不声称 quartet mechanism 已无条件证明所有相互作用、非微扰规范理论中的非物理态都完全消失。Kugo-Ojima quartet mechanism、禁闭判据和无鬼定理属于更高阶专题。

## 状态空间上同调与局域算符上同调

### 状态空间上同调

BRST 荷作用在候选态空间：

$$
Q:\mathcal H^n\to\mathcal H^{n+1}.
$$

其主要用途是提取物理态：

$$
H^n(Q)=\ker Q/\operatorname{im}Q.
$$

这里需要讨论内积、范数、渐近态和物理 S 矩阵。

### 局域算符上同调

BRST 微分也可作用在局域场多项式或局域算符空间 $\mathcal A^g$：

$$
s:\mathcal A^g\to\mathcal A^{g+1},
\qquad
s^2=0.
$$

定义

$$
\boxed{
H^g(s)
=
\frac{\ker(s:\mathcal A^g\to\mathcal A^{g+1})}
{\operatorname{im}(s:\mathcal A^{g-1}\to\mathcal A^g)}.
}
$$

ghost number 0 的局域上同调常与局域规范不变观测量有关：

$$
H^0(s).
$$

但不能无条件声称“全部物理可观测量严格等于 $H^0(s)$”。还需指定：

- off-shell 或 on-shell；
- 是否模去运动方程；
- 是否引入 antifield；
- 是否考虑边界和拓扑扇区；
- 是否包含 Wilson 线等非局域算符。

### 两者不能直接等同

| 项目 | 状态空间上同调 | 局域算符上同调 |
|------|----------------|----------------|
| 作用对象 | 候选量子态 | 局域场、算符或局域泛函 |
| 微分 | 通常写 $Q$ | 通常写 $s$ |
| 主要用途 | 提取物理态 | 分类局域观测量、形变和反常候选 |
| 内积 | 涉及态空间内积和范数 | 定义通常不依赖态范数 |
| 常见 ghost number | 依理论与真空约定 | 观测量常在 0，反常候选常在 1 |

只有在具有合适状态—算符对应的共形场论中，二者才能建立受控联系，也不能不加条件地视为同一对象。

## 模去全微分的局域上同调

对积分后的局域泛函，拉氏密度相差一个全微分时可给出相同作用量。因此常研究

$$
H^{g,d}(s\mid d),
$$

其中第一个上标 $g$ 是 ghost number，第二个 $d$ 表示顶阶时空形式次数；竖线后的 $d$ 是外微分。相同字母承担两个相关角色，阅读文献时必须由上下文区分。

闭条件写成下降方程

$$
s a_d^{\,g}+d a_{d-1}^{\,g+1}=0.
$$

若

$$
a_d^{\,g}
=s b_d^{\,g-1}+d b_{d-1}^{\,g},
$$

则它代表平凡类。

## 可观测量的上同调边界

候选局域可观测量 $\mathcal O$ 满足

$$
s\mathcal O=0.
$$

若

$$
\mathcal O'=\mathcal O+sX,
$$

则在测度 BRST 不变、边界项可控、正规化保持恒等式且没有反常等条件下，二者通常给出相同物理信息。因此局域可观测量与 $H^0(s)$ 或积分泛函的 $H^{0,d}(s\mid d)$ 有关。

非局域 Wilson 线、边界算符、拓扑扇区和全局规范问题可能超出这个最简局域分类，不能被一句 $H^0(s)$ 全部覆盖。

## 反常的上同调入口

一致反常的局域候选密度常满足 Wess-Zumino 一致性条件，其 BRST 形式为

$$
\boxed{
s a_d^{\,1}+d a_{d-1}^{\,2}=0.
}
$$

候选分类位于

$$
\boxed{H^{1,d}(s\mid d).}
$$

若

$$
a_d^{\,1}
=s b_d^{\,0}+d b_{d-1}^{\,1},
$$

则它是平凡类，通常可通过加入局域反项移除。

非平凡类表示不能用这种局域反项消除的候选阻碍，但必须区分：

- 上同调非平凡只说明允许存在候选反常；
- 不表示具体理论中的反常系数一定非零；
- 实际结果依赖物质表示、维数、正规化和量子计算；
- 全局反常未必由局域 $H^{1,d}(s\mid d)$ 完整分类。

下一节点 [[弦理论/物理学/量子反常]] 将讨论路径积分测度、Wess-Zumino 一致性条件和反常消除。

## Yang-Mills 与世界面 BRST 上同调

两者共享：

- ghost number 分次空间；
- Grassmann 奇的 BRST 算符；
- 幂零性 $Q^2=0$；
- 闭对象 $Q\psi=0$；
- 等价关系 $\psi\sim\psi+Q\chi$；
- 物理内容由上同调类而非单一代表元描述；
- 量子反常可能破坏幂零性或相关恒等式。

Yang-Mills 一侧：

- 固定目标时空内部规范群；
- $c^a,\bar c^a$ 是带伴随指标的 Lorentz 标量；
- 常在渐近态空间中用 $H^0(Q)$ 表示物理扇区；
- $H^0(s)$ 和 $H^{1,d}(s\mid d)$ 分别与局域观测量和一致反常候选有关；
- 经典幂零性来自 Lie 代数闭合和 Jacobi 恒等式。

弦世界面一侧：

- 固定二维 Diff×Weyl，RNS 还固定局部世界面超对称；
- 玻色弦使用有确定共形权的 $bc$ 鬼；
- RNS 还包含 commuting/bosonic 的 $\beta\gamma$ 超鬼和 picture number；
- 物理弦态位于由鬼真空、开闭弦和相对/绝对条件决定的特定 ghost-number 扇区；
- 世界面量子 BRST 荷的幂零性要求总中心荷和正规序常数满足一致性条件；
- 状态—算符对应使物理弦态与顶点算符上同调密切相关。

本页不展开世界面 $Q_B$ 的振子表达式、相对上同调、顶点算符 ghost number、picture-changing 或 no-ghost theorem。

## 与大模型路径的边界

BRST 上同调与大模型训练没有直接物理或算法对应。明确禁止：

- BRST 上同调 $\ne$ 聚类、降维或表征学习；
- $\ker Q/\operatorname{im}Q\ne$ quotient embedding；
- closed/exact 分类 $\ne$ 正样本/负样本分类；
- ghost number $\ne$ token 位置、层数、特征维度或训练步数；
- $Q^2=0\ne$ 梯度消失、梯度裁剪或 Hessian 为零；
- $Q|\psi\rangle=0\ne$ 模型收敛、停止条件或零损失；
- BRST-exact 态 $\ne$ 冗余特征、低秩方向或被剪枝参数；
- quartet mechanism $\ne$ 剪枝、蒸馏、MoE 路由或特征消除；
- BRST 可观测量 $\ne$ 可解释特征；
- BRST 反常 $\ne$ 模型幻觉、训练异常或数据漂移。

两边有时都使用“等价类”和“商空间”等一般数学词汇，但作用对象、微分结构、物理含义和验证标准完全不同。[[弦理论与大模型跨学科关系图谱]] 只记录这些禁止误连。

## 适用条件与事实边界

1. $Q^2=0$ 只保证 $\operatorname{im}Q\subseteq\ker Q$ 和上同调可定义，不保证上同调非零或正定。
2. $H^n(Q)$ 的上标是 ghost number，不是普通乘方。
3. 物理态位于 $H^0(Q)$ 是常见 Yang-Mills 约定，不能无条件套用所有弦世界面系统。
4. 状态空间上同调、局域算符上同调和模全微分的局域上同调作用于不同对象。
5. 恰当态正交和零范数结论依赖 $Q^\ddagger=Q$、定义域、边界条件和量子幂零性。
6. doublet/quartet 不贡献上同调需要收缩同伦、计数算符、完备分解和无遗漏零模等条件。
7. 取商后的物理内积正定和 S 矩阵幺正性需要额外定理，不由 $Q^2=0$ 单独保证。
8. $H^0(s)$ 只给出局域可观测量分类的核心结构，不自动覆盖非局域、边界和拓扑可观测量。
9. $H^{1,d}(s\mid d)$ 分类局域一致反常候选；非平凡类不表示具体理论的系数必然非零。
10. BRST 上同调不自动解决 Gribov copies、全局规范固定或全局反常。

## 常见误区

1. **所有闭态都是物理上不同的态。** 恰当闭态在上同调中等于零。
2. **$Q^2=0$ 所以 $Q=0$。** 在不定内积和分次候选空间中可有非零幂零 BRST 荷。
3. **所有零范数态都是 BRST-exact。** 这不由幂零性自动推出。
4. **取商后内积必然正定。** 还需要 quartet/no-ghost 等附加结果。
5. **物理态总是 $H^0(Q)$。** 弦世界面 ghost-number 扇区依约定和系统而变。
6. **状态空间上同调就是局域算符上同调。** 二者的作用对象和用途不同。
7. **存在非平凡反常上同调就表示理论一定有反常。** 还要计算具体系数。
8. **BRST 上同调就是机器学习降维。** 两者没有算法等价关系。

## 练习

1. 写出 $Z^n(Q)$、$B^n(Q)$ 和 $H^n(Q)$ 的定义。
2. 从 $Q^2=0$ 证明 $\operatorname{im}Q\subseteq\ker Q$。
3. 对本页有限维例子 $Qa=b,Qb=Qc=0$ 计算 $H^0(Q)$ 和 $H^1(Q)$。
4. 证明 $|\psi\rangle$ 与 $|\psi\rangle+Q|\chi\rangle$ 代表同一个上同调类。
5. 区分 $H^0(Q)$、$H^0(s)$ 和 $H^{1,d}(s\mid d)$ 的作用对象与用途。
6. 已知 $Qu=v,Qv=0$ 和 $\{Q,K\}=N$，证明 $N$ 的正本征值闭态是恰当态。
7. 在 $Q^\ddagger=Q$ 的假设下，证明恰当态与闭态正交，并说明证明所需条件。
8. 为什么非零恰当态可以有零范数？为什么这不能直接放在普通正定 Hilbert 空间中理解？
9. 比较 Yang-Mills 与弦世界面 BRST 上同调的共同结构和关键区别。
10. 解释 $s a_d^{\,1}+d a_{d-1}^{\,2}=0$ 与 $a_d^{\,1}=s b_d^{\,0}+d b_{d-1}^{\,1}$ 的意义。

## 答案与提示

1. $Z^n(Q)=\ker(Q:\mathcal H^n\to\mathcal H^{n+1})$；$B^n(Q)=\operatorname{im}(Q:\mathcal H^{n-1}\to\mathcal H^n)$；$H^n(Q)=Z^n(Q)/B^n(Q)$。
2. 若 $|\eta\rangle=Q|\chi\rangle$，则 $Q|\eta\rangle=Q^2|\chi\rangle=0$，所以每个像中的元素都在核中。
3. $a$ 不闭，所以 $H^0(Q)=0$。$b,c$ 都闭，但 $b=Qa$ 是恰当态；$c$ 不在像中，所以 $H^1(Q)=\operatorname{span}\{[c]\}$。
4. 两者之差是恰当态 $Q|\chi\rangle$。上同调按恰当态子空间取商，因此代表同一等价类。
5. $H^0(Q)$ 作用于候选态并提取物理态；$H^0(s)$ 作用于 ghost number 0 的局域表达式并分类局域观测量候选；$H^{1,d}(s\mid d)$ 在模去全微分后分类 ghost number 1 的局域一致反常候选。
6. 若 $Q|\psi\rangle=0$ 且 $N|\psi\rangle=n|\psi\rangle$、$n>0$，则 $n|\psi\rangle=\{Q,K\}|\psi\rangle=QK|\psi\rangle$，故 $|\psi\rangle=Q(K|\psi\rangle/n)$。
7. 对 $|\eta\rangle=Q|\chi\rangle$ 和 $Q|\psi\rangle=0$，有 $\langle\psi|\eta\rangle=\langle Q^\ddagger\psi|\chi\rangle=0$。需 $Q^\ddagger=Q$、共同定义域、边界项可控且量子 $Q^2=0$。
8. $\langle Q\chi|Q\chi\rangle=\langle\chi|Q^\ddagger Q|\chi\rangle=0$，但扩展候选空间具有不定内积，零范数不必推出向量为零；在正定空间中则会强烈限制非零自伴幂零 $Q$。
9. 共同点是 ghost-number 分次、幂零荷、闭/恰当等价类；Yang-Mills 固定内部规范群，世界面固定 Diff×Weyl（RNS 还含局部超对称），鬼系统和物理 ghost-number 扇区不同，世界面量子幂零性还要求中心荷反常消失。
10. 第一式是 Wess-Zumino 一致性条件的下降方程；第二式表示候选反常是 BRST-exact 加全微分的平凡类，通常可由局域反项移除。非平凡类只表示允许存在候选阻碍，不保证具体系数非零。

## 与其他概念的关系

- [[弦理论/物理学/BRST 对称性]] 提供幂零荷 $Q$、ghost number 和物理态条件；
- [[弦理论/数学/上同调]] 提供闭对象模去恰当对象的一般数学结构；
- [[弦理论/物理学/Faddeev-Popov 鬼场]] 提供鬼自由度和 ghost number 的路径积分来源；
- [[弦理论/数学/Hilbert 空间]] 帮助区分不定内积候选空间与最终物理态空间；
- [[弦理论/物理学/场的正则量子化]] 和 [[弦理论/物理学/Fock 空间]] 提供候选振子态空间；
- [[弦理论/物理学/Yang-Mills 理论]] 提供目标时空内部规范群的主要应用；
- [[弦理论/物理学/Maxwell 场量子化]] 提供 Abelian 物理极化的原型；
- [[弦理论/弦理论完整学习路线图]] 将本节点放在 BRST 对称性与量子反常之间。
- [[弦理论/物理学/量子反常]] 把 BRST 上同调作为局域一致反常候选的分类工具，并展开完整的反常总览、消除和边界。

## 参考资料

- Taichiro Kugo and Izumi Ojima, "Local Covariant Operator Formalism of Non-Abelian Gauge Theories and Quark Confinement Problem," *Progress of Theoretical Physics Supplement* 66 (1979), 1–130.
- Marc Henneaux and Claudio Teitelboim, *Quantization of Gauge Systems*, Princeton University Press, 1992.
- Glenn Barnich, Friedemann Brandt, and Marc Henneaux, "Local BRST Cohomology in Gauge Theories," *Physics Reports* 338 (2000), 439–569, arXiv:hep-th/0002245.
- Steven Weinberg, *The Quantum Theory of Fields, Vol. 2*, Cambridge University Press, 1996, Chapters 15–16.
- Michael E. Peskin and Daniel V. Schroeder, *An Introduction to Quantum Field Theory*, Westview Press, 1995, Chapter 16.
- Joseph Polchinski, *String Theory, Vol. 1*, Cambridge University Press, 1998, Chapters 3–4.
- Barton Zwiebach, *A First Course in String Theory*, 2nd ed., Cambridge University Press, 2009, Chapters 11–12.
