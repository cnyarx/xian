---
aliases: [Born Rule, Born Probability Rule]
english_name: Born Rule
tags: [物理学, 量子力学, 测量, 弦理论先修]
prerequisites:
  - "[[弦理论/物理学/概率]]"
  - "[[弦理论/物理学/量子态]]"
  - "[[弦理论/数学/Hilbert 空间]]"
  - "[[弦理论/数学/复数]]"
used_by:
  - "[[弦理论/物理学/量子算符]]"
  - "[[弦理论/物理学/量子测量]]"
  - "[[弦理论/物理学/期望值]]"
  - "[[弦理论/物理学/散射截面]]"
evidence_status: 教材事实
---

# Born 规则（Born Rule）

## 一句话解释

Born 规则说：量子态投影到某个测量结果上的复振幅，其绝对值平方就是得到该结果的概率。

## 为什么要学它

Schrödinger 方程告诉我们量子态怎样演化，但只有 Born 规则把抽象复向量连接到实验统计。没有这条规则，波函数和态向量无法给出探测器读数的概率。

弦理论计算的散射振幅、顶点算符关联函数和不同弦态之间的跃迁振幅，最终也必须通过量子概率规则与可观测概率或截面联系。

## 离散正交基中的规则

若归一化状态在正交归一基中展开：

$$
|\psi\rangle=
\sum_n c_n|n\rangle,
$$

其中：

$$
c_n=\langle n|\psi\rangle,
$$

那么测量得到结果 $n$ 的概率为：

$$
P(n)=|c_n|^2
=|\langle n|\psi\rangle|^2.
$$

符号含义：

- $|\psi\rangle$：测量前的归一化量子态；
- $|n\rangle$：与测量结果 $n$ 对应的归一化本征态；
- $c_n$：状态沿 $|n\rangle$ 方向的复概率振幅；
- $P(n)$：得到结果 $n$ 的普通非负概率；
- $|c_n|^2=c_n^*c_n$：复数振幅的绝对值平方。

归一化保证：

$$
\sum_nP(n)=
\sum_n|c_n|^2=1.
$$

## 为什么使用绝对值平方

复振幅 $c_n$ 可能含相位，不能直接当作概率，因为：

- 概率必须是实数；
- 概率不能为负；
- 互斥完备结果的概率总和必须为 $1$。

绝对值平方：

$$
|c_n|^2=c_n^*c_n
$$

自动给出非负实数，并与 Hilbert 空间范数一致。

Born 规则不是仅凭这些要求就能在所有可能理论中用初等方法唯一“证明”出来的普通定理。它是标准量子理论连接数学状态与实验概率的基本规则；在增加非情境性等假设后，Gleason 定理等结果能说明 Hilbert 空间中概率赋值为何具有 Born 形式。

## 投影算符形式

对应结果 $n$ 的一维投影算符为：

$$
P_n=|n\rangle\langle n|.
$$

Born 规则可写成：

$$
\Pr(n|\psi)
=
\langle\psi|P_n|\psi\rangle.
$$

因为：

$$
\langle\psi|P_n|\psi\rangle
=
\langle\psi|n\rangle
\langle n|\psi\rangle
=
|\langle n|\psi\rangle|^2.
$$

这条推导只是证明两种写法等价，不是在更基础的经典原理中推导 Born 规则本身。

## 退化测量结果

一个测量值可能对应多个正交态。若结果 $a$ 对应子空间投影 $P_a$，则：

$$
\Pr(a|\psi)
=
\langle\psi|P_a|\psi\rangle.
$$

若该子空间有正交归一基 $|a,r\rangle$，其中 $r$ 区分同一测量值下的不同态，则：

$$
P_a=
\sum_r|a,r\rangle\langle a,r|,
$$

所以：

$$
\Pr(a|\psi)
=
\sum_r|\langle a,r|\psi\rangle|^2.
$$

无法区分的同一测量结果要对相应子空间投影，而不是任意挑其中一个基向量。

## 一般自伴算符测量

若可观测量由自伴算符 $A$ 表示，离散谱分解为：

