---
aliases: [LoRA公式, 低秩更新公式, Low-Rank Adaptation, PEFT]
tags: [公式, 微调, 参数高效, 大模型, 学习教程]
prerequisites: ["[[比例分数与百分数]]", "[[坐标维度与形状]]", "[[标量向量矩阵与张量]]", "[[矩阵乘法与仿射层公式]]"]
---
# LoRA 低秩更新公式

## 1. 核心公式

LoRA 冻结原权重 $W$，用两个小矩阵表示更新：

$$
W'=W+\Delta W=W+BA
$$

若 $W\in\mathbb{R}^{d_{out}\times d_{in}}$：

$$
A\in\mathbb{R}^{r\times d_{in}},\qquad B\in\mathbb{R}^{d_{out}\times r}
$$

所以 $BA\in\mathbb{R}^{d_{out}\times d_{in}}$，与 $W$ 形状相同。

$r$ 是秩上界，通常远小于 $d_{in}$ 和 $d_{out}$。

## 2. 缩放

常见实现写作：

$$
W'=W+\frac{\alpha}{r}BA
$$

- $\alpha$：LoRA scaling；
- $\alpha/r$：控制适配器更新的整体幅度。

前向传播为：

$$
y=Wx+\frac{\alpha}{r}B(Ax)
$$

先算 $Ax$ 得到 $r$ 维中间向量，再经 $B$ 投影回 $d_{out}$。

## 3. 参数量

全量更新参数数：

$$
d_{out}d_{in}
$$

LoRA 新增参数数：

$$
r(d_{in}+d_{out})
$$

### 数值例子

$W$ 为 $4096\times4096$，$r=8$：

$$
\text{full}=4096^2=16,777,216
$$

$$
\text{LoRA}=8(4096+4096)=65,536
$$

比例：

$$
\frac{65,536}{16,777,216}\approx0.003906=0.3906\%
$$

## 4. 初始化

常见做法是随机初始化 $A$、将 $B$ 初始化为 0，使训练开始时 $BA=0$，模型初始行为与基础模型相同。具体初始化以框架实现为准。

## 5. QLoRA

QLoRA 将冻结的基础模型权重量化到 4-bit，并以较高精度训练 LoRA 适配器。它不表示所有计算或优化器状态都以 4-bit 进行。

## 6. 边界

- 低秩更新限制了可学习更新空间，rank 越小参数越省但表达能力可能受限；
- 目标层、rank、缩放和数据质量均需实验选择；
- 合并适配器前必须确认基础模型版本一致。

## 最小自测

1. $1024\times1024$ 权重使用 rank 16 LoRA，新增参数量是多少？
2. 为什么 $BA$ 的秩不超过 $r$？
3. QLoRA 中被量化的是什么，被训练的是什么？

答案：

1. 若 $B\in\mathbb R^{1024\times16}$、$A\in\mathbb R^{16\times1024}$，新增参数为 $1024\times16+16\times1024=32,768$。
2. 矩阵乘积的秩不超过任一因子的秩，而 $A,B$ 的中间维度为 $r$，所以 $\operatorname{rank}(BA)\le r$。
3. QLoRA 通常把冻结的基础模型权重量化存储，并训练附加的 LoRA 低秩参数；优化器状态对应可训练适配器，而非全部量化基础权重。

## 正文

- [[LoRA 与参数高效微调|LoRA 与参数高效微调]]

## 来源

- Hu et al. (2022), *LoRA: Low-Rank Adaptation of Large Language Models*：https://arxiv.org/abs/2106.09685 `[A]`
- Dettmers et al. (2023), *QLoRA*：https://arxiv.org/abs/2305.14314 `[A]`