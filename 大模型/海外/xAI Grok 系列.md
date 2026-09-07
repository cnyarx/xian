---
aliases:
  - xAI Grok
  - Grok-1
tags:
  - 计算机学
  - 开放权重
  - 海外模型
  - 模型档案
family: xAI Grok
status: 已核验开放权重（仅 Grok-1）
---

# xAI Grok 系列

## 已确认开放权重：Grok-1

| 字段 | 内容 |
|---|---|
| 参数 | 314B |
| 架构 | 8-expert MoE，每 token 激活 2 个专家 |
| 层数 | 64 |
| Query/KV heads | 48 / 8 |
| Embedding size | 6,144 |
| 词表 | 131,072 |
| 上下文 | 8,192 |
| 位置编码 | RoPE |
| 许可证 | Apache 2.0 |

Grok-1 权重和 JAX 参考推理实现开放；训练数据、训练代码、对齐方法和激活参数未公开。

## 不纳入的版本

Grok-1.5、Grok-1.5V、Grok-2、Grok-3、Grok-4 及 Heavy 的 API 或产品页面不能证明权重开放。Grok-2.5 虽有负责人公开声明，但本次未完成权重文件、配置、tokenizer、许可证和可运行源码的文件级闭环，暂不纳入已确认主表。

## 许可证

Grok-1 使用 Apache 2.0；训练数据、训练代码、对齐方法和激活参数未公开。

## 未公开字段

训练数据、训练代码、对齐方法、激活参数、Grok-2.5 文件级权重证据和许可证：未知。

## 官方来源

- [Grok-1 GitHub](https://github.com/xai-org/grok-1)
- [Grok-1 权重](https://huggingface.co/xai-org/grok-1)

证据等级：Grok-1 权重和架构为 A；其他型号的开放状态为 U 或排除。