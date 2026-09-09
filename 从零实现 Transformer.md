---
aliases: [手写 Transformer, Tiny Transformer]
tags: [项目, PyTorch, Transformer, 大模型, 学习教程]
prerequisites: ["[[完整 Transformer 积木]]"]
---
# 从零实现 Transformer

## 目标

不用 `nn.Transformer` 和高层注意力模块，自己实现一个可训练、可生成的 decoder-only 微型 Transformer，包括：

- token embedding；
- 可学习位置 embedding；
- 多头因果自注意力；
- 残差连接、LayerNorm 和 FFN；
- 多层堆叠；
- 词表输出层；
- 交叉熵损失；
- 自回归生成；
- 形状、概率和因果掩码测试。

理论对应：[[缩放点积注意力|缩放点积注意力]]、[[多头注意力]]、[[Decoder-Only 架构]]。

## 环境

以下代码面向 Python 3.10+ 和 PyTorch 2.x。安装方式应以 PyTorch 官方“Start Locally”页面为准，因为 CPU、CUDA 和操作系统对应的安装命令不同：

https://pytorch.org/get-started/locally/

当前知识库所在机器未安装 PyTorch，因此本项目只完成了代码语法检查，未声称在本机执行通过。

## 完整单文件程序

保存为 `tiny_transformer.py`：

```python
import math
from dataclasses import dataclass

import torch
import torch.nn.functional as F
from torch import nn


@dataclass
class Config:
    vocab_size: int = 32
    max_seq_len: int = 64
    dim: int = 64
    num_heads: int = 4
    num_layers: int = 2
    ffn_hidden: int = 256
    dropout: float = 0.0


class CausalSelfAttention(nn.Module):
    def __init__(self, config: Config):
        super().__init__()
        if config.dim % config.num_heads != 0:
            raise ValueError("dim must be divisible by num_heads")

        self.num_heads = config.num_heads
        self.head_dim = config.dim // config.num_heads
        self.qkv = nn.Linear(config.dim, 3 * config.dim, bias=False)
        self.out = nn.Linear(config.dim, config.dim, bias=False)
        self.attn_dropout = nn.Dropout(config.dropout)
        self.resid_dropout = nn.Dropout(config.dropout)

        mask = torch.triu(
            torch.ones(config.max_seq_len, config.max_seq_len, dtype=torch.bool),
            diagonal=1,
        )
        self.register_buffer("causal_mask", mask, persistent=False)

    def forward(self, x: torch.Tensor, return_weights: bool = False):
        batch, time, dim = x.shape
        if time > self.causal_mask.size(0):
            raise ValueError("sequence exceeds max_seq_len")

        qkv = self.qkv(x)
        q, k, v = qkv.chunk(3, dim=-1)

        def split_heads(tensor: torch.Tensor) -> torch.Tensor:
            return tensor.view(batch, time, self.num_heads, self.head_dim).transpose(1, 2)

        q, k, v = map(split_heads, (q, k, v))
        scores = q @ k.transpose(-2, -1) / math.sqrt(self.head_dim)
        scores = scores.masked_fill(self.causal_mask[:time, :time], float("-inf"))
        weights = torch.softmax(scores, dim=-1)
        weights = self.attn_dropout(weights)

        context = weights @ v
        context = context.transpose(1, 2).contiguous().view(batch, time, dim)
        output = self.resid_dropout(self.out(context))
        if return_weights:
            return output, weights
        return output


class FeedForward(nn.Module):
    def __init__(self, config: Config):
        super().__init__()
        self.net = nn.Sequential(
            nn.Linear(config.dim, config.ffn_hidden),
            nn.GELU(),
            nn.Linear(config.ffn_hidden, config.dim),
            nn.Dropout(config.dropout),
        )

    def forward(self, x: torch.Tensor) -> torch.Tensor:
        return self.net(x)


class Block(nn.Module):
    def __init__(self, config: Config):
        super().__init__()
        self.norm1 = nn.LayerNorm(config.dim)
        self.attn = CausalSelfAttention(config)
        self.norm2 = nn.LayerNorm(config.dim)
        self.ffn = FeedForward(config)

    def forward(self, x: torch.Tensor) -> torch.Tensor:
        x = x + self.attn(self.norm1(x))
        return x + self.ffn(self.norm2(x))


class TinyTransformerLM(nn.Module):
    def __init__(self, config: Config):
        super().__init__()
        self.config = config
        self.token_embedding = nn.Embedding(config.vocab_size, config.dim)
        self.position_embedding = nn.Embedding(config.max_seq_len, config.dim)
        self.dropout = nn.Dropout(config.dropout)
        self.blocks = nn.ModuleList([Block(config) for _ in range(config.num_layers)])
        self.final_norm = nn.LayerNorm(config.dim)
        self.lm_head = nn.Linear(config.dim, config.vocab_size, bias=False)

        self.lm_head.weight = self.token_embedding.weight
        self.apply(self._init_weights)

    @staticmethod
    def _init_weights(module: nn.Module) -> None:
        if isinstance(module, (nn.Linear, nn.Embedding)):
            nn.init.normal_(module.weight, mean=0.0, std=0.02)
        if isinstance(module, nn.Linear) and module.bias is not None:
            nn.init.zeros_(module.bias)

    def forward(self, token_ids: torch.Tensor, targets: torch.Tensor | None = None):
        batch, time = token_ids.shape
        if time > self.config.max_seq_len:
            raise ValueError("sequence exceeds max_seq_len")

        positions = torch.arange(time, device=token_ids.device)
        x = self.token_embedding(token_ids) + self.position_embedding(positions)[None, :, :]
        x = self.dropout(x)
        for block in self.blocks:
            x = block(x)
        logits = self.lm_head(self.final_norm(x))

        loss = None
        if targets is not None:
            loss = F.cross_entropy(
                logits.reshape(batch * time, self.config.vocab_size),
                targets.reshape(batch * time),
            )
        return logits, loss

    @torch.no_grad()
    def generate(
        self,
        token_ids: torch.Tensor,
        max_new_tokens: int,
        temperature: float = 1.0,
        top_k: int | None = None,
    ) -> torch.Tensor:
        if temperature <= 0:
            raise ValueError("temperature must be positive")

        for _ in range(max_new_tokens):
            context = token_ids[:, -self.config.max_seq_len :]
            logits, _ = self(context)
            next_logits = logits[:, -1, :] / temperature

            if top_k is not None:
                k = min(top_k, next_logits.size(-1))
                threshold = torch.topk(next_logits, k).values[:, [-1]]
                next_logits = next_logits.masked_fill(next_logits < threshold, float("-inf"))

            probabilities = torch.softmax(next_logits, dim=-1)
            next_token = torch.multinomial(probabilities, num_samples=1)
            token_ids = torch.cat([token_ids, next_token], dim=1)
        return token_ids


def run_checks() -> None:
    torch.manual_seed(7)
    config = Config(vocab_size=20, max_seq_len=16, dim=32, num_heads=4, num_layers=2)
    model = TinyTransformerLM(config).eval()

    tokens = torch.randint(0, config.vocab_size, (2, 8))
    targets = torch.randint(0, config.vocab_size, (2, 8))
    logits, loss = model(tokens, targets)
    assert logits.shape == (2, 8, config.vocab_size)
    assert loss is not None and torch.isfinite(loss)

    normalized = model.blocks[0].norm1(model.token_embedding(tokens))
    _, weights = model.blocks[0].attn(normalized, return_weights=True)
    assert weights.shape == (2, config.num_heads, 8, 8)
    assert torch.allclose(weights.sum(dim=-1), torch.ones_like(weights.sum(dim=-1)))
    assert torch.count_nonzero(torch.triu(weights, diagonal=1)) == 0

    changed = tokens.clone()
    changed[:, 5:] = torch.randint(0, config.vocab_size, changed[:, 5:].shape)
    original_logits, _ = model(tokens)
    changed_logits, _ = model(changed)
    assert torch.allclose(original_logits[:, :5], changed_logits[:, :5], atol=1e-6)

    generated = model.generate(tokens[:, :2], max_new_tokens=4, top_k=5)
    assert generated.shape == (2, 6)
    print("all checks passed")
    print("logits shape:", tuple(logits.shape))
    print("loss:", round(loss.item(), 4))
    print("generated shape:", tuple(generated.shape))


if __name__ == "__main__":
    run_checks()
```

