---
title: "HumanEval"
aliases: ["human-eval"]
---

# HumanEval

HumanEval 是 [[OpenAI]] 于 2021 年推出的代码生成评测基准，评估模型从函数签名和文档字符串生成正确 Python 代码的能力。

## 评测设计

- **题目数量**：164 道 Python 编程题
- **评估方式**：给定函数签名和文档字符串，生成函数体
- **验证方式**：自动生成的单元测试用例验证正确性
- **指标**：pass@k（k 次生成中至少一次通过的概率）

## 题目特点

| 特性 | 说明 |
|------|------|
| 难度 | 从简单算法到中等复杂度 |
| 领域 | 数学、字符串处理、数据结构、算法 |
| 长度 | 平均约 10 行代码 |
| 测试 | 平均约 7 个测试用例 |

## 顶级模型表现（2025）

| 模型 | pass@1 | 机构 |
|------|--------|------|
| [[Grok 3]] | ~93% | [[xAI]] |
| [[Claude Opus 4]] | ~92% | [[Anthropic]] |
| [[GPT-4o]] | ~90% | [[OpenAI]] |
| [[DeepSeek V3]] | ~89% | [[DeepSeek]] |
| [[Qwen 3]] | ~88% | [[Alibaba]] |
| [[Gemini 2.5 Pro]] | ~87% | [[Google DeepMind]] |

## 衍生评测

- **HumanEval+**：扩展测试用例，减少假阳性
- **MultiPL-E**：多语言版本（C++、Java、JavaScript 等）
- **MBPP**：Google 推出的类似基准（974 题）
- **CodeContests**：竞赛级代码评测

## 行业影响

HumanEval 成为代码生成模型的标准评测：
- 所有主流模型发布时都会报告 HumanEval 分数
- 推动了代码大模型（Codex、CodeLlama、DeepSeek-Coder）的发展
- 分数从 2021 年的 ~30% 提升到 2025 年的 ~93%

## 局限性

- 仅覆盖 Python 语言
- 题目难度有限，无法评估复杂工程能力
- 测试用例可能不够全面
- 催生了更难的评测（如 [[SWE-bench]]、[[Codeforces]]）

## 学术引用

Chen, M., et al. "Evaluating Large Language Models Trained on Code." arXiv 2021. 引用量超过 5000 次。
