---
aliases:
  - Clifford Algebra
  - 克利福德代数
english_name: Clifford Algebra
tags:
  - 数学
  - 代数
  - 几何
  - 弦理论先修
prerequisites:
  - "[[弦理论/数学/向量空间]]"
  - "[[弦理论/数学/内积空间]]"
  - "[[弦理论/数学/矩阵]]"
  - "[[弦理论/数学/张量积]]"
  - "[[弦理论/数学/SO 群]]"
  - "[[弦理论/数学/SU(2) 与 SO(3) 的双覆盖]]"
used_by:
  - "[[弦理论/数学/Gamma 矩阵]]"
  - "[[弦理论/数学/旋量]]"
  - "[[弦理论/物理学/Dirac 场]]"
  - "[[弦理论/物理学/Ramond 零模]]"
  - "[[弦理论/物理学/时空旋量]]"
evidence_status: 教材事实
---

# Clifford 代数（Clifford Algebra）

## 一句话解释

Clifford 代数把带内积的向量放进一个可乘法的代数中，并规定向量平方由它的长度决定。

## 为什么要学它

普通向量可以相加和数乘，却没有天然的向量乘法。Clifford 代数增加一种乘法，使长度、角度、反射和旋转都能编码进代数运算。

Gamma 矩阵是 Clifford 代数的矩阵表示，旋量是它的表示空间。Dirac 方程、Spin 群以及超弦 R 扇区零模都以 Clifford 关系为核心。

## 从一个向量平方开始

设 $V$ 是实向量空间，$Q:V\to\mathbb R$ 是二次型。一种常见数学约定规定：

$$
v^2=Q(v)1,
$$

其中：

- $v\in V$；
- $1$：代数的乘法单位元；
- $Q(v)$：向量 $v$ 的二次长度信息。

有些资料采用 $v^2=-Q(v)1$。两种约定都会使用，必须先核对符号。

## 从平方关系得到反对易关系

对两个向量 $u,v\in V$，展开：

$$
(u+v)^2=u^2+uv+vu+v^2.
$$

另一方面，二次型的极化给出对应对称双线性型 $B$：

$$
Q(u+v)=Q(u)+2B(u,v)+Q(v).
$$

比较两式得到：

$$
uv+vu=2B(u,v)1.
$$

使用反对易子：

$$
\{u,v\}=uv+vu,
$$

可写成：

$$
\{u,v\}=2B(u,v)1.
$$

## 正式定义

Clifford 代数 $Cl(V,Q)$ 是由向量空间 $V$ 生成的带单位结合代数，并满足：

$$
v^2=Q(v)1
$$

对所有 $v\in V$ 成立。

“由 $V$ 生成”表示代数中的元素由标量、向量以及向量乘积的有限线性组合构成。

严格构造可从张量代数 $T(V)$ 出发，对关系：

$$
v\otimes v-Q(v)1
$$

生成的双边理想取商：

$$
Cl(V,Q)
=T(V)\big/\langle v\otimes v-Q(v)1\rangle.
$$

## 每个符号是什么意思

- $V$：底层向量空间；
- $Q$：二次型；
- $B$：由 $Q$ 极化得到的对称双线性型；
- $Cl(V,Q)$：对应的 Clifford 代数；
- $T(V)$：由各阶张量积组成的张量代数；
- $\langle\cdots\rangle$：由指定关系生成的双边理想；
- 取商：把违反所需关系的差异视为零。

## 正交基下的关系

若 $e_1,\ldots,e_n$ 是正交基，并且：

$$
B(e_i,e_j)=\eta_{ij},
$$

则：

$$
e_ie_j+e_je_i=2\eta_{ij}1.
$$

当 $i\ne j$ 且基向量正交时：

$$
e_ie_j=-e_je_i.
$$

因此不同正交方向的生成元彼此反对易。

## Euclidean 符号约定

在正定 Euclidean 内积下，可取：

$$
e_i^2=+1.
$$

于是：

$$
\{e_i,e_j\}=2\delta_{ij}.
$$

