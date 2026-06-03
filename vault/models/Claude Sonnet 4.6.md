---
title: "Claude Sonnet 4.6"
aliases: ["Claude Sonnet 4.6", "claude-sonnet-4-6", "Sonnet 4.6"]
---

# Claude Sonnet 4.6

[[Claude Sonnet 4.6]] 是 [[Anthropic]] 发布的中高端模型，定位为速度与智能的最佳平衡点。它在保持 Sonnet 系列响应速度优势的同时，提供了接近 Opus 级别的推理能力。

## 核心参数

| 指标 | 数值 |
|------|------|
| API ID | claude-sonnet-4-6 |
| 上下文窗口 | 1M tokens (~750k words) |
| 最大输出 | 64k tokens |
| 可靠知识截止 | 2025年8月 |
| 扩展思考 | 是 |
| 自适应思考 | 是 |
| API 定价 | $3 / 1M input，$15 / 1M output |

## 架构与训练

[[Claude Sonnet 4.6]] 基于 [[Anthropic]] 最新的 [[Transformer]] 架构，融合了扩展思考和自适应思考技术，能够根据任务复杂度自动调整推理深度。

训练特点：
- 大规模预训练，特别强化代码和数学领域
- [[RLHF]] 和 [[DPO]] 的精细对齐
- [[Constitutional AI]] 安全框架
- 支持扩展思考（Extended Thinking）和自适应思考（Adaptive Thinking）

## 核心能力

### 速度与智能平衡
[[Claude Sonnet 4.6]] 是 Claude 产品线中"主力车型"，在编码、对话、分析等常见任务中提供接近 [[Claude Opus 4.8]] 的能力，同时保持更快的响应速度和更友好的价格。

### 扩展思考
支持扩展思考模式，在数学推理、逻辑分析等复杂任务上可显著提升准确率。同时也支持自适应思考，自动根据任务复杂度调整推理深度。

### 1M 上下文
拥有 1M token 的超大上下文窗口（约 750k 英文单词），远超前代 [[Claude Sonnet 4]] 的 200K，能够处理更长的文档和更大的代码库。

### 编码能力
作为 [[Claude Sonnet 4]] 的继任者，在编码任务上持续优化，支持复杂的代码生成、调试和重构。

## 产品定位

[[Claude Sonnet 4.6]] 面向大多数生产场景，是性价比最高的选择。与 [[Claude Opus 4.8]]（最强推理）和 [[Claude Haiku 4.5]]（最快速度）形成完整产品线。

## Claude Code 集成

[[Claude Sonnet 4.6]] 是 Claude Code 工具的核心模型之一，优化了代码生成、调试和重构的工作流。

## 与竞品对比

| 模型 | 上下文 | 最大输出 | 思考模式 | 定价(input) |
|------|--------|---------|---------|-------------|
| Claude Sonnet 4.6 | 1M | 64k | Extended + Adaptive | $3/1M |
| [[Claude Sonnet 4]] | 200K | 16k | Extended | $3/1M |
| [[Claude Sonnet 4.5]] | 200K | - | Extended | $3/1M |
| [[GPT-4o]] | 128K | 16k | - | $2.50/1M |
| [[Gemini 2.5 Flash]] | 1M | - | - | $0.15/1M |
