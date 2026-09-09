---
aliases: [Green's Function, Green Function]
english_name: Green's Function
tags: [数学, 微分方程, 弦理论先修]
prerequisites:
  - "[[弦理论/数学/线性映射]]"
  - "[[弦理论/数学/Dirac delta]]"
  - "[[弦理论/数学/Fourier 变换]]"
used_by:
  - "[[弦理论/物理学/传播子]]"
  - "[[弦理论/物理学/二维 Euclidean 场论]]"
  - "[[弦理论/物理学/二维自由玻色子]]"
  - "[[弦理论/物理学/弦散射振幅]]"
evidence_status: 教材事实
---

# Green 函数（Green's Function）

## 一句话解释

Green 函数是线性微分算符对单位点源的响应；知道点源响应后，就能叠加得到任意源的响应。

## 为什么要学它

静电势、波传播、量子传播子和二维场论相关函数都可用 Green 函数统一描述。弦论世界面上的自由场二点函数本质上也是相应算符的 Green 函数。

## 基本问题

设线性微分算符 $L$ 作用于未知函数 $u$：

$$
Lu(x)=f(x).
$$

Green 函数 $G(x,x')$ 满足：

$$
L_xG(x,x')=\delta(x-x').
$$

下标 $x$ 表示算符作用于第一个变量。$x'$ 是点源位置，$x$ 是观察位置。

## 从点源到一般源

若边界条件匹配，则：

$$
u(x)=\int G(x,x')f(x')\,dx'
$$

给出方程的一个解。验证：

$$
L_xu(x)
=
\int L_xG(x,x')f(x')dx'
=
\int\delta(x-x')f(x')dx'
=f(x).
$$

关键是线性性允许把算符移入积分，并把许多点源响应叠加。

## 边界条件是定义的一部分

同一个微分算符可有不同 Green 函数，取决于：

- 固定值或固定导数边界条件；
- 周期边界条件；
- 波问题中的延迟、超前或 Feynman 条件；
- 空间拓扑。

只写方程而不说明边界条件，Green 函数通常不唯一。

## 一个简单例子

对一维算符：

$$
L=-\frac{d^2}{dx^2}
$$

在整条实线上，一种 Green 函数为：

$$
G(x,x')=-\frac12|x-x'|,
$$

因为其一阶导数在 $x=x'$ 跳跃，二阶分布导数产生 delta，并满足：

$$
-\frac{d^2G}{dx^2}=\delta(x-x').
$$

整体符号取决于算符定义。

## Fourier 空间求法

若算符具有平移不变性，$G(x,x')=G(x-x')$。对 Fourier 变换后：

$$
L(k)\tilde G(k)=1,
$$

所以形式上：

$$
\tilde G(k)=\frac1{L(k)}.
$$

例如 $L=-\partial_x^2+m^2$ 对应：

$$
\tilde G(k)=\frac1{k^2+m^2}.
$$

若分母在积分路径上有零点，还必须指定极点处方，如 $i\varepsilon$，不能直接忽略。

## 静电学例子

三维 Poisson 方程：

$$
-\nabla^2V(\mathbf x)=
\frac{\rho(\mathbf x)}{\varepsilon_0}.
$$

自由空间 Laplace 算符的 Green 函数与 $1/|\mathbf x-\mathbf x'|$ 成正比，因此任意电荷分布的电势是各点电荷势的积分叠加。

## 延迟与超前 Green 函数

波动方程有多种 Green 函数：

- 延迟 Green 函数只允许源影响未来，符合因果响应；
- 超前 Green 函数允许响应出现在源之前；
- Feynman Green 函数按量子场论时间排序处方定义。

它们满足相同局部微分方程，但全局边界条件不同。

## 与逆算符的关系

Green 函数可视为 $L^{-1}$ 的积分核：

$$
(L^{-1}f)(x)=
\int G(x,x')f(x')dx'.
$$

若 $L$ 有零模，它可能不可逆，需要移除零模、加约束或选择广义逆。

## 弦世界面中的例子

二维自由玻色场 $X^\mu$ 的二点函数是二维 Laplace 算符的 Green 函数，呈对数形式。它进一步决定算符乘积展开和顶点算符相关函数。

## 常见误区

1. **Green 函数只由微分算符决定。** 还由边界条件决定。
2. **Green 函数一定是普通光滑函数。** 点源处通常有奇性，并在分布意义下满足方程。
3. **任何算符都可以直接取倒数。** 零模或极点会阻止简单求逆。
4. **延迟、超前和 Feynman Green 函数相同。** 它们边界条件不同。
5. **传播子与经典 Green 函数毫无关系。** 传播子通常是带量子边界处方的 Green 函数。

## 练习

1. 写出 Green 函数的定义方程。
2. 为什么一般源的解能由点源响应积分得到？
3. 同一算符为何可能有多个 Green 函数？
4. Fourier 空间中 Green 函数形式上是什么？
5. 算符有零模时会遇到什么问题？

## 答案与提示

1. $L_xG(x,x')=\delta(x-x')$。
2. 线性方程允许点源响应叠加，delta 抽样恢复源。
3. 边界和因果处方不同。
4. $\tilde G(k)=1/L(k)$，还需处理零点和处方。
5. 算符不可直接全局求逆，Green 函数不唯一或不存在。

## 与其他概念的关系

- [[弦理论/数学/Dirac delta]] 定义单位点源；
- [[弦理论/数学/Fourier 变换]] 把微分算符求逆化为代数除法；
- [[弦理论/物理学/传播子]] 是带量子处方的 Green 函数；
- [[弦理论/物理学/二维 Euclidean 场论]] 给出二维对数 Green 函数、质量调节器和紧致曲面常数零模投影；
- [[弦理论/物理学/二维自由玻色子]] 将二维对数 Green 函数具体解释为弦坐标场二点函数，并由其求出导数收缩与局域奇异项；
- 世界面自由场 Green 函数决定弦散射相关函数。

## 参考资料

- [MIT OCW 18.03SC, Green's Functions](https://ocw.mit.edu/courses/18-03sc-differential-equations-fall-2011/)
- George Arfken, Hans Weber, Frank Harris, *Mathematical Methods for Physicists*
- [David Tong, Lectures on Quantum Field Theory](https://www.damtp.cam.ac.uk/user/tong/qft.html)
