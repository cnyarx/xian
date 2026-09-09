---
aliases: [MoE路由公式, Top-k专家公式, 负载均衡损失, Mixture of Experts Routing]
tags: [公式, Transformer, MoE, 大模型, 学习教程]
prerequisites: ["[[求和与下标]]", "[[MoE路由与专家负载]]", "[[Softmax稳定计算与温度公式]]", "[[FFN与SwiGLU公式]]"]
---
# MoE 路由与专家组合公式

## 1. 路由分数与概率

对 token 表示 $x$：

$$
z=W_rx
$$

$$
p(e\mid x)=\frac{e^{z_e}}{\sum_{j=1}^{N}e^{z_j}}
$$

- $W_r$：路由器权重；
- $N$：专家数量；
- $z_e$：专家 $e$ 的 logit；
- $p(e\mid x)$：该 token 对专家 $e$ 的路由权重。

## 2. Top-k 选择与重新归一化

令 $S(x)=\operatorname{TopK}(p(\cdot\mid x),k)$。只保留集合 $S(x)$ 中的专家：

$$
\tilde p_e(x)=
\begin{cases}
\dfrac{p(e\mid x)}{\sum_{j\in S(x)}p(j\mid x)},&e\in S(x)\\
0,&e\notin S(x)
\end{cases}
$$

有些实现不重新归一化或使用不同路由规则，应按模型定义核对。

## 3. 专家输出组合

$$
y=\sum_{e\in S(x)}\tilde p_e(x)E_e(x)
$$

$E_e$ 是第 $e$ 个专家 FFN。不同专家输出形状必须相同，才能加权求和。

## 4. 数值例子

4 个专家的路由权重：

$$
p=[0.55,0.25,0.15,0.05]
$$

Top-2 选择专家 1 和 2，保留权重总和为 0.8：

$$
\tilde p=[0.6875,0.3125,0,0]
$$

若两个专家输出为：

$$
E_1(x)=[2,0],\qquad E_2(x)=[0,4]
$$

则：

$$
y=0.6875[2,0]+0.3125[0,4]=[1.375,1.25]
$$

## 5. Switch Transformer 的负载均衡辅助损失

一种常见形式是：

$$
L_{aux}=\alpha N\sum_{e=1}^{N}f_eP_e
$$

- $f_e$：批次中实际路由到专家 $e$ 的 token 比例；
- $P_e$：批次中专家 $e$ 的平均路由概率；
- $N$：专家数；
- $\alpha$：辅助损失权重。

当路由较均匀时，$f_e$ 和 $P_e$ 都接近 $1/N$。该辅助项与主任务损失共同优化。

不同 MoE 架构的负载均衡目标并不相同；例如有些方法使用无辅助损失的偏置更新，不能把上式视为所有 MoE 的统一公式。

## 6. 容量

若一批有 $T$ 个 token、$N$ 个专家，容量因子为 $c$，Top-1 路由的单专家容量常粗略设为：

$$
C=\left\lceil c\frac{T}{N}\right\rceil
$$

Top-k、分布式分组和具体框架会改变容量核算。

## 7. 边界

- 路由概率是计算中间量，不是专家质量的绝对概率；
- Top-k 选择不可简单等同于随机采样；
- 激活参数少不自动等于低延迟，All-to-All 通信与负载不均可能主导成本；
- 总参数量、激活参数量和每 token FLOPs 必须分别报告。

## 最小自测

1. 权重 $[0.1,0.6,0.2,0.1]$ 的 Top-2 归一化结果是多少？
2. 为什么专家输出必须形状相同？
3. 负载均衡损失太强可能造成什么问题？

答案：

1. Top-2 是索引 1 和 2（若从 0 开始编号，则是第 2、3 个专家），保留权重总和为 $0.6+0.2=0.8$，重新归一化后为 $[0,0.75,0.25,0]$。
2. 最终输出是各专家输出的加权和，形状不同无法相加。
3. 强制均匀分配可能牺牲路由质量，把 token 送到不擅长的专家，影响模型效果。

## 正文

- [[稠密模型与 MoE|稠密模型与 MoE]]

## 来源

- Shazeer et al. (2017), *Outrageously Large Neural Networks*：https://arxiv.org/abs/1701.06538 `[A]`
- Fedus, Zoph & Shazeer (2022), *Switch Transformers*：https://jmlr.org/papers/v23/21-0998.html `[A]`
- Lepikhin et al. (2021), *GShard*：https://arxiv.org/abs/2006.16668 `[A]`
