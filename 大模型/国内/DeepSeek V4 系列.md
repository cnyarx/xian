---
aliases:
  - DeepSeek V4
  - DeepSeek-V4-Pro
  - deepseek-v4-pro
tags:
  - 计算机学
  - 开放权重
  - 国内模型
  - 模型档案
family: DeepSeek V4
status: 已核验开放权重
---

# DeepSeek V4 系列

## 身份

官方规范名为 `DeepSeek-V4-Pro`，API 名为 `deepseek-v4-pro`。原写法 `deepseek v4 pro` 属于名称格式差异，不是另一个模型。

## 开放权重证据

官方更新日志确认正式版上线；DeepSeek V4 开源公告明确说明 V4 预览版同步开源，并提供官方 ModelScope 集合。具体 Pro 仓库的文件 API 确认存在连续的 64 个 Safetensors 分片、`model.safetensors.index.json`、非零大小、LFS 标记和 SHA-256，权重合计约 864.72 GB。

## 许可证与开放边界

当前证据足以确认正式发布和可下载权重，但档案尚未从技术报告逐项闭环总参数、激活参数、专家结构、上下文、训练 token 数、数据、后训练、量化和许可证。未公开信息统一写未知。

## 未公开字段

总参数、激活参数、专家结构、上下文、训练 token 数、数据、后训练、量化和许可证：未知。

## 官方来源

- [DeepSeek 官方更新日志](https://api-docs.deepseek.com/zh-cn/updates/)
- [DeepSeek V4 开源公告](https://www.deepseek.com/news/v4-preview/)
- [DeepSeek V4 ModelScope 集合](https://modelscope.cn/collections/deepseek-ai/DeepSeek-V4)
- [DeepSeek-V4-Pro ModelScope](https://modelscope.cn/models/deepseek-ai/DeepSeek-V4-Pro)

验证边界：本次确认官方公告和约 865GB 权重文件元数据，未全量下载或本地推理。