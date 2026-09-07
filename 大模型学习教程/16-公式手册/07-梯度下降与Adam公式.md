---
aliases: [梯度下降公式, Momentum公式, Adam公式, AdamW公式, Gradient Descent, Adam Optimizer]
tags: [公式, 优化, 训练]
prerequisites: ["[[../15-概念词典/04-求和与下标]]", "[[../15-概念词典/05-坐标维度与形状]]", "[[../15-概念词典/13-计算图自动微分与梯度累加]]", "[[../15-概念词典/16-参数梯度与优化器]]", "[[05-导数梯度与链式法则公式]]"]
---
# 梯度下降、Momentum、Adam 与 AdamW 公式

## 1. 梯度下降

设第 $t$ 步的参数为 $\theta_t$，损失函数为 $L$：

$$
g_t=\nabla_{\theta}L(\theta_t)
$$

$$
\theta_{t+1}=\theta_t-\eta g_t
$$

- $g_t$：当前位置的梯度；
- $\eta>0$：学习率（learning rate）；
- 负号：沿局部一阶下降方向更新。

### 最小数值例子

若 $\theta_t=3$、$g_t=2$、$\eta=0.1$：

$$
\theta_{t+1}=3-0.1\times2=2.8
$$

梯度下降只利用当前位置附近的一阶信息。对非凸损失，它不保证到达全局最优点；学习率过大还可能越过低点或发散。

## 2. Momentum

一种常见写法是：

$$
v_t=\beta v_{t-1}+g_t
$$

$$
\theta_{t+1}=\theta_t-\eta v_t
$$

- $v_t$：累积的更新方向；
- $0\le\beta<1$：保留历史信息的比例；
- $v_0$ 通常初始化为 0。

若连续多步梯度方向一致，历史项会增强该方向；若梯度来回变号，部分波动会互相抵消。

> 不同教材和软件可能把 $(1-\beta)$ 放进第一条公式，或把 $v_t$ 定义成实际更新量。比较公式时必须先核对变量定义，不能只看名称。

## 3. Adam 的一阶矩与二阶矩

Adam 对每个参数分量分别维护两个指数移动平均：

$$
m_t=\beta_1m_{t-1}+(1-\beta_1)g_t
$$

$$
v_t=\beta_2v_{t-1}+(1-\beta_2)g_t\odot g_t
$$

- $m_t$：梯度的一阶矩估计，可以理解为带方向的平滑平均；
- $v_t$：梯度平方的二阶原点矩估计，反映近期梯度大小；
- $\odot$：逐元素乘法；因此 $g_t\odot g_t$ 是每个分量分别平方；
- $0\le\beta_1,\beta_2<1$；
- $m_0=v_0=0$。

这里的“二阶矩”不是 Hessian，也不是对损失求二阶导数。

## 4. 为什么需要偏差修正

因为状态从 0 开始，训练初期的 $m_t$ 和 $v_t$ 会偏向 0。Adam 使用：

$$
\hat m_t=\frac{m_t}{1-\beta_1^t}
$$

$$
\hat v_t=\frac{v_t}{1-\beta_2^t}
$$

在梯度的统计性质近似稳定等条件下，这能修正由零初始化造成的主要缩小偏差。

### 首步手算

令一个标量参数的首步梯度 $g_1=2$，并取：

$$
\beta_1=0.9,\qquad \beta_2=0.999
$$

则：

$$
m_1=0.9\times0+0.1\times2=0.2
$$

$$
v_1=0.999\times0+0.001\times2^2=0.004
$$

修正后：

$$
\hat m_1=\frac{0.2}{1-0.9}=2
$$

$$
\hat v_1=\frac{0.004}{1-0.999}=4
$$

可以看到，首步修正恢复了这个例子中的梯度 $2$ 和梯度平方 $4$。

## 5. Adam 参数更新

$$
\theta_{t+1}=\theta_t-
\eta\frac{\hat m_t}{\sqrt{\hat v_t}+\epsilon}
$$

所有乘法、除法和平方根都按参数分量逐元素计算。

