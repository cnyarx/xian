---
aliases: [Wick Rotation, Euclidean Continuation, 威克旋转]
english_name: Wick Rotation
tags: [物理学, 量子场论, 复分析, 弦理论先修]
prerequisites:
  - "[[弦理论/数学/复数]]"
  - "[[弦理论/物理学/Minkowski 时空]]"
  - "[[弦理论/物理学/路径积分]]"
  - "[[弦理论/数学/Gaussian 积分]]"
used_by:
  - "[[弦理论/物理学/二维 Euclidean 场论]]"
  - "[[弦理论/物理学/生成泛函]]"
  - "[[弦理论/物理学/传播子]]"
  - "[[弦理论/物理学/世界面路径积分]]"
  - "[[弦理论/物理学/有限温场论]]"
evidence_status: 教材事实
---

# Wick 旋转（Wick Rotation）

## 一句话解释

Wick 旋转是在满足解析条件时，把 Lorentz 时间沿复平面旋转为 Euclidean 时间，使振荡权重 $e^{iS}$ 变成衰减权重 $e^{-S_E}$。

## 为什么要学它

实时量子路径积分含有快速振荡的复相位，直接定义和计算很困难。Euclidean 形式更像统计力学配分函数，Gaussian 积分通常收敛，也便于格点数值计算。

弦的世界面路径积分经常先在 Euclidean 世界面上定义。关联函数、传播子、真空投影和有限温理论都依赖正确理解 Wick 旋转及其边界。

## 直观图景

实时间轴与虚时间轴可看成复时间平面中的两条方向。Wick 旋转不是改变钟表读数，而是把积分变量或外部时间参数沿复平面连续变形。

若被积函数在变形区域内解析，且无穷远圆弧贡献消失，积分轮廓可旋转而保持同一解析函数的信息。若途中穿过极点、分支切线或增长方向，旋转就可能失败或产生额外项。

## 基本代换

采用 mostly-minus Minkowski 度量：

$$
ds^2=dt^2-d\mathbf x^2.
$$

定义 Euclidean 时间：

$$
t=-i\tau,
$$

于是：

$$
dt=-i\,d\tau.
$$

时间导数变为：

$$
\frac{\partial}{\partial t}
=i\frac{\partial}{\partial\tau}.
$$

因为 $\tau=it$，链式法则给出上式。

不同教材可能采用 $t=+i\tau$ 或不同度量号差。最终符号必须与传播子极点处方和 Euclidean 作用量约定一致。

## 度量怎样变化

代入 $dt=-i\,d\tau$：

$$
ds^2
=(-i\,d\tau)^2-d\mathbf x^2
=-d\tau^2-d\mathbf x^2.
$$

去掉整体负号后得到正定 Euclidean 线元：

$$
ds_E^2=d\tau^2+d\mathbf x^2.
$$

Lorentz 时空有一个时间方向和若干空间方向，二次型不正定；Euclidean 空间所有方向同号，旋转群取代 Lorentz boost 结构。

这是一种解析延拓关系，不表示真实时空已经实验上变成普通四维 Euclidean 空间。

## 粒子路径积分

实时传播振幅形式为：

$$
K
=\int\mathcal D x\,
\exp\left(\frac{i}{\hbar}S_M[x]\right).
$$

对普通粒子：

$$
S_M
=\int dt
\left[
\frac12m\left(\frac{dx}{dt}\right)^2
-V(x)
\right].
$$

令 $t=-i\tau$ 后，定义 Euclidean 作用量：

$$
S_E
=\int d\tau
\left[
\frac12m\left(\frac{dx}{d\tau}\right)^2
+V(x)
\right].
$$

指数变为：

$$
\exp\left(\frac{i}{\hbar}S_M\right)
\longrightarrow
\exp\left(-\frac{1}{\hbar}S_E\right).
$$

势能项在 $S_E$ 中变成加号。若 $V$ 有下界，较大作用量的路径受到指数抑制。

## 公式中每个符号的意思

- $t$：Lorentz 实时间；
- $\tau$：Euclidean 时间；
- $S_M$：Minkowski 或 Lorentz 作用量；
- $S_E$：Euclidean 作用量；
- $\mathcal D x$：路径积分的形式测度；
- $\hbar$：约化 Planck 常数；
- $i$：虚数单位；
- $e^{iS_M/\hbar}$：实时复相位权重；
- $e^{-S_E/\hbar}$：Euclidean 衰减权重。

