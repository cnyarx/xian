---
aliases:
  - Wick's Theorem
  - Wick Expansion
english_name: Wick's Theorem
tags:
  - 物理学
  - 量子场论
  - 微扰论
  - 弦理论先修
prerequisites:
  - "[[弦理论/物理学/时序乘积]]"
  - "[[弦理论/物理学/传播子]]"
  - "[[弦理论/物理学/产生算符]]"
  - "[[弦理论/物理学/湮灭算符]]"
  - "[[弦理论/物理学/Fock 空间]]"
  - "[[弦理论/物理学/Dirac 场]]"
  - "[[弦理论/物理学/微扰论]]"
used_by:
  - "[[弦理论/物理学/生成泛函]]"
  - "[[弦理论/物理学/Feynman 图]]"
  - "[[弦理论/物理学/圈展开]]"
  - "[[弦理论/物理学/正规序]]"
  - "[[弦理论/物理学/算符乘积展开]]"
  - "[[弦理论/物理学/弦散射振幅]]"
evidence_status: 教材事实
---

# Wick 定理（Wick's Theorem）

## 一句话解释

Wick 定理把自由场的时间有序算符乘积系统地改写为正规序乘积与所有可能收缩之和，而每条收缩就是一个自由传播子。

## 为什么要学它

Dyson 级数会产生许多时间有序场算符乘积，例如：

$$
T\{\phi(x_1)\phi(x_2)\phi(x_3)\phi(x_4)\}.
$$

直接展开每个场中的产生与湮灭算符，项数会迅速增长。Wick 定理把这类计算压缩为组合规则：

1. 没有收缩的项给正规序乘积；
2. 每做一条收缩就放入一个传播子；
3. 对所有不相交收缩方式求和；
4. 费米场还需乘置换符号。

它是从算符微扰论通向 [[弦理论/物理学/Feynman 图]] 的桥梁。图中的内线对应收缩，顶点来自相互作用，外部未收缩场对应外线。

在弦世界面自由场论中，同样的 Gaussian/Wick 结构把顶点算符相关函数化为二点函数的组合。

## 本篇约定

- $T\{\cdots\}$ 表示 [[弦理论/物理学/时序乘积]]；
- $:\cdots:$ 表示相对于选定自由真空的正规序；
- 讨论的标准 Wick 定理首先适用于自由场或 Gaussian 理论；
- 标量 Feynman 传播子定义为：

$$
\Delta_F(x-y)
=\langle0|T\{\phi(x)\phi(y)\}|0\rangle;
$$

- 对费米场，交换费米奇算符必须记录负号；
- 相互作用理论的微扰展开以自由场的 Wick 定理为基础，不能把完整相互作用场无条件当作 Gaussian 场。

## 每个符号是什么意思

- $\phi(x)$：自由实标量场；
- $\psi(x)$、$\bar\psi(x)$：自由 Dirac 场及其 Dirac 共轭；
- $T$：时序算符；
- $:\cdots:$：正规序；
- $\operatorname{Contr}(A,B)$：$A$ 与 $B$ 的收缩；
- $\Delta_F(x-y)$：标量 Feynman 传播子；
- $S_F(x-y)$：Dirac Feynman 传播子；
- $P$：为达到某一费米配对所需的奇算符置换次数；
- $(-1)^P$：费米置换符号；
- Gaussian 理论：作用量至多为场的二次型，所有高阶关联由二点函数决定。

## 什么是正规序

把自由玻色场分成正频和负频部分：

$$
\phi(x)=\phi^+(x)+\phi^-(x),
$$

其中：

- $\phi^+(x)$ 含湮灭算符；
- $\phi^-(x)$ 含产生算符。

正规序把所有产生部分移到所有湮灭部分左边。例如：

$$
:\phi(x)\phi(y):
$$

表示先按产生、湮灭类型重新排列，而不是按时间排列。

相对于自由真空：

