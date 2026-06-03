---
title: "Transformer"
aliases: ["Transformer 架构", "注意力机制模型", "Transformer Architecture"]
---

# Transformer

**Transformer** 是现代大语言模型的基础架构，由 [[Ashish Vaswani]] 等人于 2017 年在 Google 团队提出，论文 *"Attention Is All You Need"* 彻底改变了自然语言处理领域的技术方向。

## 核心架构

Transformer 完全基于 [[Attention Mechanism]]，摒弃了传统的 RNN/LSTM 递归结构，采用**编码器-解码器（Encoder-Decoder）**架构：

- **编码器（Encoder）**：由 N=6 层堆叠，每层包含多头自注意力（Multi-Head Self-Attention）和前馈神经网络（FFN），使用残差连接和层归一化
- **解码器（Decoder）**：同样 N=6 层，在自注意力基础上增加了交叉注意力（Cross-Attention），并使用掩码防止看到未来信息

## 关键创新

1. **并行计算**：不同于 RNN 的顺序处理，Transformer 可以并行处理整个序列，极大提升了训练效率
2. **位置编码（Positional Encoding）**：使用正弦/余弦函数编码位置信息，弥补自注意力机制无法感知顺序的缺陷
3. **[[Attention Mechanism|注意力机制]]**：通过 Q、K、V 矩阵计算注意力权重

$$\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V$$

## 架构演进

| 架构变体 | 代表模型 | 特点 |
|---------|---------|------|
| 仅编码器 | BERT, RoBERTa | 双向注意力，适合理解任务 |
| 仅解码器 | [[GPT-4o]], [[Claude 3.5 Sonnet]], [[Llama 4 Scout]] | 因果注意力，适合生成任务 |
| 编码器-解码器 | T5, BART | 完整架构，适合 seq2seq 任务 |

当前主流的大语言模型（如 [[GPT-4.1]]、[[Claude Opus 4]]、[[Gemini 2.5 Pro]]、[[DeepSeek V3]]）均采用**仅解码器（Decoder-Only）**架构。

## 技术影响

Transformer 的提出直接催生了 [[Foundation Model]] 时代，推动了 [[Scaling Laws]] 的发现。其高效的并行训练能力使得 [[Pre-training]] 大规模语料成为可能，也为后续的 [[MoE]]（混合专家）、[[Long Context]] 等技术奠定了架构基础。

## 关键论文

- Vaswani et al., "Attention Is All You Need", NeurIPS 2017
- 原始模型参数量：~65M（编码器+解码器）
- 模型维度 $d_{\text{model}} = 512$，注意力头数 $h = 8$

## 局限性

- **二次方复杂度**：自注意力的计算复杂度为 $O(n^2)$，限制了上下文长度
- **位置编码外推**：基础正弦编码在超出训练长度时性能下降
- **推理效率**：自回归生成需要逐 token 解码，延迟较高

这些局限性催生了 [[Inference]] 优化（如 [[KV Cache]]、投机解码）和长上下文技术的发展。
