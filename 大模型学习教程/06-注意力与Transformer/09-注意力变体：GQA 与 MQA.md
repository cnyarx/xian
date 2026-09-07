---
aliases: [GQA, MQA, 分组查询注意力, 多查询注意力, Grouped-Query Attention, Multi-Query Attention]
tags: [Transformer, 注意力, 推理优化, 教程]
prerequisites: ["[[03-多头注意力]]", "[[08-Decoder-Only 架构]]"]
next: ["[[../09-推理与生成/03-KV Cache]]"]
---
# 注意力变体：GQA 与 MQA

## 问题：KV cache 太大

生成时，每层过去 token 的 Key 和 Value 会保存到 KV cache，避免反复计算。标准多头注意力（MHA）每个 Query 头都有独立 K、V 头，长上下文时缓存很大。

## 三种结构

### MHA

若有 32 个 Query 头，也有 32 个 K 头和 32 个 V 头。

### MQA

多查询注意力（Multi-Query Attention）让全部 Query 头共享一组 K、V。缓存最小，但共享过强可能影响模型质量。

### GQA

分组查询注意力（Grouped-Query Attention）把 Query 头分组，每组共享一组 K、V。例如 32 个 Query 头、8 个 KV 头，每 4 个 Query 头共享一组 K、V。它在 MHA 与 MQA 之间折中。

## 缓存量级

忽略批量和字节数，每层缓存元素约：

$$2\times T\times H_{kv}\times d_{head}$$

- 2：K 和 V 两份。
- $T$：已生成与输入 token 数。
- $H_{kv}$：KV 头数。
- $d_{head}$：每头维度。

从 32 个 KV 头降到 8 个，理论缓存元素降为四分之一。

## 为什么 Query 不缓存

生成下一 token 时，只有当前新位置需要 Query；过去 Query 不再用于后续计算。过去 K、V 仍要被新 Query 查询，所以必须缓存。

## 质量与效率

原始 MQA 论文和 GQA 论文报告了在相应实验设置中的速度/质量折中，但不能推断所有模型、硬件和任务都具有同样收益。实际效果需要基准测试。

## 常见误区

- GQA 不减少 Query 头数，只减少 KV 头数。
- 头数减少比例不必严格等于端到端速度提升，因为还有其他计算和内存开销。
- MQA/GQA 主要优化推理解码内存带宽，也会改变训练架构。

## 概念与公式导航

- [[../15-概念词典/18-注意力分数与注意力权重|注意力分数与注意力权重]]
- [[../16-公式手册/17-KV-Cache容量公式|KV Cache 容量公式]]

## 练习

1. 32 个 Query 头、8 个 KV 头，每组几个 Query 头？
2. 为什么过去的 K/V 要缓存，Q 不需要？
3. MHA、GQA、MQA 按 KV cache 大小排序。
4. 为什么缓存缩小 4 倍不代表服务速度一定提高 4 倍？

## 来源

- Shazeer, N. (2019). *Fast Transformer Decoding: One Write-Head is All You Need*. https://arxiv.org/abs/1911.02150 `[A]`
- Ainslie, J. et al. (2023). *GQA: Training Generalized Multi-Query Transformer Models from Multi-Head Checkpoints*. EMNLP. https://arxiv.org/abs/2305.13245 `[A]`