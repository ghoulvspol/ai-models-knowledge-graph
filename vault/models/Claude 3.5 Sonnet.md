---
title: "Claude 3.5 Sonnet"
aliases: ["Claude 3.5 Sonnet", "claude-3-5-sonnet", "Sonnet 3.5"]
---

# Claude 3.5 Sonnet

[[Claude 3.5 Sonnet]] 是 [[Anthropic]] 于 **2024年6月20日** 发布的大语言模型，在性能上超越了前代旗舰 [[Claude 3 Opus]]，同时保持 Sonnet 级别的速度和成本。

## 核心参数

| 指标 | 数值 |
|------|------|
| 发布日期 | 2024年6月20日 |
| 上下文窗口 | 200K tokens |
| 最大输出 | 8,192 tokens |
| 训练数据截止 | 2024年4月 |
| 架构 | [[Transformer]] |
| API 定价 | $3.00 / 1M input，$15.00 / 1M output |

## 架构与训练

Claude 3.5 Sonnet 基于 [[Anthropic]] 自研的 [[Transformer]] 架构，采用了改进的 [[Attention Mechanism]] 和更高效的训练策略。

训练方法包括：
- 大规模预训练，涵盖多语言和代码数据
- [[RLHF]] 和 [[DPO]] 的多阶段对齐
- [[Constitutional AI]]（CAI）确保安全性和有用性的平衡
- 强调 [[Alignment]] 的训练范式，注重诚实、无害、有帮助

## Benchmark 表现

| 基准测试 | 分数 | 备注 |
|----------|------|------|
| [[MMLU]] | 88.7% | 多领域知识 |
| [[HumanEval]] | 92.0% | 代码生成 |
| [[MATH]] | 71.1% | 数学推理 |
| [[GPQA]] | 59.4% | 研究生级问答 |
| [[Arena]] | Top 3 | 人类偏好排名 |

## 核心能力

### 代码能力
Claude 3.5 Sonnet 在发布时被认为是编码能力最强的模型之一，在 [[SWE-bench]] 上达到 49.0%，显著超越同期 [[GPT-4o]]。

### 视觉理解
支持图像输入，在文档理解、图表分析、OCR 等任务上表现优异。

### 长文本处理
200K token 的上下文窗口使其能够处理完整的代码仓库、长篇学术论文和复杂的业务文档。

## 版本迭代

| 版本 | 日期 | 主要改进 |
|------|------|----------|
| Claude 3.5 Sonnet (June) | 2024年6月 | 初始发布 |
| Claude 3.5 Sonnet (October) | 2024年10月 | 支持 Computer Use |
| Claude 3.5 Sonnet (v2) | 2025年3月 | 性能小幅提升 |

## 与竞品对比

| 模型 | MMLU | HumanEval | 上下文 | 定价(input) |
|------|------|-----------|--------|-------------|
| Claude 3.5 Sonnet | 88.7% | 92.0% | 200K | $3.00/1M |
| [[GPT-4o]] | 88.7% | 90.2% | 128K | $2.50/1M |
| [[Gemini 1.5 Pro]] | 85.9% | 84.1% | 1M | $3.50/1M |
| [[Claude 3 Opus]] | 86.8% | 84.9% | 200K | $15.00/1M |

## Computer Use

2024年10月更新后，Claude 3.5 Sonnet 成为首个支持"计算机使用"（Computer Use）的商用模型，能够像人类一样操作计算机界面——移动鼠标、点击按钮、输入文字。这一能力开创了 [[AI Agent]] 的新范式。

## 行业影响

Claude 3.5 Sonnet 确立了 [[Anthropic]] 在编码和长文本领域的领先地位，其"超越自家旗舰"的策略影响了后续 [[Claude Sonnet 4]] 的产品定位。
