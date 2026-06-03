---
title: "RAG"
aliases: ["Retrieval-Augmented Generation"]
---

# RAG

RAG（Retrieval-Augmented Generation，检索增强生成）是将外部知识检索与大语言模型生成相结合的技术。它解决了 LLM 知识截止日期和幻觉问题，是企业级 AI 应用的核心架构模式。

## 核心流程

RAG 的标准工作流：

1. **索引阶段**：将文档分块，生成向量嵌入，存入向量数据库
2. **检索阶段**：用户查询 → 向量相似度搜索 → 返回相关文档块
3. **生成阶段**：将检索到的上下文 + 用户查询发送给 LLM 生成回答

## 技术组件

| 组件 | 作用 | 代表产品 |
|------|------|---------|
| 向量数据库 | 存储和检索文档向量 | Pinecone, Weaviate, Milvus |
| 嵌入模型 | 文本转向量 | OpenAI Embedding, Cohere Embed |
| 重排序模型 | 优化检索结果排序 | Cohere Rerank, BGE-Reranker |
| LLM | 基于上下文生成回答 | [[GPT-4o]], [[Claude Opus 4]], [[Qwen 3]] |

## 高级 RAG 技术

- **HyDE**：假设性文档嵌入，先生成假设答案再检索
- **Multi-Query**：将用户查询改写为多个子查询
- **Re-Ranking**：对检索结果进行二次排序
- **Self-RAG**：模型自我决定是否需要检索
- **Graph RAG**：结合知识图谱的检索增强
- **Agentic RAG**：[[AI Agent]] 驱动的自适应检索

## 与 Fine-tuning 的对比

| 特性 | RAG | [[Fine-tuning]] |
|------|-----|-----------------|
| 知识更新 | 实时更新 | 需要重新训练 |
| 成本 | 较低 | 较高 |
| 可追溯性 | 可引用来源 | 知识隐含在参数中 |
| 私有数据 | 数据不出域 | 数据进入训练 |
| 上下文窗口 | 受窗口限制 | 无显式限制 |
| 准确性 | 依赖检索质量 | 依赖训练质量 |

## 行业应用

- **企业知识库**：内部文档问答
- **客服系统**：基于产品文档的自动回复
- **法律/合规**：法规和案例检索
- **医疗**：医学文献辅助诊断
- **代码助手**：基于代码库的代码生成

## [[Cohere]] 的 RAG 优化

[[Cohere]] 的 Command R 系列专门为 RAG 场景优化，内置引文生成和来源归属能力。

## 学术引用

Lewis, P., et al. "Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks." NeurIPS 2020. 引用量超过 5000 次。
