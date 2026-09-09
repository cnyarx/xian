---
aliases:
  - Dirac Field
  - Dirac Spinor Field
english_name: Dirac Field
tags:
  - 物理学
  - 量子场论
  - 费米子
  - 弦理论先修
prerequisites:
  - "[[弦理论/物理学/Klein-Gordon 场]]"
  - "[[弦理论/物理学/费米子]]"
  - "[[弦理论/数学/旋量]]"
  - "[[弦理论/数学/Gamma 矩阵]]"
  - "[[弦理论/数学/Clifford 代数]]"
  - "[[弦理论/物理学/作用量]]"
  - "[[弦理论/物理学/场的 Euler-Lagrange 方程]]"
  - "[[弦理论/物理学/Minkowski 时空]]"
  - "[[弦理论/物理学/量子算符]]"
used_by:
  - "[[弦理论/物理学/场的正则量子化]]"
  - "[[弦理论/物理学/传播子]]"
  - "[[弦理论/物理学/时序乘积]]"
  - "[[弦理论/物理学/Wick 定理]]"
  - "[[弦理论/物理学/二维自由费米子]]"
  - "[[弦理论/物理学/世界面费米子]]"
  - "[[弦理论/物理学/RNS 超弦理论]]"
  - "[[弦理论/物理学/规范协变导数]]"
  - "[[弦理论/物理学/手征反常]]"
evidence_status: 教材事实
---

# Dirac 场（Dirac Field）

## 一句话解释

Dirac 场是按 Lorentz 旋量变换的相对论场；它的一阶方程用 Gamma 矩阵把时间和空间导数统一起来，量子化后描述自旋 $1/2$ 的费米子与反费米子。

## 为什么要学它

Klein-Gordon 方程是时间二阶方程，不能直接提供正定的单粒子位置概率密度。Dirac 的目标是构造一个时间一阶、空间也一阶，同时保持 Lorentz 协变的相对论方程。

Dirac 场把以下概念连在一起：

- 相对论能量—动量关系；
- Clifford 代数与 Gamma 矩阵；
- 旋量和半整数自旋；
- 粒子与反粒子；
- Pauli 不相容原理和费米反对易关系；
- 手征性、质量项与规范相互作用。

RNS 超弦的世界面费米子、Ramond 扇区零模和时空旋量谱都建立在同一套旋量与 Clifford 代数语言上。

## 直观图景

普通标量场在每个时空点只放一个数。Dirac 场则在每一点放一个多分量“旋量箭头”：它不是普通空间箭头，而是在旋转 $360^\circ$ 后可能变号、旋转 $720^\circ$ 才完全回到原状的对象。

Gamma 矩阵像一组齿轮，把时空方向的导数与旋量分量连接起来。它们满足特殊反对易关系，使一阶 Dirac 算符平方后正好产生二阶 Klein-Gordon 算符。

因此 Dirac 方程不是绕开相对论质量壳，而是对它进行“矩阵平方根”。

## 本篇约定

采用自然单位：

$$
\hbar=c=1,
$$

四维 mostly-minus Minkowski 度规：

$$
\eta_{\mu\nu}
=\operatorname{diag}(+1,-1,-1,-1),
$$

Gamma 矩阵满足：

$$
\{\gamma^\mu,\gamma^\nu\}
=2\eta^{\mu\nu}I_4.
$$

因此：

$$
(\gamma^0)^2=I_4,
\qquad
(\gamma^i)^2=-I_4.
$$

Dirac 共轭定义为：

$$
\bar\psi=\psi^\dagger\gamma^0.
$$

若改用 mostly-plus 度规或不同 Clifford 关系，部分公式的符号和共轭约定会变化，比较资料时必须整套核对。

## 每个符号是什么意思

- $\psi(x)$：四分量 Dirac 旋量场；
- $\bar\psi$：Dirac 共轭，不是逐分量普通复共轭；
- $\psi^\dagger$：Hermitian 共轭，即复共轭后转置；
- $\gamma^\mu$：Gamma 矩阵，作用在旋量分量上；
- $\mu=0,1,2,3$：时空指标；
- $i=1,2,3$：空间指标；
- $m$：质量参数；
- $\slashed\partial=\gamma^\mu\partial_\mu$：Feynman 斜线记号；
- $I_4$：四阶单位矩阵；
- $\{A,B\}=AB+BA$：反对易子；
- $u_s(p)$、$v_s(p)$：正能粒子和反粒子的旋量波函数；
- $s$：自旋或 helicity 标签。

