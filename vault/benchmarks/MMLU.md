---
title: "MMLU"
aliases: ["Massive Multitask Language Understanding"]
---

# MMLU

MMLU（Massive Multitask Language Understanding）是评估大语言模型多学科知识能力的主流评测基准，由 Hendrycks 等人于 2021 年提出。

## 评测概述

- **题目数量**：约 15,000 道选择题
- **学科覆盖**：57 个科目，涵盖 STEM、人文、社科等
- **难度范围**：从高中到专业级别
- **评估方式**：4 选 1 多选题，评估零样本和少样本能力

## 57 个科目分类

| 类别 | 代表科目 |
|------|---------|
| STEM | 数学、物理、化学、计算机科学、工程 |
| 人文 | 历史、哲学、法律、伦理 |
| 社科 | 经济学、心理学、政治学 |
| 其他 | 医学、商业、专业考试 |

## 顶级模型表现（2025）

| 模型 | MMLU 得分 | 机构 |
|------|----------|------|
| [[Gemini 2.5 Pro]] | ~92% | [[Google DeepMind]] |
| [[GPT-4o]] | ~88% | [[OpenAI]] |
| [[Claude Opus 4]] | ~88% | [[Anthropic]] |
| [[DeepSeek V3]] | ~88% | [[DeepSeek]] |
| [[Grok 3]] | ~87% | [[xAI]] |
| [[Qwen 3]] | ~86% | [[Alibaba]] |
| [[Mistral Large 2]] | ~85% | [[Mistral AI]] |

## 局限性

- 选择题格式限制了评估深度
- 部分题目存在歧义或错误答案
- 无法评估推理过程，只看最终答案
- 已被"刷分"，区分度下降
- 催生了更新、更难的评测（如 [[GPQA]]、[[MUSR]]）

## 衍生版本

- **MMLU-Pro**：10 选 1，更难版本
- **MMLU-Redux**：修正原版错误答案
- **C-Eval / CMMLU**：中文多学科评测
- **Global-MMLU**：多语言版本

## 学术引用

Hendrycks, D., et al. "Measuring Massive Multitask Language Understanding." ICLR 2021. 引用量超过 3000 次。
