---
aliases: [LoRA, QLoRA, 参数高效微调, 低秩适配, Parameter-Efficient Fine-Tuning, PEFT, Low-Rank Adaptation]
tags: [概念, 微调, 参数高效]
level: L10
prerequisites: ["[[08-标量向量矩阵与张量]]", "[[16-参数梯度与优化器]]", "[[44-后训练与指令微调]]"]
---
# LoRA 与参数高效微调

## 一句话定义

LoRA（Low-Rank Adaptation）冻结基础模型权重，只训练两个小型低秩矩阵的乘积来近似权重更新；QLoRA 进一步把基础模型量化以节省显存。

## 直觉理解

不重写整本百科全书，只在关键页面贴上便签。LoRA 的"便签"参数很少，可以为不同任务保存不同适配器。

## 严格定义

原权重 $W_0\in\mathbb R^{d\times k}$ 保持不变，训练：

$$W=W_0+\Delta W=W_0+BA$$

其中 $B\in\mathbb R^{d\times r}$，$A\in\mathbb R^{r\times k}$，且 $r\ll\min(d,k)$。参数从 $dk$ 减少到 $r(d+k)$。

## 例子

一个 $4096\times4096$ 矩阵有约 1680 万参数。取 $r=16$，LoRA 只训练 $4096\times16+16\times4096=131072$ 个参数，约为原来的 0.78%。

## 边界

- LoRA 只减少可训练参数，不一定减少推理显存；
- 秩 $r$ 太小会限制表达能力；
- QLoRA 的量化误差可能影响质量；
- 不同任务适配器不能简单叠加。

## 最小自测

1. LoRA 为什么能节省训练显存？
2. QLoRA 和 LoRA 的区别是什么？

答案：1. 冻结基础权重，只为小型 A/B 矩阵保存梯度和优化器状态；2. QLoRA 额外把基础模型量化到 4-bit。

## 详细教程

- [[../08-后训练与对齐/08-LoRA 与参数高效微调|LoRA 与参数高效微调]]

## 来源

- Hu et al. (2022), *LoRA: Low-Rank Adaptation of Large Language Models*：https://arxiv.org/abs/2106.09685 `[A]`
- Dettmers et al. (2023), *QLoRA: Efficient Finetuning of Quantized LLMs*：https://arxiv.org/abs/2305.14314 `[A]`