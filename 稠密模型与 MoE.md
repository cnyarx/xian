---
aliases: [MoE, Mixture of Experts, 稀疏专家模型, Dense]
tags: [Transformer, 模型架构, 教程, 大模型, 学习教程]
prerequisites: ["[[前馈网络]]", "[[Logit概率与采样|Logit、概率与采样]]", "[[MoE路由与专家负载|MoE 路由、Top-k 与专家负载]]"]
next: ["[[模型并行]]"]
---
# 稠密模型与 MoE

## 稠密模型

Dense 模型中，每个 token 基本经过同一套主要层和参数。总参数量通常接近每 token 实际参与计算的参数量。

## MoE

Mixture of Experts（专家混合）把某些 FFN 换成多个专家网络。路由器为每个 token 选择少数专家：

$$p(e\mid x)=\operatorname{softmax}(W_rx)$$

选择 top-k 专家后：

$$y=\sum_{e\in\operatorname{TopK}}p(e\mid x)E_e(x)$$

- $E_e$：第 $e$ 个专家 FFN。
- $p(e\mid x)$：路由权重。

完整符号、Top-k 归一化和负载均衡见[[MoE路由与组合公式|MoE 路由与专家组合公式]]。

## 一个 token 的路由例子

4 个专家的路由概率为：

$$
[0.55,0.25,0.15,0.05]
$$

Top-2 选择前两个专家。若重新归一化，权重变为：

$$
[0.6875,0.3125]
$$

若两个专家输出分别是 $[2,0]$ 和 $[0,4]$，组合输出为：

$$
0.6875[2,0]+0.3125[0,4]=[1.375,1.25]
$$

## 总参数与激活参数

例如 64 个专家、每 token 只激活 2 个：模型可拥有很大总参数，但每 token 只用一小部分专家参数。比较 MoE 时必须分别报告总参数量与激活参数量。

## 负载均衡

路由器可能总选少数专家，导致其他专家闲置、设备拥堵。训练通常加入负载均衡损失，鼓励 token 更均匀分配；过强又可能损害专业化。

## 代价

MoE 增加路由、跨设备 All-to-All 通信、负载不均和部署复杂度。激活参数少不自动等于延迟低。

## 概念与公式导航

- [[MoE路由与专家负载|MoE 路由与专家负载]]
- [[MoE路由与组合公式|MoE 路由与专家组合公式]]

## 练习

1. Dense 与 MoE 的主要区别是什么？
2. 为什么要区分总参数和激活参数？
3. 路由器塌缩会造成什么问题？
4. MoE 为什么依赖高效专家并行？

## 来源

- Shazeer, N. et al. (2017). *Outrageously Large Neural Networks: The Sparsely-Gated Mixture-of-Experts Layer*. ICLR https://arxiv.org/abs/1701.06538 `[A]`
- Fedus, W. et al. (2022). *Switch Transformers: Scaling to Trillion Parameter Models with Simple and Efficient Sparsity*. JMLR https://arxiv.org/abs/2101.03961 `[A]`
- Lepikhin et al. (2021). *GShard: Scaling Giant Models with Conditional Computation and Automatic Sharding*. ICLR https://arxiv.org/abs/2006.16668 `[A]`