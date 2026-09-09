---
aliases:
  - Wilson Line and Wilson Loop
  - Wilson Line
  - Wilson Loop
  - 威尔逊线
  - 威尔逊圈
english_name: Wilson Line and Wilson Loop
tags:
  - 物理学
  - 量子场论
  - 规范理论
  - 弦理论先修
  - 弦理论
prerequisites:
  - "[[规范协变导数]]"
  - "[[Yang-Mills 理论]]"
  - "[[联络]]"
  - "[[曲率]]"
  - "[[群表示]]"
  - "[[Lie 群与 Lie 代数的对应]]"
used_by:
  - "[[弦理论完整学习路线图]]"
evidence_status: 教材事实
---

# Wilson 线与 Wilson 圈（Wilson Line and Wilson Loop）

## 学习导航

- 上一页：[[规范协变导数]]
- 下一页：[[规范固定]]
- 总路线：[[弦理论完整学习路线图]]

## 一句话解释

Wilson 线是规范联络沿有限路径的平行输运矩阵；路径闭合后取表示迹得到 Wilson 圈，它是规范不变的非局域算符，可探测有限 holonomy、全局群结构和非微扰规范动力学。

## 为什么要学它

[[规范协变导数]] 描述无穷小邻域内怎样比较物质场的内部方向，[[Yang-Mills 理论]] 用对易子 $[D_\mu,D_\nu]$ 定义局部场强 $F_{\mu\nu}$。但局部曲率不能完整回答以下问题：

1. 沿一条有限路径平行移动后，内部态发生什么群变换；
2. 绕闭合回路回到原点后，是否留下非平凡 holonomy；
3. 局部 $F_{\mu\nu}=0$ 时，全局拓扑是否仍能产生可观测相位；
4. 规范理论的禁闭、静态势和弦紧致化中的规范对称性破缺怎样用非局域算符表述。

Wilson 线与 Wilson 圈正是从局部联络过渡到有限路径和全局信息的基本工具。

## 本篇约定

继承前两页的约定：

$$
D_\mu=\partial_\mu-igA_\mu^{(R)},
\qquad
A_\mu^{(R)}=A_\mu^aT_R^a,
$$

其中同一个抽象 Lie 代数值规范势 $A_\mu=A_\mu^aT^a$ 在表示 $R$ 中写成矩阵 $A_\mu^{(R)}=A_\mu^aT_R^a$，$T_R^a$ 是 Hermitian 生成元。局域规范变换在该表示中写成

$$
\psi'(x)=U_R(x)\psi(x),
$$

$$
A_\mu^{(R)\prime}=U_RA_\mu^{(R)}U_R^{-1}+\frac{i}{g}U_R(\partial_\mu U_R^{-1}).
$$

后文在表示已经明确时，为简洁起见把 $A_\mu^{(R)}$ 记作 $A_\mu$。本页用 $C:x\to y$ 表示从起点 $x$ 到终点 $y$ 的定向分段光滑路径，并用参数 $s\in[0,1]$ 写成 $z^\mu(s)$，其中 $z(0)=x$、$z(1)=y$。

## 从协变导数到有限平行输运

沿路径 $C$ 平行移动表示 $R$ 中的场，要求切向协变导数为零：

$$
\dot z^\mu D_\mu\psi_R(z(s))=0.
$$

代入 $D_\mu=\partial_\mu-igA_\mu$：

$$
\frac{d\psi_R}{ds}
=
ig\,\dot z^\mu(s)A_\mu^a(z(s))T_R^a\psi_R.
$$

定义平行输运矩阵 $W_R[z(s),x;C]$ 使

$$
\psi_R(z(s))=W_R[z(s),x;C]\psi_R(x),
$$

则它满足初值问题

$$
\frac{dW_R(s)}{ds}
=
ig\,\dot z^\mu(s)A_\mu^a(z(s))T_R^aW_R(s),
\qquad
W_R(0)=I_R.
$$

其解就是开放 Wilson 线：

$$
\boxed{
W_R[y,x;C]
=
\mathcal P
\exp\left[
ig\int_C A_\mu^a(z)T_R^a\,dz^\mu
\right].
}
$$

这里 $W_R[y,x;C]$ 把起点纤维中的向量输运到终点纤维。它依赖路径、方向、表示以及规范联络。

## 路径排序为什么必要

若把路径参数记为 $s$，定义

