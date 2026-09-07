---
aliases:
  - TeleChat
  - Tele-AI
tags:
  - 计算机学
  - 开放权重
  - 国内模型
  - 模型档案
family: TeleChat
status: 已核验开放权重
---

# TeleChat 系列

## 身份

开发机构：Tele-AI。当前纳入 `TeleChat3`、`TeleChat3-Coder`、`TeleChat2.5` 和 `TeleChat2 MoE`。文本、代码和 MoE 版本分开记录。

## 主要开放权重

| 系列 | 代表版本 | 参数/激活参数 | 类型 | 上下文 |
|---|---|---:|---|---:|
| TeleChat3 | 105B-A4.7B-Thinking | 105B / 4.7B | MoE | 未公开 |
| TeleChat3 | 36B-Thinking | 36B | Dense | 未公开 |
| TeleChat3-Coder | 36B-Thinking | 36B | Dense | 128K |
| TeleChat2.5 | 35B、115B | 35B、115B | Dense | 未公开 |
| TeleChat2 | 39B-A12B | 39B / 12B | MoE | 未公开 |

## 架构与训练

TeleChat3 105B-A4.7B-Thinking：45 层、hidden size 2560、FFN intermediate size 7680、MLA、192 个 routed experts、每 token 激活 4 个专家、1 个 shared expert。

TeleChat3 36B-Thinking：64 层、hidden size 6144、FFN intermediate size 24576、GQA。

TeleChat3-Coder：经历 8K 通用代码继续预训练、32K 仓库级代码和 SWE 数据、128K 长程代码与 Agent 数据、冷启动 SFT、规则奖励和 Reward Model 强化学习、Agentic RL 与 Interleaved Thinking。

TeleChat2.5：公开描述涉及理科和编程合成数据、多阶段课程学习、规则奖励强化学习、Function Calling、安全和指令遵循增强。

## 训练与部署

TeleChat3 公开说明使用国产 NPU、4096 个 NPU、专家并行、多维并行和通信计算重叠；预训练 token 数、完整数据、训练成本和后训练配方未知。官方部署生态包括 Transformers、vLLM、SGLang、LLaMA-Factory、MindSpore Transformers 和昇腾 Atlas。

## 许可证与开放边界

官方权重可下载，但 Tele-AI 主要仓库许可证字段为 null，README 未提供 Apache-2.0 或 MIT 等标准许可证文本。因此不能自行标注为标准开源许可证。完整训练数据、训练代码、奖励模型和训练成本未知。

## 未公开字段

完整训练数据、训练 token 数、上下文长度、训练成本、后训练配方、奖励模型和标准许可证：未知。

## 官方来源

- [TeleChat3 GitHub](https://github.com/Tele-AI/TeleChat3)
- [TeleChat3-Coder GitHub](https://github.com/Tele-AI/TeleChat3-Coder)
- [TeleChat2.5 GitHub](https://github.com/Tele-AI/TeleChat2.5)
- [TeleChat2 GitHub](https://github.com/Tele-AI/TeleChat2)
- [TeleChat3 105B ModelScope](https://modelscope.cn/models/TeleAI/TeleChat3-105B-A4.7B-Thinking)
- [TeleChat3 36B ModelScope](https://modelscope.cn/models/TeleAI/TeleChat3-36B-Thinking)
- [TeleChat3 技术报告](https://arxiv.org/abs/2512.24157)

证据等级：规格和权重为 A；社区或推测性训练信息不纳入结论。