$S_M/\hbar$ 与 $S_E/\hbar$ 都无量纲。旋转关系的精确符号依赖度量和 $t=\mp i\tau$ 约定。

## 为什么振荡变成衰减

若形式上有：

$$
S_M=iS_E,
$$

则：

$$
\frac{i}{\hbar}S_M
=\frac{i}{\hbar}(iS_E)
=-\frac{S_E}{\hbar}.
$$

因此单位模长的振荡相位变成实指数衰减。

这使许多 Euclidean 积分接近概率权重，但只有在归一化后且权重非负时才能直接解释为概率测度。费米行列式、化学势或拓扑项可能使权重不正，产生符号问题。

## 自由标量场

mostly-minus 约定下，自由实标量场的 Lorentz 作用量为：

$$
S_M
=\int d^Dx\,
\left[
\frac12\partial_\mu\phi\partial^\mu\phi
-\frac12m^2\phi^2
\right].
$$

Wick 旋转后得到：

$$
S_E
=\int d^Dx_E\,
\left[
\frac12(\partial_E\phi)^2
+\frac12m^2\phi^2
\right].
$$

对实场和 $m^2>0$，二次型在适当边界条件下为非负，Euclidean Gaussian 泛函积分更容易处理。

若势能无下界或存在负模，Wick 旋转本身不会自动修复不稳定性。

## 能量变量的旋转

Fourier 变换中，时间与能量共轭：

$$
e^{-ip^0t}.
$$

当：

$$
t=-i\tau,
$$

常相应定义 Euclidean 频率：

$$
p^0=ip_E^0
$$

或等价约定，使指数成为 Euclidean Fourier 或 Laplace 型因子。

积分轮廓从实 $p^0$ 轴旋转到虚轴时，必须追踪传播子极点的位置。

## Feynman 传播子的极点处方

标量 Feynman 传播子含：

$$
\frac{i}{p^2-m^2+i\varepsilon}.
$$

其中：

$$
p^2=(p^0)^2-\mathbf p^2
$$

采用 mostly-minus 约定。$i\varepsilon$ 指定极点略微偏离实轴，也规定时间有序边界条件。

正是这个处方告诉我们 $p^0$ 积分轮廓可以向哪个方向旋转而不穿过极点。忽略 $i\varepsilon$，就无法唯一说明 Wick 旋转和返回 Lorentz 理论的方法。

## Euclidean 传播子

旋转后，Euclidean 动量满足：

$$
p_E^2=(p_E^0)^2+\mathbf p^2.
$$

自由标量 Euclidean 传播子为：

$$
G_E(p_E)
=\frac{1}{p_E^2+m^2}.
$$

分母对实 Euclidean 动量为正，不再在实积分域上出现 Lorentz 壳极点。

返回实时传播子需要按正确解析延拓和 $i\varepsilon$ 处方恢复，不能只把 $p_E^0$ 换回一个符号而忽略边界值。

## Euclidean 演化与基态投影

实时演化：

$$
U(t)=e^{-iHt/\hbar}
$$

在能量本征态上只改变相位。

令 $t=-i\tau$：

$$
e^{-iH(-i\tau)/\hbar}
=e^{-H\tau/\hbar}.
$$

若：

$$
|\psi\rangle=\sum_n c_n|n\rangle,
$$

则：

$$
e^{-H\tau/\hbar}|\psi\rangle
=\sum_n c_ne^{-E_n\tau/\hbar}|n\rangle.
$$

当 $\tau$ 很大，高能态相对基态受到更强抑制。因此 Euclidean 时间演化可提取基态和低能谱。

若 Hamiltonian 无下界或初态与基态正交，这个简单结论需要修改。

## 与统计力学的关系

量子统计配分函数为：

$$
Z(\beta)=\operatorname{Tr}e^{-\beta H}.
$$

把 Euclidean 时间取为周期：

$$
0\le\tau<\beta\hbar,
$$

可把配分函数写成 Euclidean 路径积分。

玻色场满足周期边界条件：

$$
\phi(\tau+\beta\hbar)=\phi(\tau),
$$

费米场满足反周期边界条件：

$$
\psi(\tau+\beta\hbar)=-\psi(\tau).
$$

这产生玻色与费米不同的 Matsubara 频率。

