---
aliases:
  - DBRX
  - Databricks DBRX
tags:
  - 计算机学
  - 开放权重
  - 海外模型
  - 模型档案
  - 大模型
family: Databricks DBRX
status: 已核验开放权重
---

# Databricks DBRX 系列

## 主要版本

| 版本 | 总/激活参数 | 上下文 | 架构 |
|---|---:|---:|---|
| DBRX Base | 132B / 36B | 32K | Decoder-only，细粒度 MoE |
| DBRX Instruct | 132B / 36B | 32K | 同上，指令后训练 |

架构包含 16 experts、每 token 选择 4 个专家、GQA、RoPE 和 GLU。

## 训练与能力

约 12T 文本和代码 tokens，训练使用 3,072 张 H100。完整数据比例和训练代码未开放。Instruct 经过后训练、精炼、红队测试和人类反馈相关工作，但 RLHF、DPO 或其他方法的完整组合未知。能力覆盖通用语言、代码、推理、知识问答、RAG 和 Agent。

## 许可证与开放边界

采用 Databricks Open Model License，不能等同于 Apache 2.0。权重和模型卡开放，完整训练数据与过程未完全开放。

## 未公开字段

完整数据比例、训练代码、Instruct 的具体 RLHF/DPO 组合、训练成本和中间 checkpoint：未知。

## 官方来源

- [DBRX 发布文章](https://www.databricks.com/blog/introducing-dbrx-new-state-art-open-llm)
- [DBRX Base](https://huggingface.co/databricks/dbrx-base)
- [DBRX Instruct](https://huggingface.co/databricks/dbrx-instruct)
- [Databricks Open Model License](https://www.databricks.com/legal/open-model-license)