## Dirac 方程

自由 Dirac 方程为：

$$
\boxed{
(i\gamma^\mu\partial_\mu-m)\psi=0
}.
$$

用斜线记号写成：

$$
(i\slashed\partial-m)\psi=0.
$$

它对时间和空间都是一阶微分方程。展开时间导数：

$$
i\partial_t\psi
=\left(-i\boldsymbol\alpha\cdot\nabla+\beta m\right)\psi,
$$

其中：

$$
\alpha^i=\gamma^0\gamma^i,
\qquad
\beta=\gamma^0.
$$

括号中的算符就是单粒子 Dirac Hamiltonian：

$$
H_D=-i\boldsymbol\alpha\cdot\nabla+\beta m.
$$

在量子场论中，$\psi$ 本身进一步提升为算符值分布；不能把整个量子 Dirac 场只当作一个普通单粒子波函数。

## 为什么需要 Gamma 矩阵

相对论质量壳关系为：

$$
E^2=\mathbf p^2+m^2.
$$

Dirac 希望找一个对能量和动量都一阶的方程：

$$
E\psi=(\boldsymbol\alpha\cdot\mathbf p+\beta m)\psi.
$$

平方后要恢复质量壳：

$$
(\boldsymbol\alpha\cdot\mathbf p+\beta m)^2
=\mathbf p^2+m^2.
$$

这要求矩阵满足：

$$
\{\alpha^i,\alpha^j\}=2\delta^{ij},
$$

$$
\{\alpha^i,\beta\}=0,
\qquad
\beta^2=I.
$$

这些关系正是 Minkowski Clifford 代数的另一种写法。普通数无法同时满足这些条件，所以系数必须是矩阵，波函数必须有多个旋量分量。

## Dirac 方程怎样推出 Klein-Gordon 方程

从：

$$
(i\gamma^\mu\partial_\mu-m)\psi=0
$$

左乘：

$$
(i\gamma^\nu\partial_\nu+m).
$$

得到：

$$
\left[(i\slashed\partial)^2-m^2\right]\psi=0.
$$

由于偏导数彼此对易：

$$
\gamma^\mu\gamma^\nu\partial_\mu\partial_\nu
=\frac12\{\gamma^\mu,\gamma^\nu\}
\partial_\mu\partial_\nu
=\eta^{\mu\nu}\partial_\mu\partial_\nu
=\Box.
$$

而 $i^2=-1$，所以：

$$
(i\slashed\partial)^2=-\Box.
$$

最终得到：

$$
\boxed{(\Box+m^2)\psi=0}.
$$

这里表示 $\psi$ 的每个旋量分量都满足 Klein-Gordon 方程。但反过来不成立：满足 KG 方程的四分量函数未必满足 Dirac 的一阶约束。

## 平面波解

取：

$$
\psi(x)=u(p)e^{-ip\cdot x}.
$$

因为：

$$
i\partial_\mu e^{-ip\cdot x}
=p_\mu e^{-ip\cdot x},
$$

Dirac 方程变成代数方程：

$$
\boxed{(\slashed p-m)u(p)=0},
$$

其中：

$$
\slashed p=\gamma^\mu p_\mu.
$$

左乘 $\slashed p+m$：

$$
(\slashed p+m)(\slashed p-m)u
=(p^2-m^2)u=0.
$$

非零解要求：

$$
p^2=m^2.
$$

所以 Dirac 场仍服从同一相对论质量壳。

## 粒子与反粒子旋量

量子场展开通常写成：

$$
\psi(x)
=\sum_s\int
\frac{d^3p}{(2\pi)^3\sqrt{2E_{\mathbf p}}}
\left[
b_s(\mathbf p)u_s(p)e^{-ip\cdot x}
+d_s^\dagger(\mathbf p)v_s(p)e^{+ip\cdot x}
\right],
$$

其中：

$$
E_{\mathbf p}=\sqrt{\mathbf p^2+m^2},
\qquad p^0=E_{\mathbf p}>0.
$$

两类旋量满足：

$$
(\slashed p-m)u_s(p)=0,
$$

$$
(\slashed p+m)v_s(p)=0.
$$

符号含义：