## 相关函数的解析延拓

Euclidean 相关函数：

$$
G_E(\tau,\mathbf x)
$$

与 Lorentz 时间有序相关函数之间可在满足谱条件和解析性时通过复时间延拓联系。

Euclidean 数据并非任意函数都能对应一致的 Lorentz 量子场论。Osterwalder–Schrader 条件中的反射正性等性质保证可重构正定 Hilbert 空间和幺正时间演化。

数值格点计算只得到离散、带误差的 Euclidean 数据，从中恢复实时谱函数通常是病态逆问题，需要额外方法和先验。

## 为什么不是普通坐标旋转

空间中的旋转由实正交矩阵作用，保持 Euclidean 长度。Wick 旋转涉及复化时间或能量，并在 Lorentz 与 Euclidean 签名之间解析延拓。

名称中的“旋转”来自复平面中把积分轮廓转过约 $90^\circ$，不是实验室里转动坐标轴。

也不能说“时间轴乘 $i$ 后时间就不真实”。$i$ 是计算中的解析延拓工具，最终可观测量仍需回到物理 Lorentz 时空解释。

## 何时可能失败

Wick 旋转需要检查：

1. 被积函数在轮廓变形区域是否解析；
2. 是否穿过极点或分支切线；
3. 无穷远圆弧贡献是否消失；
4. Euclidean 作用量是否有适当下界；
5. 边界条件和真空选择是否匹配；
6. 是否存在化学势、实时非平衡或引力等额外困难。

有限密度费米系统常出现复行列式，Euclidean 权重不再正定。实时非平衡过程也通常不能只靠 Euclidean 数据直接得到。

在一般曲时空中，未必存在全局自然的实 Euclidean 截面；引力路径积分的共形因子还会造成作用量无下界问题。

## 与弦世界面的关系

Lorentz 世界面坐标可写为 $(\tau,\sigma)$。在微扰弦论中，常把世界面时间 Wick 旋转为 Euclidean 坐标，使世界面成为 Riemann 曲面。

Euclidean Polyakov 作用量示意为：

