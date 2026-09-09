---
aliases: [残差连接公式, LayerNorm公式, RMSNorm公式, Pre-Norm, Post-Norm, Residual Connection]
tags: [公式, Transformer, 归一化, 大模型, 学习教程]
prerequisites: ["[[求和与下标]]", "[[坐标维度与形状]]", "[[逐元素运算与广播]]"]
---
# 残差连接、LayerNorm 与 RMSNorm 公式

## 残差连接

$$
y=x+F(x)
$$

- $x$：子层输入；
- $F(x)$：子层输出（如注意力或 FFN 产出）；
- 要求 $F(x)$ 与 $x$ 形状相同。

模块只需学习“在输入基础上改多少”，同时为梯度提供直接传播路径。

## LayerNorm

对单个 token 向量 $x\in\mathbb{R}^d$：

$$
\mu=\frac1d\sum_{i=1}^{d}x_i
$$

$$
\sigma^2=\frac1d\sum_{i=1}^{d}(x_i-\mu)^2
$$

$$
\operatorname{LayerNorm}(x)_i=\gamma_i\frac{x_i-\mu}{\sqrt{\sigma^2+\epsilon}}+\beta_i
$$

- $\mu$：该 token 各维度的均值；
- $\sigma^2$：方差；
- $\epsilon>0$：防止分母为 0；
- $\gamma_i,\beta_i$：可学习的缩放和平移参数，维度 $d$。

### 数值例子

$x=[1,2,3]$：

$$
\mu=\frac{1+2+3}{3}=2
$$

$$
\sigma^2=\frac{(1-2)^2+(2-2)^2+(3-2)^2}{3}=\frac{2}{3}\approx0.667
$$

## RMSNorm

RMSNorm 不减均值，只按均方根缩放：

$$
\operatorname{RMSNorm}(x)_i=\gamma_i\frac{x_i}{\sqrt{\frac1d\sum_{j=1}^{d}x_j^2+\epsilon}}
$$

计算量比 LayerNorm 略少，现代 LLM 广泛使用。

## Pre-Norm 与 Post-Norm

**Post-Norm（原始 Transformer）**：

$$
y=\operatorname{Norm}(x+F(x))
$$

**Pre-Norm**：

$$
y=x+F(\operatorname{Norm}(x))
$$

Pre-Norm 中残差主管道更直接，深模型训练常更稳定。

## 常见误区

- LayerNorm 沿隐藏维度归一化，BatchNorm 沿批次维度归一化；两者统计方向不同，不直接互换。
- RMSNorm 不减均值，不代表它一定比 LayerNorm 差或好；具体性能取决于架构与训练设置。
- $\epsilon$ 建议参考文献与框架默认值，不能随意设为 0。

## 一个完整 Transformer 块

```text
x
├─ Norm → Attention ─┐
└────────────────────+→ h
                       ├─ Norm → FFN ─┐
                       └──────────────+→ y
```

两个子层各有一条残差连接。

## 最小自测

1. 对 $[-2,0,4]$ 计算 LayerNorm 的 $\mu$ 和 $\sigma^2$。
2. 为什么 Pre-Norm 的残差通路比 Post-Norm 更直接？
3. 手算 $[3,4]$ 的 RMSNorm（忽略 $\gamma$ 和 $\epsilon$）。

答案：

1. $\mu=(-2+0+4)/3=2/3$；$\sigma^2=[(-8/3)^2+(-2/3)^2+(10/3)^2]/3=56/9\approx6.222$。
2. Pre-Norm 写成 $y=x+F(\operatorname{Norm}(x))$，恒等残差支路从 $x$ 到 $y$ 不经过归一化层；Post-Norm 的和还要经过 $\operatorname{Norm}$。
3. 均方根 $\sqrt{(3^2+4^2)/2}=\sqrt{12.5}\approx3.536$，输出约为 $[0.849,1.131]$。

## 正文

- [[残差连接与层归一化|残差连接与层归一化]]

## 来源

- He et al. (2016), *Deep Residual Learning for Image Recognition* https://doi.org/10.1109/CVPR.2016.90 `[A]`
- Ba et al. (2016), *Layer Normalization*：https://arxiv.org/abs/1607.06450 `[A]`
- Zhang & Sennrich (2019), *Root Mean Square Layer Normalization* https://arxiv.org/abs/1910.07467 `[A]`
- Xiong et al. (2020), *On Layer Normalization in the Transformer Architecture* https://arxiv.org/abs/2002.04745 `[B]`