$$
\langle0|:\phi(x_1)\cdots\phi(x_n):|0\rangle=0,
\qquad n>0,
$$

对不含独立 $c$ 数项的自由场单项式成立。该结论不能直接推广到一般状态、正规序指数或含零模的算符。

对费米场做正规序时，每交换一对费米奇算符还要附加负号。

## 什么是收缩

两个自由场算符的收缩定义为它们的时序乘积减去正规序乘积：

$$
\boxed{
\operatorname{Contr}(A,B)
\equiv T\{AB\}-:AB:
}.
$$

对自由实标量场：

$$
\operatorname{Contr}\!\bigl(\phi(x),\phi(y)\bigr)
=\Delta_F(x-y)I.
$$

收缩是 Fock 空间上的 $c$ 数操作，标量收缩可从其他算符之间移出。Dirac 收缩仍带旋量指标，因此后续矩阵乘法和指标次序必须保留。

对自由 Dirac 场：

$$
\operatorname{Contr}\!\bigl(\psi_\alpha(x),\bar\psi_\beta(y)\bigr)
=(S_F(x-y))_{\alpha\beta},
$$

$$
\operatorname{Contr}\!\bigl(\bar\psi_\alpha(x),\psi_\beta(y)\bigr)
=-(S_F(y-x))_{\beta\alpha}.
$$

同种带电费米场中：

$$
\operatorname{Contr}\!\bigl(\psi(x),\psi(y)\bigr)=0,
$$

$$
\operatorname{Contr}\!\bigl(\bar\psi(x),\bar\psi(y)\bigr)=0,
$$

因为对应真空二点函数不匹配粒子—反粒子结构。

## 两个场的 Wick 定理

两个自由标量场的情形就是收缩定义本身：

$$
\boxed{
T\{\phi_1\phi_2\}
=:\phi_1\phi_2:
+\operatorname{Contr}\!\bigl(\phi_1,\phi_2\bigr)
},
$$

其中 $\phi_i=\phi(x_i)$。

取真空期望值，正规序项消失：

$$
\langle0|T\{\phi_1\phi_2\}|0\rangle
=\Delta_F(x_1-x_2).
$$

## 三个自由标量场

Wick 展开为：

$$
\begin{aligned}
T\{\phi_1\phi_2\phi_3\}
={}&:\phi_1\phi_2\phi_3:
+\operatorname{Contr}\!\bigl(\phi_1,\phi_2\bigr):\phi_3:\\
&+\operatorname{Contr}\!\bigl(\phi_1,\phi_3\bigr):\phi_2:\\
&+\operatorname{Contr}\!\bigl(\phi_2,\phi_3\bigr):\phi_1:.
\end{aligned}
$$

更简洁地说：正规序三场项，加上所有单收缩项。

不存在完全收缩，因为三个对象无法两两配完。因此自由实标量场的奇数点真空相关函数为零：

$$
\langle0|T\{\phi_1\phi_2\phi_3\}|0\rangle=0.
$$

这个结论依赖零均值 Gaussian 真空。若背景中 $\langle\phi\rangle\ne0$，应先平移到涨落场，不能机械套用。

## 四个自由标量场

Wick 定理给出：

$$
T\{\phi_1\phi_2\phi_3\phi_4\}
=:\phi_1\phi_2\phi_3\phi_4:
+\text{全部单收缩项}
+\text{全部双收缩项}.
$$

单收缩共有：

$$
\binom42=6
$$

种。双收缩即完全配对共有三种：

$$
(12)(34),
\qquad
(13)(24),
\qquad
(14)(23).
$$

取真空期望值后，含未收缩场的正规序项全部消失，只剩完全收缩：

$$
\boxed{
\begin{aligned}
\langle0|T\{\phi_1\phi_2\phi_3\phi_4\}|0\rangle
={}&\Delta_{12}\Delta_{34}
+\Delta_{13}\Delta_{24}
+\Delta_{14}\Delta_{23},
\end{aligned}
}
$$

