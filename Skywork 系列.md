---
aliases:
  - Skywork
  - 天工模型
tags:
  - 计算机学
  - 开放权重
  - 国内模型
  - 模型档案
  - 大模型
family: Skywork
status: 已核验开放权重
---

# Skywork 系列

## 身份

开发机构：SkyworkAI。当前纳入本档案的正式开放权重系列包括 `Skywork-MoE-Base`、`Skywork-OR1`、`Skywork-R1V3`、`SkyReels-V3` 和 `UniPic-3`。这些模型用途不同，不应当视为同一个架构版本。

## 主要开放权重

| 系列 | 代表版本 | 参数/激活参数 | 类型 |
|---|---|---:|---|
| Skywork-MoE | Base、Base-FP8 | 146B / 22B | MoE |
| Skywork-OR1 | 7B、32B | 7B、32B | Dense，规则奖励 RL |
| Skywork-R1V3 | 38B | 38B | 视觉语言推理 |
| SkyReels-V3 | R2V/V2V-14B、A2V-19B | 14B、19B | 视频生成 |
| UniPic-3 | UniPic-3 | 未公开 | 图像理解、生成和编辑 |

## 训练方法

- Skywork-MoE：从 Skywork-13B 初始化，使用 Gating Logit Normalization 和 Adaptive Auxiliary Loss Coefficients；完整预训练数据、token 数和算力未知。
- Skywork-OR1：在 DeepSeek-R1-Distill-Qwen 基础上进行大规模规则奖励强化学习，官方同时发布 RL 数据集。
- Skywork-R1V3：基于 InternVL3-38B，采用多模态强化微调。
- SkyReels-V3：图像—视频混合训练、多分辨率训练和音视频对齐训练。
- UniPic-3：使用 CM、DMD distillation 和约 8-step 推理；完整训练数据未知。

## 上下文与部署

传统文本上下文长度：除 OR1 训练脚本出现 8K/16K/32K 配置外，多数系列官方未明确正式最大上下文，不能把训练配置直接当作服务上限。官方部署涉及 Transformers、vLLM、FP8、block offload 和多卡 tensor parallelism。

## 许可证与开放边界

- Skywork-MoE 使用 Skywork Community License。
- OR1、R1V3、SkyReels-V3、UniPic-3 的权重许可证需按具体模型卡核对；代码许可证不能替代权重许可证。
- 完整训练数据、训练代码、训练成本和全部中间 checkpoint 未统一开放。

## 未公开字段

总训练 token 数、完整数据配比、清洗去重、奖励模型细节、完整网络配置、训练硬件与成本、部分权重许可证：未知。

## 官方来源

- [Skywork-MoE GitHub](https://github.com/SkyworkAI/Skywork-MoE)
- [Skywork-OR1 GitHub](https://github.com/SkyworkAI/Skywork-OR1)
- [Skywork-R1V GitHub](https://github.com/SkyworkAI/Skywork-R1V)
- [SkyReels-V3 GitHub](https://github.com/SkyworkAI/SkyReels-V3)
- [UniPic GitHub](https://github.com/SkyworkAI/UniPic)
- [Skywork Hugging Face 组织](https://huggingface.co/Skywork)

证据等级：主要字段为 A（官方仓库、模型页或技术报告）；缺少官方确认的字段标记为 U。