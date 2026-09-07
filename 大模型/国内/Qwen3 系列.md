---
aliases:
  - Qwen3
  - 通义千问 Qwen3
tags:
  - 计算机学
  - 开放权重
  - 国内模型
  - 模型档案
family: Qwen3
status: 已核验开放权重
---

# Qwen3 系列

## 身份与开放权重

Qwen3 是阿里云 Qwen 团队正式发布的开放权重模型系列。官方仓库和模型组织提供多种 Dense、MoE、Base、Instruct/Thinking 及部署制品。具体变体应以官方模型组织实时列表和各 checkpoint 模型卡为准。

`qwen3.8-max` 不是本系列公开权重的规范命名，而是阿里云百炼云服务型号；不能与 `Qwen3-8B` 混同。

## 主要特点

- 同系列包含 Dense 与 MoE；总参数和每 token 激活参数必须分别记录；
- 支持 thinking 与 non-thinking 等不同交互模式；
- 支持多语言、代码、数学、工具调用与 Agent 场景；
- 官方生态覆盖 Transformers、vLLM、SGLang、llama.cpp、Ollama、ModelScope 等。

## 训练与证据边界

官方仓库和模型卡披露架构、用法、部分训练与评测信息。完整预训练数据、精确配比、全部训练代码、算力和后训练轨迹未完全开放，因此仍属于开放权重而非完整开放训练。

## 许可证

许可证必须按具体 Qwen3 checkpoint 核对，不能把 API 服务条款或第三方量化许可证套用给官方权重。

## 官方来源

- [Qwen3 GitHub](https://github.com/QwenLM/Qwen3)
- [Qwen Hugging Face 组织](https://huggingface.co/Qwen)
- [Qwen ModelScope 组织](https://modelscope.cn/organization/qwen)
- [Qwen3-8B](https://huggingface.co/Qwen/Qwen3-8B)

## 未公开字段

完整训练数据、数据配比、全部后训练配方、训练成本和部分变体的独立训练细节：未知。