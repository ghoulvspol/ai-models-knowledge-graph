---
title: "RAG"
aliases: ["检索增强生成", "Retrieval-Augmented Generation", "检索增强"]
---

# RAG

**RAG（Retrieval-Augmented Generation，检索增强生成）**是将外部知识检索与大语言模型生成相结合的技术架构。通过在生成前检索相关信息，RAG 有效缓解了 [[Hallucination|幻觉]] 问题，并使模型能够访问训练数据之外的最新知识。

## 核心流程

```
用户查询 → 查询处理 → 检索相关文档 → 将文档注入上下文 → LLM 生成回答
```

详细步骤：
1. **文档预处理**：将文档分块（chunking），通过 [[Embeddings|嵌入模型]] 转为向量
2. **索引构建**：将向量存入向量数据库，建立索引
3. **查询检索**：将用户查询转为向量，检索最相似的 Top-K 文档块
4. **上下文注入**：将检索结果拼接到 [[Prompt Engineering|提示]] 中
5. **生成回答**：[[Foundation Model|大模型]] 基于上下文生成答案

## 关键组件

### 文档分块策略

| 策略 | 方法 | 适用场景 |
|------|------|---------|
| 固定长度 | 按字符/token 数切分 | 通用 |
| 句子级别 | 按句子边界切分 | 文本质量高时 |
| 语义分块 | 按主题/段落切分 | 结构化文档 |
| 递归分块 | 先大块再细分 | 复杂文档 |

推荐块大小：256-1024 tokens，重叠 10-20%。

### 检索方法

**向量检索（Dense Retrieval）**
- 使用 [[Embeddings|嵌入模型]] 将查询和文档映射到同一向量空间
- 通过余弦相似度等度量检索最相关文档
- 擅长语义匹配

**关键词检索（Sparse Retrieval）**
- 基于 BM25 等传统信息检索算法
- 精确匹配关键词，适合专有名词

**混合检索（Hybrid Search）**
- 结合向量检索和关键词检索
- 融合策略：RRF（Reciprocal Rank Fusion）、加权求和
- 通常优于单一方法

### 重排序（Reranking）
- 在初步检索后，使用专门的重排序模型对结果精排
- Cross-encoder 重排序比 bi-encoder 检索更精确
- 显著提升最终结果质量

## RAG 变体

### Naive RAG
- 基础流程：检索 → 生成
- 简单但有效

### Advanced RAG
- 增加查询改写、多步检索、重排序
- Self-RAG：模型自主决定何时需要检索
- Corrective RAG：评估检索结果质量并修正

### Modular RAG
- 将 RAG 拆解为可组合的模块
- 支持灵活的架构定制

### Graph RAG
- 使用知识图谱辅助检索
- 支持关系推理和多跳问答
- Microsoft 的 GraphRAG 框架

## RAG vs 其他方法

| 方法 | 优势 | 劣势 |
|------|------|------|
| RAG | 知识可更新，减少幻觉 | 检索质量是瓶颈 |
| [[Fine-tuning\|微调]] | 深度定制，风格可控 | 知识固化，需要重新训练 |
| 长上下文 | 简单直接 | 成本高，仍有幻觉 |
| 知识图谱 | 精确关系推理 | 构建成本高 |

## 向量数据库选择

详见 [[Embeddings#向量数据库]] 部分。关键考虑因素：
- **规模**：数据量级（百万 vs 十亿向量）
- **延迟**：实时 vs 离线
- **部署**：云服务 vs 自托管
- **成本**：开源 vs 商业

## 评估指标

- **检索质量**：Recall@K、MRR（Mean Reciprocal Rank）
- **生成质量**：忠实度（Faithfulness）、答案相关性
- **端到端**：RAGAS 框架综合评估

## 关键论文

- Lewis et al., "Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks", NeurIPS 2020
- Gao et al., "Retrieval-Augmented Generation for Large Language Models: A Survey", 2024
- Edge et al., "From Local to Global: A Graph RAG Approach", 2024