但另一常见数学记号把 $Cl_{p,q}$ 定义成前 $p$ 个基向量平方为 $+1$、后 $q$ 个平方为 $-1$；也有文献交换 $p,q$ 的顺序。只看符号 $Cl_{p,q}$ 不足以判断约定，必须看定义。

## Lorentzian 情形

若度量号差为：

$$
\eta=\operatorname{diag}(-1,+1,\ldots,+1),
$$

则相应生成元满足：

$$
\{e_\mu,e_\nu\}=2\eta_{\mu\nu}.
$$

因此时间方向生成元平方为 $-1$，空间方向平方为 $+1$。

若采用相反号差或 $v^2=-Q(v)$ 的定义，所有平方符号会相应改变，但物理内容在一致约定下等价。

## Clifford 乘积包含内积与外积

对向量 $u,v$，Clifford 乘积可分成对称和反对称部分：

$$
uv=\frac12(uv+vu)+\frac12(uv-vu).
$$

第一部分是：

$$
B(u,v)1,
$$

第二部分可与二向量或外积联系：

$$
u\wedge v=\frac12(uv-vu).
$$

所以：

$$
uv=B(u,v)+u\wedge v.
$$

Clifford 乘法同时编码内积信息和有向平面信息。

## 一个二维 Euclidean 例子

取正交单位基 $e_1,e_2$，满足：

$$
e_1^2=e_2^2=1,
\qquad e_1e_2=-e_2e_1.
$$

定义：

$$
I=e_1e_2.
$$

则：

$$
I^2=e_1e_2e_1e_2=-e_1^2e_2^2=-1.
$$

因此有向平面元 $I$ 的平方像虚数单位一样为 $-1$。

一般元素可写为：

$$
a+be_1+ce_2+d e_1e_2.
$$

所以二维 Clifford 代数作为实向量空间有四维。

## 维数为什么是 $2^n$

若 $V$ 有 $n$ 个基向量，通过反对易关系可把任意乘积整理成索引严格递增的形式：

$$
e_{i_1}e_{i_2}\cdots e_{i_k},
\qquad i_1<i_2<\cdots<i_k.
$$

每个基方向只有“出现”或“不出现”两种选择，因此总数为：

$$
\sum_{k=0}^{n}\binom nk=2^n.
$$

在非退化二次型情形下，这些标准单项式构成 $Cl(V,Q)$ 的向量空间基。

## 分次结构

Clifford 代数按向量因子个数的奇偶性分成：

$$
Cl(V,Q)=Cl^0(V,Q)\oplus Cl^1(V,Q).
$$

其中：

- $Cl^0$：偶数个向量乘积的线性组合；
- $Cl^1$：奇数个向量乘积的线性组合。

乘法满足奇偶规则：偶乘偶为偶，偶乘奇为奇，奇乘奇为偶。这叫 $\mathbb Z_2$ 分次。

## 偶 Clifford 子代数

偶数部分 $Cl^0(V,Q)$ 在乘法下封闭，因此是子代数。

Spin 群位于可逆的偶 Clifford 元素中。旋转由两个反射合成，所以自然由偶数个单位向量乘积表示。

## 反射如何写进 Clifford 代数

设非零向量 $a$ 可逆。向量 $v$ 关于垂直于 $a$ 的超平面的反射，可在相应符号约定下写成：

$$
v\longmapsto -ava^{-1}.
$$

若 $a$ 是单位向量且 $a^2=1$，则 $a^{-1}=a$。

这个公式把几何反射变成 Clifford 乘法。Cartan–Dieudonné 定理说明，非退化二次空间中的正交变换可由有限次反射合成。

## Pin 群与 Spin 群

由单位向量乘积生成的适当子群称为 Pin 群，它双覆盖正交群：

$$
Pin(p,q)\to O(p,q).
$$

其中由偶数个单位向量乘积构成的部分称为 Spin 群，并双覆盖特殊正交群的相应单位分支；在 Euclidean 情形常写成：

$$
Spin(n)\to SO(n).
$$

