---
title: "Chain of Thought"
aliases: ["CoT", "思维链"]
---

# Chain of Thought

Chain of Thought（CoT，思维链）是一种通过让模型显式展示推理步骤来提升推理能力的提示和训练方法。由 Wei 等人于 2022 年提出，已成为提升 LLM 推理能力的核心技术。

## 核心思想

CoT 的关键洞察：
- 传统提示要求模型直接给出答案
- CoT 要求模型先展示推理过程，再给出答案
- 显式推理步骤帮助模型分解复杂问题
- 推理过程中的中间结果作为"工作记忆"

## CoT 变体

| 变体 | 说明 | 提出者 |
|------|------|--------|
| Few-shot CoT | 提供推理示例 | Wei et al., 2022 |
| Zero-shot CoT | "Let's think step by step" | Kojima et al., 2022 |
| Self-Consistency | 多次采样取多数投票 | Wang et al., 2022 |
| Tree of Thoughts | 树形搜索推理路径 | Yao et al., 2023 |
| Graph of Thoughts | 图形推理结构 | Besta et al., 2023 |

## 效果验证

CoT 在以下评测上效果显著：

| 评测 | 无 CoT | 有 CoT | 提升 |
|------|--------|--------|------|
| [[GSM8K]] | ~35% (GPT-3) | ~57% | +22% |
| [[MATH]] | ~6.9% | ~15% | +8% |
| [[GPQA]] | ~30% | ~50% | +20% |

## 推理模型

CoT 思想催生了专门的"推理模型"：
- **[[OpenAI]] o1/o3**：内置长链推理
- **[[DeepSeek R1]]**：通过 [[RLHF]] 训练推理能力
- **[[Grok 3]]**：集成推理模式
- 这些模型在 [[MATH]]、[[Codeforces]] 等评测上表现优异

## 训练方法

CoT 不仅是提示技术，也是训练方法：
- **过程奖励模型（PRM）**：奖励每一步推理而非仅最终答案
- **[[RLHF]] 训练**：通过强化学习学习推理路径
- **Self-Play**：模型自我对弈生成推理数据
- **蒸馏**：从强模型的推理链中学习

## 局限性

- 增加推理成本（更多 token）
- 推理链可能包含错误步骤
- 难以验证推理过程的正确性
- 对简单问题可能过度推理

## 学术引用

Wei, J., et al. "Chain-of-Thought Prompting Elicits Reasoning in Large Language Models." NeurIPS 2022. 引用量超过 8000 次。
