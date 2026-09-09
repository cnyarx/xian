---
aliases: [Gaussian Integral, Gaussian Integration, 高斯积分]
english_name: Gaussian Integral
tags: [数学, 积分, 线性代数, 量子场论先修]
prerequisites:
  - "[[弦理论/数学/积分]]"
  - "[[弦理论/数学/多重积分]]"
  - "[[弦理论/数学/指数函数]]"
  - "[[弦理论/数学/矩阵]]"
  - "[[弦理论/数学/复数]]"
used_by:
  - "[[弦理论/物理学/路径积分]]"
  - "[[弦理论/物理学/Wick 旋转]]"
  - "[[弦理论/物理学/生成泛函]]"
  - "[[弦理论/物理学/传播子]]"
  - "[[弦理论/物理学/微扰论]]"
evidence_status: 教材事实
---

# Gaussian 积分（Gaussian Integral）

## 一句话解释

Gaussian 积分是指数中含负二次函数的积分；最基本结果是 $\int_{-\infty}^{\infty}e^{-x^2}dx=\sqrt\pi$。

## 为什么要学它

Gaussian 函数出现在正态分布、扩散、量子谐振子、热核和最小不确定波包中。更重要的是，自由量子场的作用量对场是二次的，因此它的路径积分本质上是无限维 Gaussian 积分。

加入线性源后，Gaussian 积分直接产生两点函数和传播子。微扰论则把相互作用看成围绕 Gaussian 自由理论的展开。

## 直观图景

函数：

$$
e^{-x^2}
$$

在 $x=0$ 取最大值 $1$，离原点越远衰减越快。它在整条实轴下仍有有限面积。

看似需要先求 $e^{-x^2}$ 的原函数，但这个原函数不能用有限个常见初等函数表示。Gaussian 积分的巧妙之处是：不直接求原函数，而是把一维积分平方，转成容易处理的二维圆对称积分。

## 基本定义

最基本的 Gaussian 积分记为：

$$
I=\int_{-\infty}^{\infty}e^{-x^2}dx.
$$

被积函数为正，因此 $I>0$。由于 $e^{-x^2}$ 在无穷远比任意幂函数下降得更快，积分收敛。

结果为：

$$
I=\sqrt\pi.
$$

## 平方技巧

先写：

$$
I^2
=\left(\int_{-\infty}^{\infty}e^{-x^2}dx\right)
\left(\int_{-\infty}^{\infty}e^{-y^2}dy\right).
$$

把两个独立积分合成平面积分：

$$
I^2
=\int_{\mathbb R^2}
e^{-(x^2+y^2)}dx\,dy.
$$

因为被积函数非负，可用 Tonelli 定理交换和组合积分；入门计算中也可先在有限正方形上计算再取极限。

## 改用极坐标

令：

$$
x=r\cos\theta,
\qquad
y=r\sin\theta.
$$

于是：

$$
x^2+y^2=r^2,
$$

面积元变为：

$$
dx\,dy=r\,dr\,d\theta.
$$

因此：

$$
I^2
=\int_0^{2\pi}d\theta
\int_0^{\infty}re^{-r^2}dr.
$$

其中额外因子 $r$ 是极坐标变换的 Jacobian，不能漏掉。

## 完成推导

令：

$$
u=r^2,
\qquad
du=2r\,dr.
$$

则：

$$
\int_0^{\infty}re^{-r^2}dr
=\frac12\int_0^{\infty}e^{-u}du
=\frac12.
$$

角度积分为：

$$
\int_0^{2\pi}d\theta=2\pi.
$$

所以：

$$
I^2=2\pi\times\frac12=\pi.
$$

由于 $I>0$：

$$
I=\sqrt\pi.
$$

正根的选择来自原积分的被积函数为正。

## 带正系数的 Gaussian 积分

对实数 $a>0$：

$$
\int_{-\infty}^{\infty}e^{-ax^2}dx
=\sqrt{\frac\pi a}.
$$

推导只需令：

$$
u=\sqrt a\,x,
\qquad
dx=\frac{du}{\sqrt a}.
$$

于是：

$$
\int e^{-ax^2}dx
=\frac1{\sqrt a}\int e^{-u^2}du.
$$