$$
M(s)=ig\,\dot z^\mu(s)A_\mu(z(s)),
$$

则一般有

$$
[M(s_1),M(s_2)]\ne0.
$$

因此不能把矩阵积分当作普通数直接指数化。路径排序指数定义为 Dyson 型级数：

$$
\begin{aligned}
\mathcal P e^{\int_0^1ds\,M(s)}
={}&I
+\int_0^1ds_1\,M(s_1)\\
&+\int_0^1ds_1\int_0^{s_1}ds_2\,M(s_1)M(s_2)
+\cdots,
\end{aligned}
$$

其中较大的路径参数排在左侧。若采用相反排序约定，微分方程和矩阵乘法顺序也必须一起调整。

在 Abelian 理论中所有 $M(s)$ 彼此对易，$\mathcal P$ 才可以省略。

## 开放 Wilson 线的规范变换

规范变换后，平行输运矩阵满足

$$
\boxed{
W_R[y,x;C]
\longrightarrow
U_R(y)W_R[y,x;C]U_R^{-1}(x).
}
$$

证明可以把右边代入 Wilson 线的初值微分方程：终点的 $U_R(y)$ 作用于输出纤维，起点的 $U_R^{-1}(x)$ 作用于输入纤维。

因此开放 Wilson 线本身通常不是规范不变量，而是一个双端协变对象。它可与端点物质场组合，例如当 $\psi$ 属于同一表示时：

$$
\boxed{
\bar\psi(y)W_R[y,x;C]\psi(x)
}
$$

在相应端点变换下是规范不变量。

## 路径拼接与方向反转

设 $C_1:x\to y$、$C_2:y\to z$，先沿 $C_1$ 再沿 $C_2$，则

$$
\boxed{
W_R[z,x;C_2\circ C_1]
=
W_R[z,y;C_2]W_R[y,x;C_1].
}
$$

矩阵顺序与作用顺序一致：最先经过的路径段对应右侧矩阵。

若 $C^{-1}:y\to x$ 是反向路径，则

$$
\boxed{
W_R[x,y;C^{-1}]
=
W_R[y,x;C]^{-1}.
}
$$

对紧致群的幺正表示和实耦合 $g$，$A_\mu$ 为 Hermitian，Wilson 线是幺正矩阵，所以还可写成

$$
W_R[y,x;C]^{-1}=W_R[y,x;C]^\dagger.
$$

最后一个等号依赖幺正表示，不能无条件推广到任意复表示矩阵约定。

## 闭合路径与 Wilson 圈

当路径闭合为 $C:x\to x$ 时，未取迹的 holonomy 元素变换为

$$
W_R[x,x;C]
\longrightarrow
U_R(x)W_R[x,x;C]U_R^{-1}(x).
$$

它只在共轭意义下规范协变。取表示迹后得到 Wilson 圈算符：

$$
\boxed{
\mathcal W_R(C)
=
\operatorname{tr}_R
\mathcal P
\exp\left[
ig\oint_C A_\mu^aT_R^a\,dx^\mu
\right].
}
$$

利用迹的循环性，$\mathcal W_R(C)$ 在局域规范变换下不变。部分文献用 $\frac{1}{\dim R}\operatorname{tr}_R$ 归一化，使平凡联络时 $\mathcal W_R(C)=1$；本页默认不除以 $\dim R$，引用数值时必须核对归一化。

表示 $R$ 是物理定义的一部分。基本表示、伴随表示或其他表示的 Wilson 圈通常不是同一个可观测量；它们可探测规范群中心和允许的电荷表示。

## Abelian 极限与 Aharonov-Bohm 相位

在 $U(1)$ 理论中，生成元只是电荷数，矩阵彼此对易：

$$
W_q[y,x;C]
=
\exp\left(iq\int_C A_\mu dx^\mu\right),
$$

$$
\mathcal W_q(C)
=
\exp\left(iq\oint_C A_\mu dx^\mu\right).
$$

这里使用电磁约定 $D_\mu=\partial_\mu-iqA_\mu$；若采用 [[Dirac 场]] 中的 $D_\mu=\partial_\mu+iqA_\mu$，指数符号相反。

即使局部经过区域满足 $F_{\mu\nu}=0$，若路径绕过不可达磁通区域，闭合相位仍可非平凡。这就是 Aharonov-Bohm 效应揭示的全局 holonomy：局部场强为零不等于所有闭合 Wilson 圈都平凡。

