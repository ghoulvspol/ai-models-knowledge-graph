---
title: "Claude Opus 4.7"
aliases: ["Claude Opus 4.7", "claude-opus-4-7", "Opus 4.7"]
---

# Claude Opus 4.7

[[Claude Opus 4.7]] 是 [[Anthropic]] 发布的旗舰推理模型，作为 [[Claude Opus 4.6]] 的后继者和 [[Claude Opus 4.8]] 的前代。它采用新一代分词器（new tokenizer），在上下文效率上有显著提升。现已标记为 Legacy 模型。

## 核心参数

| 指标 | 数值 |
|------|------|
| API ID | claude-opus-4-7 |
| 上下文窗口 | 1M tokens (使用新分词器) |
| 最大输出 | 128k tokens |
| 扩展思考 | 否 |
| 自适应思考 | 是 |
| 状态 | Legacy |
| API 定价 | $5 / 1M input，$25 / 1M output |

## 核心特性

### 新分词器
[[Claude Opus 4.7]] 引入了新一代分词器，在 1M token 的上下文窗口下实现了更高的信息密度，同等 token 数能编码更多内容。

### Adaptive Thinking
作为 [[Anthropic]] 首批采用自适应思考机制的模型之一，[[Claude Opus 4.7]] 能够根据任务复杂度自动调整推理深度，无需用户手动切换思考模式。

### 128k 输出
支持 128k token 的长输出，适合生成长文档和进行大规模代码重构。

## 产品定位

[[Claude Opus 4.7]] 已被 [[Claude Opus 4.8]] 取代，现为 Legacy 模型。对于新项目，建议使用 [[Claude Opus 4.8]]。

## 模型系列

- [[Claude Opus 4.8]] - 最新旗舰
- [[Claude Opus 4.7]] - Legacy（当前）
- [[Claude Opus 4.6]] - Legacy
- [[Claude Opus 4.5]] - Legacy
- [[Claude Opus 4.1]] - Legacy
- [[Claude Opus 4]] - 已弃用