- $b_s$：湮灭一个粒子的算符；
- $b_s^\dagger$：产生一个粒子的算符；
- $d_s$：湮灭一个反粒子的算符；
- $d_s^\dagger$：产生一个反粒子的算符；
- $u_s$：粒子旋量；
- $v_s$：反粒子旋量。

负频部分不表示存在可自由掉到任意负能量的粒子。量子场论把它重新组织成正能反粒子的产生算符，从而使 Hamiltonian 有下界。

## 为什么 Dirac 共轭不是普通复共轭

Lorentz 变换下：

$$
\psi'(x')=S(\Lambda)\psi(x).
$$

普通内积 $\psi^\dagger\psi$ 对旋转不变，但一般 Lorentz boost 下不能直接组成标量。

定义：

$$
\bar\psi=\psi^\dagger\gamma^0
$$

后，在本篇约定下满足：

$$
\bar\psi'(x')
=\bar\psi(x)S^{-1}(\Lambda).
$$

因此：

$$
\bar\psi\psi
$$

是 Lorentz 标量，而：

$$
\bar\psi\gamma^\mu\psi
$$

按 Lorentz 向量变换。

## Dirac 场的作用量

自由 Dirac 场作用量为：

$$
\boxed{
S[\psi,\bar\psi]
=\int d^4x\,
\bar\psi(i\gamma^\mu\partial_\mu-m)\psi
}.
$$

Lagrangian 密度为：

$$
\mathcal L_D
=\bar\psi(i\slashed\partial-m)\psi.
$$

它对 $\psi$ 只含一阶导数，因此场方程也是一阶的。

经典费米场通常取 Grassmann 奇变量。做变分时必须固定左导数或右导数约定，因为交换 Grassmann 奇量会产生负号。

## 从作用量得到场方程

在经典变分中，把 $\psi$ 和 $\bar\psi$ 当作独立 Grassmann 变量。

对 $\bar\psi$ 变分，直接得到：

$$
(i\slashed\partial-m)\psi=0.
$$

对 $\psi$ 变分并分部积分，得到共轭方程：

$$
\bar\psi
(i\overleftarrow{\slashed\partial}+m)=0,
$$

其中：

$$
\bar\psi\overleftarrow{\slashed\partial}
=(\partial_\mu\bar\psi)\gamma^\mu.
$$

展开为：

$$
i(\partial_\mu\bar\psi)\gamma^\mu
+m\bar\psi=0.
$$

边界项消失需要变分在边界为零，或场满足适当衰减条件。

## Lagrangian 的 Hermitian 性

直接写出的 $\mathcal L_D$ 与其 Hermitian 共轭可相差一个总导数。常使用显式对称形式：

$$
\mathcal L_D
=\frac{i}{2}
\left[
\bar\psi\gamma^\mu\partial_\mu\psi
-(\partial_\mu\bar\psi)\gamma^\mu\psi
\right]
-m\bar\psi\psi.
$$

它与原形式在忽略边界总导数时给出同一作用量和运动方程。

## 全局 U(1) 对称性

Dirac 作用量在常数相位变换下不变：

$$
\psi\to e^{-i\alpha}\psi,
\qquad
\bar\psi\to\bar\psi e^{+i\alpha}.
$$

Noether 流为：

$$
\boxed{j^\mu=\bar\psi\gamma^\mu\psi}.
$$

由 Dirac 方程及其共轭方程：

$$
\partial_\mu j^\mu=0.
$$

守恒荷为：

$$
Q=\int d^3x\,j^0.
$$

由于：

$$
j^0
=\bar\psi\gamma^0\psi
=\psi^\dagger\psi,
$$

经典 $j^0$ 非负。这是 Dirac 方程早期可作单粒子概率流解释的优点；在完整量子场论中，$j^\mu$ 更自然解释为守恒电荷流，而不是粒子位置概率流。

## 正则共轭动量

从未对称的 Lagrangian：

$$
\mathcal L_D
=i\psi^\dagger\partial_t\psi
+i\bar\psi\gamma^i\partial_i\psi
-m\bar\psi\psi
$$

读出共轭动量：

$$
\pi_\psi
=\frac{\partial^R\mathcal L_D}
{\partial(\partial_t\psi)}
=i\psi^\dagger.
$$

上标 $R$ 表示采用右 Grassmann 导数的一种约定。$\bar\psi$ 没有独立时间导数，因此系统含有约束；严谨的 Hamiltonian 分析使用 Dirac 约束方法。

入门正则量子化通常直接使用等时反对易关系。

## 等时反对易关系