$$
S_E
=\frac{1}{4\pi\alpha'}
\int d^2\sigma\,
\sqrt h\,h^{ab}
\partial_aX^\mu\partial_bX_\mu.
$$

其中：

- $h_{ab}$：Euclidean 世界面度量；
- $X^\mu$：嵌入目标时空的坐标场；
- $\alpha'$：Regge 斜率参数；
- 世界面二次作用量使固定背景下的 $X^\mu$ 积分具有 Gaussian 结构。

Euclidean 化后可使用复坐标、全纯分解、Riemann 曲面和模空间。最终散射振幅仍需按外部动量和世界面处方解析延拓到物理运动学区域。

## 具体例子：谐振子

Lorentz Lagrangian：

$$
L_M
=\frac12m\dot x^2
-\frac12m\omega^2x^2.
$$

Wick 旋转后：

$$
S_E
=\int d\tau
\left[
\frac12m\left(\frac{dx}{d\tau}\right)^2
+\frac12m\omega^2x^2
\right].
$$

两项都非负。Euclidean 权重：

$$
e^{-S_E/\hbar}
$$

会抑制变化过快或偏离平衡位置过远的路径。

长 Euclidean 时间传播核近似：

$$
K_E(x_f,\tau;x_i,0)
\sim
\psi_0(x_f)\psi_0^*(x_i)
e^{-E_0\tau/\hbar}
$$

当基态唯一且端点与基态波函数重叠非零时成立。

## 适用条件与事实边界

1. Wick 旋转是解析延拓和轮廓变形，不是物理时间真的变成虚数。
2. $t=-i\tau$ 的符号依赖度量和 Fourier 约定，必须全程一致。
3. 传播子旋转必须结合 $i\varepsilon$ 极点处方。
4. Euclidean 作用量有下界时衰减权重最有用；负模和共形因子问题需额外处理。
5. Euclidean 相关函数返回 Lorentz 理论需要解析性、谱条件和反射正性等结构。
6. 有限密度、实时非平衡和一般曲时空可能没有简单 Wick 旋转。
7. 格点 Euclidean 数据到实时谱的解析延拓是困难逆问题。
8. 弦世界面 Euclidean 化后仍需规范固定、鬼场、模空间和物理运动学延拓。

## 常见误区

1. **Wick 旋转证明真实时间是虚数。** 它是复分析中的计算与定义工具。
2. **任何公式把 $t$ 换成 $-i\tau$ 都正确。** 必须同步变换测度、导数、场、作用量和边界条件。
3. **Euclidean 权重总能当作普通概率。** 费米行列式或拓扑项可能使权重为负或复数。
4. **旋转轮廓时可以穿过极点而不改变积分。** 穿过奇点通常会增加留数或改变结果。
5. **有了 Euclidean 理论就总能稳定恢复实时动力学。** 解析延拓对带噪离散数据通常病态。
6. **Wick 旋转会自动解决所有不稳定性。** 若 Euclidean 作用量无下界，积分仍有问题。
7. **Euclidean 弦世界面就是物理目标时空也变成 Euclidean。** 世界面和目标时空是不同几何对象，可分别选择签名与延拓。

## 练习

1. 用自己的话说明 Wick 旋转为什么叫复平面中的“旋转”。
2. 从 $t=-i\tau$ 推出 $\partial_t=i\partial_\tau$。
3. 把谐振子 Lorentz 作用量变为 Euclidean 作用量。
4. 为什么 $e^{iS_M/\hbar}$ 不是普通概率权重，而 $e^{-S_E/\hbar}$ 更适合数值采样？
5. $i\varepsilon$ 在传播子 Wick 旋转中起什么作用？
6. 为什么长 Euclidean 时间能投影到基态？
7. 列出至少两种简单 Wick 旋转可能失败或变复杂的情形。

## 答案与提示

1. 积分变量或时间轮廓从复平面的实轴方向连续转向虚轴方向，角度约为 $90^\circ$。
2. $\tau=it$，链式法则给 $\partial_t=(d\tau/dt)\partial_\tau=i\partial_\tau$。
3. 动能与势能在 $S_E$ 中均取正号：$S_E=\int d\tau[m(x')^2/2+m\omega^2x^2/2]$。
4. 前者是复相位并强烈振荡；后者在 $S_E$ 有下界时为衰减实权重，但仍需检查正定性。
5. 它移动极点并规定轮廓从哪侧经过，从而定义时间有序边界条件和可允许的旋转方向。
6. 每个能量分量乘 $e^{-E_n\tau/\hbar}$，高能态比最低能态衰减更快。
7. 例如有限化学势导致复行列式、实时非平衡、穿过极点或分支切线、引力共形因子无下界、无全局 Euclidean 截面的曲时空。

## 与其他概念的关系

- [[弦理论/数学/复数]] 和复平面轮廓变形提供解析延拓语言；
- [[弦理论/物理学/Minkowski 时空]] 与 Euclidean 空间具有不同度量签名；
- [[弦理论/物理学/路径积分]] 的实时权重经旋转变为 Euclidean 衰减权重；
- [[弦理论/物理学/二维 Euclidean 场论]] 固定二维复坐标、面积元、Green 函数与反射正性的共同约定；
- [[弦理论/数学/Gaussian 积分]] 在 Euclidean 正定二次型下更易收敛；
- [[弦理论/物理学/传播子]] 的解析延拓由极点和 $i\varepsilon$ 处方控制；
- [[弦理论/物理学/有限温场论]] 把 Euclidean 时间紧致为长度 $\beta\hbar$ 的圆；
- [[弦理论/物理学/世界面路径积分]] 常在 Euclidean Riemann 曲面上定义。

## 参考资料

- Gian-Carlo Wick, “Properties of Bethe-Salpeter Wave Functions,” *Physical Review* **96** (1954), 1124–1134.
- Michael E. Peskin and Daniel V. Schroeder, *An Introduction to Quantum Field Theory*, Westview Press, 1995.
- Steven Weinberg, *The Quantum Theory of Fields, Vol. 1*, Cambridge University Press, 1995.
- James Glimm and Arthur Jaffe, *Quantum Physics: A Functional Integral Point of View*, Springer, 1987.
- Konrad Osterwalder and Robert Schrader, “Axioms for Euclidean Green's Functions,” *Communications in Mathematical Physics* **31** (1973), 83–112; **42** (1975), 281–305.
- [David Tong, Quantum Field Theory](https://www.damtp.cam.ac.uk/user/tong/qft.html)
- Joseph Polchinski, *String Theory, Vol. 1*, Cambridge University Press, 1998.
