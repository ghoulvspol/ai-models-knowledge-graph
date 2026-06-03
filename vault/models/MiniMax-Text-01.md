---
title: "MiniMax-Text-01"
aliases: ["MiniMax-Text-01", "MiniMax Text 01", "MiniMax"]
---

# MiniMax-Text-01

[[MiniMax-Text-01]] 是 [[MiniMax]] 于 **2025年1月15日** 发布的大语言模型，以 456B 参数和超长上下文能力为核心特点，是中国 AI 创业公司的代表作。

## 核心参数

| 指标 | 数值 |
|------|------|
| 发布日期 | 2025年1月15日 |
| 总参数 | 456B |
| 激活参数 | 45.9B（每次推理） |
| 上下文窗口 | 1,000,000 tokens（1M） |
| 最大输出 | 16,384 tokens |
| 架构 | [[Transformer]]，[[MoE]] |
| 许可 | MiniMax Community License |

## 架构与训练

MiniMax-Text-01 采用 [[MoE]] 架构，与 [[DeepSeek V3]] 类似但有独特创新：

| 组件 | 数值 |
|------|------|
| 总参数量 | 456B |
| 激活参数 | 45.9B |
| 注意力机制 | Lightning Attention（线性注意力） |
| 架构创新 | 超长上下文优化 |

核心创新：
- **Lightning Attention**：线性注意力机制，复杂度从 O(n²) 降至 O(n)
- **超长上下文**：1M token 上下文窗口
- [[MoE]] 架构：高效推理

## Benchmark 表现

| 基准测试 | 分数 | 备注 |
|----------|------|------|
| [[MMLU]] | 87.2% | 多领域知识 |
| [[HumanEval]] | 85.5% | 代码生成 |
| [[MATH]] | 80.8% | 数学推理 |
| [[Arena]] | Top 10 | 人类偏好 |
| 长上下文检索 | 99.5% | 1M token |

## 核心能力

### 超长上下文
MiniMax-Text-01 拥有 1M token 的上下文窗口，与 [[Gemini 2.5 Pro]] 和 [[GPT-4.1]] 并列，是中国模型中最长的。

### Lightning Attention
线性注意力机制使模型在处理超长序列时效率远高于标准 [[Attention Mechanism]]，是超长上下文的技术基础。

### 综合能力
在 [[MMLU]] 87.2% 的成绩在开源模型中处于领先水平。

## 与竞品对比

| 模型 | 总参数 | 激活参数 | 上下文 | MMLU |
|------|--------|----------|--------|------|
| MiniMax-Text-01 | 456B | 45.9B | 1M | 87.2% |
| [[DeepSeek V3]] | 671B | 37B | 128K | 88.5% |
| [[Llama 4 Maverick]] | 400B | 17B | 1M | 87.5% |
| [[Gemini 2.5 Pro]] | 未公开 | 未公开 | 1M | 89.8% |

## MiniMax 公司

[[MiniMax]] 是中国领先的 AI 创业公司，由前商汤科技副总裁创立，专注于：
- 大语言模型研发
- AI 对话产品（海螺 AI）
- 语音合成和对话

公司获得了阿里巴巴、腾讯等投资，是中国 AI 独角兽之一。

## 行业影响

MiniMax-Text-01 的发布证明了中国 AI 创业公司可以在超长上下文领域与全球领先模型竞争，其 Lightning Attention 技术对长上下文处理有重要参考价值。
