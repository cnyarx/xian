---
aliases: [Token ID, 词元编号, Vocabulary Index]
tags: [概念, Token]
level: L4
prerequisites: ["[[04-求和与下标]]", "[[06-集合与映射]]"]
---
# Token、词表与 Token ID

## 一句话定义

Token（词元）是 tokenizer 处理文本时使用的离散单位；词表（Vocabulary）是全部可用 token 的集合；token ID 是某个 token 在词表中的编号。

## 一个最小词表

```text
0 → <pad>
1 → <unk>
2 → 我
3 → 爱
4 → 学习
```

“我爱学习”可编码为 `[2,3,4]`。编号只用于查表，`4` 不表示“学习”比“我”大两倍。

## Token 不一定是什么

Token 不一定等于：

- 一个汉字；
- 一个英文单词；
- 一个固定字节数；
- 一个有独立语义的单位。

它可能是字符、子词、标点、字节组合或特殊控制符，取决于 tokenizer。

## 编码与解码

- 编码（Encoding）：文本 → token → ID。
- 解码（Decoding）：ID → token → 文本。

解码未必能恢复所有原始排版细节，取决于归一化和 tokenizer 规则。

## 与模型的关系

模型的嵌入矩阵和输出层与特定词表 ID 一起训练，因此不能随意把模型与另一个 tokenizer 混用。

## 最小自测

题目：token ID 100 和 101 在语义上一定比 100 和 500 更相近吗？

答案：不一定。ID 距离只是编号差，不是语义距离。

## 详细教程

- [[../05-语言与Token/01-什么是 Token|什么是 Token]]
- [[../05-语言与Token/02-词表与编码|词表与编码]]

## 来源

- Hugging Face, Tokenizer Summary：https://huggingface.co/docs/transformers/tokenizer_summary `[A]`
- Kudo & Richardson (2018), *SentencePiece*：https://arxiv.org/abs/1808.06226 `[A]`
