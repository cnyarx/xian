---
aliases: [Token, 词元, 分词, Tokenization, BPE, SentencePiece]
tags: [大模型, NLP, 教程, 学习教程]
prerequisites: ["[[嵌入]]"]
next: ["[[词表与编码]]"]
---
# 什么是 Token

## 一句话定义

Token（词元）是语言模型一次读取或生成的基本文字单位。它可能是一个字、一个词、词的一部分、标点或空格。

## 为什么不直接按“词”处理

语言中的词数量近乎无限：新名字、错别字、代码、网址不断出现。若每个完整词都占一个词表位置，词表会巨大，而且无法处理新词。

按单个字符处理虽然不会遇到未知词，但序列太长，而且一个词的意义被拆得太碎。现代 tokenizer 通常在字符与完整词之间折中，使用子词（Subword）。

## 一个例子

同一句话在不同 tokenizer 下可能被分成：

```text
输入：unbelievable!
按字符：u | n | b | e | l | i | e | v | a | b | l | e | !
按词：unbelievable | !
子词：un | believ | able | !
```

切分没有唯一正确答案；它是模型设计的一部分。

## BPE

字节对编码（Byte Pair Encoding，BPE）从小单位开始，反复合并训练语料中最常见的相邻组合。

简化例子：

```text
初始：l o w, l o w e r, n e w e s t
发现 l+o 常见 → 合并为 lo
发现 lo+w 常见 → 合并为 low
```

合并次数决定词表大小。高频片段可能成为一个 token，低频词会被拆成多个 token。

## SentencePiece

SentencePiece 把文本当作原始 Unicode 字符序列直接训练子词模型，不要求先按空格分词，因此适合中文、日文等没有天然空格分词的语言。它支持 BPE 和 Unigram 两类算法。

## 字节级分词

字节级 tokenizer 先把文本转为 UTF-8 字节，再合并常见字节序列。基础字节集合有限，因此原则上可以表示任何文本，不需要真正的未知字符；代价是某些文字可能占多个 token。

## Token 数为什么重要

- 模型上下文长度按 token 而不是汉字或单词计算。
- API 常按 token 计费。
- 训练数据规模用 token 数衡量。
- 不同语言的平均 token 长度不同，会影响成本和可用上下文。

## 常见误区

- 一个 token 不等于一个汉字或英语单词。
- token ID 只是编号，没有大小意义。
- tokenizer 与模型必须配套；换 tokenizer 后原有嵌入矩阵不再对应。

## 概念与公式导航

- [[Token词表与Token-ID|Token、词表与 Token ID]]

## 练习

1. 尝试把“人工智能改变世界”按字符、词和子词分别切分。
2. 为什么完整词级词表无法可靠处理新词？
3. 为什么中文不能简单照搬按空格分词？
4. 同一段文字使用不同 tokenizer，token 数会相同吗？

## 来源

- Sennrich, R. et al. (2016). *Neural Machine Translation of Rare Words with Subword Units*. ACL. https://arxiv.org/abs/1508.07909 `[A]`
- Kudo, T. & Richardson, J. (2018). *SentencePiece*. EMNLP System Demonstrations. https://arxiv.org/abs/1808.06226 `[A]`
- Radford, A. et al. (2019). *Language Models are Unsupervised Multitask Learners*. GPT-2 report https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf `[A]`