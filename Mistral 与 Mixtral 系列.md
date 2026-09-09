---
aliases:
  - Mistral
  - Mixtral
tags:
  - 计算机学
  - 开放权重
  - 海外模型
  - 模型档案
  - 大模型
family: Mistral/Mixtral
status: 已核验开放权重
---

# Mistral 与 Mixtral 系列

## 主要开放权重

| 版本 | 总/激活参数 | 上下文 | 类型 |
|---|---:|---:|---|
| Mistral Medium 3.5 | 128B / 128B | 256K | Dense，多模态 |
| Mistral Small 4 | 119B / 6.5B | 256K | Hybrid 稀疏激活 |
| Mistral Large 3 | 675B / 41B | 256K | granular MoE，多模态 |
| Ministral 3 | 3B/8B/14B | 256K | Dense，多模态 |
| Mixtral 8x22B v0.3 | 约141B / 约39B | 64K | 8 experts、top-2 MoE |

## 训练与能力

公开资料涉及文本、代码、图文交错数据、开放数据和 proprietary sources。各型号的完整训练 token、数据比例、SFT、DPO、RLHF 和奖励模型未完整披露。能力覆盖通用文本、代码、文档问答、结构化输出、函数调用、多模态图像理解、Agent 和长上下文。

## 许可证

大型模型需要多 GPU，性能必须结合精度、硬件、引擎和并发记录。许可证按 checkpoint 区分：Apache 2.0、Modified MIT 或具体定制条款均可能存在；不能用推理代码许可证替代权重许可证。

## 未公开字段

多数版本完整训练配方、数据、训练成本和全部中间 checkpoint：未知。

## 官方来源

- [Mistral 模型定义](https://github.com/mistralai/platform-docs-public/tree/main/src/schema/models/models)
- [Mistral Hugging Face](https://huggingface.co/mistralai)
- [Ministral 3 技术报告](https://arxiv.org/abs/2601.08584)
- [Mixtral 8x22B 权重](https://huggingface.co/mistralai/Mixtral-8x22B-v0.1)

未公开字段：多数版本完整训练配方、数据、训练成本和全部中间 checkpoint。