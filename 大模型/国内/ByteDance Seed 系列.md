---
aliases:
  - Seed 模型
  - ByteDance Seed
tags:
  - 计算机学
  - 开放权重
  - 国内模型
  - 模型档案
family: ByteDance Seed
status: 已核验开放权重
---

# ByteDance Seed 系列

## 身份

开发机构：ByteDance Seed。当前纳入代码、GUI Agent、形式化证明和研究型多模态开放权重，不把 Seed2.x、Seedance、Seedream 等仅 API 或产品型号放入本档案。

## 主要开放权重

| 系列 | 代表版本 | 参数/激活参数 | 类型 |
|---|---|---:|---|
| Seed-Coder | 8B Base/Instruct/Reasoning | 8B | Dense 代码模型 |
| Stable-DiffCoder | 8B | 8B | Block Diffusion 代码模型 |
| BAGEL | 7B-MoT | 14B / 7B | Mixture-of-Transformer 多模态 |
| UI-TARS | 1.5-7B | 7B | GUI Agent |
| BFS-Prover | V1-7B | 7B | Lean4 定理证明 |
| M3-Agent | Memorization/Control | 未公开 | 研究型多模态 Agent |

## 训练方法

Seed-Coder：Base 做代码预训练，Instruct 进行 SFT 与偏好优化，Reasoning 进行 LongCoT 强化学习；上下文分别为 Base/Instruct 32K、Reasoning 64K。

Stable-DiffCoder：基于 Seed-Coder，使用 Block Diffusion continued pretraining、SFT、clipped noise schedule 和 any-order modeling，上下文 8K。

BAGEL：统一多模态理解和生成，使用交错多模态数据；完整 token 数、数据规模和训练算力未知。

UI-TARS：视觉语言模型结合 GUI 动作生成和强化学习推理，服务桌面、浏览器、移动端和游戏操作。

BFS-Prover：使用 Best-first search、Scalable expert iteration、DPO 和 Lean 编译器错误反馈自动构造 state-tactic pairs。

M3-Agent：涉及 episodic memory、semantic memory、跨模态检索和 Agent 行为控制；不应把它当作通用 LLM 家族。

## 许可证与部署

Seed-Coder 和 Stable-DiffCoder 标注 MIT。BAGEL、UI-TARS、BFS-Prover、M3-Agent 的代码多为 Apache-2.0，但权重许可证必须按具体模型卡核对，不能由代码许可证推断。官方提供 Hugging Face 权重和本地推理代码；具体吞吐、硬件和量化信息按版本分别核验。

## 未公开字段

除明确版本外的完整架构、训练 token 数、数据配比、奖励模型、训练硬件、训练成本、部分上下文和权重许可证：未知。

## 官方来源

- [Seed-Coder GitHub](https://github.com/ByteDance-Seed/Seed-Coder)
- [Stable-DiffCoder GitHub](https://github.com/ByteDance-Seed/Stable-DiffCoder)
- [BAGEL GitHub](https://github.com/ByteDance-Seed/Bagel)
- [UI-TARS GitHub](https://github.com/bytedance/UI-TARS)
- [M3-Agent GitHub](https://github.com/bytedance-seed/m3-agent)
- [ByteDance-Seed Hugging Face 组织](https://huggingface.co/ByteDance-Seed)
- [Seed-Coder 技术报告](https://arxiv.org/abs/2506.03524)
- [BFS-Prover 论文](https://arxiv.org/abs/2502.03438)

证据等级：权重和公开规格为 A；未明确披露字段为 U。