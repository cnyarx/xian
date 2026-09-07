---
aliases: [NumPy, ndarray, 广播]
tags: [Python, NumPy, 数值计算, 教程]
prerequisites:
  - "[[02-变量与基本运算]]"
  - "[[../01-数学基础/01-向量与矩阵]]"
next: ["[[04-函数与模块]]"]
---
# NumPy 入门

## 一句话定义

NumPy 是 Python 的数值计算库。它用 `ndarray`（多维数字数组）高效表示向量、矩阵和更高维张量。

## 为什么不用普通列表

普通列表能装任意对象，灵活但数值计算较慢。NumPy 数组通常保存同一种数据类型，可由底层优化代码批量运算。

```python
import numpy as np

x = np.array([1.0, 2.0, 3.0])
print(x.shape)   # (3,)
print(x.dtype)   # 通常是 float64
```

- `import numpy as np`：导入 NumPy，并用短名字 `np`。
- `shape`：数组每个方向的长度。
- `dtype`：每个元素的数据类型。

## 创建数组

```python
vector = np.array([1, 2, 3])
matrix = np.array([[1, 2, 3], [4, 5, 6]])
zeros = np.zeros((2, 3))
ones = np.ones((2, 3))
random_values = np.random.default_rng(0).normal(size=(2, 3))
```

`matrix.shape` 是 `(2, 3)`，表示 2 行 3 列。

## 索引和切片

```python
matrix[0, 1]    # 第0行第1列，得到2
matrix[0]       # 第0行
matrix[:, 1]    # 所有行的第1列
matrix[:, 0:2]  # 所有行，第0到第1列
```

冒号 `:` 表示取该方向上的全部；`0:2` 包含 0 和 1，不包含 2。

## 批量运算

```python
x = np.array([1, 2, 3])

x + 1       # [2, 3, 4]
x * 2       # [2, 4, 6]
x ** 2      # [1, 4, 9]
np.exp(x)   # 对每个元素计算e的幂
x.sum()     # 6
x.mean()    # 2.0
```

这些操作叫**向量化（Vectorization）**：一次描述整组数据的运算，不手写逐元素循环。

## 点积和矩阵乘法

```python
x = np.array([1, 2, 3])
y = np.array([4, 5, 6])
print(np.dot(x, y))  # 32

A = np.array([[1, 2], [3, 4]])
B = np.array([[5, 6], [7, 8]])
print(A @ B)
```

`@` 是矩阵乘法运算符。结果为：

```text
[[19 22]
 [43 50]]
```

## 广播

**广播（Broadcasting）**让不同形状的数组在符合规则时自动扩展后运算。

```python
A = np.array([[1, 2, 3],
              [4, 5, 6]])
b = np.array([10, 20, 30])
print(A + b)
```

结果：

```text
[[11 22 33]
 [14 25 36]]
```

可以把 `b` 想成自动复制成两行。广播从形状最右侧开始比较：两个长度相同，或其中一个长度为 1，才兼容。

## 手写 softmax

```python
import numpy as np

scores = np.array([2.0, 1.0, 0.1])
stable_scores = scores - scores.max()
exp_scores = np.exp(stable_scores)
probabilities = exp_scores / exp_scores.sum()
print(probabilities)
```

先减最大值是为了避免 `exp` 产生过大的数；所有分数同时减同一个数不会改变 softmax 结果。

## 常见错误

- `*` 是逐元素乘法，`@` 才是矩阵乘法。
- 形状不兼容会报错；先打印 `shape`。
- 切片通常返回原数组的“视图”；修改视图可能影响原数组。需要独立副本时调用 `.copy()`。

## 概念与公式导航

- [[../15-概念词典/09-逐元素运算与广播|逐元素运算与广播]]

## 练习

1. 创建形状为 `(3, 4)` 的全零矩阵。
2. 计算 `[1, 2, 3]` 与 `[3, 2, 1]` 的点积。
3. 用 NumPy 计算一个 `2×3` 矩阵乘 `3×2` 矩阵。
4. 修改 softmax 输入，验证输出总和接近 1。
5. 解释广播为何能让二维矩阵和一维向量相加。

## 来源

- NumPy Developers, *NumPy User Guide*：https://numpy.org/doc/stable/user/ `[A]`
- NumPy Developers, *Broadcasting*：https://numpy.org/doc/stable/user/basics.broadcasting.html `[A]`