$$
A=
\sum_a aP_a,
$$

则：

- 可能测量值是 $a$；
- 得到 $a$ 的概率是 $\langle\psi|P_a|\psi\rangle$。

这里 $P_a$ 投影到本征值 $a$ 的整个本征子空间。算符的谱与投影结构决定“有哪些结果”，量子态决定“各结果有多大概率”。

## 混合态形式

若系统由密度算符 $\rho$ 描述，Born 规则推广为：

$$
\Pr(a)=
\operatorname{Tr}(\rho P_a).
$$

对纯态：

$$
\rho=|\psi\rangle\langle\psi|,
$$

有：

$$
\operatorname{Tr}(\rho P_a)
=
\langle\psi|P_a|\psi\rangle.
$$

所以纯态公式是密度算符公式的特例。

## 连续位置测量

在位置表象中：

$$
\psi(x)=\langle x|\psi\rangle.
$$

在区间 $[a,b]$ 找到粒子的概率是：

$$
P(a\le x\le b)
=
\int_a^b|\psi(x)|^2dx.
$$

因此概率密度为：

$$
p(x)=|\psi(x)|^2.
$$

归一化要求：

$$
\int_{-\infty}^{\infty}|\psi(x)|^2dx=1.
$$

$p(x)$ 是概率密度，不是恰好取到单点 $x$ 的有限概率。$p(x)dx$ 才近似表示极小区间中的概率。

## 连续动量测量

动量表象波函数为：

$$
\widetilde\psi(p)=\langle p|\psi\rangle.
$$

在动量区间 $[p_1,p_2]$ 测得动量的概率是：

$$
P(p_1\le p\le p_2)
=
\int_{p_1}^{p_2}
|\widetilde\psi(p)|^2dp.
$$

位置波函数和动量波函数通常由 Fourier 变换联系。它们是同一抽象量子态在不同测量基中的坐标表示。

## 整体相位为什么不影响概率

把状态乘整体相位：

$$
|\psi\rangle
\to e^{i\alpha}|\psi\rangle.
$$

振幅变成：

$$
\langle n|\psi\rangle
\to e^{i\alpha}\langle n|\psi\rangle.
$$

但概率：

$$
|e^{i\alpha}
\langle n|\psi\rangle|^2
=
|e^{i\alpha}|^2
|\langle n|\psi\rangle|^2
=
|\langle n|\psi\rangle|^2.
$$

因为 $|e^{i\alpha}|=1$，所以整体相位不改变任何 Born 概率。

## 相对相位为什么能改变概率

考虑：

$$
|\psi\rangle
=
\frac{|0\rangle+e^{i\varphi}|1\rangle}{\sqrt2}.
$$

在 $|0\rangle,|1\rangle$ 基中，两个结果概率都是 $1/2$，与 $\varphi$ 无关。

但定义：

$$
|+\rangle=
\frac{|0\rangle+|1\rangle}{\sqrt2},
\qquad
|-\rangle=
\frac{|0\rangle-|1\rangle}{\sqrt2},
$$

则：

$$
\langle+|\psi\rangle
=
\frac{1+e^{i\varphi}}{2}.
$$

所以：

$$
P(+)
=
\left|
\frac{1+e^{i\varphi}}{2}
\right|^2
=
\frac{1+\cos\varphi}{2}.
$$

相对相位 $\varphi$ 改变另一基中的概率，这就是干涉的数学核心。

## 可区分路径与不可区分路径

若同一个最终结果可由两条不可区分量子路径得到，其振幅先相加：

$$
\mathcal A=
\mathcal A_1+
\mathcal A_2.
$$

概率为：

$$
P=|\mathcal A|^2
=|\mathcal A_1|^2
+|\mathcal A_2|^2
+2\operatorname{Re}
(\mathcal A_1^*\mathcal A_2).
$$

最后一项是干涉项。

若路径在原则上被环境或记录可靠地区分，描述中要把路径标签纳入更大的量子态；忽略这些标签后，干涉可能减弱或消失。不能只凭“观察者有没有亲眼看见”判断是否干涉，关键是物理上是否留下可区分信息。

