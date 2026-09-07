---
aliases: [Fock Space, Occupation Number Space, 福克空间]
english_name: Fock Space
tags: [物理学, 量子力学, 量子场论, 弦理论先修]
prerequisites:
  - "[[弦理论/数学/Hilbert 空间]]"
  - "[[弦理论/数学/张量积]]"
  - "[[弦理论/物理学/产生算符]]"
  - "[[弦理论/物理学/湮灭算符]]"
  - "[[弦理论/物理学/全同粒子]]"
used_by:
  - "[[弦理论/物理学/玻色子]]"
  - "[[弦理论/物理学/费米子]]"
  - "[[弦理论/物理学/场的正则量子化]]"
  - "[[弦理论/物理学/振子代数]]"
  - "[[弦理论/物理学/弦的量子态]]"
evidence_status: 教材事实
---

# Fock 空间（Fock Space）

## 一句话解释

Fock 空间是同时容纳零个、一个、两个乃至更多全同粒子状态的 Hilbert 空间，也可看成用各模式占据数组织量子态的空间。

## 为什么要学它

普通单粒子量子力学通常固定粒子数，但相对论量子过程允许粒子产生和湮灭。量子场论需要一个空间，把不同粒子数的状态放在同一数学框架中，Fock 空间正是这个框架。

弦量子化也使用 Fock 空间语言：从一个基态出发，用不同模式的产生算符构造激发态。不过弦的全部 Fock 态并不自动是物理态，还要施加 Virasoro、BRST、GSO 等相应约束或投影。

## 直观图景

想象一排可以存放振动量子的盒子，每个盒子代表一个单粒子模式，例如一个确定动量、偏振或弦振动编号。

一个状态可记录为：

$$
|n_1,n_2,n_3,\ldots\rangle.
$$

$n_r$ 表示第 $r$ 个模式中有多少个量子。例如：

$$
|2,0,1,\ldots\rangle
$$

表示第一个模式有两个量子，第二个模式为空，第三个模式有一个量子。

这个“盒子”比喻只适合说明占据数。模式不是空间中的实体容器，粒子也不一定能被贴上永久编号。

## 从单粒子 Hilbert 空间开始

设单粒子 Hilbert 空间为：

$$
\mathcal H_1.
$$

一个粒子的状态属于 $\mathcal H_1$。两个可区分粒子的状态通常属于张量积：

$$
\mathcal H_1\otimes\mathcal H_1.
$$

$n$ 个可区分粒子的状态属于：

$$
\mathcal H_1^{\otimes n}.
$$

但是同种粒子是全同粒子，交换两个粒子标签不能产生新的物理状态。因此还必须限制到对称或反对称子空间。

## 玻色与费米的多粒子子空间

$n$ 个全同玻色子的状态属于对称张量积：

$$
\operatorname{Sym}^n\mathcal H_1.
$$

$n$ 个全同费米子的状态属于反对称张量积：

$$
\wedge^n\mathcal H_1.
$$

符号含义：

- $\operatorname{Sym}^n$：取 $n$ 重张量积中的完全对称部分；
- $\wedge^n$：取完全反对称部分；
- $\mathcal H_1$：单粒子 Hilbert 空间；
- $n$：粒子数。

对称表示交换两个玻色子不改变状态；反对称表示交换两个费米子使状态多一个负号。

## 正式定义

玻色 Fock 空间定义为：

$$
\mathcal F_+(\mathcal H_1)
=
\bigoplus_{n=0}^{\infty}
\operatorname{Sym}^n\mathcal H_1.
$$

费米 Fock 空间定义为：

$$
\mathcal F_-(\mathcal H_1)
=
\bigoplus_{n=0}^{\infty}
\wedge^n\mathcal H_1.
$$

这里：

- $\mathcal F_+$：玻色 Fock 空间；
- $\mathcal F_-$：费米 Fock 空间；
- $\bigoplus$：Hilbert 空间直和；
- $n=0$ 的部分：零粒子子空间；
- $n=1$ 的部分：单粒子子空间；
- $n=2$ 的部分：双粒子子空间；
- 依此类推。

直和表示一个一般状态可以含有不同粒子数部分，但这些部分彼此正交。数学上还要求各部分范数平方之和有限。

