---
title: "GSM8K"
aliases: ["Grade School Math 8K"]
---

# GSM8K

GSM8K（Grade School Math 8K）是评估大语言模型基础数学推理能力的评测基准，由 [[OpenAI]] 于 2021 年提出。题目为小学数学应用题，需要 2-8 步推理。

## 评测概述

- **题目数量**：8,500 道（训练集 7,500，测试集 1,319）
- **难度**：小学数学水平，2-8 步推理
- **评估方式**：生成数值答案，精确匹配
- **特点**：自然语言描述，需要多步计算

## 题目示例

*"Natalia sold clips to 48 of her friends in April, and then she sold half as many clips in May. How many clips did Natalia sell altogether in April and May?"*

答案：48 + 48/2 = 72

## 顶级模型表现（2025）

| 模型 | GSM8K 得分 | 机构 |
|------|-----------|------|
| [[DeepSeek R1]] | ~97% | [[DeepSeek]] |
| [[Grok 3]] | ~97% | [[xAI]] |
| [[GPT-4o]] | ~96% | [[OpenAI]] |
| [[Claude Opus 4]] | ~96% | [[Anthropic]] |
| [[Gemini 2.5 Pro]] | ~96% | [[Google DeepMind]] |
| [[Qwen 3]] | ~96% | [[Alibaba]] |

*注：顶级模型已基本"解决"此评测*

## 进展速度

GSM8K 见证了 AI 数学能力的快速提升：
- 2021 年（GPT-3）：约 35%
- 2023 年（GPT-4）：约 92%
- 2024 年（推理模型）：约 95%
- 2025 年：约 97%

## 与 MATH 的对比

| 特性 | GSM8K | [[MATH]] |
|------|-------|----------|
| 难度 | 小学 | 高中竞赛 |
| 题目数 | 8,500 | 12,500 |
| 推理步数 | 2-8 步 | 多步复杂推理 |
| 状态 | 基本解决 | 仍有挑战 |
| 指标 | 精确匹配 | 精确匹配 |

## 衍生应用

GSM8K 被广泛用于：
- **[[Chain of Thought]]** 研究的验证基准
- **[[Distillation]]** 和 [[Quantization]] 的效果评估
- **[[Fine-tuning]]** 数据集
- [[RLHF]] 和 [[DPO]] 训练数据源

## 学术引用

Cobbe, K., et al. "Training Verifiers to Solve Math Word Problems." arXiv 2021. 引用量超过 2000 次。
