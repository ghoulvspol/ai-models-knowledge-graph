---
title: "Claude Sonnet 4"
aliases: ["Claude Sonnet 4", "claude-sonnet-4", "Sonnet 4"]
---

# Claude Sonnet 4

[[Claude Sonnet 4]] 是 [[Anthropic]] 于 **2025年5月22日** 发布的中端模型，定位为性能与速度的最佳平衡点，是 [[Claude 3.5 Sonnet]] 的正式升级。

## 核心参数

| 指标 | 数值 |
|------|------|
| 发布日期 | 2025年5月22日 |
| 上下文窗口 | 200K tokens |
| 最大输出 | 16,384 tokens |
| 训练数据截止 | 2025年3月 |
| 架构 | [[Transformer]] |
| API 定价 | $3.00 / 1M input，$15.00 / 1M output |

## 架构与训练

Claude Sonnet 4 基于 [[Anthropic]] 改进的 [[Transformer]] 架构，在保持 Sonnet 系列速度优势的同时，大幅提升了推理和编码能力。

训练特点：
- 扩展预训练数据，特别是代码和数学领域
- [[RLHF]] 和 [[DPO]] 的精细对齐
- [[Constitutional AI]] 安全框架
- 支持混合推理模式（快速/深度思考可切换）

## Benchmark 表现

| 基准测试 | 分数 | 备注 |
|----------|------|------|
| [[SWE-bench]] | 60.0% | 软件工程 |
| [[MATH]] | 88.7% | 数学推理 |
| [[GPQA]] | 68.5% | 研究生级问答 |
| [[HumanEval]] | 93.7% | 代码生成 |
| [[MMLU]] | 88.5% | 多领域知识 |
| [[Arena]] | Top 5 | 人类偏好 |

## 核心能力

### 编码能力
Claude Sonnet 4 在 [[SWE-bench]] 上达到 60.0%，较 [[Claude 3.5 Sonnet]]（49.0%）提升超过 10 个百分点。在日常编程任务中，其编码效率和准确性均显著提升。

### 混合推理
支持在快速响应和深度推理之间切换，用户可根据任务复杂度选择模式。深度推理模式下，模型在数学和逻辑任务上的准确率可提升 10-15%。

### 工具使用
原生支持 [[Function Calling]] 和工具使用，在 [[AI Agent]] 场景中表现出色。支持并行工具调用和复杂的工具编排。

## 与竞品对比

| 模型 | SWE-bench | MATH | 上下文 | 定价(input) |
|------|-----------|------|--------|-------------|
| Claude Sonnet 4 | 60.0% | 88.7% | 200K | $3.00/1M |
| [[Claude 3.5 Sonnet]] | 49.0% | 71.1% | 200K | $3.00/1M |
| [[GPT-4o]] | 33.2% | 76.6% | 128K | $2.50/1M |
| [[Gemini 2.5 Flash]] | 48.0% | 82.5% | 1M | $0.15/1M |

## 产品定位

Claude Sonnet 4 是 [[Anthropic]] 产品线中的"主力车型"，面向大多数生产场景。在编码、对话、分析等常见任务中提供接近 [[Claude Opus 4]] 的能力，同时保持更友好的价格和更快的响应速度。

## Claude Code 集成

Claude Sonnet 4 是 [[Anthropic]] 官方编码工具 Claude Code 的默认模型，优化了代码生成、调试和重构的工作流。