## 期望值与 Born 规则

若：

$$
A=\sum_a aP_a,
$$

则 Born 概率给出期望值：

$$
\langle A\rangle
=
\sum_a a\Pr(a)
=
\langle\psi|A|\psi\rangle.
$$

混合态中：

$$
\langle A\rangle
=
\operatorname{Tr}(\rho A).
$$

期望值是大量同样制备实验的平均，不保证等于单次测量值。

## 测量后的状态更新

对理想投影测量，若得到结果 $a$，常用 Lüders 规则把状态更新为：

$$
|\psi\rangle
\to
\frac{P_a|\psi\rangle}
{\sqrt{\langle\psi|P_a|\psi\rangle}},
$$

前提是该结果概率非零。

分母正是结果 $a$ 的概率平方根，用来重新归一化投影后的状态。

Born 规则给出结果概率；状态更新规则给出已知结果后后续实验应使用的条件状态。二者相关但不是同一句规则。

状态更新究竟代表物理塌缩、信息更新、分支选择还是其他机制，属于量子测量解释问题。不同解释必须给出相同的已验证实验概率，才与标准量子理论经验等价。

## 一般量子测量

并非所有测量都必须是理想投影测量。一般测量可由正算符值测度（POVM）元素 $E_k$ 描述：

$$
E_k\ge0,
\qquad
\sum_kE_k=I.
$$

结果 $k$ 的概率为：

$$
P(k)=
\operatorname{Tr}(\rho E_k).
$$

投影测量是 $E_k=P_k$ 且各投影互相正交时的特殊情况。

POVM 适合描述有噪声、非理想探测器或通过辅助系统间接完成的测量。若还要描述测量后的状态，需要指定比 $E_k$ 更多的信息，例如测量算符或量子仪器。

## 与散射振幅的关系

在散射理论中，先计算从初态到末态的复振幅：

$$
\mathcal A_{i\to f}.
$$

可观测跃迁概率、衰变率或散射截面与：

$$
|\mathcal A_{i\to f}|^2
$$

有关，同时还要乘相空间因子、通量因子并处理归一化与守恒 delta 函数。

因此不能简单说“截面就等于振幅平方”；振幅平方是核心概率权重，但完整可观测量还依赖实验运动学和规范化。

弦散射也遵守这一量子概率结构，只是振幅通过世界面路径积分或共形场论关联函数计算。

## 具体例子：三结果测量

设：

$$
|\psi\rangle
=
\frac{1}{3}|1\rangle
+
\frac{2}{3}|2\rangle
+
\frac{2i}{3}|3\rangle.
$$

归一化检查：

$$
\left|\frac13\right|^2
+
\left|\frac23\right|^2
+
\left|\frac{2i}{3}\right|^2
=
\frac19+
\frac49+
\frac49=1.
$$

在该基中测量时：

$$
P(1)=\frac19,
\qquad
P(2)=\frac49,
\qquad
P(3)=\frac49.
$$

第三个振幅含 $i$，但其概率仍是非负实数 $4/9$。这个相位在当前基的单项概率中消失，却可能在与其他分量重新组合的测量基中产生干涉。

## 适用条件与事实边界

1. Born 规则是标准量子理论的基本经验规则，不是从经典概率或 Schrödinger 方程单独推出的普通代数结论。
2. 规则要求明确量子态、测量描述和归一化。
3. 投影公式适用于理想投影测量；一般实验可能需要 POVM。
4. 连续谱使用概率密度和区间积分，不能把 $|\psi(x)|^2$ 误当成单点有限概率。
5. 概率预测针对同样制备实验的统计；标准理论一般不预测单次随机结果具体是哪一个。
6. 关于 Born 规则为什么成立的决策论、典型性、频率或多世界推导，依赖额外解释框架和假设，不能冒充无假设的普遍证明。

## 常见误区

