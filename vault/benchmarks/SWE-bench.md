---
title: "SWE-bench"
aliases: ["SWE bench", "SWEbench"]
---

# SWE-bench

SWE-bench 是评估 AI 系统解决真实 GitHub Issue 能力的评测基准，由 Princeton NLP 于 2023 年提出。它被认为是评估 [[AI Agent]] 编程能力最接近真实场景的评测。

## 评测设计

- **数据来源**：真实 GitHub 仓库的 Issue 和对应的 Pull Request
- **任务**：给定 Issue 描述和代码库，生成修复补丁
- **验证方式**：运行仓库的测试套件验证修复正确性
- **版本**：SWE-bench（2294 题）和 SWE-bench Lite（300 题子集）

## 题目特点

| 特性 | 说明 |
|------|------|
| 真实性 | 来自 Django、Flask、scikit-learn 等知名开源项目 |
| 复杂度 | 需要理解代码库结构、定位问题、生成修复 |
| 多文件 | 通常需要修改多个文件 |
| 测试驱动 | 有现成的测试用例验证正确性 |

## 顶级系统表现（2025）

| 系统 | SWE-bench Lite | 机构 |
|------|---------------|------|
| OpenAI Codex Agent | ~70% | [[OpenAI]] |
| Claude Code | ~72% | [[Anthropic]] |
| Devin | ~55% | Cognition |
| SWE-agent + GPT-4 | ~28% | Princeton |

*注：AI Agent 系统在此评测上进步极快*

## 行业意义

SWE-bench 代表了 AI 编程能力的"终极测试"：
- 不是简单的代码生成，而是理解真实代码库并修复 Bug
- 需要阅读文档、理解代码结构、定位问题
- 推动了 [[AI Agent]] 和自动化编程工具的发展
- 从 2023 年的 ~5% 到 2025 年的 ~72%，进步惊人

## 衍生评测

- **SWE-bench Verified**：人工验证的高质量子集
- **SWE-bench Multimodal**：包含截图等多模态信息
- **WebArena**：网页应用的类似评测

## 学术引用

Jimenez, C. E., et al. "SWE-bench: Can Language Models Resolve Real-World GitHub Issues?" ICLR 2024. 引用量超过 1000 次。