其中：

$$
\Delta_{ij}=\Delta_F(x_i-x_j).
$$

这就是零均值 Gaussian 变量四阶矩的量子场论版本。

## 一般 Wick 定理

对自由玻色场：

$$
\boxed{
T\{\phi_1\phi_2\cdots\phi_n\}
=:\phi_1\phi_2\cdots\phi_n:
+\sum_{\text{单收缩}}
:\!\text{剩余场}\!:
+\sum_{\text{双收缩}}
:\!\text{剩余场}\!:
+\cdots
}.
$$

规则是：

1. 每个场至多参与一条收缩；
2. 对所有彼此不重叠的收缩集合求和；
3. 收缩之外的场保持在同一个正规序符号内；
4. 若 $n$ 为偶数，最后一层是所有完全收缩；
5. 若 $n$ 为奇数，最后一层仍留下一个未收缩场。

取自由真空期望值时，只保留完全收缩。

## 完全收缩有多少种

$2n$ 个不同标记对象完全两两配对的数量为：

$$
\boxed{
(2n-1)!!
=\frac{(2n)!}{2^n n!}
}.
$$

解释：

- 先把 $2n$ 个对象任意排列，共 $(2n)!$；
- 每一对内部交换不改变配对，除以 $2^n$；
- $n$ 对之间交换顺序不改变配对，除以 $n!$。

因此六点自由标量真空相关函数有：

$$
5!!=15
$$

个完全收缩项。

## 为什么 Wick 定理成立

把自由场写成产生部分与湮灭部分：

$$
\phi=\phi^-+\phi^+.
$$

从时序排列改成正规序排列时，需要把湮灭部分越过产生部分。每次交换产生一个对易子：

$$
[\phi^+(x),\phi^-(y)].
$$

在自由场中，这个对易子是 $c$ 数分布。反复使用：

$$
AB=BA+[A,B]
$$

就会得到：

- 完全重新排列后的正规序项；
- 每次交换产生的单收缩；
- 多次交换产生的多收缩。

因此 Wick 定理本质上是自由振子代数与组合计数共同产生的恒等式。

## 归纳证明思路

假设 $n$ 个场的公式成立。加入第 $n+1$ 个场，并把它的正频湮灭部分移过已有正规序乘积。

它每越过一个负频产生部分，就产生一个 $c$ 数对易子，也就是一条新收缩。结果分成：

1. 新场不与任何旧场收缩；
2. 新场分别与任意一个旧场收缩。

这恰好枚举了 $n+1$ 个场的全部不重叠收缩集合，从而完成归纳。

费米场的证明结构相同，但对易子换成反对易或分级代数，并保留所有奇算符置换的符号。

## 费米场的 Wick 符号

对费米场，Wick 定理仍是“正规序加全部收缩”，但每一项带有把被收缩算符移动到相邻位置所需的费米置换符号。

若 $A_i$ 是处于零均值 Gaussian（准自由）态中的 Grassmann 奇线性场算符，并采用一致的分级时序和二点函数顺序约定，则四点完全配对为：

$$
\langle T\{A_1A_2A_3A_4\}\rangle
=C_{12}C_{34}
-C_{13}C_{24}
+C_{14}C_{23},
$$

其中：

$$
C_{ij}=\langle T\{A_iA_j\}\rangle.
$$

符号以原始顺序 $A_1A_2A_3A_4$ 为基准；中间配对 $(13)(24)$ 需要额外一次奇置换，所以带负号。一般非 Gaussian 态还要加四点连通部分。

对具体 Dirac 场，只有 $\psi$ 与 $\bar\psi$ 的允许收缩非零；还必须保留旋量指标和矩阵乘法顺序。

## 闭合费米回路为什么有负号

在由标准 Grassmann 费米场微扰展开得到、且顶点场顺序已经固定的 Feynman 图规则中，一条独立闭合费米收缩环相对于相同连接结构贡献一个额外因子 $-1$：

