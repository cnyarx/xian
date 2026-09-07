---
aliases: [偏好数据, 奖励模型, RLHF, RLAIF, 奖励破解, Bradley-Terry, Preference Data, Reward Model, Reward Hacking]
tags: [概念, 后训练, 对齐, 强化学习]
level: L10
prerequisites: ["[[19-策略奖励优势与基线]]", "[[44-后训练与指令微调]]", "[[36-熵与信息度量]]"]
---
# 偏好数据、奖励模型与 RLHF

## 一句话定义

RLHF（Reinforcement Learning from Human Feedback）利用人类反馈构造训练信号；常见流程是先收集回答偏好、训练奖励模型，再用强化学习优化语言模型。RLAIF（Reinforcement Learning from AI Feedback）让 AI 在明确准则或人类制定的原则下参与生成或评判反馈，但通常仍需要人工设计目标、校准和审计，不能简单理解为完全取消人类。

## 直觉理解

老师不直接写标准答案，而是比较两个学生的回答，说"A 比 B 好"。奖励模型学会这种比较规则，然后训练模型老师觉得好的回答。就像用裁判打分代替标准答案。

## 严格定义

Bradley-Terry 偏好模型（类似 Elo 等级分）：对偏好回答 $y_w$ 和非偏好回答 $y_l$：

$$P(y_w\succ y_l)=\frac{\exp(r(y_w))}{\exp(r(y_w))+\exp(r(y_l))}$$

奖励模型用交叉熵学习排序。之后用 PPO 等算法优化生成策略，使奖励模型给高分的同时不偏离 SFT 模型太远。

## 例子

标注员比较两个回答："猫是哺乳动物" 和 "猫是一种会飞的爬行动物"，始终选择前者。奖励模型学到的奖励函数会给前者更高分。

## 边界

- 奖励模型可能学到意外规则（"奖励破解"），如长度偏差、风格偏好；
- 人类偏好不一致、有噪声，且随时间变化；
- RLHF 训练比 SFT 更不稳定，需要仔细调参。

## 最小自测

1. 为什么需要奖励模型，不直接让人类打分？
2. 奖励破解的典型例子是什么？

答案：1. 人类标注成本高、速度慢，无法在训练循环中实时打分；2. 模型学会输出冗长回答或使用某些格式词来获得高分，而不真正改善内容。

## 详细教程

- [[../08-后训练与对齐/03-人类反馈强化学习|RLHF]]

## 来源

- Christiano et al. (2017), *Deep Reinforcement Learning from Human Preferences*：https://arxiv.org/abs/1706.03741 `[A]`
- Ouyang et al. (2022), *Training Language Models to Follow Instructions with Human Feedback*：https://arxiv.org/abs/2203.02155 `[A]`
- Bai et al. (2022), *Constitutional AI: Harmlessness from AI Feedback*：https://arxiv.org/abs/2212.08073 `[A]`