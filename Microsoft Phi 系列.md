---
aliases:
  - Microsoft Phi
  - Phi-4
tags:
  - 计算机学
  - 开放权重
  - 海外模型
  - 模型档案
  - 大模型
family: Microsoft Phi
status: 已核验开放权重
---

# Microsoft Phi 系列

## 主要版本

| 版本 | 参数 | 上下文 | 说明 |
|---|---:|---:|---|
| Phi-4 | 14B | 未公开 | Dense 文本 |
| Phi-4-mini-instruct | 3.8B | 128K | Dense、GQA |
| Phi-4-multimodal-instruct | 5.6B | 128K 级 | 文本/图像/音频 |
| Phi-4-reasoning | 14B | 未公开 | 推理后训练 |
| Phi-4-reasoning-vision | 15B | 未公开 | Mid-fusion，多模态推理 |

## Phi-4-reasoning-vision

采用 SigLIP-2 NaFlex 视觉编码器和 Phi-4-Reasoning 语言骨干，最终数据约 200B 多模态 tokens，其中约 20% reasoning、80% non-reasoning。数据包括筛选开放数据、内部领域数据、定向采购数据和程序化合成数据；SFT 和安全拒答训练已确认，DPO/RLHF 未完整确认。

## 许可证

Phi 家族级许可证为 MIT，但具体模型卡仍是最终依据。

## 未公开字段

完整预训练数据、代码、安全配方、训练硬件和成本：未知。

## 官方来源

- [Phi-4 技术报告](https://arxiv.org/abs/2412.08905)
- [Phi-4-reasoning 技术报告](https://arxiv.org/abs/2504.21318)
- [Phi-4-reasoning-vision 官方博客](https://www.microsoft.com/en-us/research/blog/phi-4-reasoning-vision-and-the-lessons-of-training-a-multimodal-reasoning-model/)
- [Microsoft Phi Hugging Face](https://huggingface.co/microsoft)