量子化后，Dirac 场满足：

$$
\{\psi_\alpha(t,\mathbf x),
\psi_\beta^\dagger(t,\mathbf y)\}
=\delta_{\alpha\beta}
\delta^{(3)}(\mathbf x-\mathbf y),
$$

$$
\{\psi_\alpha(t,\mathbf x),
\psi_\beta(t,\mathbf y)\}=0,
$$

$$
\{\psi_\alpha^\dagger(t,\mathbf x),
\psi_\beta^\dagger(t,\mathbf y)\}=0.
$$

相应模式算符满足：

$$
\{b_r(\mathbf p),b_s^\dagger(\mathbf q)\}
=(2\pi)^3\delta_{rs}\delta^{(3)}(\mathbf p-\mathbf q),
$$

并对 $d,d^\dagger$ 有同样关系；其余反对易子为零。具体 $2E_{\mathbf p}$ 因子会随场展开归一化重新分配。

## Pauli 不相容原理怎样出现

由：

$$
\{b_s^\dagger,b_s^\dagger\}=0
$$

得到：

$$
(b_s^\dagger)^2=0.
$$

所以同一个费米模式不能被同种费米子占据两次。这不是额外手工添加的规则，而是反对易代数的直接结果。

## Hamiltonian 与正能量

把场展开代入 Hamiltonian，并作正规排序，可得到：

$$
:H:
=\sum_s\int d^3p\,
E_{\mathbf p}
\left[
b_s^\dagger(\mathbf p)b_s(\mathbf p)
+d_s^\dagger(\mathbf p)d_s(\mathbf p)
\right]
$$

在相应归一化下成立。

粒子和反粒子激发都贡献正能量 $E_{\mathbf p}$。未正规排序的真空常数是发散的，其处理依问题和重整化约定；不能简单把正规排序当成所有情形下的完整物理解答。

## 守恒荷与反粒子相反电荷

正规排序后的 U(1) 荷具有形式：

$$
:Q:
=\sum_s\int d^3p\,
\left[
b_s^\dagger b_s
-d_s^\dagger d_s
\right]
$$

省略共同的动量参数和归一化因子。

因此粒子与反粒子对同一 U(1) 荷贡献相反符号。若该 $U(1)$ 被规范化为电磁相位对称，二者携带相反电荷。

## 微观因果性

费米场的基本局域性条件使用反对易子。类空分离时，适当的场反对易子消失：

$$
\{\psi_\alpha(x),\bar\psi_\beta(y)\}=0,
\qquad
(x-y)^2<0.
$$

可观测的费米双线性是 Grassmann 偶对象，它们在类空分离时彼此对易。这样相隔类空的局域测量不会相互因果影响。

“费米场类空反对易”不表示可观测量本身反对易；局域可观测量必须满足普通的因果可交换性。

## 手征矩阵与投影

四维定义：

$$
\gamma^5
=i\gamma^0\gamma^1\gamma^2\gamma^3.
$$

它满足：

$$
(\gamma^5)^2=I,
\qquad
\{\gamma^5,\gamma^\mu\}=0.
$$

左右手投影算符为：

$$
P_L=\frac{1-\gamma^5}{2},
\qquad
P_R=\frac{1+\gamma^5}{2}.
$$

定义：

$$
\psi_L=P_L\psi,
\qquad
\psi_R=P_R\psi.
$$

Dirac 旋量可分解为左手和右手 Weyl 分量：

$$
\psi=\psi_L+\psi_R.
$$

## 质量项为何混合左右手

利用投影性质：

$$
\bar\psi\psi
=\bar\psi_L\psi_R
+\bar\psi_R\psi_L.
$$

同手项：

$$
\bar\psi_L\psi_L,
\qquad
\bar\psi_R\psi_R
$$

在四维 Dirac 标量质量项中为零。

因此 Dirac 质量项：

$$
-m\bar\psi\psi
$$

把左右手旋量耦合起来。质量为零时，两种手征分量在自由理论中解耦：

$$
i\slashed\partial\psi_L=0,
\qquad
i\slashed\partial\psi_R=0.
$$

## 矢量流与轴矢流

矢量流：

$$
j_V^\mu=\bar\psi\gamma^\mu\psi
$$

在自由有质量理论中守恒。

轴矢流：

$$
j_A^\mu=\bar\psi\gamma^\mu\gamma^5\psi
$$

的经典散度为：

