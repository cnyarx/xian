---
aliases:
  - OpenAI gpt-oss
  - gpt-oss
tags:
  - 计算机学
  - 开放权重
  - 海外模型
  - 模型档案
  - 大模型
family: OpenAI gpt-oss
status: 已核验开放权重
---

# OpenAI gpt-oss 系列

## 主要版本

| 版本 | 总/激活参数 | 上下文 | 架构 |
|---|---:|---:|---|
| gpt-oss-120b | 约116.83B / 约5.13B | 131,072 | 稀疏 MoE Transformer |
| gpt-oss-20b | 约20.91B / 约3.61B | 131,072 | 稀疏 MoE Transformer |

120B 有 128 experts，20B 有 32 experts，每 token 激活 4 个专家；GQA、局部/全注意力交替、RoPE 和 MXFP4 线性层量化是共同特征。

## 训练与能力

公开信息包括万亿级 token 预训练、监督微调、推理强化学习、长思维链、工具调用、安全后训练和 Harmony response format。完整预训练数据、训练代码、奖励模型、RL 轨迹、蒸馏数据和中间状态未公开。支持 Transformers、vLLM、Triton、PyTorch、Metal、Ollama 和 LM Studio。

## 许可证与开放边界

Apache 2.0 开放权重；不通过 OpenAI API 或 ChatGPT 提供。MXFP4 版本的实际硬件需求取决于上下文、batch 和 KV cache。

## 未公开字段

完整预训练数据、训练代码、奖励模型、RL 轨迹、蒸馏数据和中间状态：未知。

## 官方来源

- [gpt-oss GitHub](https://github.com/openai/gpt-oss)
- [gpt-oss-120b](https://huggingface.co/openai/gpt-oss-120b)
- [gpt-oss-20b](https://huggingface.co/openai/gpt-oss-20b)
- [OpenAI Harmony](https://github.com/openai/harmony)
