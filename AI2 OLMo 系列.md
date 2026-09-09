---
aliases:
  - AI2 OLMo
  - OLMo 3
tags:
  - 计算机学
  - 开放权重
  - 海外模型
  - 模型档案
  - 大模型
family: AI2 OLMo
status: 已核验开放权重
---

# AI2 OLMo 系列

## OLMo 3

| 版本 | 参数 | 上下文 | 主要变体 |
|---|---:|---:|---|
| OLMo 3 7B | 约7.3B | 65,536 | Base、Think、Instruct、SFT、DPO |
| OLMo 3 32B | 约32.23B | 65,536 | Base、Think、Instruct、SFT、DPO |
| OLMo-Hybrid-7B | 约7B | 65,536 | Gated Delta Net + Attention |

## 许可证与开放边界

OLMo 公开最终权重、Base/Think/Instruct checkpoint、训练代码、数据配方和大量训练信息；原始数据受上游许可证限制，optimizer state 并非所有阶段完整开放。代码 Apache 2.0，权重以具体模型卡为准。

## 未公开字段

原始数据的完整再分发权限、所有阶段的 optimizer state、部分硬件拓扑和统一能耗记录：未知。

## 官方来源

- [OLMo GitHub](https://github.com/allenai/OLMo)
- [OLMo-core](https://github.com/allenai/OLMo-core)
- [OLMo 3 技术报告](https://arxiv.org/abs/2512.13961)
