---
aliases: [KV Cache基础, 键值缓存, 显存增长, KV Cache, Memory Growth]
tags: [概念, 推理, 显存, 大模型, 学习教程]
level: L9
prerequisites: ["[[注意力分数与注意力权重]]", "[[标量向量矩阵与张量]]", "[[推理阶段与延迟指标]]"]
---
# KV Cache 基础

## 一句话定义

KV Cache 在自回归生成时保存所有历史 token 的 Key 和 Value 向量，避免每次生成新 token 时重复计算全部历史位置的注意力。

## 直觉理解

每写一个字，需要回顾前面所有字。不缓存的话，每写一个字就把整篇文章重读一遍（O(n²)），缓存后只读新字和在已存信息中查找（O(n)）。

## 严格定义

对于 $L$ 层、每层 $H_{kv}$ 个 KV 头、每头维度 $d$ 的模型，用 FP16 存储：

$$\text{KV Cache 大小}=2\times L\times H_{kv}\times d\times \text{序列长度}\times 2\text{ 字节}$$

若模型使用 GQA 或 MQA，$H_{kv}$ 小于注意力头总数 $H$，缓存相应减少。例如一个 7B 规模模型（$L=32,H_{kv}=8,d=128$），序列长度 2048：

$$
2\times 32\times 8\times 128\times 2048\times 2
=268,435,456\text{ 字节}\approx 256\text{ MiB}
$$

若同一模型使用 MHA（$H_{kv}=32$），同样条件下的缓存约 1 GiB。不同模型的具体层数、头数和头维度各异，实际数值需按目标模型参数代入。

## 例子

生成第 1000 个 token 时，没有缓存需要计算 1000² 次点积；有缓存只需计算 1000 次（新 token 与所有历史 Key 的点积）。

## 边界

- KV Cache 显存随序列长度线性增长，长对话或长文档可能成为瓶颈；
- 多请求并发时 KV Cache 翻倍；
- 量化 KV Cache 是降低显存占用的常用手段；
- PagedAttention 可以减少碎片。

## 最小自测

1. KV Cache 为什么能加速推理？
2. 序列长度翻倍，KV Cache 显存如何变化？

答案：1. 避免每个 Decode 步都重新计算历史 token 的 Key 和 Value；2. 线性增长，大致翻倍。

## 详细教程

- [[KV Cache|KV Cache]]

## 来源

- Vaswani et al. (2017), *Attention Is All You Need*：https://arxiv.org/abs/1706.03762 `[A]`
- Kwon et al. (2023), *Efficient Memory Management for Large Language Model Serving with PagedAttention*：https://arxiv.org/abs/2309.06180 `[A]`