## 运行

```bash
python tiny_transformer.py
```

预期至少看到：

```text
all checks passed
logits shape: (2, 8, 20)
generated shape: (2, 6)
```

`loss` 的具体小数随 PyTorch 版本和硬件可能略有差异，不应固定比较。

## 代码怎样对应公式

1. `qkv.chunk(3)` 产生 Query、Key、Value；
2. `scores = q @ k.transpose(...) / sqrt(head_dim)` 对应缩放点积；
3. `causal_mask` 把未来位置设为负无穷；
4. softmax 后每行权重之和为 1；
5. `weights @ v` 聚合 Value；
6. 多个头拼回 `dim`；
7. 两次 `x + ...` 是残差连接；
8. `lm_head` 为每个位置输出词表 logits；
9. 交叉熵让第 $t$ 个位置预测目标 token。

公式入口：[[缩放点积与多头注意力公式|缩放点积与多头注意力公式]]、[[语言模型损失与困惑度公式|语言模型损失公式]]。

## 验收解释

- **形状测试**：确认 batch、时间和词表维没有混乱；
- **权重和为 1**：确认 softmax 维度正确；
- **未来权重为 0**：确认因果掩码生效；
- **修改未来 token 不影响过去 logits**：从端到端检查没有信息泄漏；
- **生成长度正确**：确认自回归循环每次追加一个 token。

## 进一步实验

- 把可学习位置 embedding 换成 RoPE；
- 比较共享与不共享 embedding/lm_head 权重；
- 把 GELU 换成 SwiGLU；
- 增加 KV Cache，并比较生成速度；
- 删除 $1/\sqrt{d_k}$ 缩放，观察注意力熵和梯度。

## 来源

- Vaswani et al. (2017), *Attention Is All You Need*：https://arxiv.org/abs/1706.03762 `[A]`
- PyTorch `nn.Module`：https://pytorch.org/docs/stable/generated/torch.nn.Module.html `[A]`
- PyTorch `nn.Embedding`：https://pytorch.org/docs/stable/generated/torch.nn.Embedding.html `[A]`
- PyTorch `CrossEntropyLoss`：https://pytorch.org/docs/stable/generated/torch.nn.CrossEntropyLoss.html `[A]`
