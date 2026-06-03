---
title: "Codestral"
aliases: ["Codestral", "codestral", "Mistral Codestral"]
---

# Codestral

[[Codestral]] 是 [[Mistral AI]] 于 **2024年5月29日** 发布的代码专用大语言模型，专注于代码生成、补全和理解任务。

## 核心参数

| 指标 | 数值 |
|------|------|
| 发布日期 | 2024年5月29日 |
| 参数量 | 22B |
| 上下文窗口 | 32K tokens |
| 最大输出 | 8,192 tokens |
| 架构 | [[Transformer]] |
| 许可 | Non-production license（初始），后续开放 |

## 架构与训练

Codestral 基于 [[Mistral AI]] 的 [[Transformer]] 架构，针对代码任务进行了深度优化。

训练特点：
- 大规模代码数据预训练（80+ 编程语言）
- 代码特定的 [[Tokenization]] 优化
- [[RLHF]] 代码质量对齐
- 支持 Fill-in-the-Middle（FIM）代码补全

## Benchmark 表现

| 基准测试 | 分数 | 备注 |
|----------|------|------|
| [[HumanEval]] | 81.1% | 代码生成 |
| 代码补全 | 优秀 | FIM 模式 |
| 多语言代码 | 80+ | 编程语言支持 |

## 核心能力

### 代码生成
Codestral 支持 80+ 种编程语言，包括 Python、JavaScript、TypeScript、Java、C++、Rust、Go 等主流语言。

### Fill-in-the-Middle (FIM)
支持代码中间插入模式，能够在现有代码的中间位置补全代码，这是代码编辑器的核心能力。

### IDE 集成
Codestral 设计为 IDE 代码助手的后端模型，支持：
- 代码补全
- 代码解释
- Bug 修复建议
- 代码重构

## 与代码模型对比

| 模型 | 参数 | HumanEval | 定位 |
|------|------|-----------|------|
| Codestral | 22B | 81.1% | 代码专用 |
| [[Claude 3.5 Sonnet]] | 未公开 | 92.0% | 通用（代码强） |
| [[GPT-4o]] | 未公开 | 90.2% | 通用（代码强） |
| Code Llama 70B | 70B | 80.0% | 代码专用 |

## Mistral 产品线

| 模型 | 参数 | 定位 | 发布日期 |
|------|------|------|----------|
| [[Mistral Large 2]] | 123B | 旗舰 | 2024年7月 |
| [[Mistral Small 3.1]] | 24B | 轻量 | 2025年3月 |
| Codestral | 22B | 代码 | 2024年5月 |
| [[Pixtral Large]] | 124B | 多模态 | 2024年11月 |

## 应用场景

- IDE 代码助手后端
- 代码审查自动化
- 代码文档生成
- 测试用例生成
- 代码翻译（跨语言转换）

## 局限性

- 22B 参数限制了复杂推理能力
- 32K 上下文窗口相对较小
- 通用能力不如大型模型
- 代码质量在某些场景下不如 [[Claude 3.5 Sonnet]]
