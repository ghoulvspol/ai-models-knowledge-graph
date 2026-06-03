---
title: "AI Agent"
aliases: ["AI智能体", "Agent", "AI agent"]
---

# AI Agent

AI Agent 是能够自主感知环境、制定计划、使用工具并执行任务的 AI 系统。它是大语言模型从"对话工具"向"行动系统"演进的关键方向。

## 核心组件

| 组件 | 说明 | 代表实现 |
|------|------|---------|
| LLM 大脑 | 推理和决策的核心 | [[GPT-4o]], [[Claude Opus 4]], [[Qwen 3]] |
| 记忆 | 短期（上下文）和长期（外部存储） | 向量数据库 |
| 工具 | 调用外部 API、代码执行等 | Function Calling |
| 规划 | 任务分解和执行策略 | [[Chain of Thought]], ReAct |

## Agent 架构模式

### ReAct（Reasoning + Acting）

推理和行动交替进行：
1. 思考（Thought）：分析当前状态
2. 行动（Action）：调用工具或执行操作
3. 观察（Observation）：获取行动结果
4. 重复循环

### Plan-and-Execute

先制定完整计划，再逐步执行：
1. 将任务分解为子任务列表
2. 按顺序执行每个子任务
3. 根据结果调整后续计划

### Multi-Agent

多个 Agent 协作完成复杂任务：
- **主从模式**：一个协调者 + 多个执行者
- **对等模式**：多个 Agent 平等协作
- **辩论模式**：多个 Agent 讨论达成共识

## 工具使用

AI Agent 可调用的典型工具：
- **代码执行**：Python、JavaScript 等
- **网页浏览**：搜索和信息获取
- **API 调用**：第三方服务集成
- **文件操作**：读写文件和数据库
- **[[RAG]] 检索**：知识库查询

## 产品实例

| 产品 | 机构 | 特点 |
|------|------|------|
| ChatGPT Code Interpreter | [[OpenAI]] | 代码执行 Agent |
| Claude Code | [[Anthropic]] | 编程 Agent |
| Gemini Gems | [[Google DeepMind]] | 定制 Agent |
| Devin | Cognition | 软件工程 Agent |
| Cursor | Anysphere | AI 编程助手 |

## 挑战

- **可靠性**：Agent 可能犯错或陷入循环
- **安全性**：工具调用可能产生不可逆操作
- **评估**：缺乏标准化的 Agent 评测方法
- **成本**：多步推理和工具调用增加延迟和成本
- **可控性**：需要平衡自主性和人类监督

## 评测基准

- [[SWE-bench]]：软件工程任务
- WebArena：网页操作任务
- AgentBench：综合 Agent 能力
- GAIA：通用 AI Agent 评测
