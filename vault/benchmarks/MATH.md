---
title: "MATH"
aliases: ["MATH benchmark"]
---

# MATH

MATH 是评估大语言模型数学推理能力的评测基准，由 Hendrycks 等人于 2021 年提出。题目来自高中数学竞赛，难度分级。

## 评测概述

- **题目数量**：12,500 道数学题
- **难度等级**：5 个级别（Level 1 最简单，Level 5 最难）
- **格式**：需要生成精确数值或表达式答案
- **领域**：代数、几何、概率、数论、微积分等 7 个子领域

## 难度分布

| 级别 | 难度描述 | 示例 |
|------|---------|------|
| Level 1 | 基础代数 | 简单方程求解 |
| Level 2 | 中等难度 | 二次函数、基础几何 |
| Level 3 | 竞赛入门 | AMC 10/12 水平 |
| Level 4 | 竞赛中级 | AIME 水平 |
| Level 5 | 竞赛高级 | AMC 12 / 简单 IMO 水平 |

## 顶级模型表现（2025）

| 模型 | MATH 得分 | 机构 |
|------|----------|------|
| [[DeepSeek R1]] | ~97% | [[DeepSeek]] |
| [[Grok 3]] | ~96% | [[xAI]] |
| [[Gemini 2.5 Pro]] | ~95% | [[Google DeepMind]] |
| [[Claude Opus 4]] | ~96% | [[Anthropic]] |
| [[GPT-4o]] | ~76% | [[OpenAI]] |
| [[Qwen 3]] | ~95% | [[Alibaba]] |

*注：推理模型（如 DeepSeek R1）在此评测上表现显著优于通用模型*

## 进展

数学推理是 AI 能力提升最快的领域之一：
- 2021 年：最好模型约 6.9%
- 2023 年：GPT-4 达到约 42%
- 2024 年：推理模型突破 90%
- 2025 年：顶级模型接近 97%

## 衍生评测

- **MATH-500**：500 题子集，更高效的评测
- **OlympiadBench**：奥林匹克竞赛级别
- **AIME**：美国数学邀请赛题目
- **[[GSM8K]]**：更简单的小学数学题

## 学术引用

Hendrycks, D., et al. "Measuring Mathematical Problem Solving with the MATH Dataset." NeurIPS 2021. 引用量超过 2000 次。
