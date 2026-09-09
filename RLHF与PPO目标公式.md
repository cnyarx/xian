---
aliases: [RLHF目标公式, PPO裁剪目标, KL奖励, RLHF Objective, PPO Clipped Objective]
tags: [公式, 对齐, 强化学习, 大模型, 学习教程]
prerequisites: ["[[求和与下标]]", "[[似然最大似然与负对数似然]]", "[[策略奖励优势与基线]]", "[[熵交叉熵与KL散度公式]]"]
---
# RLHF 与 PPO 目标公式

## 1. RLHF 的概念性目标

语言模型 RLHF 常概括为：

$$
\max_\theta\;\mathbb E_{x\sim D,\,y\sim\pi_\theta(\cdot\mid x)}
\left[r_\phi(x,y)-\beta D_{KL}\!\left(\pi_\theta(\cdot\mid x)\parallel\pi_{ref}(\cdot\mid x)\right)\right]
$$

- $D$：提示数据分布；
- $\pi_\theta$：正在训练的策略模型；
- $\pi_{ref}$：冻结的参考模型；
- $r_\phi(x,y)$：奖励模型对回答 $y$ 的评分；
- $\beta>0$：KL 惩罚强度。

第一项鼓励高奖励回答，第二项限制策略过度偏离参考模型。

这是一条概念性目标，不是 PPO 实现的全部损失。实际系统还要处理逐 token 概率比、优势估计、价值函数、裁剪和批次采样。

## 2. PPO 概率比

对状态 $s_t$ 和动作 $a_t$：

$$
r_t(\theta)=\frac{\pi_\theta(a_t\mid s_t)}{\pi_{old}(a_t\mid s_t)}
$$

$r_t>1$ 表示新策略提高了该动作概率，$r_t<1$ 表示降低了概率。

## 3. PPO 裁剪代理目标

$$
L^{CLIP}(\theta)=\mathbb E_t\left[
\min\left(
r_t(\theta)A_t,
\operatorname{clip}(r_t(\theta),1-\epsilon,1+\epsilon)A_t
\right)
\right]
$$

- $A_t$：动作相对基线的优势；
- $\epsilon$：允许概率比变化的裁剪范围；
- `clip`：把比值限制到 $[1-\epsilon,1+\epsilon]$。

取两项较小值，目的是不让单批数据推动策略概率改变过大。

## 4. 数值例子

设 $\epsilon=0.2$、$A_t=2$，旧策略概率为 0.4，新策略概率为 0.6：

$$
r_t=0.6/0.4=1.5
$$

未裁剪项为 $1.5\times2=3$，裁剪比值为 1.2，裁剪项为 $1.2\times2=2.4$：

$$
\min(3,2.4)=2.4
$$

目标不会继续奖励超出裁剪范围的这次概率增长。

若 $A_t<0$，`min` 的行为会限制概率下降过多；不能只用正优势例子的直觉机械理解所有情况。

## 5. 奖励中的 KL 近似

工程实现常把逐 token KL 惩罚加入奖励，例如：

$$
r_t^{total}=r_t^{task}-\beta\left(\log\pi_\theta(a_t\mid s_t)-\log\pi_{ref}(a_t\mid s_t)\right)
$$

这是采样动作上的对数概率差，用于估计策略偏离；它与对所有可能动作精确求和的完整 KL 不是同一个计算过程。

## 6. 边界

- PPO 不等于“奖励减 KL”这一条概念式；
- 裁剪降低单次更新过大的风险，但不能保证训练绝对稳定；
- 奖励模型可能被利用，KL 也不能自动保证事实性和安全性；
- 不同实现对 KL、优势、价值损失和熵奖励的组合不同，应以论文与代码为准。

## 最小自测

1. 旧概率 0.5、新概率 0.55，概率比是多少？
2. $A=1,\epsilon=0.2,r=1.4$ 时，裁剪目标取哪一项？
3. 为什么概念性 RLHF 目标不能替代 PPO 的完整实现？

答案：

1. $r=0.55/0.5=1.1$。
2. 未裁剪项为 $1.4$，裁剪后概率比为 $1.2$，裁剪项为 $1.2$；目标取两者较小值 $1.2$。
3. 完整 PPO 还涉及逐 token 概率比、优势估计、价值损失、熵项、裁剪、批量与多轮更新、终止处理和参考策略 KL 的具体估计。概念公式只说明方向，缺少实现正确性所需的全部细节。

## 正文

- [[人类反馈强化学习|人类反馈强化学习]]

## 来源

- Schulman et al. (2017), *Proximal Policy Optimization Algorithms*：https://arxiv.org/abs/1707.06347 `[A]`
- Ouyang et al. (2022), *Training Language Models to Follow Instructions with Human Feedback*：https://arxiv.org/abs/2203.02155 `[A]`
- Stiennon et al. (2020), *Learning to Summarize with Human Feedback*：https://arxiv.org/abs/2009.01325 `[A]`
