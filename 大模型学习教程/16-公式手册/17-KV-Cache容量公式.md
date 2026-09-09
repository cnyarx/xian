---
aliases: [KV Cache公式, KV缓存容量, Key Value Cache Memory]
tags: [公式, 推理, 显存]
prerequisites: ["[[../15-概念词典/01-数与实数]]", "[[../15-概念词典/02-比例分数与百分数]]", "[[../15-概念词典/05-坐标维度与形状]]", "[[10-缩放点积与多头注意力公式]]"]
---
# KV Cache 容量公式

## 1. 为什么缓存 K 和 V

生成第 $t$ 个 token 时，新 Query 要与所有历史 Key 比较，再用权重混合历史 Value。过去 token 的 K/V 不再改变，重复计算是浪费，因此保存到 KV cache。

## 2. 单序列元素数

$$
\text{elements}=2LTH_{kv}d_{head}
$$

- $2$：Key 和 Value 两份；
- $L$：Transformer 层数；
- $T$：缓存 token 数；
- $H_{kv}$：每层 KV 头数；
- $d_{head}$：每个 KV 头维度。

## 3. 字节数

$$
\text{bytes}=2LTH_{kv}d_{head}\times b
$$

$b$ 是每元素字节数：FP32 为 4，FP16/BF16 通常为 2，INT8 为 1。

## 4. 数值例子

32 层、4096 token、8 个 KV 头、头维 128、BF16：

$$
2\times32\times4096\times8\times128\times2
=536,870,912\text{ bytes}
$$

$$
\frac{536,870,912}{1024^2}=512\text{ MiB}
$$

这是单序列、未计批量和框架额外开销的近似值。

## 5. 批量与并发

若有 $B$ 条序列、长度相同：

$$
\text{bytes}_{batch}\approx B\times2LTH_{kv}d_{head}b
$$

实际服务中序列长度不同，需对每条序列分别求和。

## 6. GQA / MQA 为什么省缓存

标准 MHA 通常 $H_{kv}=H_q$；GQA 让多组 Query 头共享较少的 KV 头；MQA 所有 Query 头共享一组 KV，$H_{kv}=1$。缓存大小与 $H_{kv}$ 成正比，因此显著降低显存。

## 7. PagedAttention

PagedAttention 将 KV cache 分成固定大小的块，按需分配和共享，减少连续内存预留造成的碎片。它优化内存管理，不改变上述理论元素数。

## 8. 边界

- KV cache 只保存历史 K/V，不保存所有中间激活；
- 缓存减少重复计算，但增加显存占用；
- 量化 KV cache 可省显存，但精度和速度收益需要实测；
- 某些实现还存元数据、对齐填充或分块索引，实际占用会更高。

## 最小自测

1. 上述模型上下文从 4096 翻到 8192，缓存变多少？
2. 若 $H_{kv}$ 从 32 降到 8，缓存变为原来的多少？
3. 为什么 PagedAttention 不改变理论元素数却能提高服务容量？

答案：

1. 缓存与 $T$ 线性增长，从 512 MiB 变为 1024 MiB，即 1 GiB。
2. 与 $H_{kv}$ 成正比，变为 $8/32=1/4$。
3. 它减少连续内存预留和长度差异造成的碎片，并可复用同一批序列的共享前缀块；因此可用显存中能容纳更多有效缓存。但块内未填满会导致物理消耗略高于按元素数直接计算的理论值，且不同序列按需分配时实际总占用不等于 $B$ 条等长序列的固定公式。

## 正文

- [[../09-推理与生成/03-KV Cache|KV Cache]]
- [[../06-注意力与Transformer/09-注意力变体：GQA 与 MQA|GQA 与 MQA]]

## 来源

- Pope et al. (2023), *Efficiently Scaling Transformer Inference* https://arxiv.org/abs/2211.05102 `[A]`
- Kwon et al. (2023), *Efficient Memory Management for Large Language Model Serving with PagedAttention*：https://arxiv.org/abs/2309.06180 `[A]`