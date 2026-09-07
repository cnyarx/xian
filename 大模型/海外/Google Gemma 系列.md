---
aliases:
  - Google Gemma
  - Gemma 4
tags:
  - 计算机学
  - 开放权重
  - 海外模型
  - 模型档案
family: Google Gemma
status: 已核验开放权重
---

# Google Gemma 系列

## Gemma 4

| 版本 | 总/激活参数 | 上下文 | 架构/模态 |
|---|---:|---:|---|
| Gemma 4 E2B | 未公开 / 有效约2B | 128K | 端侧，多模态 |
| Gemma 4 E4B | 未公开 / 有效约4B | 128K | 端侧，多模态 |
| Gemma 4 26B-A4B | 26B / 3.8B | 256K | MoE，多模态 |
| Gemma 4 31B | 31B | 256K | Dense，多模态 |

## 训练与能力

支持 140 多种语言、多模态预训练、图像/视频/音频输入、function calling、结构化输出、Agent 工作流和长文档。完整训练数据、token 数、数据比例、SFT、DPO、RLHF/RLAIF、奖励模型、训练硬件和成本未公开。

## 许可证与部署

代码为 Apache 2.0；权重受 Gemma Terms of Use 和 Prohibited Use Policy 约束。官方提供 Hugging Face、Kaggle 和其他入口。26B、31B 的 BF16 可面向单张 80GB H100 级别 GPU，量化可降低资源需求。

## 官方来源

- [Gemma 4 发布页](https://blog.google/innovation-and-ai/technology/developers-tools/gemma-4/)
- [Gemma 4 Hugging Face Collection](https://huggingface.co/collections/google/gemma-4)
- [Google Gemma GitHub](https://github.com/google-deepmind/gemma)
- [Gemma Terms of Use](https://ai.google.dev/gemma/terms)

## 未公开字段

完整训练数据、训练代码、奖励模型和训练成本：未知。