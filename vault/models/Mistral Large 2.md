---
title: "Mistral Large 2"
aliases: ["Mistral Large 2", "mistral-large-2", "Mistral Large"]
---

# Mistral Large 2

[[Mistral Large 2]] 是 [[Mistral AI]] 于 **2024年7月24日** 发布的大语言模型，是 Mistral 产品线中的旗舰模型。

## 核心参数

| 指标 | 数值 |
|------|------|
| 发布日期 | 2024年7月24日 |
| 参数量 | 123B |
| 上下文窗口 | 128K tokens |
| 最大输出 | 8,192 tokens |
| 架构 | [[Transformer]] |
| 许可 | Mistral Research License |

## 架构与训练

Mistral Large 2 基于标准 [[Transformer]] 架构，123B 参数的 dense 模型设计。

训练特点：
- 大规模多语言预训练，支持 80+ 语言
- 代码和数学数据的高权重训练
- [[RLHF]] 对齐优化
- 支持 [[Function Calling]] 和结构化输出

## Benchmark 表现

| 基准测试 | 分数 | 备注 |
|----------|------|------|
| [[MMLU]] | 84.0% | 多领域知识 |
| [[HumanEval]] | 92.0% | 代码生成 |
| [[MATH]] | 69.1% | 数学推理 |
| [[GPQA]] | 53.8% | 研究生级问答 |
| 多语言任务 | 优秀 | 80+ 语言 |

## 核心能力

### 代码能力
Mistral Large 2 在 [[HumanEval]] 上达到 92.0%，在发布时处于领先水平。模型对多种编程语言有良好的支持。

### 多语言
支持 80+ 种语言，包括法语、德语、西班牙语、中文、日语、韩语等，在欧洲语言上表现尤为突出。

### 工具使用
原生支持 [[Function Calling]]，能够与外部工具和 API 无缝集成，适合构建 [[AI Agent]] 系统。

## 与同期模型对比

| 模型 | 参数 | MMLU | HumanEval | 上下文 | 开源 |
|------|------|------|-----------|--------|------|
| Mistral Large 2 | 123B | 84.0% | 92.0% | 128K | 部分 |
| [[GPT-4o]] | 未公开 | 88.7% | 90.2% | 128K | 否 |
| [[Claude 3.5 Sonnet]] | 未公开 | 88.7% | 92.0% | 200K | 否 |
| [[Llama 3.1 405B]] | 405B | 88.6% | 89.0% | 128K | 是 |

## Mistral 产品线

| 模型 | 参数 | 定位 | 发布日期 |
|------|------|------|----------|
| [[Mistral Large 2]] | 123B | 旗舰 | 2024年7月 |
| [[Mistral Small 3.1]] | 24B | 轻量 | 2025年3月 |
| [[Codestral]] | 22B | 代码专用 | 2024年5月 |
| [[Pixtral Large]] | 124B | 多模态 | 2024年11月 |

## 欧洲 AI 力量

[[Mistral AI]] 作为欧洲（法国）的 AI 公司，Mistral Large 2 代表了欧洲在全球 AI 竞赛中的竞争力。公司获得了欧盟的大力支持，致力于打造"欧洲的 OpenAI"。
