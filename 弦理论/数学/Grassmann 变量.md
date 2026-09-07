---
aliases: [Grassmann Variable, Anticommuting Variable, 格拉斯曼变量]
english_name: Grassmann Variable
tags: [数学, 代数, 量子场论, 超弦理论先修]
prerequisites:
  - "[[弦理论/数学/复数]]"
  - "[[弦理论/数学/多项式]]"
  - "[[弦理论/数学/矩阵]]"
  - "[[弦理论/物理学/费米子]]"
used_by:
  - "[[弦理论/物理学/费米场路径积分]]"
  - "[[弦理论/物理学/鬼场]]"
  - "[[弦理论/物理学/BRST 对称性]]"
  - "[[弦理论/物理学/世界面费米子]]"
  - "[[弦理论/物理学/RNS 超弦理论]]"
evidence_status: 教材事实
---

# Grassmann 变量（Grassmann Variable）

## 一句话解释

Grassmann 变量是一种彼此交换时会变号的代数变量，因此每个奇变量的平方为零；它是描述费米场、鬼场和超对称的标准数学语言。

## 为什么要学它

普通数相乘满足 $xy=yx$，但费米产生算符和费米场使用反对易关系。为了在路径积分中把费米自由度写成类似“函数变量”的形式，需要引入 Grassmann 变量。

RNS 超弦含有世界面费米场，规范固定又引入鬼场。它们的路径积分、行列式和 BRST 结构都依赖 Grassmann 代数。

## 直观图景

把两个 Grassmann 变量的顺序想成有方向的拼接：交换顺序会翻转方向，因此多一个负号：

$$
\theta_1\theta_2
=-\theta_2\theta_1.
$$

这个比喻接近向量外积的反对称性，但 Grassmann 变量不是普通空间向量，也不是具有某个极小数值的实数。

它们首先是抽象代数生成元。我们规定乘法规则，再研究由这些规则生成的有限多项式。

## 正式定义

一组 Grassmann 奇生成元 $\theta_i$ 满足：

$$
\theta_i\theta_j
=-\theta_j\theta_i.
$$

等价地，它们的反对易子为零：

$$
\{\theta_i,\theta_j\}
=\theta_i\theta_j+\theta_j\theta_i
=0.
$$

令 $i=j$：

$$
\theta_i^2=-\theta_i^2.
$$

在特征不为 $2$ 的数域上，两边相加得到：

$$
2\theta_i^2=0,
$$

所以：

$$
\theta_i^2=0.
$$

这里通常以实数或复数为系数域，因此 $2\ne0$。

## 平方为零不等于变量为零

对普通实数，$x^2=0$ 推出 $x=0$。Grassmann 变量不是普通实数，所以可以有：

$$
\theta\ne0,
\qquad
\theta^2=0.
$$

这种非零但某次幂后变零的元素称为幂零元素。

$\theta$ 不是一个可在数轴上标出的数值。它的意义来自代数运算规则以及它在物理表达式中的系数。

## 一个变量的 Grassmann 代数

若只有一个生成元 $\theta$，任何多项式都在一次项后终止：

$$
f(\theta)=a+b\theta.
$$

因为：

$$
\theta^2=\theta^3=\cdots=0.
$$

$a$ 和 $b$ 可以是普通实数、复数，或与 $\theta$ 有规定交换性质的系数。

因此对 Grassmann 变量的 Taylor 展开是有限的，不需要无限级数。

## 两个变量的 Grassmann 代数

有 $\theta_1,\theta_2$ 时，一般元素可写成：

$$
f
=a+b_1\theta_1+b_2\theta_2+c\theta_1\theta_2.
$$

不存在 $\theta_1^2$ 或 $\theta_2^2$ 项。并且：

$$
\theta_2\theta_1
=-\theta_1\theta_2.
$$

两个生成元的基可选为：

$$
1,\theta_1,\theta_2,\theta_1\theta_2.
$$

因此维数为 $2^2=4$。

