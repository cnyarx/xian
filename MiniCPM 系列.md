---
aliases:
  - MiniCPM
  - OpenBMB MiniCPM
tags:
  - 计算机学
  - 开放权重
  - 国内模型
  - 模型档案
  - 大模型
family: MiniCPM
status: 已核验开放权重
---

# MiniCPM 系列

## 身份

开发机构：OpenBMB。当前纳入 `MiniCPM5`、`MiniCPM-SALA`、`MiniCPM-V`、`MiniCPM-o` 和 `MiniCPM4`。文本、小型模型、长上下文和多模态版本分开记录。

## 主要开放权重

| 系列 | 代表版本 | 参数 | 类型/能力 | 上下文 |
|---|---|---:|---|---:|
| MiniCPM5 | 1B、Base、SFT | 1B 级 | Dense，推理和工具调用 | 未公开 |
| MiniCPM-SALA | SALA | 9B | 稀疏注意力 + Lightning Attention | 正式最高 1M |
| MiniCPM-V | 4.6 | 1.3B 级 | 视觉语言 | 视频最多 128 主帧 |
| MiniCPM-o | 4.5 | 9B | 实时全模态交互 | 未公开 |
| MiniCPM4.1 | 8B | 8B | Dense | 原生 65K，LongRoPE 后 131K |
| MiniCPM4 | 8B、0.5B | 8B、0.5B | 文本模型 | 预训练 32K，扩展评测最高 128K |

## 训练方法

MiniCPM5：Base training、decay training、mid-training、Deep-thinking SFT、Hybrid-thinking SFT、RL teacher 和 On-Policy Distillation；官方披露 SFT 阶段约 200B tokens，但完整数据和训练成本未知。

MiniCPM-SALA：从已有 Transformer 转换，使用 25% InfLLM-V2 sparse attention、75% Lightning Attention、HyPE 和 HALO，进行长上下文继续训练；训练长度 520K，正式支持最高 1M，评测外推至 2048K。

MiniCPM-V 4.6：SigLIP2-400M 视觉编码器、Qwen3-0.8B 语言模型、LLaVA-UHD v4 压缩和混合视觉 token 压缩。

MiniCPM-o 4.5：整合 SigLIP2、Whisper-medium、CosyVoice2、Qwen3-8B 和 Omni-Flow，支持视觉、语音和全双工对话。

MiniCPM4：公开描述涉及可训练稀疏注意力、UltraClean、UltraChat v2、LongRoPE、Model Wind Tunnel 2.0、FP8、MTP 和 reasoning/non-reasoning 混合训练。

## 许可证

官方生态包括 Transformers、SGLang、vLLM、llama.cpp、Ollama、MLX、移动端和 HarmonyOS。MiniCPM 整体采用 Apache-2.0 路线，但训练数据和第三方组件仍需单独核对。

## 未公开字段

各版本完整训练数据、数据配比、清洗去重、完整训练 token 数、训练硬件、训练成本、部分网络细节和奖励模型：未知。

## 官方来源

- [MiniCPM GitHub](https://github.com/OpenBMB/MiniCPM)
- [MiniCPM5 Release](https://github.com/OpenBMB/MiniCPM/releases/tag/5.0)
- [MiniCPM-SALA GitHub](https://github.com/OpenBMB/MiniCPM-SALA)
- [MiniCPM-V GitHub](https://github.com/OpenBMB/MiniCPM-V)
- [MiniCPM-o GitHub](https://github.com/OpenBMB/MiniCPM-o)
- [OpenBMB Hugging Face 组织](https://huggingface.co/openbmb)
- [MiniCPM4 技术报告](https://arxiv.org/abs/2506.07900)

证据等级：公开规格、权重和许可证为 A；未披露字段统一为 U。