## 与曲率和 holonomy 的关系

[[曲率]] 说明曲率测量无穷小平行移动的不对易。设一族闭合回路 $C_\ell=\partial\Sigma_\ell$ 的线性尺度为 $\ell$，并定义有向面积双向量

$$
\Sigma_\ell^{\mu\nu}
\equiv
\frac12\oint_{C_\ell}
\left[(z-x)^\mu dz^\nu-(z-x)^\nu dz^\mu\right],
$$

于是 $\Sigma_\ell^{\mu\nu}=O(\ell^2)$。当联络在基点附近足够光滑时，按本页方向和场强约定有

$$
W_R(C_\ell)
=
I_R+\frac{ig}{2}F_{\mu\nu}^a(x)T_R^a\,\Sigma_\ell^{\mu\nu}
+O(\ell^3).
$$

反对称指标按 Einstein 约定对所有 $\mu,\nu$ 求和，所以这里显式保留 $1/2$；若把 $\mu<\nu$ 的独立面积分量定义为 $\Sigma^{\mu\nu}$，同一公式常写成不带 $1/2$。$O(\ell^3)$ 项首先可含场强的协变导数，更高阶还包含多个场强的非对易排序。

在固定基点 $x$，所有以 $x$ 为起终点的分段光滑闭合路径的平行输运矩阵组成联络的 full holonomy 群 $\operatorname{Hol}_x$。其中可缩闭合路径产生的矩阵组成 restricted holonomy 群 $\operatorname{Hol}_x^0$，它是 $\operatorname{Hol}_x$ 的恒等连通分支。曲率控制 restricted holonomy 的无穷小 Lie 代数结构；不可缩回路和丛的全局结构还可贡献局部曲率看不到的离散 holonomy。

不能把非 Abelian Wilson 圈一般地写成普通的 $\exp(ig\int_\Sigma F)$。非 Abelian Stokes 公式需要曲面排序、参考路径或平行输运后的场强；省略这些结构会得到不规范协变的错误表达式。

## 非局域算符

局域算符只依赖一个时空点及其有限阶导数，而 Wilson 线依赖整条路径。因此它是规范理论中最基本的非局域算符之一。

这种非局域性不是计算缺陷，而是它能探测全局信息的原因：

- 路径是否绕过非平凡拓扑区域；
- 联络沿有限路径累积的群元素；
- 规范群的全局形式和允许表示；
- 非微扰真空及静态色源之间的相互作用。

## 静态势与禁闭判据

考虑 Euclidean 时空中空间宽度 $R$、时间长度 $T$ 的大矩形 Wilson 圈。为消除本页未归一化迹带来的平凡常数，定义

$$
w_R(C)\equiv\frac{1}{\dim R}\mathcal W_R(C).
$$

若 $T\to\infty$，其期望值与静态源势能 $V_R(R)$ 的关系为

$$
\langle w_R(C_{R\times T})\rangle
\sim
Z_R(R,T)\exp[-T V_R(R)],
$$

其中 $Z_R$ 可包含周长自能、尖点发散和方案依赖的重整化因子。使用未归一化的 $\mathcal W_R$ 只会额外引入与 $T$ 无关的 $\dim R$，不改变由大 $T$ 对数斜率提取的势能。

若大闭合圈满足面积律

$$
\langle w_R(C)\rangle
\sim
\exp[-\sigma\,\operatorname{Area}(C)],
$$

则 $V_R(R)\sim\sigma R$，表示静态源之间出现线性势。这是纯规范理论中讨论禁闭的重要判据。

边界条件必须说明：

1. 面积律通常讨论 Euclidean 真空期望值和大回路极限；
2. 动力学物质可通过弦断裂改变基本表示 Wilson 圈的渐近行为；
3. 表示的中心荷、screening 和全局规范群都会影响判据；
4. 一圈 beta 函数为负不能代替 Wilson 圈的非微扰分析。

## 与弦理论的关系

Wilson 线在弦理论中不是类比，而是实际出现的规范背景数据：

1. 开弦端点携带 Chan-Paton 标签，边界与背景规范势耦合时出现路径排序指数；
2. D-brane 世界体上的 Wilson 线描述开弦端点规范荷的平行输运；
3. 紧致维上的平坦但全局非平凡联络可由 Wilson 线模参数刻画，并能破缺低维有效理论的规范群；
4. T 对偶下，紧致方向的 Wilson 线可映射为 D-brane 在对偶圆上的位置；
5. 杂化弦紧致化中的 Wilson 线背景可改变规范群和质量谱。