$$
\partial_\mu j_A^\mu
=2im\bar\psi\gamma^5\psi.
$$

所以质量项显式破坏连续轴对称。即使 $m=0$，与规范场耦合后的量子理论中轴流还可能因手征反常而不守恒。

## 电磁最小耦合

令粒子电荷为 $q$，定义规范协变导数：

$$
D_\mu=\partial_\mu+iqA_\mu
$$

在一种常见约定下成立。Dirac Lagrangian 变为：

$$
\mathcal L
=\bar\psi(i\gamma^\mu D_\mu-m)\psi.
$$

展开：

$$
\mathcal L
=\bar\psi(i\slashed\partial-m)\psi
-q\bar\psi\gamma^\mu\psi A_\mu.
$$

在局域相位变换：

$$
\psi\to e^{-iq\alpha(x)}\psi,
$$

$$
A_\mu\to A_\mu+\partial_\mu\alpha
$$

下，$D_\mu\psi$ 与 $\psi$ 同样变换。若采用 $D_\mu=\partial_\mu-iqA_\mu$，则 $A_\mu$ 的变换和相互作用项符号相应改变。

## Dirac、Weyl 与 Majorana 场

- **Dirac 场**：通常含独立粒子与反粒子，自由四维场有四个复代数分量，运动方程约束后每个粒子种类有两个在壳自旋自由度；
- **Weyl 场**：四维质量为零时可只保留一个手征的二分量旋量；
- **Majorana 场**：满足现实条件，把场与其电荷共轭联系，粒子是自身反粒子。

这些条件能否同时施加取决于时空维数和号差。十维 Minkowski 时空允许 Majorana–Weyl 旋量，这是超弦谱的重要结构。

## 粒子数与电荷不是同一件事

相互作用可以产生或湮灭粒子—反粒子对，因此总粒子数：

$$
N_b+N_d
$$

不一定守恒。

但若全局 U(1) 对称保持，净电荷：

$$
Q=N_b-N_d
$$

守恒。

因此“反粒子存在”不是说场中总有固定数量的另一类小球，而是量子场允许具有相反守恒荷的激发。

## 与 RNS 超弦的关系

RNS 世界面费米子 $\psi^\mu(\tau,\sigma)$ 对二维世界面 Lorentz 群而言是旋量，对目标时空而言带向量指标 $\mu$。

Ramond 扇区零模满足：

$$
\{\psi_0^\mu,\psi_0^\nu\}
\propto\eta^{\mu\nu}.
$$

这就是目标时空 Clifford 代数。因此 Ramond 基态必须组成目标时空旋量表示；施加物理态条件后会出现类似无质量 Dirac 方程的约束。

世界面 Dirac 场与目标时空 Dirac 场不是同一个对象：前者生活在二维世界面，后者生活在目标时空。RNS 结构通过零模 Clifford 代数把二者联系起来。

## 适用条件与事实边界

1. 本篇主要讨论四维平直 Minkowski 时空中的自由 Dirac 场，并采用 mostly-minus 度规。
2. Dirac 方程是一阶方程，其平方蕴含 Klein-Gordon 方程；KG 方程本身不蕴含完整 Dirac 约束。
3. “Dirac 方程是相对论 Hamiltonian 的矩阵平方根”是结构性比喻，精确内容由 Clifford 反对易关系给出。
4. $\psi^\dagger\psi\ge0$ 允许早期单粒子概率解释，但相对论多粒子过程要求量子场论。
5. 经典费米场使用 Grassmann 奇变量；量子场算符使用反对易关系，二者不是同一种数学对象。
6. 反粒子不是负能粒子向更低能级无限跌落；它是量子场的独立正能激发。
7. 场展开和模式反对易子的 $2E_{\mathbf p}$ 因子取决于归一化约定，必须成套比较。
8. Dirac 质量项耦合左右手分量；无质量极限才使自由左右手方程解耦。
9. 轴流的经典质量项散度与量子手征反常是不同机制。
10. 弯曲时空中的 Dirac 场需要 vierbein、spin connection 和 Spin 结构，不能只把 $\partial_\mu$ 机械换成普通张量协变导数。
11. Majorana、Weyl 和 Majorana–Weyl 条件的可用性依赖维数与号差。
12. RNS 世界面费米子是二维旋量且带目标时空向量指标；Ramond 基态才形成目标时空旋量。

## 常见误区

