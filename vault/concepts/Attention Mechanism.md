---
title: "Attention Mechanism"
aliases: ["注意力机制", "自注意力", "Self-Attention", "多头注意力", "Multi-Head Attention"]
---

# Attention Mechanism

**注意力机制（Attention Mechanism）**是 [[Transformer]] 架构的核心组件，使模型能够动态地关注输入序列中最相关的部分，而非对所有信息同等对待。

## 基本原理

注意力机制通过**查询（Query）、键（Key）、值（Value）**三组向量计算注意力权重：

$$\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V$$

其中 $d_k$ 是键向量的维度，缩放因子 $\sqrt{d_k}$ 防止点积过大导致梯度消失。

## 三种注意力类型

### 自注意力（Self-Attention）
- Q、K、V 均来自同一序列
- 允许序列中的每个位置关注其他所有位置
- 是 [[Transformer]] 编码器和解码器的核心操作
- 捕捉序列内部的长距离依赖关系

### 交叉注意力（Cross-Attention）
- Q 来自一个序列（如解码器），K 和 V 来自另一个序列（如编码器）
- 用于编码器-解码器架构中的信息传递
- 在 [[Multimodal]] 模型中连接不同模态的表示

### 因果注意力（Causal Attention）
- 对解码器中的自注意力施加掩码，防止看到未来位置
- 即 $i$ 位置只能关注 $j \leq i$ 的位置
- 所有自回归模型（[[GPT-4o]]、[[Claude 3.5 Sonnet]]、[[DeepSeek V3]]）使用此变体

## 多头注意力（Multi-Head Attention）

将注意力操作并行执行 $h$ 次，每个头学习不同的注意力模式：

$$\text{MultiHead}(Q, K, V) = \text{Concat}(\text{head}_1, \ldots, \text{head}_h)W^O$$

其中每个头 $\text{head}_i = \text{Attention}(QW_i^Q, KW_i^K, VW_i^V)$。

**不同头的分工**：
- 某些头关注语法结构（主语-谓语关系）
- 某些头关注语义相似性
- 某些头关注位置临近性
- 某些头关注长距离依赖

## 复杂度分析

标准自注意力的计算复杂度和内存复杂度均为 $O(n^2 \cdot d)$，其中 $n$ 是序列长度，$d$ 是模型维度。这一二次方复杂度是 [[Long Context]] 技术的主要瓶颈。

**优化方案**：
- **Flash Attention**：通过 IO 感知的分块计算减少内存访问
- **稀疏注意力**：只计算部分注意力对（如滑动窗口、全局注意力）
- **线性注意力**：用核方法近似 softmax，将复杂度降至 $O(n)$
- **[[MoE]] 中的分组注意力**：[[DeepSeek V3]] 采用分组查询注意力（GQA）

## 查询注意力变体（GQA / MQA）

| 变体 | K/V 头数 | 代表模型 | 优势 |
|------|---------|---------|------|
| MHA | 与 Q 相同 | GPT-3 | 最大表达能力 |
| GQA | 少于 Q | [[Llama 4 Scout]], [[Qwen 3]] | 平衡效率与质量 |
| MQA | 仅 1 个 | PaLM | 最大推理效率 |

## 关键论文

- Bahdanau et al., "Neural Machine Translation by Jointly Learning to Align and Translate", ICLR 2015 — 注意力机制首次提出
- Vaswani et al., "Attention Is All You Need", NeurIPS 2017 — 多头自注意力
- Dao et al., "FlashAttention", NeurIPS 2022 — IO 感知注意力优化