条件 $a>0$ 保证实轴两端指数衰减。若 $a<0$，被积函数在无穷远指数增长，普通实积分发散。

## 带线性项的积分

考虑：

$$
I(a,b)
=\int_{-\infty}^{\infty}
\exp(-ax^2+bx)dx,
\qquad a>0.
$$

配方：

$$
-ax^2+bx
=-a\left(x-\frac{b}{2a}\right)^2
+\frac{b^2}{4a}.
$$

所以：

$$
I(a,b)
=
\exp\left(\frac{b^2}{4a}\right)
\int_{-\infty}^{\infty}
\exp\left[-a\left(x-\frac{b}{2a}\right)^2\right]dx.
$$

平移积分变量后：

$$
I(a,b)
=\sqrt{\frac\pi a}
\exp\left(\frac{b^2}{4a}\right).
$$

这里 $b$ 可为实数；在满足收敛与解析延拓条件时也可推广到复数。

## 公式中每个符号的意思

在：

$$
\int_{-\infty}^{\infty}
e^{-ax^2+bx}dx
=
\sqrt{\frac\pi a}
e^{b^2/(4a)}
$$

中：

- $x$：实积分变量；
- $a$：二次项系数，实积分收敛要求 $a>0$；
- $b$：线性源或偏移参数；
- $\pi$：圆周率；
- $dx$：对 $x$ 的积分测度；
- $b^2/(4a)$：完成平方后留下的常数项。

若指数必须无量纲，则 $ax^2$ 和 $bx$ 都应无量纲。因此 $a$ 的量纲是 $x^{-2}$，$b$ 的量纲是 $x^{-1}$；右侧 $1/\sqrt a$ 与 $dx$ 具有相同量纲。

## 用源生成矩

定义归一化 Gaussian：

$$
Z(b)
=\int_{-\infty}^{\infty}
\exp\left(-\frac12ax^2+bx\right)dx.
$$

结果为：

$$
Z(b)
=\sqrt{\frac{2\pi}{a}}
\exp\left(\frac{b^2}{2a}\right).
$$

对 $b$ 求导会带下 $x$：

$$
\frac{dZ}{db}
=\int x
\exp\left(-\frac12ax^2+bx\right)dx.
$$

二阶导数带下 $x^2$：

$$
\frac{d^2Z}{db^2}
=\int x^2
\exp\left(-\frac12ax^2+bx\right)dx.
$$

因此线性参数 $b$ 像“源”，通过求导生成不同阶矩。这正是量子场论生成泛函的有限维原型。

## 奇次矩与偶次矩

对中心在零点的 Gaussian：

$$
\int_{-\infty}^{\infty}
x^{2n+1}e^{-ax^2}dx=0.
$$

原因是 $x^{2n+1}$ 为奇函数，$e^{-ax^2}$ 为偶函数，乘积为奇函数，在对称区间积分为零。

偶次矩非零。例如：

$$
\int_{-\infty}^{\infty}
x^2e^{-ax^2}dx
=
\frac{\sqrt\pi}{2a^{3/2}}.
$$

可对基本积分关于 $a$ 求导得到：

$$
-\frac{d}{da}
\int e^{-ax^2}dx
=
\int x^2e^{-ax^2}dx.
$$

## 正态分布的归一化

均值为 $\mu$、标准差为 $\sigma>0$ 的正态概率密度：

$$
p(x)
=\frac{1}{\sqrt{2\pi\sigma^2}}
\exp\left[-\frac{(x-\mu)^2}{2\sigma^2}\right].
$$

Gaussian 积分保证：

$$
\int_{-\infty}^{\infty}p(x)dx=1.
$$

其中：

- $\mu$：分布中心；
- $\sigma^2$：方差；
- 前因子：归一化常数。

如果漏掉前因子，表达式只有钟形形状，却不是总概率为一的概率密度。

## 多维 Gaussian 积分

设 $A$ 是实对称正定的 $n\times n$ 矩阵，$x\in\mathbb R^n$。则：

$$
\int_{\mathbb R^n}d^nx\,
\exp\left(-\frac12x^TAx\right)
=
\frac{(2\pi)^{n/2}}{\sqrt{\det A}}.
$$

符号含义：

