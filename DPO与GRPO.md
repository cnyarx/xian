---
aliases: [DPO, ORPO, GRPO, 直接偏好优化, 组相对策略优化, Direct Preference Optimization, Odds Ratio Preference Optimization, Group Relative Policy Optimization]
tags: [概念, 后训练, 对齐, 大模型, 学习教程]
level: L11
prerequisites: ["[[策略奖励优势与基线]]", "[[偏好数据与RLHF]]", "[[Logit概率与采样]]"]
---
# DPO、ORPO 与 GRPO

## 一句话定义

DPO（Direct Preference Optimization）直接从偏好对中学习，无需显式训练奖励模型；ORPO 在同一阶段同时学习示范和偏好；GRPO（Group Relative Policy Optimization）用同一问题的多个回答的组内相对奖励估计优势。

## 直觉理解

经典基于 PPO 的 RLHF 常先训练奖励模型，再训练策略，并额外使用价值函数（critic）估计未来回报。DPO 把特定奖励建模假设化进偏好损失，直接用胜负回答对更新策略，因此训练时不需要单独拟合一个显式奖励模型。GRPO 对同一问题采样多个回答，先由规则校验器、人工标签或奖励模型等来源给出奖励，再用组内相对奖励估计优势；它可以省去单独训练的价值函数，但不会凭空产生“哪个回答更好”的奖励信号。

## 严格定义

DPO 损失（给定偏好对 $(y_w,y_l)$）：

$$L_{\text{DPO}}=-\log\sigma\left(\beta\log\frac{\pi_\theta(y_w)}{\pi_{\text{ref}}(y_w)}-\beta\log\frac{\pi_\theta(y_l)}{\pi_{\text{ref}}(y_l)}\right)$$

- $\pi_\theta$：当前策略；$\pi_{\text{ref}}$：参考策略（通常是 SFT 模型）；
- $\beta$：控制相对参考策略偏离尺度的超参数。

GRPO 对同一问题的 $G$ 个回答先得到奖励 $r_1,\ldots,r_G$，再用组内均值和标准差进行相对标准化，例如：

$$
A_i=\frac{r_i-\operatorname{mean}(r_1,\ldots,r_G)}{\operatorname{std}(r_1,\ldots,r_G)+\epsilon}
$$

这里省去的是 PPO 中另行学习的价值函数基线，不是奖励来源。完整策略目标还包含概率比裁剪和对参考策略的约束，见对应正文与公式页。

## 例子

偏好对：问题"猫是什么"，回答 A "哺乳动物" 胜出，回答 B "爬行动物" 失败。DPO 提高 A 相对 B 的概率比，同时用参考策略防止偏离太远。

## 边界

- DPO 通常需要先做 SFT，而 ORPO 在同一阶段融入示范学习；
- 偏好数据质量、覆盖范围和标注一致性会显著影响效果，不能只比较算法名称；
- 参考策略是 DPO 中限制策略偏离的正则化锚点，而不是性能上限；结果还取决于偏好数据覆盖、参考分布支持、模型能力和正则强度；
- GRPO 更依赖组内回答的多样性。

## 最小自测

1. DPO 和经典“奖励模型 + PPO”训练流程的最大区别是什么？
2. GRPO 中“组相对”是什么意思？GRPO 是否仍需要奖励信号？

答案：1. DPO 直接从偏好对构造损失更新策略，训练时不必另行拟合显式奖励模型；2. 对同一问题生成多个回答，用组内奖励的相对位置估计优势。它仍需要规则、人工或奖励模型等来源提供奖励，省去的通常是单独学习的价值函数基线。

## 详细教程

- [[直接偏好优化|DPO]]
- [[组相对策略优化|GRPO]]

## 来源

- Rafailov et al. (2024), *Direct Preference Optimization*：https://arxiv.org/abs/2305.18290 `[A]`
- Hong et al. (2024), *ORPO: Monolithic Preference Optimization without Reference Model*：https://arxiv.org/abs/2403.07691 `[A]`
- Shao et al. (2024), *DeepSeekMath: Pushing the Limits of Mathematical Reasoning*：https://arxiv.org/abs/2402.03300 `[A]`