一般有 $N$ 个 Grassmann 生成元时，代数维数为：

$$
2^N.
$$

原因是每个生成元在一个有序单项式中只能选择“不出现”或“出现一次”。

## 偶元素与奇元素

含偶数个 Grassmann 生成元乘积的项称为 Grassmann 偶元素；含奇数个的项称为 Grassmann 奇元素。

例如：

- $1$、$\theta_1\theta_2$ 是偶的；
- $\theta_1$、$\theta_1\theta_2\theta_3$ 是奇的。

奇元素彼此交换通常带负号。偶元素与普通复数以及其他齐次元素通常按规定对易。

用奇偶度 $|A|\in\{0,1\}$ 表示，可写分次交换规则：

$$
AB=(-1)^{|A||B|}BA
$$

对齐次超交换元素成立。

## 与外代数的关系

设向量空间 $V$ 的基为 $e_i$。外代数使用外积：

$$
e_i\wedge e_j
=-e_j\wedge e_i.
$$

Grassmann 代数可理解为由生成空间 $V$ 构造的外代数：

$$
\Lambda(V)
=
\bigoplus_{p=0}^{N}
\Lambda^p(V).
$$

因此 Grassmann 变量与微分形式的反对称楔积使用同类代数结构。

但在物理中，Grassmann 变量还带有场、时空、复共轭和积分规则，不能只把它们当作普通微分形式。

## 指数函数为何会截断

因为 $\theta^2=0$：

$$
e^\theta
=1+\theta+\frac{\theta^2}{2!}+\cdots
=1+\theta.
$$

若 $\eta$ 与 $\theta$ 都是奇变量，则 $\eta\theta$ 是偶元素，而且：

$$
(\eta\theta)^2=0.
$$

因此：

$$
e^{\eta\theta}
=1+\eta\theta.
$$

有许多不同变量时，指数仍因每个变量最多出现一次而在有限阶终止。

## 左导数

对 Grassmann 奇变量，可定义左导数：

$$
\frac{\partial}{\partial\theta}\theta=1.
$$

左导数的分次乘积法则为：

$$
\frac{\partial}{\partial\theta}(AB)
=
\frac{\partial A}{\partial\theta}B
+(-1)^{|A|}A
\frac{\partial B}{\partial\theta}
$$

当导数本身是奇操作，且 $A$ 为齐次元素时成立。

例如：

$$
\frac{\partial}{\partial\theta_1}
(\theta_1\theta_2)
=\theta_2.
$$

而：

$$
\frac{\partial}{\partial\theta_2}
(\theta_1\theta_2)
=-\theta_1.
$$

第二式的负号来自导数越过奇变量 $\theta_1$。

## 左导数与右导数

也可以定义右导数。由于奇变量交换会变号，左、右导数对奇表达式可能相差符号。

教材和论文可能使用不同约定，因此计算前必须说明导数从哪一侧作用。

本文件默认使用左导数。不能在同一推导中无说明地混用两种约定。

## Berezin 积分

Grassmann 积分也称 Berezin 积分。对一个变量定义：

$$
\int d\theta\,1=0,
$$

$$
\int d\theta\,\theta=1.
$$

若：

$$
f(\theta)=a+b\theta,
$$

则：

$$
\int d\theta\,f(\theta)=b.
$$

积分提取 $\theta$ 的最高次系数，因此在一个变量情形中与求导作用相同：

$$
\int d\theta\,f(\theta)
=
\frac{\partial f}{\partial\theta}.
$$

这不是普通面积积分。$d\theta$ 也按 Grassmann 奇对象处理，顺序会影响符号。

## 多变量积分与顺序

对两个变量，约定：

$$
\int d\theta_2\,d\theta_1\,
\theta_1\theta_2=1.
$$

积分从右侧最邻近变量开始理解。若交换积分测度顺序：

$$
d\theta_1d\theta_2
=-d\theta_2d\theta_1,
$$

结果会改变符号。

