---
aliases: [GRPO公式, 组相对优势, Group Relative Policy Optimization]
tags: [公式, 对齐, 强化学习]
prerequisites: ["[[../15-概念词典/04-求和与下标]]", "[[../15-概念词典/19-策略奖励优势与基线]]", "[[19-RLHF与PPO目标公式]]"]
---
# GRPO 优势与目标公式

## 1. 组内奖励

对同一提示 $q$，旧策略生成 $G$ 个候选：

$$
\{o_1,o_2,\ldots,o_G\}\sim\pi_{old}(\cdot\mid q)
$$

每个候选得到奖励 $r_i$。

## 2. 组相对优势

简化的中心化形式是：

$$
\bar r=\frac1G\sum_{j=1}^{G}r_j
$$

$$
A_i=r_i-\bar r
$$

DeepSeekMath 中使用组内标准化：

$$
A_i=\frac{r_i-\bar r}{s_r+\epsilon}
$$

$$
s_r=\sqrt{\frac1G\sum_{j=1}^{G}(r_j-\bar r)^2}
$$

标准化让不同题目上的奖励尺度更可比；若组内奖励完全相同，$s_r=0$，实现需要用 $\epsilon$ 或跳过该组，具体以代码为准。

## 3. 数值例子

奖励：

$$
[1,0,-1,1]
$$

平均值：

$$
\bar r=0.25
$$

中心化优势：

$$
[0.75,-0.25,-1.25,0.75]
$$

总体标准差：

$$
s_r=\sqrt{\frac{0.75^2+(-0.25)^2+(-1.25)^2+0.75^2}{4}}
=\sqrt{0.6875}\approx0.829
$$

标准化优势约为：

$$
[0.905,-0.302,-1.508,0.905]
$$

## 4. GRPO 的裁剪目标

令第 $i$ 个候选第 $t$ 个 token 的概率比为：

$$
\rho_{i,t}(\theta)=
\frac{\pi_\theta(o_{i,t}\mid q,o_{i,<t})}
{\pi_{old}(o_{i,t}\mid q,o_{i,<t})}
$$

核心裁剪项与 PPO 相似：

$$
\min\left(
\rho_{i,t}A_i,
\operatorname{clip}(\rho_{i,t},1-\varepsilon,1+\varepsilon)A_i
\right)
$$

对组内候选和 token 求平均，并加入相对参考策略的 KL 惩罚，可以写成概括形式：

$$
J_{GRPO}(\theta)=\mathbb E\left[
\frac1G\sum_{i=1}^{G}\frac1{|o_i|}\sum_t
\left(
\min(\rho_{i,t}A_i,\operatorname{clip}(\rho_{i,t},1-\varepsilon,1+\varepsilon)A_i)
-\beta D_{KL}(\pi_\theta\parallel\pi_{ref})
\right)
\right]
$$

论文与实现可能使用特定的逐 token KL 估计器；上式用于展示组成部分，不应替代代码级定义。

## 5. 与 PPO 的关键区别

PPO 通常训练价值模型估计基线；GRPO 用同一提示下多个候选的组内奖励统计量构造优势，从而省去独立价值模型。但 GRPO 仍属于策略优化，仍会涉及采样、概率比、裁剪和 KL 约束。

## 6. 边界

- “无需价值模型”不等于“无需奖励”；
- 可验证奖励只适合能可靠自动判定的目标；
- 组太小或奖励全相同，组内比较提供的信息有限；
- 后续 GRPO 变体可能修改归一化、裁剪或 KL 设计，应按具体论文区分。

## 最小自测

1. 奖励 $[2,4,0]$ 的中心化优势是多少？
2. 为什么组内所有奖励相同时无法区分候选？
3. GRPO 省去的是奖励模型还是价值模型？

答案：

1. 均值为 2，中心化优势为 $[0,2,-2]$。
2. 此时每个候选的 $r_i-\bar r=0$；即使加入 $\epsilon$ 防止除零，所有优势仍为 0，组内没有“谁更好”的相对信息。
3. 经典 GRPO 主要省去的是单独训练的价值模型（critic）；它仍需要规则、人工或奖励模型等来源提供奖励信号。

## 正文

- [[../08-后训练与对齐/05-组相对策略优化|组相对策略优化]]

## 来源

- Shao et al. (2024), *DeepSeekMath: Pushing the Limits of Mathematical Reasoning in Open Language Models*：https://arxiv.org/abs/2402.03300 `[A]`
- Schulman et al. (2017), *Proximal Policy Optimization Algorithms*：https://arxiv.org/abs/1707.06347 `[A]`
