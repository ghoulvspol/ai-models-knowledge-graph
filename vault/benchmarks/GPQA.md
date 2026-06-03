---
title: "GPQA"
aliases: ["Graduate-Level Google-Proof Q&A"]
---

# GPQA

GPQA（Graduate-Level Google-Proof Q&A）是评估大语言模型在研究生级别科学问题上表现的评测基准，由 Rein 等人于 2023 年提出。

## 评测概述

- **题目数量**：448 道（主集），198 道（Diamond 子集最常用）
- **出题者**：各领域的博士级专家
- **难度**：即使有搜索引擎辅助，非专家正确率仅约 34%
- **领域**：物理、化学、生物

## 题目特点

| 特性 | 说明 |
|------|------|
| 专家设计 | 由领域博士撰写，确保科学准确性 |
| Google-proof | 即使使用搜索引擎，非专家也难以回答 |
| 4 选 1 | 多选题格式 |
| 高难度 | 人类专家正确率约 65% |

## 顶级模型表现（2025）

| 模型 | GPQA Diamond | 机构 |
|------|-------------|------|
| [[Grok 3]] | ~72% | [[xAI]] |
| [[Gemini 2.5 Pro]] | ~70% | [[Google DeepMind]] |
| [[GPT-4o]] | ~56% | [[OpenAI]] |
| [[Claude Opus 4]] | ~59% | [[Anthropic]] |
| [[DeepSeek R1]] | ~71% | [[DeepSeek]] |

*注：数据为近似值，不同评测设置结果可能不同*

## 意义

GPQA 的重要性在于：
- **接近人类专家水平**：顶级模型已接近博士级专家的正确率
- **推理能力评估**：测试模型的深度推理而非简单记忆
- **科学能力基准**：衡量 AI 在科学领域的实际能力
- **Chain of Thought** 效果显著：使用 [[Chain of Thought]] 提示可显著提升表现

## 局限性

- 题目数量有限（198 题 Diamond 子集）
- 仅覆盖物理、化学、生物三个领域
- 选择题格式限制了对推理过程的评估
- 评测结果受提示格式影响较大

## 学术引用

Rein, D., et al. "GPQA: A Graduate-Level Google-Proof Q&A Benchmark." arXiv 2023. 引用量超过 500 次。
