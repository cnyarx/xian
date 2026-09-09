---
aliases:
  - NVIDIA Nemotron
tags:
  - 计算机学
  - 开放权重
  - 海外模型
  - 模型档案
  - 大模型
family: NVIDIA Nemotron
status: 已核验开放权重
---

# NVIDIA Nemotron 系列

## 主要开放权重

| 系列 | 代表版本 | 参数/激活参数 | 上下文 |
|---|---|---:|---:|
| Nemotron Nano | Nano 2、3 Nano | 12B/9B；30B/约3.2B | 最高 1M 级 |
| Nemotron Super | 3 Super 120B-A12B | 120B/12B | 最高 1M |
| Nemotron Ultra | 3 Ultra 550B-A55B | 550B/55B | 最高 1M |
| Nemotron Omni | 3 Nano Omni | 30B/约3B | 家族级 1M 方向 |
| Nemotron Lightning | 3.5 Lightning | 约30B/3B | 版本未单独明确 |
| Llama Nemotron | Nano/Super/Ultra | 8B–253B | 128K 级 |

## 许可证与开放边界

多数型号提供官方权重。训练语料、教师输出、奖励模型、完整 RL 轨迹、完整训练成本和中间 checkpoint 未完全公开。Llama 底座还受 Meta 许可证约束，Qwen 底座需结合 Qwen 许可证；不能把 Nemotron 全部统一标为 Apache 2.0。

## 未公开字段

逐 checkpoint 的完整许可证、训练数据、教师输出、奖励模型、RL 轨迹、训练成本和全部中间 checkpoint：未知。

## 官方来源

- [Nemotron 研究主页](https://research.nvidia.com/labs/nemotron/)
- [Nemotron 3 Nano](https://research.nvidia.com/labs/nemotron/Nemotron-3/)
- [Nemotron 3 Super](https://developer.nvidia.com/blog/introducing-nemotron-3-super-an-open-hybrid-mamba-transformer-moe-for-agentic-reasoning/)
- [Nemotron 3 Ultra](https://research.nvidia.com/labs/nemotron/Nemotron-3-Ultra/)
- [Nemotron 3.5 Lightning](https://developer.nvidia.com/blog/nvidia-nemotron-3-5-lightning-delivers-fast-accurate-specialized-task-execution-for-long-running-agents/)

证据等级：权重和版本规格为 A；未逐 checkpoint 核实的字段为 U。