对 $n\ge3$，覆盖核为：

$$
\{+1,-1\}.
$$

## 为什么旋转由半角表示

在二维 Euclidean 平面中，令 $I=e_1e_2$ 且 $I^2=-1$。定义 rotor：

$$
R(\theta)=e^{-I\theta/2}
=\cos\frac\theta2-I\sin\frac\theta2.
$$

向量通过夹乘变换：

$$
v\longmapsto RvR^{-1}.
$$

左右各出现一个半角，合起来使向量旋转角度 $\theta$。当 $\theta=2\pi$ 时 $R=-1$，但夹乘中的两个负号抵消，所以向量已回到原位；当 $\theta=4\pi$ 时 rotor 本身才回到 $+1$。

## $Spin(3)$ 与 $SU(2)$

三维 Euclidean Clifford 代数的偶子代数可用于构造：

$$
Spin(3)\cong SU(2).
$$

其对三维向量的夹乘作用给出：

$$
Spin(3)\to SO(3).
$$

元素 $R$ 与 $-R$ 产生同一三维旋转，正是 $SU(2)$ 双覆盖 $SO(3)$ 的 Clifford 代数版本。

## Clifford 代数与外代数的关系

作为向量空间，Clifford 代数与外代数：

$$
\Lambda^*V
$$

具有相同维数 $2^n$，并可在选择适当映射后建立向量空间同构。

但乘法不同：外代数中 $v\wedge v=0$；Clifford 代数中 $v^2=Q(v)1$。因此二者不能作为代数直接混同。

## Clifford 代数的表示

Clifford 代数表示是保持加法与乘法的映射：

$$
\rho:Cl(V,Q)\to\operatorname{End}(S),
$$

其中 $S$ 是表示空间。

在选定基后，生成元 $e_\mu$ 的像通常记作 Gamma 矩阵：

$$
\rho(e_\mu)=\Gamma_\mu.
$$

它们满足：

$$
\{\Gamma_\mu,\Gamma_\nu\}
=2\eta_{\mu\nu}I.
$$

$S$ 中的向量称为 Clifford 模；在物理语境中相应不可约表示空间中的对象就是旋量。

## Pauli 矩阵例子

Pauli 矩阵满足：

$$
\{\sigma_i,\sigma_j\}=2\delta_{ij}I.
$$

因此它们给出三维 Euclidean Clifford 关系的一种复矩阵表示。

同时：

$$
\sigma_i\sigma_j
=\delta_{ij}I+i\varepsilon_{ijk}\sigma_k.
$$

对称部分给内积，反对称部分编码旋转生成元。

## Dirac Gamma 矩阵

Minkowski 时空中的 Gamma 矩阵满足：

$$
\{\Gamma^\mu,\Gamma^\nu\}
=2\eta^{\mu\nu}I.
$$

它们使 Dirac 算符的一次方在平方后产生 Klein–Gordon 型二阶算符：

$$
(\Gamma^\mu\partial_\mu)^2
=\eta^{\mu\nu}\partial_\mu\partial_\nu
$$

在偏导数彼此对易且忽略具体符号约定所带整体号时成立。

这就是 Clifford 关系在线性化相对论能量—动量关系中的作用。

## 手征算符

偶数维时空中，可把所有 Gamma 矩阵按约定乘起来构造手征算符，常记作：

$$
\Gamma_*.
$$

它与每个 $\Gamma^\mu$ 反对易，并可把 Dirac 旋量分成两个手征子空间。

精确相位和符号依赖维数、度量号差和 Gamma 矩阵约定，因此应在具体维数中单独定义。

## 实、复 Clifford 代数

底层标量域不同会改变 Clifford 代数分类：

- 实 Clifford 代数使用实数系数；
- 复 Clifford 代数使用复数系数。

实 Clifford 代数的同构类型依赖号差，并呈现模 $8$ 周期；复 Clifford 代数主要依赖维数奇偶，并呈现模 $2$ 周期。

