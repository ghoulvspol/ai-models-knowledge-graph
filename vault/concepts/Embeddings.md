---
title: "Embeddings"
aliases: ["嵌入", "向量嵌入", "词嵌入", "文本嵌入", "Embedding"]
---

# Embeddings

**嵌入（Embeddings）**是将离散的符号（如单词、句子、图像）映射到连续的高维向量空间的技术。嵌入是 [[Transformer]] 架构的基础组成部分，也是 [[RAG]] 等应用的核心。

## 基本原理

嵌入将离散输入映射为稠密向量：

$$\text{Embedding}: \text{token\_id} \in \mathbb{Z} \rightarrow \mathbf{v} \in \mathbb{R}^d$$

其中 $d$ 是嵌入维度（如 768、1024、4096 等）。

**关键特性**：
- **语义相似性**：语义相近的词在向量空间中距离更近
- **可组合性**：向量运算可反映语义关系（如 $\vec{king} - \vec{man} + \vec{woman} \approx \vec{queen}$）
- **可学习**：嵌入矩阵随模型训练自动优化

## 嵌入类型

### 词嵌入（Word Embeddings）
- **Word2Vec**（2013）：CBOW 和 Skip-gram 两种架构
- **GloVe**（2014）：基于全局共现矩阵的嵌入
- **FastText**（2016）：支持子词级别的嵌入

### 上下文嵌入（Contextual Embeddings）
- 传统词嵌入中，同一词在不同上下文中向量相同
- [[Transformer]] 模型产生**上下文相关的**嵌入：
  - "bank" 在 "river bank" 和 "bank account" 中有不同向量
- BERT、GPT 系列的每一层输出都是上下文嵌入

### 句子/文档嵌入
- **Sentence-BERT**：专门为句子级别语义相似度设计
- **OpenAI Embeddings**：text-embedding-3-small/large
- **开源替代**：E5、BGE、GTE 等

### 多模态嵌入
- **CLIP**：将图像和文本映射到同一向量空间
- **ImageBind**：连接图像、文本、音频、深度等多种模态

## 向量数据库

嵌入的高效存储和检索催生了专门的**向量数据库**：

| 数据库 | 特点 | 适用场景 |
|--------|------|---------|
| Pinecone | 全托管，易用 | 快速原型 |
| Weaviate | 支持混合搜索 | 企业应用 |
| Milvus | 高性能，开源 | 大规模部署 |
| Chroma | 轻量级 | 本地开发 |
| Qdrant | Rust 实现，高效 | 性能敏感场景 |
| pgvector | PostgreSQL 扩展 | 已有 PG 基础设施 |

## 相似度度量

$$\text{余弦相似度} = \frac{\mathbf{a} \cdot \mathbf{b}}{|\mathbf{a}| \cdot |\mathbf{b}|}$$

$$\text{欧氏距离} = |\mathbf{a} - \mathbf{b}|_2$$

$$\text{点积} = \mathbf{a} \cdot \mathbf{b}$$

余弦相似度是最常用的度量方式，范围 $[-1, 1]$。

## 在 RAG 中的应用

[[RAG]]（检索增强生成）的核心流程：
1. 将文档分块，通过嵌入模型转为向量
2. 存入向量数据库，建立索引
3. 用户查询转为向量，在数据库中检索最相似的文档块
4. 将检索结果注入 [[Foundation Model|大模型]] 上下文生成回答

## 维度与性能

| 维度 | 参数量 | 适用场景 | 代表模型 |
|------|--------|---------|---------|
| 384 | ~30M | 资源受限，快速检索 | all-MiniLM-L6 |
| 768 | ~100M | 通用场景 | BGE-base |
| 1024 | ~300M | 高质量检索 | text-embedding-3-small |
| 3072 | ~500M | 最高精度 | text-embedding-3-large |

## 关键论文

- Mikolov et al., "Efficient Estimation of Word Representations in Vector Space" (Word2Vec), 2013
- Pennington et al., "GloVe: Global Vectors for Word Representation", 2014
- Reimers & Gurevych, "Sentence-BERT: Sentence Embeddings using Siamese BERT-Networks", EMNLP 2019