## 零粒子子空间与真空

零粒子子空间按约定是一维的：

$$
\mathcal H_0\cong\mathbb C.
$$

选择一个归一化基向量记为真空：

$$
|0\rangle.
$$

对每个模式 $r$，真空满足：

$$
a_r|0\rangle=0.
$$

这表示没有该模式的粒子可被移去。真空不是零向量，因为：

$$
\langle0|0\rangle=1.
$$

零向量不能代表归一化物理状态，而真空是一个正常的量子态。

## 用产生算符构造状态

玻色多模式状态可写成：

$$
|n_1,n_2,\ldots\rangle
=
\prod_r
\frac{(a_r^\dagger)^{n_r}}{\sqrt{n_r!}}
|0\rangle.
$$

其中：

- $a_r^\dagger$：向模式 $r$ 加入一个玻色量子；
- $n_r$：模式 $r$ 的占据数；
- $n_r!$：保证归一化所需的阶乘；
- $\prod_r$：对所有被占据模式依次作用。

若只有有限个 $n_r$ 非零，乘积实际只包含有限项。完整无限维 Fock 空间还通过范数完备化包含适当极限。

## 玻色模式的代数

玻色产生和湮灭算符满足：

$$
[a_r,a_s^\dagger]=\delta_{rs}I,
$$

$$
[a_r,a_s]=0,
\qquad
[a_r^\dagger,a_s^\dagger]=0.
$$

模式数算符为：

$$
N_r=a_r^\dagger a_r.
$$

作用在占据数态上：

$$
N_r|\ldots,n_r,\ldots\rangle
=n_r|\ldots,n_r,\ldots\rangle.
$$

产生和湮灭作用分别为：

$$
a_r^\dagger|\ldots,n_r,\ldots\rangle
=
\sqrt{n_r+1}
|\ldots,n_r+1,\ldots\rangle,
$$

$$
a_r|\ldots,n_r,\ldots\rangle
=
\sqrt{n_r}
|\ldots,n_r-1,\ldots\rangle.
$$

## 费米模式的代数

费米产生和湮灭算符满足反对易关系：

$$
\{b_r,b_s^\dagger\}
=\delta_{rs}I,
$$

$$
\{b_r,b_s\}=0,
\qquad
\{b_r^\dagger,b_s^\dagger\}=0.
$$

令 $r=s$，可得：

$$
(b_r^\dagger)^2=0.
$$

所以每个费米模式的占据数只能是：

$$
n_r=0\quad\text{或}\quad1.
$$

这体现 Pauli 不相容原理。对费米态，产生算符的书写顺序会影响符号，因此必须固定模式排序约定。

## 总粒子数算符

在粒子数定义良好的 Fock 表示中，总粒子数算符为：

$$
N=\sum_r N_r.
$$

它满足：

$$
N|n_1,n_2,\ldots\rangle
=
\left(\sum_r n_r\right)
|n_1,n_2,\ldots\rangle.
$$

$\sum_r n_r$ 是总占据数。

若理论中的相互作用允许粒子产生或湮灭，Hamiltonian 不一定与 $N$ 对易，因此总粒子数不一定守恒。电荷、能量等其他量仍可能守恒。

## 一个双模式玻色例子

设有两个玻色模式 $a$ 和 $b$。状态：

$$
|2,1\rangle
=
\frac{(a^\dagger)^2b^\dagger}{\sqrt{2!}}|0,0\rangle.
$$

作用 $a$：

$$
a|2,1\rangle
=\sqrt2|1,1\rangle.
$$

作用 $b^\dagger$：

$$
b^\dagger|2,1\rangle
=\sqrt2|2,2\rangle.
$$

总粒子数为：

$$
N|2,1\rangle=3|2,1\rangle.
$$

## 为什么占据数表象适合全同粒子

若试图给三个全同玻色子编号为“甲、乙、丙”，再分别记录它们在哪个状态，会重复描述同一个物理情形。

占据数表象只回答：每个单粒子模式有几个粒子。它自动消除了无物理意义的粒子标签。

例如两个玻色子分别占据模式 $r,s$，状态由：

$$
a_r^\dagger a_s^\dagger|0\rangle
$$

