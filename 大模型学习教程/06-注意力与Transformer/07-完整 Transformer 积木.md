---
aliases: [Transformer Block, Transformer 块, Transformer 架构]
tags: [Transformer, 教程]
prerequisites: ["[[01-注意力直觉]]", "[[02-缩放点积注意力]]", "[[03-多头注意力]]", "[[04-位置编码]]", "[[05-残差连接与层归一化]]", "[[06-前馈网络]]"]
next: ["[[08-Decoder-Only 架构]]"]
---
# 完整 Transformer 积木

## 从文字到一层输出

一个现代 Pre-Norm Transformer 块可写成：

$$h'=h+\operatorname{Attention}(\operatorname{Norm}(h))$$
$$h_{out}=h'+\operatorname{FFN}(\operatorname{Norm}(h'))$$

## 完整数据流

```text
文字
 ↓ tokenizer
Token IDs
 ↓ Embedding + Position
隐藏向量 h
 ↓ Norm
多头自注意力
 ↓ 与 h 相加（残差）
h'
 ↓ Norm
前馈网络 FFN
 ↓ 与 h' 相加（残差）
h_out
```

许多块重复堆叠，最后归一化并映射到词表 logits。

## 张量形状

设：

- 批量大小 $B$。
- 序列长度 $T$。
- 隐藏维度 $D$。

输入隐藏状态形状：

$$[B,T,D]$$

Q、K、V 投影后拆头：

$$[B,H,T,D/H]$$

每个头的注意力分数：

$$[B,H,T,T]$$

合并头后回到：

$$[B,T,D]$$

残差相加要求输入输出形状一致。

## 最后一层

隐藏状态映射到词表大小 $V$：

$$\text{logits}=hW_{vocab}$$

形状从 `[B,T,D]` 变成 `[B,T,V]`。softmax 后得到每个位置对所有 token 的概率。

## 原始 Transformer 与现代 LLM

原始论文包含 encoder 和 decoder，用于机器翻译。GPT 类模型通常只保留带因果掩码的 decoder 结构。现代实现还常换用 RoPE、RMSNorm、SwiGLU、GQA 等组件。名称仍叫 Transformer，但细节不是固定不变。

## 为什么能并行训练

训练时整段正确文本已知，所有位置的 Query、Key、Value 可同时计算；因果 mask 只阻止读取未来信息，不要求按位置逐次执行。生成时新 token 未知，因此通常必须逐步生成。

## 概念与公式导航

- [[../15-概念词典/18-注意力分数与注意力权重|注意力分数与注意力权重]]

## 练习

1. 画出一个 Pre-Norm Transformer 块的数据流。
2. 输入 `[2,128,768]`、12 个头，每头 Q 形状是什么？
3. 为什么残差连接要求子层输出仍是维度 $D$？
4. 训练可并行、生成通常不可完全并行，原因是什么？

## 来源

- Vaswani et al. (2017). *Attention Is All You Need*. https://arxiv.org/abs/1706.03762 `[A]`
- Radford et al. (2018). *Improving Language Understanding by Generative Pre-Training* https://cdn.openai.com/research-covers/language-unsupervised/language_understanding_paper.pdf `[A]`
- Brown et al. (2020). *Language Models are Few-Shot Learners* https://arxiv.org/abs/2005.14165 `[A]`