因此必须同时固定单项式顺序和积分测度顺序。

## 平移不变性

令 $\eta$ 为与 $\theta$ 独立的 Grassmann 奇常数。Berezin 积分满足：

$$
\int d\theta\,f(\theta+\eta)
=
\int d\theta\,f(\theta).
$$

若 $f(\theta)=a+b\theta$，则：

$$
f(\theta+\eta)=a+b\eta+b\theta.
$$

积分只提取 $\theta$ 的系数 $b$，所以平移前后相同。

这与普通积分的平移不变性相似，是路径积分构造的重要性质。

## 一个 Grassmann Gaussian 积分

取两个独立奇变量 $\bar\psi,\psi$ 和普通非零数 $A$。由于指数截断：

$$
e^{-\bar\psi A\psi}
=1-\bar\psi A\psi.
$$

采用约定：

$$
\int d\bar\psi\,d\psi\,
\bar\psi\psi=-1
$$

或等价的另一组测度顺序约定时，可以得到标准结果：

$$
\int d\bar\psi\,d\psi\,
e^{-\bar\psi A\psi}
=A.
$$

不同教材可能把变量与测度顺序排成另一形式；只要全程一致，结果的物理内容相同。

关键结构是：复 Grassmann Gaussian 积分产生 $A$，而普通实数 Gaussian 积分产生与 $A^{-1/2}$ 成比例的结果。

## 多变量 Gaussian 积分与行列式

对 $N$ 对独立复 Grassmann 变量：

$$
\bar\psi_i,\psi_j,
$$

以及普通可逆矩阵 $A$，标准约定下：

$$
\int
\prod_i d\bar\psi_i\,d\psi_i\,
\exp\left(-\bar\psi_iA_{ij}\psi_j\right)
=\det A.
$$

这里重复指标 $i,j$ 求和。

相比之下，普通玻色 Gaussian 积分形式上给出：

$$
\int d^n x\,
\exp\left(-\frac12x^TAx\right)
\propto(\det A)^{-1/2}
$$

在 $A$ 正定等收敛条件下成立。

费米积分给行列式在分子，玻色积分给行列式的负幂。这种差别对量子修正和超对称抵消非常重要。

## 实 Grassmann 二次型与 Pfaffian

对 $2N$ 个实 Grassmann 变量 $\theta_i$ 和反对称矩阵 $A$：

$$
\int d^{2N}\theta\,
\exp\left(
-\frac12\theta_iA_{ij}\theta_j
\right)
\propto\operatorname{Pf}(A).
$$

$\operatorname{Pf}(A)$ 是 Pfaffian，并满足：

$$
\operatorname{Pf}(A)^2=
\det A.
$$

比例号和可能的符号依赖积分测度排序约定。高级计算中必须固定取向和相位，不能只记平方关系。

## 变量变换的 Jacobian

普通变量变换 $x'=Mx$ 时，积分测度通常乘 $\det M$。

Grassmann 变量的 Berezin 测度具有相反变换规律。若：

$$
\theta'=M\theta,
$$

则：

$$
d^N\theta'
=(\det M)^{-1}d^N\theta
$$

在固定顺序约定下成立。

一个变量即可看出：若 $\theta'=a\theta$，要保持：

$$
\int d\theta'\,\theta'=1,
$$

必须有：

$$
d\theta'=a^{-1}d\theta.
$$

这与普通积分测度正好相反。

## 与费米产生算符的关系

费米产生算符满足：

$$
\{b_r^\dagger,b_s^\dagger\}=0,
$$

所以：

$$
(b_r^\dagger)^2=0.
$$

Grassmann 变量也满足：

$$
\theta_r\theta_s=-\theta_s\theta_r,
\qquad
\theta_r^2=0.
$$

两者代数相似，但对象不同：

- $b_r^\dagger$ 是作用在 Fock 空间上的算符；
- $\theta_r$ 是 Grassmann 代数元素；
- 路径积分用 Grassmann 数场来编码费米算符理论的振幅。