表示。因为两个产生算符对易，交换它们的书写顺序不会产生新状态。

## 与普通张量积的关系

Fock 空间并不是“不使用张量积”。相反，每个固定粒子数子空间都来自单粒子空间的张量积，只是再进行对称化或反对称化。

结构可概括为：

$$
\text{单粒子空间}
\xrightarrow{\text{张量积}}
\text{多粒子空间}
\xrightarrow{\text{交换对称性}}
\text{玻色或费米子空间}
\xrightarrow{\text{直和}}
\text{Fock 空间}.
$$

因此理解 Hilbert 空间、张量积和全同粒子，是理解 Fock 空间的三条主线。

## 与量子场的关系

自由量子场可分解为许多独立模式。每个模式像一个量子谐振子，并有自己的 $a_r,a_r^\dagger$。

场算符可示意写成：

$$
\hat\phi(x)
=\sum_r
\left[
f_r(x)a_r+f_r^*(x)a_r^\dagger
\right].
$$

这里：

- $f_r(x)$：模式函数；
- $a_r$：移去模式 $r$ 的一个量子；
- $a_r^\dagger$：加入模式 $r$ 的一个量子；
- 星号：复共轭。

具体积分测度、归一化和指标取决于场的类型与时空背景。这条式子只展示标准模式展开结构。

## 与弦的关系

一条弦包含无穷多个振动模式。量子化后，可以从适当基态出发，用振子产生方向构造状态，例如开玻色弦中的示意状态：

$$
\alpha_{-n_1}^{\mu_1}
\alpha_{-n_2}^{\mu_2}
\cdots
|0;k\rangle.
$$

其中：

- $\alpha_{-n}^{\mu}$：负模式振子，通常扮演产生方向；
- $n>0$：模式编号；
- $\mu$：目标时空方向指标；
- $|0;k\rangle$：带中心动量 $k$ 的基态。

这些状态组成一个振子 Fock 空间，但不是每个形式状态都代表物理粒子。还要满足质量壳条件、Virasoro 约束；协变量子化中还要处理鬼与 BRST 上同调。超弦还涉及世界面费米振子和 GSO 投影。

## Fock 空间不总是唯一

有限自由度的正则量子力学中，在适当连续性条件下，不可约正则对易关系表示具有 Stone–von Neumann 唯一性。

量子场包含无穷多自由度，可能存在彼此幺正不等价的表示。因此不同背景、相、边界条件或观察者可能采用不同真空与 Fock 空间。

这在曲时空量子场论、热场论和自发对称破缺中很重要。不能把某一个模式分解下的粒子概念无条件当成绝对定义。

## Fock 空间的适用边界

Fock 空间最自然地描述可由某个真空附近的粒子激发组织的系统。强耦合、束缚态、拓扑扇区或非微扰背景中，原来的粒子基底可能不是最有效描述。

即使 Fock 空间仍可形式构造，真实 Hamiltonian 的本征态也可能是许多自由粒子数态的复杂叠加。

弦理论中还存在不同背景、D-brane 边界条件、闭弦与开弦扇区。每种扇区的振子模、真空和约束需分别定义。

## 具体例子：光子数态

单个电磁场模式可近似看作频率为 $\omega$ 的谐振子。数态 $|n\rangle$ 表示该模式含 $n$ 个光子，其能量为：

$$
E_n=\hbar\omega\left(n+\frac12\right).
$$

作用产生算符：

$$
a^\dagger|n\rangle=\sqrt{n+1}|n+1\rangle.
$$

作用湮灭算符：

$$
a|n\rangle=\sqrt n|n-1\rangle.
$$

这里的半个量子是模式零点能。在完整电磁场中，要对所有模式求和，形式上会出现发散，需要正规化和物理边界条件。

## 适用条件与事实边界

1. 标准 Fock 空间依赖选定的单粒子空间、模式分解和真空。
2. 玻色与费米空间分别取对称和反对称多粒子子空间。
3. 粒子数可变不等于任何相互作用都不受守恒律约束；允许过程由 Hamiltonian 和对称性决定。
4. 无穷自由度系统可能有幺正不等价表示，因此 Fock 空间不总是唯一。
5. 强相互作用理论的物理态不一定接近自由粒子数态。
6. 弦振子 Fock 空间包含非物理候选态，必须再施加世界面约束和投影。
7. 无穷模式的算符和与真空能要处理收敛、定义域和正规化问题。

