---
title: "Long Context"
aliases: ["长上下文", "长上下文窗口", "上下文扩展"]
---

# Long Context

**长上下文（Long Context）**指大语言模型处理长序列输入的能力。从最初 [[Transformer]] 的 512 token，到如今支持数百万 token 的上下文窗口，长上下文技术经历了巨大发展。

## 上下文窗口演进

| 时期 | 模型 | 上下文长度 | 技术方案 |
|------|------|-----------|---------|
| 2017 | 原始 Transformer | 512 | 标准自注意力 |
| 2020 | GPT-3 | 2,048 | 标准自注意力 |
| 2023 | GPT-4 | 8K/32K | 位置编码优化 |
| 2024 | [[Claude 3.5 Sonnet]] | 200K | 位置插值 |
| 2024 | [[Gemini 2.5 Pro]] | 1M~10M | Ring Attention |
| 2025 | [[GPT-4.1]] | 1M | 位置编码外推 |
| 2025 | [[Qwen 3]] | 128K | YaRN |
| 2025 | [[Llama 4 Scout]] | 10M | 分块注意力 |

## 技术挑战

### 二次方复杂度
标准 [[Attention Mechanism|自注意力]] 的计算和内存复杂度为 $O(n^2)$：
- 4K token：计算量约 16M 次注意力操作
- 128K token：计算量约 16B 次注意力操作
- 1M token：计算量约 1T 次注意力操作

### 位置编码外推
- 模型在训练长度之外的位置编码上表现急剧下降
- 需要专门技术使模型泛化到更长序列

## 关键技术方案

### 位置编码优化

**RoPE 位置插值（Position Interpolation）**
- 将长序列的位置索引线性压缩到训练长度范围内
- 简单有效，但会损失部分短序列性能

**YaRN（Yet Another RoPE Extension）**
- 结合 NTK-Aware 插值和温度缩放
- [[Qwen 3]] 采用此方案扩展到 128K

**ABF（Adjusted Base Frequency）**
- 调整 RoPE 的频率基数
- [[Llama 4 Scout]] 和 [[GPT-4.1]] 使用类似方案

### 高效注意力

**Flash Attention**
- IO 感知的分块注意力计算
- 内存从 $O(n^2)$ 降至 $O(n)$，计算量不变
- 已成为所有现代模型的标准组件

**Ring Attention**
- 将长序列分布在多个设备上环形传递
- [[Gemini 2.5 Pro]] 支持 10M 上下文的核心技术

**分块注意力（Chunked Attention）**
- [[Llama 4 Scout]] 的方案：将序列分块处理，块内全注意力，块间稀疏注意力

### KV Cache 优化

- **GQA（Grouped Query Attention）**：减少 KV 头数，降低缓存大小
- **MQA（Multi-Query Attention）**：KV 头数为 1，极致压缩
- **KV Cache 量化**：将 KV 缓存量化为 INT4/INT8
- **PagedAttention**：类似操作系统虚拟内存的 KV Cache 管理

## "大海捞针"测试（Needle in a Haystack）

评估长上下文能力的标准测试：
- 在长文本的不同位置插入一条关键信息
- 测试模型能否在文末正确检索该信息
- 结果通常以热力图展示（位置 × 长度）

[[Claude 3.5 Sonnet]]、[[Gemini 2.5 Pro]]、[[GPT-4.1]] 在 200K+ 长度下均能保持高检索准确率。

## 实际应用

- **整本书分析**：一次性输入完整书籍进行分析
- **大型代码库理解**：输入完整代码仓库进行重构
- **长视频分析**：将视频帧转换为长 token 序列
- **多文档问答**：同时处理数十份文档

## 关键论文

- Dao et al., "FlashAttention: Fast and Memory-Efficient Exact Attention", NeurIPS 2022
- Chen et al., "Extending Context Window of Large Language Models via Positional Interpolation", 2023
- Liu et al., "Ring Attention with Blockwise Transformers for Near-Infinite Context", 2024