$$
(-1)^{N_{\mathrm{fermion\ loops}}}.
$$

这条图规则来自 Wick 展开中费米奇对象的循环置换，不是人为添加。

它不包含外部费米态重排产生的其他负号，也不能替代 Majorana 场等情形中的方向、重复计数和对称因子分析。完整符号还受相互作用顶点中的场顺序、外部费米线交换和旋量指标收缩影响。

## Wick 定理与真空期望值

对零均值自由玻色场：

$$
\langle0|T\{\phi_1\cdots\phi_n\}|0\rangle
$$

在 $n$ 为奇数时为零；在 $n=2m$ 时等于所有完全配对传播子乘积之和：

$$
\boxed{
\langle0|T\{\phi_1\cdots\phi_{2m}\}|0\rangle
=\sum_{\text{完全配对}}
\prod_{(ij)}\Delta_F(x_i-x_j)
}.
$$

这说明自由场真空是 Gaussian 态：二点函数决定全部高阶时序相关函数。

反过来，若一个态的所有连通相关函数在二阶以上都为零，它具有 Gaussian 或准自由结构。

## 与连通相关函数的关系

四点自由场相关函数：

$$
\Delta_{12}\Delta_{34}
+\Delta_{13}\Delta_{24}
+\Delta_{14}\Delta_{23}
$$

全部由两个不相连的二点块组成，所以自由 Gaussian 理论的四点连通相关函数为零。

加入相互作用后，高于二阶的连通相关函数一般不再为零。微扰论仍使用自由 Wick 定理，把相互作用插入展开为自由传播子的组合。

因此“Wick 定理把一切化为二点函数”只对 Gaussian 测度或以自由理论为基准的微扰展开成立，不表示任意相互作用理论的完整高阶相关都可直接因子化。

## 与 Dyson 展开的关系

相互作用图景的 S 矩阵为：

$$
S
=T\exp\left[-i\int d^4x\,\mathcal H_I(x)\right],
$$

其中 $H_I(t)=\int d^3x\,\mathcal H_I(t,\mathbf x)$。对没有时间导数相互作用、且正则动量不被相互作用改变的情形：

$$
\mathcal H_I=-\mathcal L_I,
$$

所以也可写成：

$$
S
=T\exp\left[i\int d^4x\,\mathcal L_I(x)\right].
$$

存在导数相互作用时，不能无条件使用 $\mathcal H_I=-\mathcal L_I$。

展开到第 $n$ 阶会出现：

$$
\frac{(-i)^n}{n!}
\int d^4x_1\cdots d^4x_n\,
T\{\mathcal H_I(x_1)\cdots\mathcal H_I(x_n)\}.
$$

每个 $\mathcal H_I$ 又含多个自由场。Wick 定理把整个时序乘积变成：

- 正规序的未收缩外部场；
- 收缩形成的内部传播子；
- 全部允许连接方式之和。

这正是 Feynman 图的组合来源。

## 一个 $\phi^4$ 顶点例子

相互作用：

$$
\mathcal L_I
=-\frac{\lambda}{4!}\phi^4.
$$

一阶二点函数修正含：

$$
\frac{-i\lambda}{4!}
\int d^4z\,
\langle0|T\{\phi(x)\phi(y)\phi(z)^4\}|0\rangle.
$$

Wick 收缩中，可把 $x$ 与一个 $z$ 场连接、$y$ 与另一个 $z$ 场连接，剩余两个 $z$ 场彼此收缩，形成 tadpole 图。这样的等价收缩有：

$$
4\times3=12
$$

种，与 $1/4!$ 合并后给出连通 tadpole 结构的系数：

$$
-\frac{i\lambda}{2}
\int d^4z\,
\Delta_F(x-z)\Delta_F(0)\Delta_F(z-y).
$$