这些周期性是 Majorana 条件、Weyl 条件和不同维数旋量类型的重要数学背景，但完整分类需另行学习。

## 在量子场论中的作用

Dirac 场是 Lorentzian Clifford 代数相关 Spin 群的旋量表示。Gamma 矩阵让 Lorentz 生成元在旋量空间上写成：

$$
\Sigma^{\mu\nu}
=\frac14[\Gamma^\mu,\Gamma^\nu]
$$

或带额外因子 $i$ 的等价约定。

这些生成元满足 Lorentz Lie 代数的对易关系。

## 在 RNS 超弦中的作用

R 扇区的世界面费米子具有整数模。其零模满足形如：

$$
\{\psi_0^\mu,\psi_0^\nu\}
=\eta^{\mu\nu}
$$

的反对易关系，归一化因具体约定而异。

这正是目标时空 Clifford 代数。因此 R 扇区基态必须形成 Clifford 代数的表示，也就是目标时空旋量。

这不是类比，而是超弦谱中时空费米子出现的直接代数机制。

## 在十维超弦中的作用

十维 RNS 超弦使用十维 Lorentzian Clifford 代数。结合 Majorana、Weyl 和 GSO 投影，可得到具有特定实性与手征性的时空旋量态。

允许同时施加哪些条件取决于维数和号差。十维 $(1,9)$ 或 $(9,1)$ Minkowski 时空恰好允许 Majorana–Weyl 旋量，这是十维超对称结构的重要组成部分。

## 一个计算例子

设 $e_1^2=e_2^2=1$ 且 $e_1e_2=-e_2e_1$。计算：

$$
(e_1+e_2)^2
=e_1^2+e_1e_2+e_2e_1+e_2^2.
$$

中间两项抵消，所以：

$$
(e_1+e_2)^2=2.
$$

这与向量 $e_1+e_2$ 的 Euclidean 长度平方为 $2$ 一致。

## 适用条件与事实边界

1. Clifford 代数由向量空间和二次型共同决定；只给向量空间不足以确定乘法关系。
2. 本文主约定为 $v^2=Q(v)1$，但大量文献使用相反号，$Cl_{p,q}$ 的指标顺序也不统一。
3. Clifford 乘法一般不交换；正交的不同生成元彼此反对易。
4. 对 $n$ 维非退化二次空间，Clifford 代数作为向量空间通常有维数 $2^n$。
5. Clifford 代数与外代数可有相同底层向量空间维数，但乘法不同。
6. Spin 群位于偶 Clifford 子代数的可逆元素中，并通过夹乘双覆盖相应旋转群。
7. Gamma 矩阵是 Clifford 代数的一种矩阵表示，不是抽象 Clifford 代数本身。
8. 旋量属于 Clifford 代数或 Spin 群的表示空间，不是普通向量或张量。
9. 实 Clifford 代数分类依赖号差；复化后部分号差信息消失。
10. Dirac 与手征公式的因子 $i$、指标位置和整体符号依赖度量与矩阵约定。
11. R 扇区零模的反对易关系可能含 $1/2$、$2$ 或 $\alpha'$ 等归一化因子，但经重标度后给出同一 Clifford 结构。
12. Majorana–Weyl 条件的兼容性是维数和号差相关结论，不能推广到任意维度。

## 常见误区

1. **Clifford 代数只是矩阵集合。** 抽象代数先由生成元和关系定义，矩阵只是表示。
2. **向量乘法满足交换律。** 正交生成元反而满足反对易关系。
3. **$e_i^2$ 永远等于 $+1$。** 它由二次型号差和符号约定决定。
4. **Clifford 代数与外代数完全相同。** 向量空间结构相关，但乘法不同。
5. **Gamma 矩阵就是旋量。** Gamma 矩阵作用在旋量上；二者角色不同。
6. **Spin 群就是 $SO(n)$。** Spin 群双覆盖 $SO(n)$，核通常为 $\{\pm1\}$。
7. **$2^n$ 是旋量分量数。** $2^n$ 是 Clifford 代数的向量空间维数；不可约旋量维数通常更小。
8. **三维 Pauli 矩阵公式可原样用于任意维。** 更高维需要相应大小和数量的 Gamma 矩阵。
9. **所有维数都可同时使用 Majorana 与 Weyl 条件。** 兼容性依赖维数和号差。