不能直接说 Grassmann 变量就是费米粒子本身。

## Grassmann 值费米场

经典玻色场通常取普通实数或复数值。经典费米场为了在量子化后得到正确反对易结构，形式上取 Grassmann 奇值：

$$
\psi(x)\psi(y)
=-\psi(y)\psi(x).
$$

Dirac 作用量：

$$
S=\int d^Dx\,
\bar\psi(i\gamma^\mu\partial_\mu-m)\psi
$$

整体是 Grassmann 偶的，因此可进入指数 $e^{iS}$。

虽然 $\psi$ 是奇的，双线性 $\bar\psi\psi$ 是偶的，可以与普通数值物理量组合。

## 鬼场为何也用 Grassmann 变量

规范固定会产生 Faddeev–Popov 行列式。可用 Grassmann 奇标量场 $c,\bar c$ 表示该行列式：

$$
\det M
=
\int D\bar c\,Dc\,
\exp\left(-\bar cMc\right)
$$

以 Euclidean 符号的示意形式书写。

鬼场是 Grassmann 奇的，但在 Yang–Mills 理论中可具有 Lorentz 标量形式。它们不是外部可观测的普通费米粒子，而是处理规范冗余的辅助场。

弦世界面的 $bc$ 鬼系统对 BRST 对称性和中心荷相消至关重要。

## 与超对称的关系

超对称把玻色自由度和费米自由度联系起来。超空间除了普通坐标 $x^\mu$，还引入 Grassmann 奇坐标：

$$
\theta^\alpha,
\qquad
\bar\theta^{\dot\alpha}.
$$

超场在这些奇坐标上的展开会自动截断，因为 Grassmann 变量的幂达到一定次数后为零。

超坐标不是额外普通空间维度。它们属于带 $\mathbb Z_2$ 分次的超几何结构。

## 与 RNS 超弦的关系

RNS 世界面作用量包含世界面费米场 $\psi^\mu$。在路径积分中，这些场取 Grassmann 奇值。

Ramond 和 Neveu–Schwarz 边界条件改变费米场的模式编号。量子化后，模式满足反对易关系；Ramond 零模形成目标时空 Clifford 代数。

规范固定还引入 Grassmann 奇 $bc$ 鬼和超共形规范固定相关的 $\beta\gamma$ 系统。后者具有不同统计与共形权重，需要单独分析。

## 具体例子

设：

$$
f(\theta_1,\theta_2)
=3+2\theta_1-5\theta_2
+7\theta_1\theta_2.
$$

左导数为：

$$
\frac{\partial f}{\partial\theta_1}
=2+7\theta_2.
$$

以及：

$$
\frac{\partial f}{\partial\theta_2}
=-5-7\theta_1.
$$

若采用：

$$
\int d\theta_2d\theta_1\,
\theta_1\theta_2=1,
$$

则：

$$
\int d\theta_2d\theta_1\,
f
=7.
$$

积分只提取与测度顺序匹配的最高阶项系数。

## 适用条件与事实边界

1. Grassmann 变量是反对易代数生成元，不是普通实数、复数或可直接测量的数值。
2. $\theta^2=0$ 不推出 $\theta=0$，因为代数含有幂零元素。
3. 左导数、右导数和积分测度顺序会影响符号，必须明确约定。
4. Grassmann Gaussian 积分产生行列式，但整体符号和归一化依赖变量及测度排序。
5. 实反对称二次型通常产生 Pfaffian，其相位和符号在量子场论中可能具有物理重要性。
6. Grassmann 值场用于编码费米统计，但 Grassmann 变量本身不是费米粒子。
7. 鬼场使用 Grassmann 统计不代表它们是可观测物质费米子。
8. 超空间的 Grassmann 坐标不是额外普通时空坐标。

## 常见误区

