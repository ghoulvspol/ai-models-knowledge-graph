---
title: "Gemini 2.5 Pro"
aliases: ["Gemini 2.5 Pro", "gemini-2.5-pro"]
---

# Gemini 2.5 Pro

[[Gemini 2.5 Pro]] 是 [[Google DeepMind]] 于 **2025年3月25日** 发布的旗舰模型，首次引入"思维模式"（Thinking Mode），是 Gemini 系列的重大升级。

## 核心参数

| 指标 | 数值 |
|------|------|
| 发布日期 | 2025年3月25日（预览），2025年5月 GA |
| 上下文窗口 | 1,048,576 tokens（1M） |
| 最大输出 | 65,536 tokens |
| 训练数据截止 | 2025年1月 |
| 架构 | [[Transformer]]，原生多模态 |
| API 定价 | $1.25 / 1M input，$10.00 / 1M output |

## 架构与训练

Gemini 2.5 Pro 基于 [[Google DeepMind]] 的 [[Transformer]] 架构，融合了 [[MoE]]（Mixture of Experts）技术，实现高效推理。

核心创新：
- **思维模式**（Thinking Mode）：类似 [[Chain of Thought]] 的显式推理过程
- **原生多模态**：文本、图像、音频、视频统一处理
- **1M 上下文**：与 [[Gemini 1.5 Pro]] 一脉相承的超长上下文能力
- [[Scaling Laws]] 在多模态数据上的验证

## Benchmark 表现

| 基准测试 | 分数 | 备注 |
|----------|------|------|
| [[MMLU]] | 89.8% | 多领域知识 |
| [[HumanEval]] | 90.5% | 代码生成 |
| [[MATH]] | 86.4% | 数学推理 |
| [[GPQA]] | 72.0% | 研究生级问答 |
| [[Arena]] | #1（发布时） | 人类偏好排名 |
| [[SWE-bench]] | 55.0% | 软件工程 |
| 长上下文检索 | 99.2% | 1M token needle-in-haystack |

## 核心能力

### 思维模式
Gemini 2.5 Pro 的思维模式允许模型在生成答案前进行内部推理，在数学和逻辑任务上提升 10-20% 的准确率。与 [[o1]] 不同，Gemini 的思维过程对用户部分可见。

### 1M 上下文
继承 [[Gemini 1.5 Pro]] 的超长上下文能力，支持处理完整的代码仓库、长视频和大型文档集。

### 多模态
原生支持文本、图像、音频、视频输入，无需额外的模态转换。在视频理解任务上具有独特优势。

## 与竞品对比

| 模型 | MMLU | MATH | 上下文 | 定价(input) |
|------|------|------|--------|-------------|
| Gemini 2.5 Pro | 89.8% | 86.4% | 1M | $1.25/1M |
| [[GPT-4o]] | 88.7% | 76.6% | 128K | $2.50/1M |
| [[Claude Sonnet 4]] | 88.5% | 88.7% | 200K | $3.00/1M |
| [[o3]] | - | 97.9% | 200K | $10/1M |

## 价格优势

Gemini 2.5 Pro 的定价极具竞争力，input 价格仅为 [[GPT-4o]] 的一半、[[Claude Sonnet 4]] 的不到一半，而性能在多项基准上持平或领先。

## Google 生态集成

Gemini 2.5 Pro 深度集成 Google 生态：
- Google Workspace（Docs、Sheets、Slides）
- Google Cloud（Vertex AI）
- Google Search（AI Overviews）
- Android（Gemini Nano 本地推理）

## 行业影响

Gemini 2.5 Pro 的发布巩固了 [[Google DeepMind]] 在 AI 第一梯队的地位，其"思维模式+1M上下文+原生多模态"的组合对 [[OpenAI]] 和 [[Anthropic]] 构成了全面竞争。