## 练习

1. 写出 Clifford 代数的生成关系。
2. 从 $(u+v)^2$ 推导 $uv+vu=2B(u,v)$。
3. 若 $e_1,e_2$ 正交且平方为 $1$，证明 $(e_1e_2)^2=-1$。
4. $n$ 维 Clifford 代数为何有 $2^n$ 个标准基单项式？
5. 偶 Clifford 子代数由什么元素组成？
6. 写出单位向量 $a$ 对向量 $v$ 的反射公式。
7. $Spin(n)$ 覆盖哪个群？典型核是什么？
8. Gamma 矩阵满足什么反对易关系？
9. 为什么 Clifford 代数与外代数不能作为代数等同？
10. RNS 超弦 R 扇区零模为何产生时空旋量？

## 答案与提示

1. $v^2=Q(v)1$，等价极化形式为 $uv+vu=2B(u,v)1$。
2. 展开左边并与 $Q(u+v)=Q(u)+2B(u,v)+Q(v)$ 比较。
3. $e_1e_2e_1e_2=-e_1^2e_2^2=-1$。
4. 每个基方向在有序单项式中选择出现或不出现，共 $2^n$ 种子集。
5. 偶数个向量乘积的线性组合。
6. 在本文约定下为 $v\mapsto-ava^{-1}$。
7. Euclidean 情形双覆盖 $SO(n)$，典型核为 $\{+1,-1\}$。
8. $\{\Gamma_\mu,\Gamma_\nu\}=2\eta_{\mu\nu}I$。
9. 外代数有 $v\wedge v=0$，Clifford 代数有 $v^2=Q(v)1$。
10. R 零模满足目标时空 Clifford 反对易关系，其基态必须承载该代数的表示。

## 与其他概念的关系

- [[弦理论/数学/向量空间]] 提供生成 Clifford 代数的向量；
- [[弦理论/数学/内积空间]] 和二次型决定生成元平方与反对易关系；
- [[弦理论/数学/张量积]] 用于通过张量代数取商严格构造 Clifford 代数；
- [[弦理论/数学/SO 群]] 是 Spin 群所覆盖的旋转群；
- [[弦理论/数学/SU(2) 与 SO(3) 的双覆盖]] 是 $Spin(3)$ 构造的低维模型；
- [[弦理论/数学/Gamma 矩阵]] 给出 Clifford 代数的具体矩阵表示；
- [[弦理论/数学/旋量]] 是 Clifford 代数与 Spin 群的表示对象；
- [[弦理论/数学/微分形式]] 与外代数结构相关，但其楔积不同于完整 Clifford 乘法；
- [[弦理论/物理学/Dirac 场]] 使用 Lorentzian Clifford 代数线性化相对论波动方程；
- [[弦理论/物理学/Ramond 零模]] 直接满足 Clifford 反对易关系。

## 参考资料

- Pertti Lounesto, *Clifford Algebras and Spinors*, 2nd ed., Cambridge University Press, 2001.
- H. Blaine Lawson and Marie-Louise Michelsohn, *Spin Geometry*, Princeton University Press, 1989.
- Thomas Friedrich, *Dirac Operators in Riemannian Geometry*, American Mathematical Society, 2000.
- Mikio Nakahara, *Geometry, Topology and Physics*, 2nd ed., CRC Press, 2003.
- Michael E. Peskin and Daniel V. Schroeder, *An Introduction to Quantum Field Theory*, Westview Press, 1995.
- Joseph Polchinski, *String Theory, Vol. 1*, Cambridge University Press, 1998.
- Joseph Polchinski, *String Theory, Vol. 2*, Cambridge University Press, 1998.
- David Tong, *Lectures on String Theory*, [arXiv:0908.0333](https://arxiv.org/abs/0908.0333)