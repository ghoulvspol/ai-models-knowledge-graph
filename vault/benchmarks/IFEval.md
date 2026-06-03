---
title: "IFEval"
aliases: ["Instruction Following Evaluation"]
---

# IFEval

IFEval（Instruction Following Evaluation）是评估大语言模型遵循指令能力的评测基准，由 Google 于 2023 年提出。它专注于测试模型是否能精确遵循各种格式和内容约束。

## 评测概述

- **题目数量**：541 道提示
- **评估方式**：可程序化验证的指令遵循
- **指标**：Prompt-level 和 Instruction-level 准确率
- **特点**：避免人工评估的主观性

## 指令类型

| 类型 | 示例 |
|------|------|
| 格式约束 | "用 JSON 格式回答"、"回答不超过 100 词" |
| 内容约束 | "不要使用'但是'这个词"、"包含关键词 X" |
| 结构约束 | "使用编号列表"、"包含 3 个段落" |
| 语言约束 | "用中文回答"、"使用正式语气" |

## 顶级模型表现（2025）

| 模型 | IFEval 得分 | 机构 |
|------|------------|------|
| [[Claude Opus 4]] | ~95% | [[Anthropic]] |
| [[GPT-4o]] | ~92% | [[OpenAI]] |
| [[Gemini 2.5 Pro]] | ~91% | [[Google DeepMind]] |
| [[DeepSeek V3]] | ~89% | [[DeepSeek]] |
| [[Qwen 3]] | ~88% | [[Alibaba]] |

## 行业意义

IFEval 的重要性在于：
- **实用性**：指令遵循是用户最直接感知的能力
- **可验证**：程序化评估避免了人工评估的偏差
- **产品化指标**：直接影响用户体验和产品可用性
- **对齐评估**：衡量模型是否"听话"

## 评测细节

IFEval 使用两类验证：
- **严格验证（Strict）**：指令必须被精确遵循
- **宽松验证（Loose）**：允许轻微偏离
- 每条提示包含 1-5 条指令
- 难度从简单格式约束到复杂内容约束

## 学术引用

Zhou, J., et al. "Instruction-Following Evaluation for Large Language Models." arXiv 2023. 引用量超过 500 次。
