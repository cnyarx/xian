---
aliases: [MoE路由, Top-k专家, 专家负载, Router, Expert Routing, Expert Load]
tags: [概念, Transformer, MoE]
level: L6
prerequisites: ["[[04-求和与下标]]", "[[08-标量向量矩阵与张量]]", "[[17-Logit概率与采样]]", "[[../16-公式手册/12-FFN与SwiGLU公式|FFN 与 SwiGLU 公式]]"]
---
# MoE 路由、Top-k 与专家负载

## 一句话定义

MoE 路由（Mixture-of-Experts Routing）为每个 token 选择少数专家网络；Top-k 表示只保留得分最高的 $k$ 个专家；专家负载表示各专家实际收到多少 token。

## 路由器

路由器先把 token 表示 $x$ 变成每个专家的分数：

$$
z=W_rx
$$

再用 softmax 得到路由权重：

$$
p(e\mid x)=\operatorname{softmax}(z)_e
$$

$p(e\mid x)$ 是当前 token 分配给专家 $e$ 的权重，不是专家正确率。

## Top-k 选择

若有 4 个专家，路由权重为：

$$
[0.55,0.25,0.15,0.05]
$$

Top-2 只保留前两个专家。常见实现会把保留权重重新归一化：

$$
\left[\frac{0.55}{0.8},\frac{0.25}{0.8}\right]
=[0.6875,0.3125]
$$

然后组合两个专家输出。

## 专家负载

专家负载可以按收到的 token 数统计：

$$
n_e=\sum_t\mathbf 1[e\in\operatorname{TopK}(x_t)]
$$

其中指示函数 $\mathbf 1[\cdot]$ 在条件成立时为 1，否则为 0。

如果少数专家收到绝大多数 token，会发生拥堵、丢弃 token 或设备利用率低等问题。

## 容量限制

分布式 MoE 实现常为每个专家设置容量。超过容量的 token 可能被丢弃、转给其他专家或延后处理，具体行为由模型和系统实现决定。

## 负载均衡

训练常加入辅助损失，让专家接收 token 的比例和平均路由概率更均衡。辅助项过弱可能路由塌缩，过强则可能阻碍专家形成不同专长。

## 边界

- Top-k 是离散选择步骤，不等于只训练 $k$ 个永久固定专家；不同 token 可选不同专家；
- 总参数量包括全部专家，激活参数量只包括当前 token 实际调用的专家；
- 激活参数少不自动等于延迟低，跨设备 All-to-All 通信可能成为瓶颈。

## 最小自测

题目：4 个专家权重为 $[0.1,0.6,0.2,0.1]$，Top-2 选择谁？重新归一化后的权重是多少？

答案：选择专家 2 和专家 3；总权重为 0.8，归一化后为 $[0.75,0.25]$。

## 详细教程

- [[../06-注意力与Transformer/10-稠密模型与 MoE|稠密模型与 MoE]]
- [[../10-训练系统与规模化/03-模型并行|模型并行]]

## 来源

- Shazeer et al. (2017), *Outrageously Large Neural Networks: The Sparsely-Gated Mixture-of-Experts Layer*：https://arxiv.org/abs/1701.06538 `[A]`
- Fedus, Zoph & Shazeer (2022), *Switch Transformers*：https://jmlr.org/papers/v23/21-0998.html `[A]`
- Lepikhin et al. (2021), *GShard*：https://arxiv.org/abs/2006.16668 `[A]`