原始六场真空期望还包含 $\Delta_F(x-y)$ 乘以 $z$ 点真空泡的非连通收缩；在归一化二点函数的分母中，或只取连通部分时，这类真空泡被消去。

因此不能只看 Lagrangian 前面的阶乘而猜最终系数，必须枚举等价收缩或使用图的对称因子。

## 自收缩与复合算符

同一点的收缩：

$$
\operatorname{Contr}\!\bigl(\phi(x),\phi(x)\bigr)
=\Delta_F(0)
$$

通常紫外发散。正规序复合算符：

$$
:\phi^2(x):
$$

在自由平直真空中可形式上减去这项自收缩。

但相互作用理论、曲时空或一般重整化方案中的复合算符需要更系统的局域反项。普通正规序不能替代完整复合算符重整化。

## 路径积分中的 Wick 定理

固定源项约定：

$$
Z_0[J]
=\int\mathcal D\phi\,
\exp\left[
iS_0[\phi]+i\int d^4x\,J(x)\phi(x)
\right].
$$

本文把传播子定义为：

$$
\Delta_F(x-y)
=\langle0|T\{\phi(x)\phi(y)\}|0\rangle.
$$

在这套约定下，自由 Gaussian 积分给出：

$$
Z_0[J]
=Z_0[0]
\exp\left[
-\frac12
\int d^4x\,d^4y\,
J(x)\Delta_F(x-y)J(y)
\right].
$$

时间有序关联函数由：

$$
\langle0|T\{\phi(x_1)\cdots\phi(x_n)\}|0\rangle
=\left.
\frac1{Z_0[0]}
\prod_{r=1}^{n}
\left(\frac1i\frac{\delta}{\delta J(x_r)}\right)
Z_0[J]
\right|_{J=0}
$$

得到。若改用不含分子 $i$ 的数学 Green 函数，指数中的显式 $i$ 因子会相应改变；两套记号不能混用。

对 $J$ 做多次泛函导数时，每次从指数中的二次型取出一对源，因而自动枚举所有配对。这就是路径积分版 Wick 定理。

算符证明强调产生、湮灭算符代数；路径积分证明强调 Gaussian 积分。两者给出相同的配对结构。

## 与弦世界面的关系

对无边界世界面上的闭弦体场，在平直背景和平面或球面局部坐标中，$X^\mu(z,\bar z)$ 是二维自由 Gaussian 场。采用：

