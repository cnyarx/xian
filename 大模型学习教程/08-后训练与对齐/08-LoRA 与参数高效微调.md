---
aliases: [LoRA, PEFT, 参数高效微调, QLoRA]
tags: [大模型, 微调, 教程]
prerequisites: ["[[02-监督微调]]", "[[../01-数学基础/01-向量与矩阵]]"]
next: ["[[../14-动手项目/05-微调一个开源模型]]"]
---
# LoRA 与参数高效微调

## 为什么不更新全部参数

全量微调需保存所有参数梯度和优化器状态，显存成本高。参数高效微调（PEFT）只训练少量新增或选定参数。

## LoRA

LoRA 冻结原权重 $W$，用两个低秩矩阵表示更新：

$$W'=W+\Delta W=W+BA$$

若 $W\in\mathbb{R}^{d_{out}\times d_{in}}$，则：

$$A\in\mathbb{R}^{r\times d_{in}},\quad B\in\mathbb{R}^{d_{out}\times r}$$

$r$ 很小。全量更新参数数为 $d_{out}d_{in}$，LoRA 只需 $r(d_{in}+d_{out})$。

常见缩放：

$$W'=W+\frac{\alpha}{r}BA$$

$\alpha$ 控制 LoRA 更新幅度。

## 数值例子

4096×4096 矩阵有约 1678 万参数。若 $r=8$，LoRA 参数：

$$8(4096+4096)=65536$$

约为原矩阵的 0.39%。

## QLoRA

QLoRA 将冻结基础模型量化到 4-bit，并用高精度 LoRA 适配器训练，进一步降低显存。它不代表所有计算都在 4-bit 进行。

## 局限

- LoRA 可能不适合需要大幅改变模型知识或结构的任务。
- rank、目标层和数据质量需要实验选择。
- 合并适配器前要确认基础模型版本一致。

## 概念与公式导航

- [[../15-概念词典/49-LoRA与参数高效微调|LoRA 与参数高效微调]]
- [[../16-公式手册/16-LoRA低秩更新公式|LoRA 低秩更新公式]]

## 练习

1. 计算 1024×1024 矩阵使用 rank 16 LoRA 的参数量。
2. LoRA 为什么称为低秩更新？
3. QLoRA 量化了什么、训练了什么？
4. LoRA 与全量微调各适合什么场景？

## 来源

- Hu, E. et al. (2022). *LoRA: Low-Rank Adaptation of Large Language Models*. ICLR. https://arxiv.org/abs/2106.09685 `[A]`
- Dettmers, T. et al. (2023). *QLoRA*. NeurIPS. https://arxiv.org/abs/2305.14314 `[A]`