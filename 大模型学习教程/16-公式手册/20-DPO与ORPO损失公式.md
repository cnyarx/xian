---
aliases: [DPO损失公式, ORPO损失公式, Direct Preference Optimization, Odds Ratio Preference Optimization]
tags: [公式, 对齐, 偏好优化]
prerequisites: ["[[../15-概念词典/12-似然最大似然与负对数似然]]", "[[../15-概念词典/19-策略奖励优势与基线]]", "[[06-Softmax稳定计算与温度公式]]", "[[08-激活函数公式]]"]
---
# DPO 与 ORPO 损失公式

## 1. 偏好数据

每条样本包含：

$$
(x,y_w,y_l)
$$

- $x$：提示；
- $y_w$：偏好回答（winner）；
- $y_l$：非偏好回答（loser）。

## 2. DPO 损失

$$
\mathcal L_{DPO}=-\log\sigma\left[
\beta\left(
\log\frac{\pi_\theta(y_w\mid x)}{\pi_{ref}(y_w\mid x)}
-
\log\frac{\pi_\theta(y_l\mid x)}{\pi_{ref}(y_l\mid x)}
\right)
\right]
$$

- $\pi_\theta$：当前模型；
- $\pi_{ref}$：冻结的参考模型；
- $\sigma$：sigmoid；
- $\beta>0$：控制相对参考模型的偏好强度。

定义相对对数优势：

$$
\Delta=\log\frac{\pi_\theta(y_w\mid x)}{\pi_{ref}(y_w\mid x)}-
\log\frac{\pi_\theta(y_l\mid x)}{\pi_{ref}(y_l\mid x)}
$$

则 $\mathcal L_{DPO}=-\log\sigma(\beta\Delta)$。$\Delta$ 越大，损失越小。

## 3. 数值例子

设当前模型与参考模型的序列概率为：

$$
\pi_\theta(y_w\mid x)=0.30,\quad \pi_{ref}(y_w\mid x)=0.20
$$

$$
\pi_\theta(y_l\mid x)=0.10,\quad \pi_{ref}(y_l\mid x)=0.20
$$

那么：

$$
\Delta=\ln(1.5)-\ln(0.5)=\ln3\approx1.099
$$

取 $\beta=1$：

$$
\mathcal L_{DPO}=-\ln\sigma(1.099)\approx-\ln(0.75)\approx0.288
$$

若当前模型反而更偏向 $y_l$，$\Delta$ 会变小或为负，损失增大。

> 完整回答的概率通常极小，实际代码使用各 token 对数概率求和或平均，避免直接相乘下溢。长度归一化方式属于实现选择。

## 4. ORPO

ORPO 把监督微调的负对数似然与偏好 odds-ratio 损失组合：

$$
\mathcal L_{ORPO}=\mathcal L_{SFT}+\lambda\mathcal L_{OR}
$$

一种论文写法为：

$$
\mathcal L_{OR}=-\log\sigma\left(
\log\operatorname{odds}_\theta(y_w\mid x)-
\log\operatorname{odds}_\theta(y_l\mid x)
\right)
$$

其中：

$$
\operatorname{odds}_\theta(y\mid x)=
\frac{P_\theta(y\mid x)}{1-P_\theta(y\mid x)}
$$

ORPO 不需要单独的参考模型；$\lambda$ 控制偏好项相对 SFT 项的权重。

## 5. 边界

- DPO 不需要显式训练奖励模型，但仍需要偏好数据和参考模型；
- DPO 的推导建立在特定 KL 正则化奖励建模关系上，不等于任意二分类损失；
- ORPO 的序列概率和长度归一化细节应以论文或实现为准；
- 偏好数据有偏或质量差时，损失公式本身不能纠正目标。

## 最小自测

1. 若 $\Delta=0$、$\beta=1$，DPO 损失是多少？
2. 为什么实际实现使用对数概率而不是把许多 token 概率直接相乘？
3. DPO 与 ORPO 在参考模型需求上有什么区别？

答案：

1. $\sigma(0)=0.5$，$-\ln0.5\approx0.693$。
2. 序列概率是由许多 token 概率连乘得到的极小正数，直接相乘极易下溢到 0；对数概率的和在数值上稳定得多。
3. DPO 需要冻结的参考模型提供 $\pi_{ref}$ 概率；ORPO 不需要参考模型，偏好损失用当前模型自身的 odds。

## 正文

- [[../08-后训练与对齐/04-直接偏好优化|直接偏好优化]]

## 来源

- Rafailov et al. (2023), *Direct Preference Optimization*：https://arxiv.org/abs/2305.18290 `[A]`
- Hong, Lee & Thorne (2024), *ORPO: Monolithic Preference Optimization without Reference Model*：https://arxiv.org/abs/2403.07691 `[A]`
