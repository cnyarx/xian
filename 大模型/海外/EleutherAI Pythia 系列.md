---
aliases:
  - EleutherAI Pythia
  - Pythia
tags:
  - 计算机学
  - 开放权重
  - 海外模型
  - 模型档案
family: EleutherAI Pythia
status: 已核验开放权重
---

# EleutherAI Pythia 系列

## 正式尺寸

14M、31M、70M、160M、410M、1B、1.4B、2.8B、6.9B、12B，主要型号均有 Standard 和 Deduped 版本。

## 统一规格

GPT-NeoX 风格 Dense decoder-only Transformer，RoPE，上下文 2,048；训练数据为 The Pile，Deduped 使用去重版，训练规模约 300B tokens，约 143,000 steps，全局 batch 2,097,152 tokens。主要型号提供约 154 个 checkpoint，基本是 Base 模型，不是生产级 RLHF/DPO 产品。

## 许可证与开放边界

权重、配置、tokenizer、训练代码、中间 checkpoint 和 Standard/Deduped 数据配方开放程度高；原始数据受上游许可证限制，optimizer state、硬件拓扑和能耗记录未统一开放。许可证为 Apache 2.0 体系。

## 未公开字段

原始数据完整再分发权限、统一 optimizer state、硬件拓扑和能耗记录：未知。

适合研究 scaling law、训练动态、记忆和遗忘、数据重复、能力形成与机制解释。

## 官方来源

- [Pythia GitHub](https://github.com/EleutherAI/pythia)
- [Pythia 论文](https://arxiv.org/abs/2304.01373)
- [Pythia-70M](https://huggingface.co/EleutherAI/pythia-70m)
- [Pythia-12B](https://huggingface.co/EleutherAI/pythia-12b)