这些结论依紧致化几何、全局规范群、边界条件和量子一致性条件，不能只由局部 Lie 代数决定。

## 与大模型路径的边界

Wilson 线与 Wilson 圈和大模型学习路径之间没有直接物理或算法对应。明确禁止：

- Wilson 线 $\ne$ token 序列、注意力路径或计算图路径；
- 路径排序 $\mathcal P\ne$ 位置编码或自回归顺序；
- holonomy $\ne$ 参数更新、隐藏状态累积或循环网络记忆；
- Wilson 圈面积律 $\ne$ 模型规模定律；
- 闭合路径取迹 $\ne$ attention 权重归一化。

[[弦理论与大模型跨学科关系图谱]] 只记录这些禁止误连，不建立强关系。

## 适用条件与事实边界

1. Wilson 线必须指定路径方向、表示 $R$、耦合和生成元约定。
2. 开放 Wilson 线是双端协变对象，不是单独的规范不变量。
3. 闭合 holonomy 矩阵只按共轭变换；取迹后才得到 Wilson 圈规范不变量。
4. 路径排序在非 Abelian 理论中不可省略。
5. 幺正性结论依赖紧致群的幺正表示和 Hermitian 生成元约定。
6. 小回路展开只在回路尺度足够小、联络足够光滑时成立。
7. 局部曲率决定无穷小 holonomy，但不能单独决定所有全局 Wilson 圈。
8. 面积律是特定非微扰极限中的判据，受动力学物质、screening 和全局群结构影响。
9. 不同表示的 Wilson 圈是不同算符，不能只写 $\operatorname{tr}$ 而不指定表示。
10. 本页不展开规范固定、鬼场、BRST 或格点数值方法。

## 常见误区

1. **Wilson 线只依赖端点。** 一般情况下它依赖整条定向路径。
2. **开放 Wilson 线本身规范不变。** 它按 $U(y)WU^{-1}(x)$ 变换。
3. **闭合路径不取迹也规范不变。** holonomy 矩阵按基点处的群元素共轭变换；只有其共轭类或迹等类函数规范不变。
4. **路径排序只是排版符号。** 非 Abelian 联络在不同路径参数处一般不对易。
5. **$F_{\mu\nu}=0$ 就保证所有 Wilson 圈为单位元。** 局部平坦联络仍可能有全局非平凡 holonomy。
6. **非 Abelian Wilson 圈等于普通面积指数 $e^{ig\int F}$。** 非 Abelian Stokes 关系需要额外排序和平行输运结构。
7. **指定 Lie 代数就确定所有 Wilson 线。** 允许表示和全局群商结构会改变 Wilson 算符谱。
8. **Wilson 圈面积律在有任意动力学物质时都等价于永久禁闭。** 弦断裂和 screening 会改变大距离行为。

## 练习

1. 从平行移动方程 $\dot z^\mu D_\mu\psi=0$ 推导 Wilson 线的初值微分方程。
2. 把路径排序指数展开到二阶，并解释为何 $M(s_1)M(s_2)$ 的顺序不能交换。
3. 验证开放 Wilson 线的规范变换律 $W[y,x]\to U(y)W[y,x]U^{-1}(x)$。
4. 证明路径拼接公式和反向路径公式。
5. 证明闭合 Wilson 圈 $\operatorname{tr}_R W[x,x;C]$ 规范不变。
6. 在 $U(1)$ 情形说明路径排序为何消失，并写出 Aharonov-Bohm 相位。
7. 对无穷小矩形回路，说明 $F_{\mu\nu}$ 怎样出现在 Wilson 线的一阶面积项中。
8. 由矩形 Wilson 圈的 $\langle w_R\rangle\sim e^{-TV_R(R)}$ 推导面积律对应线性势。
9. 解释为何 $SU(2)$ 与 $SO(3)$ 具有相同 Lie 代数，却允许不同的 Wilson 线表示。
10. 说明紧致方向 Wilson 线在 T 对偶下为何可与 D-brane 位置相关。

## 答案与提示