- $x$：$n$ 维实列向量；
- $x^T$：转置行向量；
- $A$：实对称正定矩阵；
- $x^TAx$：二次型；
- $d^nx=dx_1\cdots dx_n$：多维积分测度；
- $\det A$：矩阵行列式。

正定性保证每个方向上二次型都为正，指数在无穷远衰减。

## 多维公式的推导思路

实对称正定矩阵可以由正交矩阵对角化：

$$
A=O^TDO,
$$

其中：

$$
D=\operatorname{diag}(\lambda_1,\ldots,\lambda_n),
\qquad\lambda_i>0.
$$

令：

$$
y=Ox.
$$

正交变换的 Jacobian 绝对值为 $1$，所以测度不变。二次型变为：

$$
x^TAx
=\sum_{i=1}^n\lambda_i y_i^2.
$$

多维积分分解成 $n$ 个一维积分：

$$
\prod_{i=1}^n
\sqrt{\frac{2\pi}{\lambda_i}}
=
\frac{(2\pi)^{n/2}}
{\sqrt{\lambda_1\cdots\lambda_n}}.
$$

由于：

$$
\det A=\lambda_1\cdots\lambda_n,
$$

得到多维公式。

## 带多维线性源

对实对称正定 $A$ 和列向量 $J$：

$$
Z(J)
=
\int d^nx\,
\exp\left(
-\frac12x^TAx+J^Tx
\right).
$$

完成平方：

$$
-\frac12x^TAx+J^Tx
=
-\frac12(x-A^{-1}J)^TA(x-A^{-1}J)
+\frac12J^TA^{-1}J.
$$

所以：

$$
Z(J)
=
\frac{(2\pi)^{n/2}}{\sqrt{\det A}}
\exp\left(\frac12J^TA^{-1}J\right).
$$

$A^{-1}$ 是二次算符的逆。在场论中，它推广为 Green 函数或传播子。

## 两点关联的有限维原型

归一化后，对源求两次导数并令 $J=0$：

$$
\langle x_ix_j\rangle
=\left.
\frac{1}{Z(0)}
\frac{\partial^2Z(J)}
{\partial J_i\partial J_j}
\right|_{J=0}
=(A^{-1})_{ij}.
$$

这条公式表示：Gaussian 分布的协方差矩阵是二次型矩阵的逆。

在自由场论中，作用量中的微分算符扮演 $A$，传播子扮演 $A^{-1}$。这就是“自由理论的二点函数是动力学算符的 Green 函数”的有限维模型。

## 零模与发散

若 $A$ 只有半正定而存在零本征值：

$$
\lambda_i=0,
$$

则：

$$
\det A=0,
$$

公式表面发散。对应方向上指数没有衰减，积分体积无限。

物理中零模可能来自：

- 平移对称性；
- 规范冗余；
- 连续真空简并；
- 边界条件产生的零频模式。

处理方法可能包括分离零模、除以对称群体积、规范固定或引入适当红外调节。不能在 $\det A=0$ 时直接套用正定公式。

## 复 Gaussian 积分

对一个复变量 $z=x+iy$，在约定 $d^2z=dx\,dy$ 下：

$$
\int_{\mathbb C}d^2z\,
e^{-a|z|^2}
=\frac\pi a,
\qquad a>0.
$$

因为：

$$
|z|^2=x^2+y^2,
$$

积分分解为两个一维 Gaussian 积分。

不同文献对 $d^2z$、$dz\,d\bar z$ 的归一化约定不同，可能出现 $2$ 或 $i$ 的因子，计算前必须核对测度定义。

## 振荡 Gaussian 积分

量子力学实时路径积分含有：

$$
e^{iS/\hbar},
$$

因此会遇到振荡积分，例如：

$$
\int_{-\infty}^{\infty}e^{iax^2}dx.
$$

它不像 $e^{-ax^2}$ 那样绝对收敛。通常引入小的阻尼处方：

$$
a\to a+i0
$$

或把时间做 Wick 旋转，使指数变成衰减的 Euclidean Gaussian，再通过解析延拓返回。

在适当支路和处方下，结果含相位：

$$
\int_{-\infty}^{\infty}e^{iax^2}dx
=e^{i\pi/4}\sqrt{\frac\pi a},
\qquad a>0,
$$

