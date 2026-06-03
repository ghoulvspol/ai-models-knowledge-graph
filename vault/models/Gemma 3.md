---
title: "Gemma 3"
aliases: ["Gemma 3", "gemma-3", "Gemma3"]
---

# Gemma 3

[[Gemma 3]] 是 [[Google DeepMind]] 于 **2025年3月12日** 发布的开源大语言模型系列，覆盖 1B 到 27B 的多种尺寸，是 Google 开源 AI 生态的重要组成部分。

## 核心参数

| 型号 | 参数 | 上下文 | 架构 |
|------|------|--------|------|
| Gemma 3 1B | 1B | 32K | [[Transformer]] |
| Gemma 3 4B | 4B | 128K | [[Transformer]] |
| Gemma 3 12B | 12B | 128K | [[Transformer]] |
| Gemma 3 27B | 27B | 128K | [[Transformer]] |

## 架构与训练

Gemma 3 基于 [[Google DeepMind]] 的 [[Transformer]] 架构，与 [[Gemini 2.5 Pro]] 共享部分技术基础。

训练特点：
- 大规模多语言预训练
- [[Distillation]] 技术：从 Gemini 大模型中蒸馏知识
- [[RLHF]] 和 [[DPO]] 对齐优化
- 支持文本和图像输入（多模态版本）
- [[Quantization】 优化，支持端侧部署

## Benchmark 表现（Gemma 3 27B）

| 基准测试 | 分数 | 备注 |
|----------|------|------|
| [[MMLU]] | 75.6% | 多领域知识 |
| [[HumanEval]] | 78.2% | 代码生成 |
| [[MATH]] | 62.5% | 数学推理 |
| [[IFEval]] | 74.8% | 指令遵循 |
| 多语言理解 | 良好 | 支持 35+ 语言 |

## 核心优势

### 多尺寸覆盖
从 1B（手机端）到 27B（服务器端），Gemma 3 提供了完整的尺寸矩阵：

| 尺寸 | 典型部署场景 | 推理硬件 |
|------|-------------|----------|
| 1B | 手机、嵌入式 | CPU / 移动 GPU |
| 4B | 笔记本、边缘设备 | 消费级 GPU |
| 12B | 工作站 | RTX 4090 |
| 27B | 服务器 | A100 / H100 |

### Distillation 技术
Gemma 3 的小模型通过 [[Distillation]] 从 Gemini 大模型中学习，在较小参数下实现了远超同规模模型的能力。

### 开源生态
采用 Gemma 许可证，支持商业使用。与 Hugging Face、Ollama、llama.cpp 等主流工具链深度集成。

## 与竞品对比（27B 级别）

| 模型 | 参数 | MMLU | HumanEval | 开源 |
|------|------|------|-----------|------|
| Gemma 3 27B | 27B | 75.6% | 78.2% | 是 |
| [[Mistral Small 3.1]] | 24B | 72.5% | 80.0% | 是 |
| [[Qwen 3 32B]] | 32B | 80.2% | 82.5% | 是 |
| Llama 3.1 8B | 8B | 73.0% | 72.0% | 是 |

## Gemma 系列发展

| 模型 | 发布日期 | 特点 |
|------|----------|------|
| Gemma 1 | 2024年2月 | 首个开源版本 |
| Gemma 2 | 2024年6月 | 改进性能 |
| Gemma 3 | 2025年3月 | 多尺寸、多模态 |

## Google 开源策略

Gemma 3 是 [[Google DeepMind]] 开源 AI 战略的核心产品，与闭源的 [[Gemini 2.5 Pro]] 形成互补：
- Gemini：闭源，面向 API 和商业服务
- Gemma：开源，面向社区和本地部署

这一"双轨策略"使 Google 同时覆盖了闭源和开源两个市场。
