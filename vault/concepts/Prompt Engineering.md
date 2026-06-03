---
title: "Prompt Engineering"
aliases: ["提示工程", "提示词工程", "Prompt 设计", "上下文学习"]
---

# Prompt Engineering

**提示工程（Prompt Engineering）**是设计和优化输入提示（prompt）以引导大语言模型产生期望输出的技术。它是使用 [[Foundation Model|大模型]] 最直接且最重要的技能之一。

## 核心策略

### Zero-Shot（零样本）
直接给出任务描述，不提供示例：

```
将以下英文翻译为中文：Hello, how are you?
```

模型利用 [[Pre-training|预训练]] 知识直接完成任务。

### Few-Shot（少样本）
在提示中提供几个示例：

```
英文：Good morning → 中文：早上好
英文：Thank you → 中文：谢谢
英文：Hello, how are you? → 中文：
```

也称为**上下文学习（In-Context Learning, ICL）**，模型从示例中"学习"任务模式。

### Chain of Thought（思维链）
要求模型展示推理过程：

```
Q: 一个农场有 15 只鸡和 8 只鸭，卖掉了 7 只鸡，还剩多少只家禽？
A: 让我一步步计算：
1. 初始：15 + 8 = 23 只家禽
2. 卖掉 7 只鸡：23 - 7 = 16 只
3. 答案：16 只家禽
```

详细内容见 [[Chain of Thought]]。

## 高级技巧

### 系统提示（System Prompt）
设定模型的角色、行为和约束：

```
你是一位资深的 Python 开发专家。回答时：
1. 优先使用 Python 3.10+ 特性
2. 包含类型注解
3. 解释关键设计决策
```

### 角色扮演
让模型扮演特定角色以获得专业视角：

```
作为一名有 20 年经验的数据科学家，请分析以下数据集...
```

### 结构化输出
要求模型按特定格式输出：

```
以 JSON 格式返回结果，包含以下字段：
{
  "summary": "...",
  "sentiment": "positive|negative|neutral",
  "confidence": 0.0-1.0
}
```

### 分步指令
将复杂任务拆解为明确步骤：

```
请按以下步骤分析这段代码：
1. 识别主要功能
2. 找出潜在的 bug
3. 建议优化方案
4. 提供重构后的代码
```

### ReAct（Reasoning + Acting）
结合推理和工具使用：

```
Thought: 用户问的是今天的天气，我需要查询天气 API
Action: call_weather_api(city="北京")
Observation: 晴，25°C
Thought: 已获得天气信息，可以回答用户
Answer: 北京今天天气晴朗，气温 25°C。
```

## 提示注入防御

**提示注入（Prompt Injection）**是针对大模型的主要安全威胁之一：

- **直接注入**：用户在输入中嵌入"忽略之前的指令"
- **间接注入**：在外部数据（网页、文档）中嵌入恶意指令
- **防御方法**：输入过滤、输出检查、使用 [[Constitutional AI]] 约束

## 不同模型的提示差异

| 模型 | 提示特点 |
|------|---------|
| [[GPT-4o]] | 对系统提示敏感，支持结构化输出 |
| [[Claude 3.5 Sonnet]] | 长系统提示表现好，XML 标签有效 |
| [[DeepSeek R1]] | 推理任务不需要显式 CoT |
| [[Gemini 2.5 Pro]] | 多模态提示能力强 |
| [[Llama 4 Scout]] | 开源模型，需要更详细的指令 |

## 评估与优化

- **A/B 测试**：比较不同提示在相同任务上的效果
- **提示模板化**：将可变部分参数化，便于系统化管理
- **自动优化**：DSPy 等框架自动搜索最优提示

## 关键论文

- Brown et al., "Language Models are Few-Shot Learners" (GPT-3), NeurIPS 2020
- Wei et al., "Chain-of-Thought Prompting Elicits Reasoning in Large Language Models", NeurIPS 2022
- Yao et al., "ReAct: Synergizing Reasoning and Acting in Language Models", ICLR 2023