应理解为带收敛处方的 Fresnel 积分，而不是普通绝对收敛积分。

## Grassmann Gaussian 对照

普通实变量 Gaussian 积分给：

$$
(\det A)^{-1/2}.
$$

复 Grassmann 变量的 Gaussian 积分给：

$$
\int\prod_i d\bar\psi_i\,d\psi_i\,
\exp(-\bar\psi_iA_{ij}\psi_j)
=\det A
$$

在固定变量和测度顺序约定下成立。

因此玻色二次涨落常给行列式的负幂，费米二次涨落常给行列式的正幂。这是量子场论一圈修正和超对称抵消的核心结构。

## 从有限维到路径积分

把时间离散成许多小段后，一条路径由有限多个坐标值近似：

$$
(x_1,x_2,\ldots,x_N).
$$

自由粒子或谐振子的离散作用量是这些变量的二次型，因此路径积分近似为高维 Gaussian 积分。

令分割越来越细，形式上得到无限维极限。此时归一化、边界条件、零模、算符行列式和收敛都需要额外定义。

所以“路径积分只是普通 Gaussian 积分”只对自由二次理论的结构而言；严格无限维测度远比有限维积分微妙。

## 鞍点近似中的 Gaussian

一般积分：

$$
I(\hbar)=\int dx\,e^{-S(x)/\hbar}
$$

在小 $\hbar$ 时主要由 $S$ 的极小点附近贡献。设：

$$
S'(x_0)=0,
$$

在 $x_0$ 附近展开：

$$
S(x)
\approx S(x_0)
+\frac12S''(x_0)(x-x_0)^2.
$$

于是积分近似为：

$$
I(\hbar)
\approx
e^{-S(x_0)/\hbar}
\sqrt{\frac{2\pi\hbar}{S''(x_0)}}
$$

当 $S''(x_0)>0$ 且高阶项受控时成立。

这说明即使理论不是严格二次的，经典解附近的首个量子涨落通常仍由 Gaussian 积分决定。

## 具体例子

计算：

$$
\int_{-\infty}^{\infty}
e^{-2x^2+4x}dx.
$$

配方：

$$
-2x^2+4x
=-2(x-1)^2+2.
$$

因此：

$$
\int e^{-2x^2+4x}dx
=e^2\int e^{-2(x-1)^2}dx.
$$

平移变量后：

$$
\int_{-\infty}^{\infty}
e^{-2x^2+4x}dx
=e^2\sqrt{\frac\pi2}.
$$

可以与通式 $a=2,b=4$ 核对：

$$
\sqrt{\frac\pi2}
\exp\left(\frac{4^2}{4\times2}\right)
=e^2\sqrt{\frac\pi2}.
$$

## 适用条件与事实边界

1. 实轴基本 Gaussian 积分要求二次项实部为正，保证无穷远衰减。
2. 多维公式要求二次型正定；有负模或零模时必须修改积分轮廓或单独处理。
3. 对非对称矩阵，二次型只依赖其对称部分；常规公式应先明确矩阵性质。
4. 复参数结果涉及平方根支路和积分轮廓，不能只把实公式机械代入。
5. 振荡 Fresnel 积分需要收敛处方或分布意义，不是普通绝对收敛积分。
6. 无限维路径积分的行列式需要正规化，有限维公式只提供结构原型。
7. Gaussian 鞍点近似要求高阶项在所研究极限中受控，并需处理负模和零模。
8. Grassmann Gaussian 的符号依赖变量和测度排序，但行列式结构是稳定核心。

## 常见误区

1. **$e^{-x^2}$ 有简单初等原函数，所以直接代上下限即可。** 它没有有限初等函数原函数，定积分用平方技巧求得。
2. **极坐标面积元仍是 $dr\,d\theta$。** 必须包含 Jacobian 因子 $r$。
3. **$\int e^{-ax^2}dx=\sqrt{\pi/a}$ 对任意实 $a$ 都收敛。** 普通实积分要求 $a>0$。
4. **多维公式对任何矩阵都可直接使用。** 收敛需要正定实部，并要处理零模和负模。
5. **行列式为零时公式仍给有限结果。** 这通常表示存在未抑制方向，积分发散或需单独处理。
6. **振荡路径积分与衰减 Gaussian 完全相同。** 它需要 $i\varepsilon$ 处方或 Wick 旋转。
7. **有限维 Gaussian 公式自动严格定义量子场路径积分。** 无限维极限还需正规化、边界条件和测度定义。

