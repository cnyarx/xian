---
aliases:
  - TII Falcon
  - Falcon-H1
tags:
  - 计算机学
  - 开放权重
  - 海外模型
  - 模型档案
  - 大模型
family: TII Falcon
status: 已核验开放权重
---

# TII Falcon 系列

## 主要开放权重

Falcon-H1 包含 0.5B、1.5B、3B、7B、34B，最高上下文 256K，采用 Attention + Mamba-2 混合结构、RoPE、μP，提供 Base、Instruct 和量化形式。Falcon-H1R-7B 基于 H1-7B，采用冷启动 SFT、GRPO 和数学/代码/科学/工具数据；训练响应目标约 48K，不能直接写成最大上下文窗口。Falcon Edge E-1B/E-3B 采用 BitNet 1.58-bit，面向 CPU 和边缘设备。

## 许可证与开放边界

公开方法涉及 continued pretraining、SFT、规则奖励强化学习和测试时推理扩展；完整预训练数据、训练代码、奖励配方和成本未开放。许可证按子系列核对，可能为 Falcon License 2.0 或型号特定条款，不能统一标为 Apache 2.0。

## 未公开字段

完整预训练数据、训练代码、奖励配方、训练成本、逐型号许可证和统一性能基准：未知。

## 官方来源

- [Falcon-H1 博客](https://falcon-lm.github.io/blog/falcon-h1/)
- [Falcon-H1 技术报告](https://arxiv.org/abs/2507.22448)
- [Falcon-H1 GitHub](https://github.com/tiiuae/falcon-h1)
- [Falcon Edge 博客](https://falcon-lm.github.io/blog/falcon-edge/)
- [Falcon Hugging Face Collection](https://huggingface.co/collections/tiiuae/falcon-h1-6819f2795bc406da60fab8df)