1. 写 $\psi(z(s))=W(s)\psi(x)$，代入 $\frac{d\psi}{ds}=ig\dot z^\mu A_\mu\psi$，对任意初态得到 $\frac{dW}{ds}=ig\dot z^\mu A_\mu W$，且 $W(0)=I$。
2. $W=I+\int_0^1ds_1M(s_1)+\int_0^1ds_1\int_0^{s_1}ds_2M(s_1)M(s_2)+\cdots$。若 $[M(s_1),M(s_2)]\ne0$，交换顺序会改变矩阵结果。
3. 令 $\widetilde W(s)=U(z(s))W(s)U^{-1}(x)$。利用 $A_\mu'$ 的变换律可验证 $\widetilde W$ 满足变换后联络的同一初值方程，且 $\widetilde W(0)=I$；解的唯一性给出终点公式。
4. 先沿 $C_1$ 后沿 $C_2$ 时，初态依次左乘 $W(C_1)$、$W(C_2)$，故总矩阵为 $W(C_2)W(C_1)$。再沿反向路径返回必须得到单位矩阵，所以 $W(C^{-1})=W(C)^{-1}$。
5. 闭合路径下 $W\to U(x)WU^{-1}(x)$，因此 $\operatorname{tr}_R(UWU^{-1})=\operatorname{tr}_R W$。
6. $U(1)$ 的联络值是普通数，所有路径参数处彼此对易，因此 $\mathcal P$ 可省略。闭合相位为 $\exp(iq\oint_C A_\mu dx^\mu)$（本题采用 $D_\mu=\partial_\mu-iqA_\mu$）。
7. 对边长均为 $O(\ell)$ 的小矩形，把四条边的短 Wilson 线按路径顺序相乘并保留到 $O(\ell^2)$；普通导数项与矩阵交换子组合成 $F_{\mu\nu}$。按正文的全反对称面积双向量定义，结果为 $W(C_\ell)=I+\frac{ig}{2}F_{\mu\nu}\Sigma_\ell^{\mu\nu}+O(\ell^3)$。
8. 面积为 $RT$，若 $\langle w_R\rangle\sim e^{-\sigma RT}$，与 $e^{-TV_R(R)}$ 的大 $T$ 指数比较得到 $V_R(R)\sim\sigma R$，忽略周长项、常数自能和重整化因子。
9. $SO(3)=SU(2)/\mathbb Z_2$ 不允许半整数自旋表示作为单值群表示，而 $SU(2)$ 允许。因此基本二维表示 Wilson 线可在 $SU(2)$ 理论定义，却不是纯 $SO(3)$ 规范理论中的合法线算符。
10. 紧致方向的常数规范势虽然局部场强可为零，但其绕圆 holonomy 改变开弦端点相位和动量量子化。T 对偶把该相位数据映射成端点所在 D-brane 在对偶圆上的位置。

## 与其他概念的关系

- [[规范协变导数]] 是 Wilson 线的无穷小起点；
- [[Yang-Mills 理论]] 定义规范势、场强和表示约定，并说明局部公式不能替代全局 holonomy；
- [[联络]] 用平行移动解释 Wilson 线的几何含义；
- [[曲率]] 给出小回路 holonomy 的局部控制量；
- [[群表示]] 说明不同表示中的 Wilson 算符为何不同；
- [[Lie 群与 Lie 代数的对应]] 说明 Wilson 线还依赖全局规范群，而不只依赖 Lie 代数；
- [[Maxwell 场量子化]] 说明紧致空间中的 Wilson 线和磁通自由度不包含在局部平面波计数中；
- [[弦理论完整学习路线图]] 将本节点放在规范协变导数之后、规范固定之前。

## 参考资料

- Kenneth G. Wilson, "Confinement of Quarks," *Physical Review D* 10 (1974), 2445–2459. https://doi.org/10.1103/PhysRevD.10.2445
- Michael E. Peskin and Daniel V. Schroeder, *An Introduction to Quantum Field Theory*, Westview Press, 1995, Chapter 15.
- Mark Srednicki, *Quantum Field Theory*, Cambridge University Press, 2007, Chapters 69–74.
- David Tong, *Gauge Theory*, arXiv:1707.07845. https://arxiv.org/abs/1707.07845
- M. Nakahara, *Geometry, Topology and Physics*, 2nd ed., IOP Publishing, 2003, Chapters 9–10.
- Joseph Polchinski, *String Theory, Vol. 1–2*, Cambridge University Press, 1998.