1. **Grassmann 变量是非常小的普通数。** 它没有普通数轴大小，定义来自反对易代数。
2. **$\theta^2=0$ 所以 $\theta=0$。** 该推理只适用于没有非零幂零元的普通数域。
3. **Grassmann 变量彼此交换。** 两个奇变量交换通常多一个负号。
4. **Grassmann 积分计算曲线下面积。** Berezin 积分是提取最高阶系数的代数操作。
5. **积分变量顺序不重要。** 交换奇测度顺序会改变符号。
6. **Grassmann 变量就是费米产生算符。** 二者代数相似，但一个是代数元素，一个是 Hilbert 空间算符。
7. **鬼场是可在探测器中观察的反常粒子。** 它们是规范固定辅助自由度，不属于外部物理态。

## 练习

1. 从 $\theta_i\theta_j=-\theta_j\theta_i$ 推出 $\theta_i^2=0$。
2. 写出两个 Grassmann 生成元的一般多项式，并说明为何只有四个基单项式。
3. 计算 $\partial(\theta_1\theta_2)/\partial\theta_2$，采用左导数。
4. 若 $f(\theta)=4-3\theta$，计算 $\int d\theta\,f(\theta)$。
5. 展开 $e^{a\theta_1\theta_2}$。
6. 普通玻色 Gaussian 积分与复 Grassmann Gaussian 积分分别产生怎样的行列式幂次？
7. 为什么 Grassmann 奇鬼场不等于可观测费米粒子？

## 答案与提示

1. 令 $i=j$ 得 $\theta_i^2=-\theta_i^2$，在特征不为 $2$ 的数域上推出 $2\theta_i^2=0$，故平方为零。
2. $a+b_1\theta_1+b_2\theta_2+c\theta_1\theta_2$；每个变量最多出现一次，反序项可化为有序项。
3. 导数越过奇变量 $\theta_1$ 带负号，结果为 $-\theta_1$。
4. 积分提取 $\theta$ 系数，结果为 $-3$。
5. 因 $(\theta_1\theta_2)^2=0$，所以 $e^{a\theta_1\theta_2}=1+a\theta_1\theta_2$。
6. 正定实玻色积分与 $(\det A)^{-1/2}$ 成比例；复 Grassmann 积分给 $\det A$。
7. 统计和 Lorentz 表示是不同属性；鬼场用于表示规范固定行列式，并被物理态条件排除。

## 与其他概念的关系

- [[弦理论/物理学/费米子]] 的产生算符和场使用反对易结构；
- [[弦理论/数学/外代数]] 与 Grassmann 代数共享反对称乘法；
- [[弦理论/数学/微分形式]] 使用楔积形成分次反交换代数；
- [[弦理论/物理学/费米场路径积分]] 用 Berezin 积分产生行列式；
- [[弦理论/物理学/鬼场]] 用 Grassmann 场表示规范固定行列式；
- [[弦理论/物理学/BRST 对称性]] 依赖鬼数和 Grassmann 奇生成元；
- [[弦理论/物理学/世界面费米子]] 在 RNS 路径积分中取 Grassmann 奇值；
- [[弦理论/物理学/RNS 超弦理论]] 同时使用世界面费米场和鬼系统。

## 参考资料

- Felix A. Berezin, *The Method of Second Quantization*, Academic Press, 1966.
- Bryce DeWitt, *Supermanifolds*, 2nd ed., Cambridge University Press, 1992.
- Michael E. Peskin and Daniel V. Schroeder, *An Introduction to Quantum Field Theory*, Westview Press, 1995.
- Steven Weinberg, *The Quantum Theory of Fields, Vol. 1*, Cambridge University Press, 1995.
- Pierre Deligne et al., eds., *Quantum Fields and Strings: A Course for Mathematicians*, American Mathematical Society, 1999.
- [David Tong, Quantum Field Theory](https://www.damtp.cam.ac.uk/user/tong/qft.html)
- Joseph Polchinski, *String Theory, Vol. 1*, Cambridge University Press, 1998.
- [David Tong, Lectures on String Theory](https://arxiv.org/abs/0908.0333)
