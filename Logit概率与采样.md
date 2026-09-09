---
aliases: [Logit, 概率, Softmax]
tags: [概念, 概率, 生成, 大模型, 学习教程]
level: L5
prerequisites: ["[[数与实数]]", "[[比例分数与百分数]]", "[[随机事件与随机变量]]"]
---
# Logit、概率与采样

## 一句话定义

Logit 是模型给每个候选 token 的未归一化实数分数；softmax 把 logits 转成概率分布；采样或解码策略再根据分布选择 token。

## 三步不能混在一起

```text
隐藏状态 → 输出层 → logits
logits → softmax → 概率
概率 → greedy / sampling → 选出的 token
```

softmax 只计算概率，不负责随机选择。

## 例子

logits 为 `[2,1,0]`，softmax 后约为 `[0.665,0.245,0.090]`。

- 贪心会选第一个候选；
- 随机采样大多数时候选第一个，也可能选后两个；
- 调温度会改变分布尖锐程度，但不改变模型参数。

## 概率意味着什么

概率总和为 1，表示模型在当前上下文、当前参数和词表下对下一个 token 的相对分配。它不是事实正确率，也不是模型对整段回答可信度的天然校准。

## 数值边界

数学上有限 logits 的 softmax 概率为正；浮点程序中极小概率可能下溢为 0。稳定实现通常减最大 logit。

## 最小自测

题目：若 softmax 已给出概率 `[0.7,0.2,0.1]`，是否已经决定输出第一个 token？

答案：没有。还要指定贪心或某种采样策略。

## 详细教程

- [[分类与回归|分类与回归]]
- [[采样策略|采样策略]]

## 来源

- Goodfellow, Bengio, Courville (2016), *Deep Learning*, Chapter 6：https://www.deeplearningbook.org/ `[A]`
- Hugging Face, Generation Strategies：https://huggingface.co/docs/transformers/generation_strategies `[A]`
