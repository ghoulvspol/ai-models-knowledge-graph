---
title: "Claude 3 Opus"
aliases: ["Claude 3 Opus", "claude-3-opus", "Opus 3"]
---

# Claude 3 Opus

[[Claude 3 Opus]] 是 [[Anthropic]] 于 **2024年3月4日** 发布的旗舰大语言模型，是 Claude 3 系列中能力最强的模型，也是首个在多项基准上与 [[GPT-4]] 持平的非 OpenAI 模型。

## 核心参数

| 指标 | 数值 |
|------|------|
| 发布日期 | 2024年3月4日 |
| 上下文窗口 | 200K tokens |
| 最大输出 | 4,096 tokens |
| 训练数据截止 | 2023年8月 |
| 架构 | [[Transformer]] |
| API 定价 | $15 / 1M input，$75 / 1M output |

## 架构与训练

Claude 3 Opus 基于 [[Anthropic]] 自研的 [[Transformer]] 架构，是 Claude 3 系列（Haiku、Sonnet、Opus）中的旗舰。

训练方法：
- 大规模预训练，多语言和代码数据
- [[RLHF]] 和 [[DPO]] 的深度对齐
- [[Constitutional AI]]（CAI）安全框架
- 200K token 长上下文训练

## Benchmark 表现

| 基准测试 | Claude 3 Opus | [[GPT-4]] | 备注 |
|----------|--------------|----------|------|
| [[MMLU]] | 86.8% | 86.4% | 略超 GPT-4 |
| [[HumanEval]] | 84.9% | 67.0% | 大幅领先 |
| [[MATH]] | 60.1% | 52.9% | 显著领先 |
| [[GPQA]] | 50.4% | - | 研究生级问答 |
| [[Arena]] | #1（发布时） | #2 | 人类偏好排名 |

Claude 3 Opus 是首个在 [[Arena]] 排行榜上超越 GPT-4 的模型，打破了 OpenAI 的垄断地位。

## 核心能力

### 安全性
继承 [[Anthropic]] 的 [[Alignment]] 理念，Claude 3 Opus 在安全性和有用性之间取得了最佳平衡。[[Constitutional AI]] 框架使模型能够在不需要大量人工标注的情况下自我改进。

### 长文本
200K token 的上下文窗口在发布时领先于 [[GPT-4 Turbo]]（128K），能够处理更长的文档和对话。

### 推理
在复杂推理任务上表现出色，[[MMLU]] 和 [[GPQA]] 分数均超过 [[GPT-4]]。

## Claude 3 系列

| 模型 | 定位 | MMLU | 上下文 | 定价(input) |
|------|------|------|--------|-------------|
| [[Claude 3 Opus]] | 旗舰 | 86.8% | 200K | $15/1M |
| Claude 3 Sonnet | 平衡 | 79.0% | 200K | $3/1M |
| Claude 3 Haiku | 轻量 | 75.2% | 200K | $0.25/1M |

## 历史意义

Claude 3 Opus 标志着 [[Anthropic]] 正式进入大模型第一梯队：
- 首次在 [[Arena]] 上超越 GPT-4
- 证明了 [[Constitutional AI]] 的有效性
- 建立了 Anthropic "安全优先"的品牌形象
- 推动了大模型竞争格局的多元化

## 后续发展

Claude 3 Opus 被 [[Claude 3.5 Sonnet]]（2024年6月）在性能上超越，后者以更低的价格提供了更强的能力。最终被 [[Claude Opus 4]]（2025年5月）正式接替旗舰位置。