1. **Dirac 场是四个彼此独立的标量场。** 四个分量按旋量表示混合，并受一阶 Dirac 方程约束。
2. **Gamma 矩阵是四维向量。** 它们是作用在旋量空间的矩阵，只携带一个时空向量标签。
3. **Dirac 方程的负频解是真实负能粒子。** 量子场论把相应模式解释为正能反粒子的产生。
4. **反粒子是为了修补数学而虚构的。** 正电子等反粒子已被实验观测；其存在是相对论量子场结构的真实预言。
5. **$\bar\psi$ 就是 $\psi^*$。** Dirac 共轭还需转置并乘 $\gamma^0$。
6. **$j^0=\psi^\dagger\psi$ 永远是粒子位置概率密度。** 在量子场论中更自然的是守恒荷密度，粒子数可因成对产生而改变。
7. **费米反对易关系只是人为加入 Pauli 原理。** 它还与局域性、正能量和自旋—统计定理相联系。
8. **质量为零自动保证所有手征流在量子层面守恒。** 手征反常可破坏经典轴对称。
9. **Dirac 场、Weyl 场和 Majorana 场只是不同名称。** 它们施加不同现实性或手征条件，独立自由度和电荷结构不同。
10. **世界面费米子就是目标时空电子型 Dirac 场。** 两者生活在不同空间并按不同 Lorentz 群变换。

## 练习

1. 写出本篇采用的 Minkowski 度规和 Gamma 反对易关系。
2. 写出自由 Dirac 方程及斜线记号。
3. 为什么 Dirac 方程需要矩阵系数？
4. 推导每个 Dirac 分量满足 Klein-Gordon 方程。
5. 平面波 $u(p)e^{-ip\cdot x}$ 满足什么代数方程和质量壳条件？
6. 写出 Dirac 共轭并说明它的用途。
7. 写出自由 Dirac 作用量。
8. 分别对 $\bar\psi$ 和 $\psi$ 变分得到什么方程？
9. 写出全局 U(1) Noether 流，并证明其守恒。
10. 为什么 $j^0=\psi^\dagger\psi$ 非负？
11. 写出量子 Dirac 场的粒子—反粒子模式展开结构。
12. 写出等时场反对易关系。
13. Pauli 不相容原理怎样从模式反对易关系得到？
14. 正规排序后的 Hamiltonian 为什么对粒子与反粒子都给出正能量？
15. 写出四维左右手投影算符。
16. 为什么 Dirac 质量项混合左右手分量？
17. 轴矢流在有质量经典理论中为何不守恒？
18. 写出电磁最小耦合的协变导数和相互作用项。
19. Dirac、Weyl 与 Majorana 场的主要区别是什么？
20. Ramond 零模为何使超弦基态成为目标时空旋量？

## 答案与提示

1. $\eta=\operatorname{diag}(+1,-1,-1,-1)$；$\{\gamma^\mu,\gamma^\nu\}=2\eta^{\mu\nu}I_4$。
2. $(i\gamma^\mu\partial_\mu-m)\psi=0$；$\slashed\partial=\gamma^\mu\partial_\mu$。
3. 线性 Hamiltonian 平方要消去交叉项并产生 $\mathbf p^2+m^2$，普通数无法满足所需反对易关系。
4. 左乘 $(i\slashed\partial+m)$，利用 $(i\slashed\partial)^2=-\Box$，得到 $(\Box+m^2)\psi=0$。
5. $(\slashed p-m)u(p)=0$；左乘 $\slashed p+m$ 得 $p^2=m^2$。
6. $\bar\psi=\psi^\dagger\gamma^0$；它使 $\bar\psi\psi$ 成为 Lorentz 标量，使 $\bar\psi\gamma^\mu\psi$ 成为向量。
7. $S=\int d^4x\,\bar\psi(i\slashed\partial-m)\psi$。
8. 对 $\bar\psi$ 得 Dirac 方程；对 $\psi$ 得 $\bar\psi(i\overleftarrow{\slashed\partial}+m)=0$。
9. $j^\mu=\bar\psi\gamma^\mu\psi$；把 Dirac 方程及共轭方程相减可得 $\partial_\mu j^\mu=0$。
10. $j^0=\bar\psi\gamma^0\psi=\psi^\dagger(\gamma^0)^2\psi=\psi^\dagger\psi\ge0$。
11. $\psi\sim bu e^{-ipx}+d^\dagger v e^{+ipx}$；第一项湮灭粒子，第二项产生反粒子。
12. $\{\psi_\alpha(t,\mathbf x),\psi_\beta^\dagger(t,\mathbf y)\}=\delta_{\alpha\beta}\delta^{(3)}(\mathbf x-\mathbf y)$，其余同类反对易子为零。
13. $\{b^\dagger,b^\dagger\}=2(b^\dagger)^2=0$，所以同一模式不能产生两次。
14. 重新解释负频模式为反粒子，并使用反对易关系与正规排序后，$H$ 含 $E(b^\dagger b+d^\dagger d)$。
15. $P_L=(1-\gamma^5)/2$，$P_R=(1+\gamma^5)/2$。
16. $\bar\psi\psi=\bar\psi_L\psi_R+\bar\psi_R\psi_L$，同手标量项为零。
17. 利用运动方程得 $\partial_\mu j_A^\mu=2im\bar\psi\gamma^5\psi$。
18. 本篇约定 $D_\mu=\partial_\mu+iqA_\mu$；相互作用项为 $-q\bar\psi\gamma^\mu\psi A_\mu$。
19. Dirac 场通常含独立粒子和反粒子；Weyl 场只取一个手征；Majorana 场满足与电荷共轭相等的现实条件。
20. $\{\psi_0^\mu,\psi_0^\nu\}\propto\eta^{\mu\nu}$ 是 Clifford 代数，基态必须承载其旋量表示。

