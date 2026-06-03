---
title: "AI Agent"
aliases: ["AI 智能体", "智能体", "Agent", "自主 AI", "Agentic AI"]
---

# AI Agent

**AI 智能体（AI Agent）**是能够自主感知环境、制定计划、使用工具并执行任务的 AI 系统。不同于传统的单轮问答，Agent 具有**自主性、持续性和目标导向性**。

## 核心能力

### 规划（Planning）
- **任务分解**：将复杂目标拆解为可执行的子任务
- **[[Chain of Thought|推理]]**：通过逐步推理制定行动方案
- **自我反思**：评估执行结果，调整后续计划
- **ReAct 模式**：交替进行推理和行动

### 记忆（Memory）
- **短期记忆**：当前对话上下文（对话窗口）
- **长期记忆**：持久化存储的历史信息（向量数据库、知识图谱）
- **工作记忆**：当前任务的中间状态和变量

### 工具使用（Tool Use）
- 调用外部 API（搜索、计算、数据库查询）
- 执行代码（Python、JavaScript 等）
- 操控软件（浏览器、文件系统、终端）
- 访问 [[RAG|知识库]]

### 多模态感知
- 理解文本、图像、音频输入
- 使用 [[Multimodal|多模态]] 模型处理不同类型的信息

## Agent 架构模式

### ReAct（Reasoning + Acting）
```
循环:
  Thought: 分析当前状态，决定下一步
  Action: 执行工具调用
  Observation: 获取工具返回结果
  → 直到任务完成
```

### Plan-and-Execute
```
1. 先制定完整计划
2. 逐步执行每个子任务
3. 根据执行结果更新计划
```

### 多 Agent 协作
```
多个专业 Agent 协作:
  - Research Agent: 负责信息收集
  - Code Agent: 负责代码编写
  - Review Agent: 负责质量检查
  - Coordinator: 负责任务分配和协调
```

## 主流 Agent 框架

| 框架 | 特点 | 适用场景 |
|------|------|---------|
| LangChain | 工具链编排 | 通用 Agent |
| AutoGPT | 全自主执行 | 开放式任务 |
| CrewAI | 多 Agent 协作 | 团队任务 |
| MetaGPT | 模拟软件公司 | 软件开发 |
| OpenAI Assistants API | 内置工具 | 快速原型 |
| Claude Code | 终端 Agent | 软件开发 |

## Claude Code 作为 Agent

[[Anthropic]] 的 Claude Code 是一个典型的开发 Agent：
- 在终端中运行，具有文件系统和命令行访问权限
- 可以读写代码、执行测试、进行 Git 操作
- 通过 [[Chain of Thought]] 进行规划和推理
- 支持长上下文（200K tokens）处理大型代码库

## 挑战与风险

1. **可靠性**：Agent 可能在循环中出错或陷入死循环
2. **安全边界**：需要严格限制 Agent 的操作权限
3. **成本控制**：多轮调用的 token 消耗可能很大
4. **评估困难**：难以系统性评估 Agent 在开放环境中的表现
5. **[[AI Safety|安全]]**：自主 Agent 可能执行非预期的危险操作

## 发展趋势

- **代码 Agent**：自动编写和调试代码（Claude Code、Cursor、Copilot）
- **浏览器 Agent**：自动操作网页完成任务
- **企业 Agent**：自动化企业工作流
- **具身智能（Embodied AI）**：Agent 控制物理机器人

## 关键论文

- Yao et al., "ReAct: Synergizing Reasoning and Acting in Language Models", ICLR 2023
- Shinn et al., "Reflexion: Language Agents with Verbal Reinforcement Learning", NeurIPS 2023
- Xi et al., "The Rise and Potential of Large Language Model Based Agents", 2023