1. **振幅就是概率。** 振幅可为复数，概率是其绝对值平方。
2. **把各条量子路径的概率直接相加总是正确。** 不可区分路径要先加振幅，因此可能干涉。
3. **整体相位和相对相位都不影响概率。** 整体相位不影响；相对相位可改变另一基中的概率。
4. **$|\psi(x)|^2$ 是恰好位于单点 $x$ 的概率。** 它是概率密度，区间概率需要积分。
5. **期望值是最可能测得的值。** 它是概率加权平均，不一定属于单次可能结果。
6. **Born 规则同时完整解释了测量为何只有一个结果。** 它给出统计概率，但测量问题的本体解释仍有争论。
7. **弦散射截面直接等于世界面振幅的绝对值平方。** 还需要运动学、相空间、通量与归一化因子。

## 练习

1. 若 $|\psi\rangle=(3|0\rangle+4i|1\rangle)/5$，求在该基中两个结果的概率。
2. 证明 $P_n=|n\rangle\langle n|$ 时，$\langle\psi|P_n|\psi\rangle=|\langle n|\psi\rangle|^2$。
3. 一个归一化波函数在区间 $[0,1]$ 上满足 $|\psi(x)|^2=2x$，求在 $[0,1/2]$ 找到粒子的概率。
4. 为什么整体相位 $e^{i\alpha}$ 不改变 Born 概率？
5. 当两个过程最终状态不可区分时，为什么不能直接把 $|\mathcal A_1|^2$ 和 $|\mathcal A_2|^2$ 相加？
6. 密度算符 $\rho$ 和 POVM 元素 $E_k$ 给出的概率公式是什么？
7. 为什么“Born 规则已被 Schrödinger 方程严格证明”这一说法不准确？

## 答案与提示

1. $P(0)=9/25$，$P(1)=16/25$；两者相加为 $1$。
2. 代入投影：$\langle\psi|n\rangle\langle n|\psi\rangle$，前一因子是后一因子的复共轭。
3. $\int_0^{1/2}2x\,dx=[x^2]_0^{1/2}=1/4$。
4. 因为 $|e^{i\alpha}|^2=1$，相位与复共轭相乘后抵消。
5. 总振幅是 $\mathcal A_1+\mathcal A_2$，平方后还有 $2\operatorname{Re}(\mathcal A_1^*\mathcal A_2)$ 干涉项。
6. $P(k)=\operatorname{Tr}(\rho E_k)$；投影测量时 $E_k=P_k$。
7. Schrödinger 方程规定状态的酉时间演化，Born 规则额外规定如何从状态得到实验概率。

## 与其他概念的关系

- [[弦理论/物理学/量子态]] 提供被投影的状态向量或密度算符；
- [[弦理论/数学/Hilbert 空间]] 的内积与投影使概率表达具有几何形式；
- [[弦理论/物理学/概率]] 给出 Born 结果必须满足的非负性、归一化和统计规则；
- [[弦理论/物理学/量子算符]] 的谱投影指定可能测量结果；
- [[弦理论/物理学/期望值]] 按 Born 概率对测量值加权；
- [[弦理论/物理学/量子测量]] 进一步讨论测量装置、POVM 和状态更新；
- [[弦理论/物理学/弦散射振幅]] 的绝对值平方进入可观测散射概率与截面。

## 参考资料

- Max Born, “Zur Quantenmechanik der Stoßvorgänge,” *Zeitschrift für Physik* **37** (1926), 863–867.
- [Nobel Prize, Max Born – Facts and Nobel Lecture](https://www.nobelprize.org/prizes/physics/1954/born/facts/)
- J. J. Sakurai and Jim Napolitano, *Modern Quantum Mechanics*, 3rd ed., Cambridge University Press, 2020.
- Barton Zwiebach, *Mastering Quantum Mechanics*, MIT Press, 2022.
- Claude Cohen-Tannoudji, Bernard Diu and Franck Laloë, *Quantum Mechanics*, Wiley.
- Andrew M. Gleason, “Measures on the Closed Subspaces of a Hilbert Space,” *Journal of Mathematics and Mechanics* **6** (1957), 885–893.
- Michael A. Nielsen and Isaac L. Chuang, *Quantum Computation and Quantum Information*, Cambridge University Press, 2010.