## 与其他概念的关系

- [[弦理论/物理学/Klein-Gordon 场]] 给出 Dirac 方程平方后满足的相对论质量壳方程；
- [[弦理论/物理学/费米子]] 解释反对易关系、Pauli 原理和费米统计；
- [[弦理论/数学/旋量]] 说明 $\psi$ 在 Lorentz 变换下为何不同于普通向量；
- [[弦理论/数学/Gamma 矩阵]] 与 [[弦理论/数学/Clifford 代数]] 构造 Dirac 算符；
- [[弦理论/物理学/作用量]] 与 [[弦理论/物理学/场的 Euler-Lagrange 方程]] 推出 Dirac 方程和共轭方程；
- [[弦理论/物理学/Minkowski 时空]] 固定号差、质量壳与 Lorentz 协变性；
- [[弦理论/物理学/量子算符]] 是把经典 Grassmann 场提升为算符值分布的基础；
- [[弦理论/物理学/场的正则量子化]] 建立场和模式反对易关系；
- [[弦理论/物理学/传播子]] 中的 Dirac 传播子是 Dirac 算符的 Green 函数；
- [[弦理论/物理学/Wick 定理]] 对费米场交换顺序时产生额外负号；
- [[弦理论/物理学/手征反常]] 说明经典轴对称怎样在量子层面破坏；
- [[弦理论/物理学/规范协变导数]] 将本页的电磁最小耦合推广到一般非 Abelian 规范群，并解释不同符号约定的对应；
- [[弦理论/物理学/二维自由费米子]] 是世界面共形场论的费米基础；
- [[弦理论/物理学/世界面费米子]] 与 [[弦理论/物理学/RNS 超弦理论]] 把二维旋量和目标时空旋量谱联系起来。

## 参考资料

- Michael E. Peskin and Daniel V. Schroeder, *An Introduction to Quantum Field Theory*, Westview Press, 1995, Chapters 3–4.
- Mark Srednicki, *Quantum Field Theory*, Cambridge University Press, 2007, Chapters 33–35.
- Steven Weinberg, *The Quantum Theory of Fields, Vol. 1*, Cambridge University Press, 1995, Chapters 5–6.
- Claude Itzykson and Jean-Bernard Zuber, *Quantum Field Theory*, McGraw-Hill, 1980.
- Lewis H. Ryder, *Quantum Field Theory*, 2nd ed., Cambridge University Press, 1996.
- Michael D. Schwartz, *Quantum Field Theory and the Standard Model*, Cambridge University Press, 2014, Chapters 10–12.
- Pierre Ramond, *Field Theory: A Modern Primer*, 2nd ed., Westview Press, 1990.
- Joseph Polchinski, *String Theory, Vol. 1*, Cambridge University Press, 1998, Chapters 10–11.
- David Tong, *Lectures on Quantum Field Theory*, University of Cambridge lecture notes.
- David Tong, *String Theory*, arXiv:0908.0333, [arXiv](https://arxiv.org/abs/0908.0333)
