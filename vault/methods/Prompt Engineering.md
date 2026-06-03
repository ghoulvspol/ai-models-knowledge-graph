---
title: "Prompt Engineering"
aliases: ["提示工程", "prompt engineering"]
---

# Prompt Engineering

Prompt Engineering 是设计和优化输入提示（Prompt）以获得更好 AI 输出的技术和方法论。它是使用大语言模型的核心技能，也是最易入门的 AI 应用技术。

## 核心技术

### 基础技巧

| 技巧 | 说明 | 示例 |
|------|------|------|
| 角色设定 | 指定模型扮演的角色 | "你是一位资深律师" |
| 任务分解 | 将复杂任务拆分为步骤 | "首先...然后...最后" |
| 格式指定 | 明确输出格式 | "以 JSON 格式回答" |
| 示例提供 | 给出输入-输出示例 | Few-shot 学习 |
| 约束条件 | 设定限制条件 | "回答不超过 200 字" |

### 高级技巧

| 技巧 | 说明 | 相关方法 |
|------|------|---------|
| [[Chain of Thought]] | 引导模型展示推理过程 | CoT, Zero-shot CoT |
| Self-Consistency | 多次采样取最佳答案 | 投票机制 |
| ReAct | 推理+行动交替进行 | [[AI Agent]] |
| Few-shot Learning | 提供少量示例 | In-context Learning |
| Meta-Prompting | 让模型生成更好的提示 | 自动优化 |

## 应用场景

- **代码生成**：通过精确描述需求获得更好代码
- **文本创作**：设定风格、语气、长度等约束
- **数据分析**：指定分析方法和输出格式
- **知识问答**：结合 [[RAG]] 的提示设计
- **Agent 构建**：系统提示定义 Agent 行为

## 企业级实践

- **系统提示（System Prompt）**：定义模型的基础行为
- **提示模板**：可复用的提示框架
- **A/B 测试**：评估不同提示的效果
- **提示管理**：版本控制和团队协作

## 与 AI Agent 的关系

Prompt Engineering 是构建 [[AI Agent]] 的基础：
- 系统提示定义 Agent 的能力和边界
- 工具调用的提示设计
- 多轮对话的状态管理
- 错误处理和恢复策略

## 学习资源

- [[OpenAI]] 官方 Prompt Engineering 指南
- [[Anthropic]] Claude 最佳实践
- [[Google]] Gemini Prompting Guide
- Learn Prompting 社区
- Lilian Weng 的 Prompt Engineering 综述