- $\eta$：基础学习率；
- $\epsilon>0$：避免分母为 0，并影响有限精度下的数值行为；
- $\sqrt{\hat v_t}$：根据近期梯度尺度调节每个分量的有效步幅。

继续使用上面的首步例子。若 $\eta=0.001$、忽略极小的 $\epsilon$：

$$
\Delta\theta_1
\approx-0.001\frac{2}{\sqrt4}
=-0.001
$$

这不表示 Adam 每一步都固定移动 $0.001$。后续更新取决于梯度历史、符号变化、$\beta_1$、$\beta_2$ 和 $\epsilon$。

## 6. AdamW 的解耦权重衰减

AdamW 在自适应梯度更新之外，单独对参数做权重衰减。一种常见写法是：

$$
\theta_{t+1}
=\theta_t
-\eta\frac{\hat m_t}{\sqrt{\hat v_t}+\epsilon}
-\eta\lambda\theta_t
$$

等价地：

$$
\theta_{t+1}
=(1-\eta\lambda)\theta_t
-\eta\frac{\hat m_t}{\sqrt{\hat v_t}+\epsilon}
$$

- $\lambda\ge0$：权重衰减系数；
- “解耦”表示衰减项不先混入 Adam 的一阶、二阶矩估计，而是单独作用于参数。

### 与把 L2 项加入梯度的区别

若把正则项 $\frac\lambda2\lVert\theta\rVert^2$ 加入损失，它贡献的梯度是 $\lambda\theta$。在普通 SGD 中，这与乘法式权重衰减可以对应起来；但在 Adam 这类自适应方法中，若先把 $\lambda\theta$ 混入 $g_t$，它还会进入 $m_t$ 和 $v_t$，随后被逐元素缩放。因此一般不等同于 AdamW 的解耦更新。

## 7. 实现时必须核对的约定

1. **步数起点**：偏差修正中的 $t$ 通常从 1 开始。
2. **逐元素运算**：Adam 的平方、平方根和除法不是向量点积。
3. **$\epsilon$ 的位置**：有的变体写在平方根外，有的写进平方根内；两者数值行为不完全相同。
4. **权重衰减范围**：工程实践常不对偏置或归一化缩放参数应用衰减，但这属于参数分组选择，不是 AdamW 公式自动决定的。
5. **混合精度**：低精度训练常保留更高精度的优化器状态或主权重；具体做法取决于训练框架。

## 8. 最小自测

### 题目 1

已知 $\theta=5$、梯度 $g=3$、学习率 $\eta=0.2$，做一步普通梯度下降后参数是多少？

答案：

$$
5-0.2\times3=4.4
$$

### 题目 2

Adam 的 $v_t$ 是损失函数的二阶导数吗？

答案：不是。标准 Adam 中的 $v_t$ 是梯度逐元素平方的指数移动平均，不是 Hessian。

### 题目 3

为什么 AdamW 不能在所有情况下简单理解为“Adam 加 L2 正则”？

答案：因为把 L2 梯度 $\lambda\theta$ 混入 $g_t$ 后，它会进入 Adam 的矩估计并接受自适应缩放；AdamW 则把权重衰减与自适应梯度更新分开。

## 正文

- [[../03-机器学习基础/04-梯度下降|梯度下降]]
- [[../04-神经网络基础/05-优化器|优化器]]
- [[../07-预训练/05-训练稳定性|训练稳定性]]

## 来源

- Sutskever, Martens, Dahl & Hinton (2013), *On the Importance of Initialization and Momentum in Deep Learning* https://proceedings.mlr.press/v28/sutskever13.html `[A]`
- Kingma & Ba (2015), *Adam: A Method for Stochastic Optimization*：https://arxiv.org/abs/1412.6980 `[A]`
- Loshchilov & Hutter (2019), *Decoupled Weight Decay Regularization*：https://arxiv.org/abs/1711.05101 `[A]`
- PyTorch, `torch.optim.AdamW`：https://pytorch.org/docs/stable/generated/torch.optim.AdamW.html `[A]`
