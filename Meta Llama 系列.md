---
aliases:
  - Meta Llama
  - Llama 4
tags:
  - 计算机学
  - 开放权重
  - 海外模型
  - 模型档案
  - 大模型
family: Meta Llama
status: 已核验开放权重
---

# Meta Llama 系列

## 主要开放权重

| 版本 | 总/激活参数 | 上下文 | 架构 |
|---|---:|---:|---|
| Llama 4 Scout 17B-16E | 109B / 17B | 10M | 原生多模态 early-fusion MoE，16 experts |
| Llama 4 Maverick 17B-128E | 400B / 17B | 1M | 原生多模态 early-fusion MoE，128 experts |

## 训练方法

Scout 约 40T 多模态 tokens，Maverick 约 22T；数据包含公开、许可及 Meta 产品和服务数据，预训练数据截止约 2024-08。后训练使用人工数据、合成数据、LLM 分类器筛选、对抗提示和安全数据。具体 RLHF、DPO、PPO、RLAIF 与奖励模型组合未完整公开。

## 能力与部署

支持文本、多语言、图像理解、OCR、图表、文档、视觉推理、代码和长上下文。提供 BF16、FP8，生态中有 INT4 制品。官方说明完整 BF16 需要多 GPU；Scout INT4 面向单张 H100 级别部署，Maverick FP8 需要更大规模 GPU。

## 许可证与开放边界

权重开放，采用 Llama 4 Community License，并受 Acceptable Use Policy、商用规模条款和命名要求约束。训练数据和完整训练代码未开放，不能直接称为完整开源。

## 官方来源

- [Llama Models GitHub](https://github.com/meta-llama/llama-models)
- [Llama 4 Model Card](https://github.com/meta-llama/llama-models/blob/main/models/llama4/MODEL_CARD.md)
- [Meta Llama Hugging Face](https://huggingface.co/meta-llama)
- [Llama 4 License](https://github.com/meta-llama/llama-models/blob/main/models/llama4/LICENSE)

## 未公开字段

完整数据配比、训练代码、奖励模型、全部训练成本和部分部署基准：未知。