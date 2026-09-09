---
aliases: [PyTorch, Tensor, 自动求导]
tags: [Python, PyTorch, 深度学习, 教程, 大模型, 学习教程]
prerequisites: ["[[NumPy 入门]]", "[[函数与模块]]"]
next: ["[[什么是机器学习]]"]
---
# PyTorch 入门

## 一句话定义

PyTorch 是深度学习框架。它提供 GPU 加速的张量运算，以及自动求导（Autograd）：只需要写前向计算过程，PyTorch 自动算出所有梯度。

## Tensor

Tensor 是 PyTorch 的多维数组，类似 NumPy 数组，但可以在 GPU 上运行。

```python
import torch

x = torch.tensor([1.0, 2.0, 3.0])
matrix = torch.tensor([[1.0, 2.0], [3.0, 4.0]])
zeros = torch.zeros(2, 3)

print(x.shape)   # torch.Size([3])
print(matrix @ x[:2])  # 矩阵乘法
```

想改用 GPU 时，把 tensor 移到对应设备：

```python
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
x = x.to(device)
```

## 自动求导

```python
x = torch.tensor(2.0, requires_grad=True)
y = x ** 2
y.backward()
print(x.grad)  # 4.0
```

- `requires_grad=True`：PyTorch 会记录这个 tensor 上的所有运算。
- `y.backward()`：从 y 开始反向自动计算梯度，存储在 `.grad` 中。
- 因为 $y = x^2$ 的导数是 $2x$，在 $x=2$ 处就是 $4.0$。

这个机制是大模型训练的核心：计算损失，调用 `loss.backward()`，PyTorch 自动填充所有参数的梯度。

## nn.Module

`nn.Module` 是 PyTorch 组织模型的基类。写一个最简单的线性层：

```python
import torch.nn as nn

class SimpleLinear(nn.Module):
    def __init__(self, in_features, out_features):
        super().__init__()
        self.linear = nn.Linear(in_features, out_features)

    def forward(self, x):
        return self.linear(x)

model = SimpleLinear(10, 1)
x = torch.randn(5, 10)
output = model(x)
print(output.shape)  # torch.Size([5, 1])
```

- `__init__`：定义网络结构，创建参数。
- `forward`：描述前向传播；PyTorch 自动处理反向传播。
- `nn.Linear`：一个线性层，内部计算 `y = xW^T + b`。

## 优化器

```python
optimizer = torch.optim.Adam(model.parameters(), lr=0.01)
loss_function = nn.MSELoss()

for step in range(100):
    optimizer.zero_grad()
    prediction = model(x)
    loss = loss_function(prediction, torch.zeros(5, 1))
    loss.backward()
    optimizer.step()
```

每一步：

1. `zero_grad()`：清空残留梯度。
2. 前向传播，计算预测和损失。
3. `loss.backward()`：自动计算梯度。
4. `optimizer.step()`：根据梯度调整参数。

## 与 NumPy 的转换

```python
import numpy as np

numpy_array = x.detach().cpu().numpy()
torch_tensor = torch.from_numpy(numpy_array)
```

`detach()` 切断梯度图，`cpu()` 把数据移回 CPU。

## 常见错误

- 忘记 `zero_grad()`：梯度会累积而不是替换。
- 不是所有 tensor 都在同一设备上：先统一 `device`。
- 没有 `requires_grad` 的 tensor 不会自动计算梯度。

## 概念与公式导航

- [[计算图自动微分与梯度累加|计算图、自动微分与梯度累加]]

## 练习

1. 创建一个 `requires_grad=True` 的 tensor，计算 `x^3`，打印梯度。
2. 实现一个 `nn.Module`，包含两个 `nn.Linear` 层，中间用 ReLU。
3. 用 Adam 优化器训练一个简单模型，打印 loss 下降过程。
4. 解释 `zero_grad()` 为什么必要。

## 来源

- PyTorch Documentation, *Tensors*：https://pytorch.org/docs/stable/tensors.html `[A]`
- PyTorch Documentation, *Autograd*：https://pytorch.org/docs/stable/autograd.html `[A]`
- PyTorch Documentation, *nn.Module*：https://pytorch.org/docs/stable/generated/torch.nn.Module.html `[A]`