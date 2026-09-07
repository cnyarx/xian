---
aliases: [Python与计算基础练习答案]
tags: [练习答案, Python]
---
# 02-Python与计算基础答案

## [[../02-Python与计算基础/01-安装与环境|01-安装与环境]]

1. `print("你的名字")`。
2. `python` 启动解释器；`-c` 表示执行后面的字符串；`print(6 * 7)` 先算乘法再输出 `42`。
3. 参考：`python -m venv .venv`，激活后运行 `python -m pip list`。激活命令随操作系统和 shell 不同，以正文和 Python 官方文档为准。
4. 虚拟环境隔离依赖及版本，避免一个项目升级软件包后破坏另一个项目，也让复现环境更容易。

## [[../02-Python与计算基础/02-变量与基本运算|02-变量与基本运算]]

1. `words = ["我", "在", "学习", "大", "模型"]`，然后 `for word in words: print(word)`。
2. `vocab = {"你": 0, "好": 1, "世界": 2}`。
3. `total = 0`；循环中执行 `total += x ** 2`，结果为 `55`。也可写 `sum(x ** 2 for x in [1,2,3,4,5])`。
4. `loss = float(input())`；`print("较低" if loss < 1 else "仍需训练")`。
5. `=` 把右侧值赋给左侧变量；`==` 比较两边是否相等并得到布尔值。

## [[../02-Python与计算基础/03-NumPy 入门|03-NumPy 入门]]

1. `np.zeros((3, 4))`。
2. `np.dot([1,2,3], [3,2,1])` 得 `10`。
3. 例如 `a=np.array([[1,2,3],[4,5,6]])`、`b=np.array([[1,2],[3,4],[5,6]])`、`a @ b`，结果形状 `(2,2)`，值为 `[[22,28],[49,64]]`。
4. `p=np.exp(x-np.max(x)); p=p/p.sum()`；用 `p.sum()` 检查，浮点误差下应非常接近 1。
5. 广播会把兼容的一维向量视作在缺失轴上重复，而不真的复制整份数据；例如 `(m,n)` 与 `(n,)` 相加时，向量作用于每一行。

## [[../02-Python与计算基础/04-函数与模块|04-函数与模块]]

1. `def relu(x): return x if x > 0 else 0`。
2. `def mean(xs): return sum(xs) / len(xs)`；空列表需由调用边界决定是报错还是另作处理。
3. 在 `math_utils.py` 定义函数，在另一文件写 `from math_utils import mean`。
4. `Path("note.txt").write_text("一行文字", encoding="utf-8")`；再用 `Path(...).read_text(encoding="utf-8")`。
5. 参数是调用者传入函数的名字；返回值是函数交回调用者的结果；局部变量只在本次函数调用内部使用；模块是可被导入的 Python 文件。

## [[../02-Python与计算基础/05-PyTorch 入门|05-PyTorch 入门]]

1. `x=torch.tensor(2.0, requires_grad=True); y=x**3; y.backward(); print(x.grad)`，输出 `12`。
2. `nn.Sequential(nn.Linear(4,8), nn.ReLU(), nn.Linear(8,1))` 是一个最小答案。
3. 建立模型和数据后循环执行：`optimizer.zero_grad()`、前向、计算 `loss`、`loss.backward()`、`optimizer.step()`；在可学习关系和合适学习率下，打印的总体趋势应下降，不要求每一步严格下降。
4. PyTorch 默认把梯度累加到 `.grad`。不清零会把前几批梯度混入当前更新，除非这正是有意的梯度累积。
