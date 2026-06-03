---
title: "WinoGrande"
aliases: ["winogrande"]
---

# WinoGrande

WinoGrande 是评估大语言模型常识推理能力的评测基准，是经典 Winograd Schema Challenge 的大规模版本，由 Sakaguchi 等人于 2020 年提出。

## 评测概述

- **题目数量**：44,000 道（训练集 40k，验证集 1.2k，测试集 1.7k）
- **任务**：填空式常识推理，选择正确的代词指代
- **格式**：2 选 1 选择题
- **人类基线**：约 94.0%

## 题目示例

*"The trophy doesn't fit in the brown suitcase because it is too [large/small]."*

- 选择"large" → "it" 指代 trophy
- 选择"small" → "it" 指代 suitcase

## 设计特点

| 特性 | 说明 |
|------|------|
| A1/A2 均衡 | 正确答案在两个选项中均匀分布 |
| Adversarial Filtering | 自动生成高迷惑性干扰项 |
| 常识推理 | 测试日常场景的合理性判断 |
| 大规模 | 比原始 Winograd 大 100 倍+ |

## 顶级模型表现（2025）

| 模型 | WinoGrande 得分 | 机构 |
|------|----------------|------|
| [[GPT-4o]] | ~87% | [[OpenAI]] |
| [[Claude Opus 4]] | ~86% | [[Anthropic]] |
| [[Gemini 2.5 Pro]] | ~86% | [[Google DeepMind]] |
| [[DeepSeek V3]] | ~85% | [[DeepSeek]] |

*注：人类基线约 94%，仍有改进空间*

## 与 HellaSwag 的对比

| 特性 | WinoGrande | [[HellaSwag]] |
|------|-----------|---------------|
| 任务 | 代词消歧 | 句子续写 |
| 格式 | 2 选 1 | 4 选 1 |
| 题目数 | 44,000 | 10,000 |
| 人类基线 | ~94% | ~95.6% |
| 状态 | 接近人类 | 已超越人类 |

## 行业意义

WinoGrande 在 AI 评测中的地位：
- **常识推理基准**：衡量模型对日常世界的理解
- **代词消歧**：自然语言理解的核心能力
- **[[Alignment]] 评估**：模型是否真正理解语言含义
- **大规模评测**：足够大的测试集确保结果可靠

## 学术引用

Sakaguchi, K., et al. "WinoGrande: An Adversarial Winograd Schema Challenge at Scale." AAAI 2020. 引用量超过 2000 次。
