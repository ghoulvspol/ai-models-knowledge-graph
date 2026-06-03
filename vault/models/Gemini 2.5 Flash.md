---
title: "Gemini 2.5 Flash"
aliases: ["Gemini 2.5 Flash", "gemini-2-5-flash"]
---

# Gemini 2.5 Flash

[[Gemini 2.5 Flash]] 是 [[Google DeepMind]] 于 **2025年4月9日** 发布的高效模型，继承 [[Gemini 2.5 Pro]] 的核心能力，以极致速度和低成本为卖点。

## 核心参数

| 指标 | 数值 |
|------|------|
| 发布日期 | 2025年4月9日 |
| 上下文窗口 | 1,048,576 tokens（1M） |
| 最大输出 | 65,536 tokens |
| 架构 | [[Transformer]]，[[MoE]] |
| API 定价 | $0.15 / 1M input，$0.60 / 1M output |
| 首 token 延迟 | < 300ms |

## 设计理念

Gemini 2.5 Flash 是 [[Google DeepMind]] 对"高效推理"的极致追求：通过 [[MoE]] 架构和 [[Distillation]] 技术，将 [[Gemini 2.5 Pro]] 的能力压缩到更高效的推理路径中。

## Benchmark 表现

| 基准测试 | 分数 | 备注 |
|----------|------|------|
| [[MMLU]] | 83.5% | 多领域知识 |
| [[HumanEval]] | 84.0% | 代码生成 |
| [[MATH]] | 82.5% | 数学推理 |
| [[IFEval]] | 84.2% | 指令遵循 |
| [[Arena]] | Top 10 | 人类偏好 |

## 核心优势

### 价格
Gemini 2.5 Flash 的定价在主流模型中极具竞争力：
- Input：$0.15/1M tokens（约为 [[GPT-4o]] 的 1/17）
- Output：$0.60/1M tokens（约为 [[GPT-4o]] 的 1/17）

### 速度
首 token 延迟低于 300ms，适合实时交互和流式场景。

### 1M 上下文
尽管定位轻量，仍保持 1M token 的超长上下文窗口，这是其相对于 [[Claude Haiku 4.5]]（200K）和 [[o4-mini]]（200K）的显著优势。

## 与竞品对比

| 模型 | MMLU | 上下文 | 定价(input) | 延迟 |
|------|------|--------|-------------|------|
| Gemini 2.5 Flash | 83.5% | 1M | $0.15/1M | < 300ms |
| [[Claude Haiku 4.5]] | 82.5% | 200K | $0.80/1M | < 500ms |
| [[GPT-4o-mini]] | 82.0% | 128K | $0.15/1M | < 300ms |
| [[o4-mini]] | 89.5% | 200K | $1.10/1M | ~2s |

## 思维模式

与 [[Gemini 2.5 Pro]] 相同，Flash 也支持思维模式（Thinking Mode），在需要时可以进行深度推理，在简单任务上自动跳过推理以保持速度。

## 应用场景

- **高并发 API**：大规模批处理和数据处理
- **实时对话**：聊天机器人和客服系统
- **代码辅助**：日常编程和代码补全
- **内容生成**：大规模文本生成和翻译
- **1M 上下文场景**：长文档分析（Flash 独有优势）

## Google 生态

Gemini 2.5 Flash 深度集成 Google Cloud Vertex AI，支持企业级部署，并可通过 Google AI Studio 免费试用。
