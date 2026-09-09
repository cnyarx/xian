---
aliases: [KV Cache, KV 缓存]
tags: [大模型, 推理, 教程, 学习教程]
prerequisites: ["[[注意力变体：GQA 与 MQA]]"]
next: ["[[推测解码]]"]
---
# KV Cache

## 为什么缓存

生成第 $t$ 个 token 时，新 Query 要与前面所有 Key 比较，并混合所有 Value。过去 token 的 K/V 不会改变，重复计算是浪费，所以保存到 KV cache。

## 缓存大小

单请求近似元素数：

$$2\times L\times T\times H_{kv}\times d_{head}$$

乘每元素字节数后得到内存：

$$\text{bytes}=2LTH_{kv}d_{head}\times\text{bytes-per-element}$$

- 2：K 与 V。
- $L$：层数。
- $T$：上下文长度。
- $H_{kv}$：KV 头数。
- $d_{head}$：头维度。

批量与并发还会继续乘大。

## 数值例子

32 层、4096 token、8 个 KV 头、头维 128、BF16（2 字节）：

$$2\times32\times4096\times8\times128\times2\approx512\text{ MiB}$$

仅一个请求就约 512 MiB；实际框架还有其他开销。

## PagedAttention

传统连续内存预留会造成碎片和浪费。PagedAttention 把 KV cache 分成固定块，像操作系统分页一样按需分配和共享，提高服务内存利用率。

## 常见误区

- KV cache 不保存所有中间激活，只保存每层历史 K/V。
- 缓存减少重复计算，但增加显存占用。
- 量化 KV cache 可能省显存，但精度和速度收益需实测。

## 概念与公式导航

- [[KV-Cache基础|KV Cache 基础]]
- [[KV-Cache容量公式|KV Cache 容量公式]]

## 练习

1. 用公式算一个给定模型的 KV cache。
2. 上下文长度翻倍，缓存怎样变化？
3. GQA 为什么降低缓存？
4. PagedAttention 解决什么问题？

## 来源

- Pope, R. et al. (2023). *Efficiently Scaling Transformer Inference*. MLSys https://arxiv.org/abs/2211.05102 `[A]`
- Kwon et al. (2023). *Efficient Memory Management for Large Language Model Serving with PagedAttention*. SOSP. https://arxiv.org/abs/2309.06180 `[A]`