$$
\langle X^\mu(z,\bar z)X^\nu(w,\bar w)\rangle
=-\frac{\alpha'}2\eta^{\mu\nu}
\ln|z-w|^2.
$$

因此指数顶点算符满足 Gaussian 指数公式。对正规序体顶点：

$$
V_k(z,\bar z)=:e^{ik\cdot X(z,\bar z)}:,
$$

多个顶点的相关函数由交叉收缩给出：

$$
\left\langle
\prod_{i=1}^n:e^{ik_i\cdot X(z_i,\bar z_i)}:
\right\rangle
\propto
\prod_{i<j}|z_i-z_j|^{\alpha' k_i\cdot k_j},
$$

并伴随零模积分产生的目标时空动量守恒 delta。

具体指数符号和幂次取决于 Euclidean 作用量、二点函数和顶点算符中的 $i$ 约定。开弦边界顶点、上半平面镜像收缩和纯手征相关函数必须使用相应的边界或手征二点函数，不能直接照搬上述闭弦体场幂次。核心结构是：指数中的所有交叉收缩重新求和成点对乘积。

## 适用条件与事实边界

1. 标准 Wick 定理适用于自由场、Gaussian 测度或准自由态。
2. 收缩定义为时序乘积减正规序乘积，并在自由理论中等于不再作用于 Fock 空间的传播子核；Dirac 收缩仍保留旋量指标顺序。
3. 取同一自由 Fock 真空对自由场单项式的期望值后，只保留完全收缩。
4. 零均值自由玻色场的奇数点相关函数为零。
5. $2n$ 个玻色场完全配对数为 $(2n-1)!!$。
6. 费米 Wick 展开必须保留奇算符置换符号和矩阵指标顺序。
7. 标准 Grassmann 费米场微扰图中每个闭合费米收缩环有额外负号，但完整振幅还可能有外态置换、Majorana 计数等其他符号和因子。
8. 相互作用理论的完整高阶相关函数一般不因子化；微扰论使用的是自由场 Wick 定理。
9. 同一点收缩通常紫外发散，涉及复合算符重整化。
10. 正规序依赖选定真空和模式分解，在曲时空或非平凡背景中并非绝对定义。
11. 路径积分版 Wick 定理依赖 Gaussian 泛函积分、源导数约定及边界处方。
12. 弦世界面指数顶点的 Wick 重求和还需结合零模积分、正规序、世界面拓扑和边界条件。

## 常见误区

1. **Wick 定理适用于任意强相互作用场的精确算符。** 标准形式只直接适用于自由或 Gaussian 场。
2. **收缩就是把两个场从公式里删掉。** 它要替换为相应传播子，并保留剩余场的正规序。
3. **正规序就是时序。** 一个按产生/湮灭类型排列，一个按时间排列。
4. **四点自由场相关函数只有一种配对。** 四个不同点有三种完全配对。
5. **奇数点函数在任何状态中都为零。** 该结论要求零均值 Gaussian 态等条件。
6. **费米 Wick 展开与玻色展开只有传播子不同。** 还必须保留每种配对的置换负号。
7. **闭合费米回路负号是人为规定。** 它来自费米奇对象的循环置换。
8. **正规序消除了所有紫外发散。** 它只处理特定自收缩，不能替代完整重整化。
9. **完全收缩数是 $(2n)!$。** 配对内部和配对之间的排列会重复计数，正确结果是 $(2n-1)!!$。
10. **Feynman 图比 Wick 定理更基本。** 图是 Wick 收缩组合的可视化记账工具。
11. **弦顶点相关函数不需要 Wick 定理。** 自由世界面场的指数相关正由 Wick 收缩重求和得到。
12. **路径积分和算符 Wick 定理是不同物理。** 它们分别从 Gaussian 积分和振子代数表达同一配对结构。

## 练习

1. 写出两个算符收缩的定义。
2. 自由实标量场的收缩等于什么？
3. 写出两个自由标量场的 Wick 展开。
4. 三个零均值自由标量场的真空时序相关函数为什么为零？
5. 写出四点自由标量场真空相关函数的三种配对。
6. 六个标量场有多少种完全收缩？
7. 推导 $2n$ 个对象的完全配对数。
8. 为什么自由场 Wick 定理可由产生、湮灭部分的对易代数证明？
9. 费米 Wick 展开为什么会出现置换负号？
10. 四个费米奇算符的三种完全配对具有什么符号结构？
11. 闭合费米回路的整体负号从哪里来？
12. Wick 定理怎样把 Dyson 展开转化为 Feynman 图？
13. 为什么同一点自收缩需要重整化？
14. 路径积分中 Wick 配对怎样从 Gaussian 生成泛函出现？
15. 弦世界面指数顶点相关函数为什么变成点对距离的乘积？

## 答案与提示

1. $\operatorname{Contr}(A,B)=T\{AB\}-:AB:$。
2. $\Delta_F(x-y)I$。
3. $T\{\phi_1\phi_2\}=:\phi_1\phi_2:+\Delta_{12}$。
4. 三个对象不能完全两两配对；取真空期望后，所有含未收缩正规序场的项为零。
5. $\Delta_{12}\Delta_{34}+\Delta_{13}\Delta_{24}+\Delta_{14}\Delta_{23}$。
6. $5!!=15$。
7. $(2n)!/(2^n n!)=(2n-1)!!$；分别除去每对内部交换和各对之间排列的重复计数。
8. 从时序改排为正规序时，每次把湮灭部分越过产生部分都会产生一个 $c$ 数对易子，即一条收缩。
9. 为形成某种配对必须交换费米奇算符，每交换一对奇算符产生一个负号。
10. 在零均值 Gaussian 或准自由态及一致的分级时序约定下，为 $C_{12}C_{34}-C_{13}C_{24}+C_{14}C_{23}$；一般态还可能有四点连通部分。
11. 在标准 Grassmann 费米场微扰展开中，把费米场收缩成独立闭合循环会产生额外奇置换，所以每个闭合费米收缩环有一个额外负号；外态交换等符号另计。
12. 收缩给传播子内线，未收缩场给外线，相互作用插入给顶点；所有收缩方式由图枚举。
13. $\Delta_F(0)$ 通常紫外发散，普通算符乘积需定义为重整化复合算符。
14. 在 $Z_0[J]=\int\mathcal D\phi\,e^{iS_0+i\int J\phi}$ 及每次取 $(1/i)\delta/\delta J$ 的约定下，Gaussian 指数中的二次源项使多次泛函导数自动枚举全部两两配对。
15. 在正文给定的无边界闭弦体场二点函数约定下，指数中的交叉收缩可重求和为 $\exp$ 的点对和，进一步化成 $\prod_{i<j}|z_i-z_j|^{\alpha'k_i\cdot k_j}$；开弦边界需改用边界二点函数。

## 与其他概念的关系

- [[弦理论/物理学/时序乘积]] 提供 Wick 定理左边的算符排序；
- [[弦理论/物理学/传播子]] 是每一条自由场收缩的数值；
- [[弦理论/物理学/产生算符]] 与 [[弦理论/物理学/湮灭算符]] 的代数给出算符证明；
- [[弦理论/物理学/Fock 空间]] 和自由真空决定正规序定义；
- [[弦理论/物理学/Dirac 场]] 展示费米收缩、旋量指标和置换负号；
- [[弦理论/物理学/微扰论]] 的 Dyson 展开产生需要 Wick 分解的时序乘积；
- [[弦理论/物理学/生成泛函]] 从 Gaussian 源泛函推导同一配对规则；
- [[弦理论/物理学/Feynman 图]] 是 Wick 收缩的图形记账；
- [[弦理论/物理学/圈展开]] 按图的拓扑和闭环数组织量子修正；
- [[弦理论/物理学/正规序]] 系统处理产生、湮灭顺序与复合算符；
- [[弦理论/物理学/算符乘积展开]] 在短距离极限组织 Wick 收缩产生的奇异项；
- [[弦理论/物理学/弦散射振幅]] 使用世界面自由场 Wick 收缩计算顶点算符相关函数。

## 参考资料

- Michael E. Peskin and Daniel V. Schroeder, *An Introduction to Quantum Field Theory*, Westview Press, 1995, Chapter 4.
- Mark Srednicki, *Quantum Field Theory*, Cambridge University Press, 2007, Chapters 5–9.
- Steven Weinberg, *The Quantum Theory of Fields, Vol. 1*, Cambridge University Press, 1995, Chapters 4–6.
- Michael D. Schwartz, *Quantum Field Theory and the Standard Model*, Cambridge University Press, 2014, Chapters 7–10.
- Claude Itzykson and Jean-Bernard Zuber, *Quantum Field Theory*, McGraw-Hill, 1980.
- N. N. Bogoliubov and D. V. Shirkov, *Introduction to the Theory of Quantized Fields*, Wiley, 1980.
- David Tong, *Lectures on Quantum Field Theory*, [course notes](https://www.damtp.cam.ac.uk/user/tong/qft.html)
- Joseph Polchinski, *String Theory, Vol. 1*, Cambridge University Press, 1998, Chapters 2 and 6.
- David Tong, *String Theory*, arXiv:0908.0333, [arXiv](https://arxiv.org/abs/0908.0333)