## 练习

1. 用自己的话解释为什么把一维 Gaussian 积分平方会有帮助。
2. 推导 $\int_{-\infty}^{\infty}e^{-ax^2}dx=\sqrt{\pi/a}$，其中 $a>0$。
3. 计算 $\int_{-\infty}^{\infty}e^{-3x^2+6x}dx$。
4. 为什么所有奇次矩 $\int x^{2n+1}e^{-ax^2}dx$ 都为零？
5. 对对角矩阵 $A=\operatorname{diag}(a,b)$，验证二维 Gaussian 公式。
6. 若 $A$ 有一个零本征值，积分为什么发散？
7. 比较玻色实变量 Gaussian 与复 Grassmann Gaussian 产生的行列式幂次。

## 答案与提示

1. 平方后指数成为 $x^2+y^2$，具有圆对称性，可用极坐标把二维积分化成简单径向积分。
2. 令 $u=\sqrt a\,x$，测度给出 $1/\sqrt a$，再使用基本积分 $\sqrt\pi$。
3. 配方 $-3x^2+6x=-3(x-1)^2+3$，结果为 $e^3\sqrt{\pi/3}$。
4. 被积函数是奇函数，积分区间关于零对称。
5. 积分分解为 $\sqrt{2\pi/a}\sqrt{2\pi/b}=2\pi/\sqrt{ab}$，而 $\det A=ab$。
6. 零本征方向上指数不含二次衰减，沿该方向积分相当于无限长度的常数积分。
7. 实玻色积分与 $(\det A)^{-1/2}$ 成比例；复 Grassmann 积分给 $\det A$。

## 与其他概念的关系

- [[弦理论/数学/积分]] 和 [[弦理论/数学/多重积分]] 提供一维与多维积分规则；
- [[弦理论/数学/矩阵]] 的特征值、对角化和行列式控制多维二次型；
- [[弦理论/物理学/概率]] 中的正态分布由 Gaussian 积分归一化；
- [[大模型学习教程/01-数学基础/04-概率分布|概率分布]] 与 [[大模型学习教程/15-概念词典/35-正态分布与常见分布|正态分布与常见分布]] 使用这里的积分结果确定正态密度的归一化常数；Gaussian 积分是积分方法，正态分布则是满足总概率为一的概率模型，二者不能直接等同；
- [[弦理论/物理学/量子谐振子]] 的基态波函数是 Gaussian；
- [[弦理论/数学/Grassmann 变量]] 给出费米 Gaussian 积分；
- [[弦理论/物理学/路径积分]] 把自由理论化为无限维 Gaussian 结构；
- [[弦理论/物理学/Wick 旋转]] 把部分振荡积分转为衰减积分；
- [[弦理论/物理学/生成泛函]] 通过源导数生成关联函数；
- [[弦理论/物理学/传播子]] 是二次动力学算符的逆；
- [[弦理论与大模型跨学科关系图谱]] 汇总本概念与大模型学习路径中的强连接及边界。

## 参考资料

- [MIT OCW 18.02SC, Multivariable Calculus](https://ocw.mit.edu/courses/18-02sc-multivariable-calculus-fall-2010/)
- George B. Arfken, Hans J. Weber and Frank E. Harris, *Mathematical Methods for Physicists*, 7th ed., Academic Press, 2012.
- Carl M. Bender and Steven A. Orszag, *Advanced Mathematical Methods for Scientists and Engineers I*, Springer, 1999.
- Michael E. Peskin and Daniel V. Schroeder, *An Introduction to Quantum Field Theory*, Westview Press, 1995.
- Hagen Kleinert, *Path Integrals in Quantum Mechanics, Statistics, Polymer Physics, and Financial Markets*, World Scientific.
- [David Tong, Quantum Field Theory](https://www.damtp.cam.ac.uk/user/tong/qft.html)
- Joseph Polchinski, *String Theory, Vol. 1*, Cambridge University Press, 1998.
