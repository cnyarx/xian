---
aliases: [FFN公式, SwiGLU公式, 前馈网络公式, Feed-Forward Network, GLU, Gated Linear Unit]
tags: [公式, Transformer, 神经网络]
prerequisites: ["[[../15-概念词典/04-求和与下标]]", "[[../15-概念词典/05-坐标维度与形状]]", "[[../15-概念词典/08-标量向量矩阵与张量]]", "[[../15-概念词典/09-逐元素运算与广播]]", "[[02-矩阵乘法与仿射层公式]]", "[[08-激活函数公式]]"]
---
# FFN 与 SwiGLU 公式

## 1. 经典 FFN

$$
\operatorname{FFN}(x)=W_2\phi(W_1x+b_1)+b_2
$$

- $x$：单个 token 向量，形状 $d_{model}$；
- $W_1$：形状 $d_{ff}\times d_{model}$；
- $W_2$：形状 $d_{model}\times d_{ff}$；
- $\phi$：激活函数，如 ReLU 或 GELU；
- $d_{ff}$：中间维度，通常大于 $d_{model}$。

所有 token 共享同一组 $W_1,W_2$，但输入不同，输出不同。FFN 在 token 间独立，不直接混合位置；位置间信息由注意力写入各 token 向量。

### 参数量

无偏置时约 $2d_{model}d_{ff}$。若 $d_{model}=4096$，$d_{ff}=11008$，约：

$$
2\times4096\times11008\approx90.2\text{M}
$$

### 为什么中间维度更大

扩展空间让网络能表示更多非线性组合，再压回模型维度。

## 2. GLU

GLU（Gated Linear Unit）用一个分支生成内容，另一个分支充当门：

$$
\operatorname{GLU}(x)=(xW_a)\odot\sigma(xW_b)
$$

- $\odot$：逐元素乘法；
- $W_a,W_b$：两个线性投影；
- $\sigma$：sigmoid，门值在 $(0,1)$。

## 3. SwiGLU

SwiGLU 用 SiLU 作为门控激活：

$$
\operatorname{SwiGLU}(x)=
\operatorname{SiLU}(xW_g)\odot(xW_u)
$$

完整输出经过下降投影：

$$
y=W_d\bigl[\operatorname{SiLU}(W_gx)\odot(W_ux)\bigr]
$$

- $W_g,W_u$：两个“升维”投影，各自形状 $d_{ff}\times d_{model}$；
- $W_d$：下降投影，形状 $d_{model}\times d_{ff}$；
- $\operatorname{SiLU}(z)=z\sigma(z)$。

### SwiGLU 参数量

三个投影各约 $d_{model}d_{ff}$，合计约 $3d_{model}d_{ff}$。设计者通常调小 $d_{ff}$ 使总参数预算与经典 FFN 可比。

## 4. 数值例子

令 $d_{model}=2$，$d_{ff}=3$（仅为演示）：

$$
x=[1,0]
$$

$$
W_g=\begin{bmatrix}1&0\\0&1\\-1&1\end{bmatrix},
\quad W_u=\begin{bmatrix}0&1\\1&0\\1&1\end{bmatrix}
$$

$$
W_gx=[1,0,-1]^T,\quad \operatorname{SiLU}(W_gx)=
\begin{bmatrix}
1\cdot\sigma(1)\\
0\cdot\sigma(0)\\
-1\cdot\sigma(-1)
\end{bmatrix}
\approx
\begin{bmatrix}0.731\\0\\-0.269\end{bmatrix}
$$

## 5. 边界

- FFN 不是“可有可无的小层”，它通常占 Transformer 很大比例参数；
- 门控激活不等于对输入求导数；
- 中间维度越大不一定越好，受参数和计算预算限制。

## 最小自测

1. $d_{model}=512$，$d_{ff}=2048$，经典 FFN 无偏置参数量是多少？
2. 为什么 SwiGLU 的参数量约为 $3d_{model}d_{ff}$ 而非 $2d_{model}d_{ff}$？
3. GLU 中的门控分支和内容分支分别完成了什么？

答案：

1. 两个矩阵参数量为 $512\times2048+2048\times512=2,097,152$。
2. SwiGLU 需要门控投影、内容投影和输出投影三块矩阵，所以约为 $3d_{model}d_{ff}$；是否含偏置由实现决定。
3. 门控分支产生逐元素调节系数，内容分支产生待传递的特征；两者逐元素相乘后再投影回模型维度。

## 正文

- [[../06-注意力与Transformer/06-前馈网络|前馈网络]]
- [[../04-神经网络基础/02-激活函数|激活函数]]

## 来源

- Vaswani et al. (2017), *Attention Is All You Need*, §3.3 https://arxiv.org/abs/1706.03762 `[A]`
- Dauphin et al. (2017), *Language Modeling with Gated Convolutional Networks* https://proceedings.mlr.press/v70/dauphin17a.html `[A]`
- Shazeer (2020), *GLU Variants Improve Transformer*：https://arxiv.org/abs/2002.05202 `[A]`