---
aliases:
  - Kimi K3
  - Kimi-K3
  - kimi-k3
tags:
  - 计算机学
  - 开放权重
  - 国内模型
  - 模型档案
family: Kimi K3
status: 已核验开放权重
---

# Kimi K3 系列

## 身份

Moonshot AI 官方产品展示名为 `Kimi K3`，仓库和模型路径常写 `Kimi-K3`。原始写法 `kimi-k3` 可对应该系列，但档案采用官方展示名。

## 开放权重证据

官方发布页宣布 Kimi K3，并说明完整模型权重发布；官方 GitHub 提供项目资料。ModelScope 文件 API 列出 `model-00001-of-000096.safetensors` 至 `model-00096-of-000096.safetensors`、索引、非零文件大小、LFS 标记和 SHA-256，分片总大小约 1.561 TB。

## 许可证与开放边界

当前核验足以确认模型正式发布和权重文件存在，但完整架构字段、总/激活参数、训练 token 数、数据配比、训练代码、后训练方法、上下文、部署基准和许可证仍需逐项从官方模型卡和技术报告补全；未披露字段不能猜测。

## 未公开字段

上述尚未逐项闭环的架构、训练、后训练、上下文、部署和许可证字段均为未知。

## 官方来源

- [Kimi K3 发布页](https://www.kimi.ai/blog/kimi-k3)
- [Kimi K3 官方仓库](https://github.com/MoonshotAI/Kimi-K3)
- [Kimi K3 ModelScope](https://modelscope.cn/models/moonshotai/Kimi-K3)
- [ModelScope 文件 API](https://modelscope.cn/api/v1/models/moonshotai/Kimi-K3/repo/files?Revision=master&Recursive=true)

验证边界：本次确认权重元数据存在，未全量下载 1.5TB 级权重，也未本地加载推理。