## 常见误区

1. **Fock 空间只是一个固定粒子数的 Hilbert 空间。** 它是所有允许粒子数子空间的直和。
2. **真空等于零向量。** 真空是归一化态；零向量不能表示物理态。
3. **每个粒子都必须有永久编号。** 对全同粒子，占据数和交换对称性才是合适描述。
4. **玻色和费米 Fock 空间完全相同。** 它们分别使用对称与反对称张量积。
5. **费米单模式可以有任意占据数。** 标准费米模式只能取 $0$ 或 $1$。
6. **所有量子场背景共享唯一真空。** 无穷自由度下可能存在不等价表示。
7. **弦 Fock 空间中的每个态都是物理态。** 还需满足 Virasoro、BRST、GSO 等相应条件。

## 练习

1. 用自己的话说明 Fock 空间为何能描述可变粒子数。
2. 写出玻色和费米 Fock 空间的直和定义。
3. 对双模式玻色态 $|1,3\rangle$，计算 $a_1^\dagger$ 和 $a_2$ 的作用。
4. 为什么费米模式的占据数只能是 $0$ 或 $1$？
5. 说明真空态与零向量的区别。
6. 若状态为 $|2,0,4\rangle$，总数算符本征值是多少？
7. 为什么弦的振子 Fock 态还需要约束筛选？

## 答案与提示

1. 它把零粒子、单粒子、双粒子等子空间用 Hilbert 直和放在一起，所以一般状态可包含不同粒子数部分。
2. $\mathcal F_+=\bigoplus_{n=0}^{\infty}\operatorname{Sym}^n\mathcal H_1$；$\mathcal F_-=\bigoplus_{n=0}^{\infty}\wedge^n\mathcal H_1$。
3. $a_1^\dagger|1,3\rangle=\sqrt2|2,3\rangle$；$a_2|1,3\rangle=\sqrt3|1,2\rangle$。
4. 费米产生算符满足 $(b_r^\dagger)^2=0$，同一模式不能连续加入两个相同费米子。
5. 真空满足 $\langle0|0\rangle=1$，是物理态；零向量范数为零，不能归一化。
6. $2+0+4=6$。
7. 协变量子化会产生规范冗余和可能的负范数候选态，只有满足 Virasoro 或 BRST 等条件的等价类才代表物理态。

## 与其他概念的关系

- [[弦理论/数学/Hilbert 空间]] 提供状态空间、内积和完备性；
- [[弦理论/数学/张量积]] 构造固定粒子数的多体空间；
- [[弦理论/物理学/全同粒子]] 决定对称或反对称交换性质；
- [[弦理论/物理学/产生算符]] 与 [[弦理论/物理学/湮灭算符]] 改变模式占据数；
- [[弦理论/物理学/玻色子]] 使用对称 Fock 空间，[[弦理论/物理学/费米子]] 使用反对称 Fock 空间；
- [[弦理论/物理学/场的正则量子化]] 把自由场表示为模式 Fock 空间；
- [[弦理论/物理学/振子代数]] 和 [[弦理论/物理学/弦的量子态]] 把这一结构用于弦模式。

## 参考资料

- Michael E. Peskin and Daniel V. Schroeder, *An Introduction to Quantum Field Theory*, Westview Press, 1995.
- Steven Weinberg, *The Quantum Theory of Fields, Vol. 1*, Cambridge University Press, 1995.
- Brian C. Hall, *Quantum Theory for Mathematicians*, Springer, 2013.
- J. J. Sakurai and Jim Napolitano, *Modern Quantum Mechanics*, 3rd ed., Cambridge University Press, 2020.
- [David Tong, Quantum Field Theory](https://www.damtp.cam.ac.uk/user/tong/qft.html)
- Nicholas D. Birrell and Paul C. W. Davies, *Quantum Fields in Curved Space*, Cambridge University Press, 1982.
- Joseph Polchinski, *String Theory, Vol. 1*, Cambridge University Press, 1998.
- [David Tong, Lectures on String Theory](https://arxiv.org/abs/0908.0333)
