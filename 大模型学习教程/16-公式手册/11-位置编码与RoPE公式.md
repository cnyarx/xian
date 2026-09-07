---
aliases: [位置编码公式, RoPE公式, 正弦位置编码, ALiBi公式, Positional Encoding, Rotary Position Embedding]
tags: [公式, Transformer, 位置编码]
prerequisites: ["[[../15-概念词典/04-求和与下标]]", "[[../15-概念词典/05-坐标维度与形状]]", "[[../15-概念词典/08-标量向量矩阵与张量]]", "[[01-点积范数与余弦公式]]"]
---
# 位置编码与 RoPE 公式

## 为什么需要位置编码

自注意力只比较向量内容，不自动感知 token 顺序。对相同 token 集合，“猫追狗”和“狗追猫”在没有位置信息时表示相同，位置编码把 token 在序列中的位置注入模型。

## 1. 正弦位置编码

原始 Transformer 使用固定正弦和余弦函数：

$$
PE_{(pos,2i)}=\sin\left(pos\big/10000^{2i/d}\right)
$$

$$
PE_{(pos,2i+1)}=\cos\left(pos\big/10000^{2i/d}\right)
$$

- $pos$：token 位置；
- $i$：维度对编号，$i=0,1,\ldots,(d/2-1)$；
- $d$：模型维度；
- 偶数维用正弦，奇数维用余弦；
- 不同维度使用不同波长，像多个转速不同的钟表共同编码位置。

位置向量与 token 嵌入相加：$h_{pos}=E_{token}+PE_{pos}$。

## 2. 可学习绝对位置嵌入

为每个位置直接训练一个向量 $E_{position}$：

$$
h_{pos}=E_{token}+E_{position}
$$

简单有效，但超出训练时最大位置没有现成向量，需要扩展或插值。

## 3. RoPE

RoPE（Rotary Position Embedding）不把位置向量直接相加，而是按位置旋转 Query 和 Key 的二维分量对。

### 二维旋转

$$
R(\theta)=
\begin{bmatrix}
\cos\theta & -\sin\theta\\
\sin\theta & \cos\theta
\end{bmatrix}
$$

### 频率定义

对第 $i$ 对分量，频率为 $\theta_i=\text{base}^{-2i/d}$，其中 `base` 常取 10000。位置 $m$ 的 Query 第 $i$ 对分量乘 $R(m\theta_i)$。

### 为什么 RoPE 能编码相对距离

旋转后，两个位置 $m$ 和 $n$ 的 Query 与 Key 在二维分量对上的内积为：

$$
(R(m\theta)q)^T(R(n\theta)k)=q^TR((n-m)\theta)k
$$

因为 $R(\alpha)^TR(\beta)=R(\beta-\alpha)$。在这里采用列向量和上面的逆时针旋转矩阵约定，所以符号是 $n-m$；若资料交换 Query/Key 次序或采用相反旋转约定，可能写成 $m-n$。关键性质是点积只依赖相对位置差，而不是绝对位置分别是多少。RoPE 是许多公开 decoder-only 模型采用的位置方法之一 `[C]`；具体实现和参数以模型配置为准。

## 4. ALiBi

ALiBi（Attention with Linear Biases）不修改向量，而是直接在注意力分数中加线性负偏置：

$$
s_{ij}=q_i\cdot k_j-m_h\cdot|i-j|
$$

- $m_h$：每个注意力头的斜率，通常随头数递增；
- 距离越远，惩罚越大，模型倾向于关注邻近 token。

## 5. 边界

- 换用更长位置编码或 RoPE 扩展 `base` 值，不自动保证模型能有效使用长上下文；
- 训练数据长度、注意力模式和评测方法共同决定真实长上下文能力。

## 最小自测

1. 二维旋转矩阵 $R(\pi/2)$ 是多少？
2. 为什么没有位置编码的自注意力难以区分词序？
3. RoPE 怎样让点积只依赖相对位置？
4. ALiBi 的斜率 $m_h$ 越大，远近分布有什么变化？

答案：

1. $R(\pi/2)=\begin{bmatrix}0&-1\\1&0\end{bmatrix}$。
2. 在没有位置输入时，自注意力只根据 token 表示及其两两内容关系计算，对输入排列具有置换等变性，不能自行知道哪个 token 在前。
3. 因为 $R(m\theta)^TR(n\theta)=R((n-m)\theta)$，旋转后点积中的绝对位置合并成位置差。
4. 对相同距离，$m_h$ 越大，远距离位置受到的负偏置越强，softmax 后通常更偏向近处；最终权重仍同时受内容分数影响。

## 正文

- [[../06-注意力与Transformer/04-位置编码|位置编码]]

## 来源

- Vaswani et al. (2017), *Attention Is All You Need*：https://arxiv.org/abs/1706.03762 `[A]`
- Su et al. (2021), *RoFormer: Enhanced Transformer with Rotary Position Embedding*：https://arxiv.org/abs/2104.09864 `[A]`
- Press et al. (2022), *Train Short, Test Long: Attention with Linear Biases Enables Input Length Extrapolation*：https://arxiv.org/abs/2108.12409 `[A]`
- “许多公开模型采用”是基于公开模型配置的工程观察，不是数学定理 `[C]`