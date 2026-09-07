---
aliases: [Decoder-only, GPT 架构, 因果注意力, Causal Attention]
tags: [Transformer, 大模型, 教程]
prerequisites: ["[[07-完整 Transformer 积木]]"]
next: ["[[09-注意力变体：GQA 与 MQA]]", "[[../07-预训练/01-预训练概览]]"]
---
# Decoder-Only 架构

## 一句话定义

Decoder-only Transformer 只使用带因果掩码的自注意力，每个位置只能读取自己和之前的 token，适合从左到右生成文本。

## 因果注意力

对于序列 `[A,B,C,D]`：

```text
A 可看：A
B 可看：A B
C 可看：A B C
D 可看：A B C D
```

上三角未来位置被 mask，避免训练时偷看答案。

## GPT 式数据流

```text
Token IDs
 ↓ token embedding + position
N × Transformer block（causal self-attention + FFN）
 ↓ final norm
词表投影
 ↓ softmax
下一个 token 概率
```

## 与 encoder-only、encoder-decoder 比较

- Encoder-only（如 BERT）：双向看上下文，适合理解和表示任务。
- Decoder-only（如 GPT 系列）：单向因果注意力，统一做生成任务。
- Encoder-decoder（如原始 Transformer、T5）：编码器读取完整输入，解码器生成输出，适合翻译和转换。

这些是常见用途，不是绝对限制。

## 为什么 decoder-only 能做多任务

把任务和示例都写成文本上下文，模型始终执行同一目标：继续生成。分类、摘要、翻译和代码生成都可转换成“根据提示生成合适后续”。

## 上下文学习

模型可根据提示中的说明和少量示例改变当前输出行为，叫 in-context learning。它通常不修改模型参数，只改变当前上下文中的计算状态。

## 常见误区

- “decoder” 不只是把编码还原成人类文字，它是架构名称。
- 因果注意力不是模型只能使用前一句；它能使用上下文窗口内全部可见历史。
- 上下文学习不等于永久训练，换一个对话通常不会保留参数变化。

## 概念与公式导航

- [[../15-概念词典/34-因果掩码与注意力掩码|因果掩码与注意力掩码]]
- [[../15-概念词典/39-上下文学习|上下文学习]]

## 练习

1. 为 4-token 序列画因果 mask。
2. 比较 BERT 和 GPT 的注意力可见范围。
3. 为什么 decoder-only 可以做分类？
4. 上下文学习和微调有什么区别？

## 来源

- Vaswani et al. (2017). *Attention Is All You Need* https://arxiv.org/abs/1706.03762 `[A]`
- Radford et al. (2018). *Improving Language Understanding by Generative Pre-Training* https://cdn.openai.com/research-covers/language-unsupervised/language_understanding_paper.pdf `[A]`
- Brown et al. (2020). *Language Models are Few-Shot Learners*. https://arxiv.org/abs/2005.14165 `[A]`