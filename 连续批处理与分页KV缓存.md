---
aliases: [连续批处理, PagedAttention, 分页KV缓存, Continuous Batching, Paged KV Cache]
tags: [概念, 模型服务, 推理, 大模型, 学习教程]
level: L6
prerequisites: ["[[坐标维度与形状]]", "[[标量向量矩阵与张量]]", "[[KV-Cache容量公式|KV Cache 容量公式]]"]
---
# 连续批处理与分页 KV 缓存

## 一句话定义

连续批处理（Continuous Batching）在每个解码步更新正在执行的请求集合；分页 KV 缓存把每个请求的 KV Cache 切成固定大小的逻辑块，再映射到可不连续的物理显存块。

## 静态批处理的问题

假设一批有两个请求：A 需要生成 2 个 token，B 需要生成 20 个。静态批处理若等整批结束，A 完成后仍占着批次位置，新的请求不能及时加入。

连续批处理在 A 结束后释放其槽位，并可在下一轮把请求 C 加入。批次成员随时间变化，所以调度器还要处理优先级、超时、取消和显存容量。

## Prefill 与 Decode

- Prefill（提示处理）：一次处理提示中的多个 token，矩阵乘法规模较大；
- Decode（逐 token 解码）：每个请求每轮通常只生成一个新 token，但要读取历史 KV Cache。

两者的计算和内存特征不同。服务系统可混合或分开调度，具体策略会影响首 token 延迟（Time to First Token，TTFT）和逐 token 延迟（Time per Output Token，TPOT）。

## 分页 KV 缓存

传统做法可能为一个请求预留连续的大块显存，但最终长度未知，容易浪费。分页方法把逻辑块号映射到物理块号：

```text
请求 A 的逻辑块: 0  1  2
物理显存块:      7  3  9
```

这些块不必相邻。请求增长时再分配新块；结束时归还块。共享前缀还可让多个逻辑序列引用相同的只读物理块，再在发生分歧时分配新块。

## 容量小例子

块大小为 16 token，一个请求当前有 33 token，需要：

$$
\left\lceil\frac{33}{16}\right\rceil=3
$$

个块，共有 48 个 token 槽位，其中最后一个块暂时使用 1 个槽位。分页不能消除最后一块的内部空闲，但把浪费限制在不足一个块。

## 边界

- PagedAttention 是注意力服务中的内存管理与执行方法，不改变模型训练得到的注意力数学定义；
- 连续批处理提高资源利用率不代表每个请求延迟都下降，排队策略可能提高尾延迟；
- 块越小，内部浪费通常越少，但元数据和调度开销会增加；
- vLLM、TensorRT-LLM 等系统的参数和支持范围随版本变化，应以对应版本文档为准。

## 最小自测

题目：块大小为 8 token，一个 17-token 请求至少需要几个 KV 块？最后一块有多少已用槽位？

答案：需要 3 块；最后一块使用 1 个槽位。

## 详细教程

- [[KV Cache|KV Cache]]
- [[模型服务|模型服务]]

## 来源

- Kwon et al. (2023), *Efficient Memory Management for Large Language Model Serving with PagedAttention*：https://arxiv.org/abs/2309.06180 `[A]`
- vLLM Documentation：https://docs.vllm.ai/ `[A]`
- NVIDIA TensorRT-LLM Inflight Batching：https://nvidia.github.io/TensorRT-LLM/advanced/gpt-attention.html `[A]`
