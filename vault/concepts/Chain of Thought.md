---
title: "Chain of Thought"
aliases: ["思维链", "链式思考", "CoT", "Chain-of-Thought"]
---

# Chain of Thought

**思维链（Chain of Thought, CoT）**是一种推理策略，要求模型在给出最终答案之前，先生成逐步的推理过程。这一技术显著提升了大语言模型在数学、逻辑和复杂推理任务上的表现。

## 核心原理

传统的 [[Prompt Engineering|提示]] 方式直接从问题映射到答案。CoT 则要求模型输出中间推理步骤：

**传统方式**：问题 → 答案
**CoT 方式**：问题 → 步骤1 → 步骤2 → ... → 答案

## 两种主要形式

### Few-Shot CoT（少样本思维链）
Wei et al. 2022 年提出，在 [[Prompt Engineering|提示]] 中提供包含推理过程的示例：

```
Q: Roger 有 5 个网球，又买了 2 罐，每罐 3 个。他现在有多少网球？
A: Roger 开始有 5 个球。2 罐各 3 个是 6 个。5 + 6 = 11。答案是 11。
```

### Zero-Shot CoT（零样本思维链）
Kojima et al. 2022 年发现，简单地添加 **"Let's think step by step"** 就能激发模型的推理能力，无需示例。

## 推理模型的 CoT

2024-2025 年，推理模型将 CoT 发展为**隐式深度推理**：

| 模型 | CoT 方式 | 特点 |
|------|---------|------|
| [[o1]] | 内部长链推理 | [[OpenAI]] 首个推理模型，推理 token 不对外展示 |
| [[o3]] | 增强推理 | 更长的推理链，更强的数学/编程能力 |
| [[DeepSeek R1]] | 开放推理链 | 推理过程对用户可见，使用 [[RLHF\|GRPO]] 训练 |
| [[Qwen 3]] | 混合推理 | 可在快速回答和深度推理间切换 |
| [[Gemini 2.5 Pro]] | 思考模式 | 内置推理能力 |

## 推理时缩放（Inference-Time Scaling）

CoT 推理模型开辟了新的 [[Scaling Laws|缩放维度]]——通过在推理时投入更多计算来提升性能：

$$\text{Performance} \propto f(\text{Model Parameters}, \text{Training Compute}, \text{Inference Compute})$$

- 更长的推理链 → 更多计算 → 通常更好的结果
- [[DeepSeek R1]] 发现，通过纯 [[RLHF|强化学习]]，模型能自主学会何时以及如何进行长链推理

## Emergent Abilities 与 CoT

CoT 是 [[Emergent Abilities|涌现能力]] 的典型案例：
- 小模型（<10B）使用 CoT 效果不明显，甚至可能变差
- 大模型（>100B）使用 CoT 后推理能力显著提升
- 这表明 CoT 依赖于模型的规模效应

## 技术变体

- **Self-Consistency**：生成多条推理路径，通过投票选择最一致的答案
- **Tree of Thoughts（ToT）**：将推理展开为树状搜索
- **Graph of Thoughts（GoT）**：允许推理步骤之间的非线性连接
- **ReAct**：结合推理（Reasoning）和行动（Acting），用于 [[AI Agent]] 场景

## 关键论文

- Wei et al., "Chain-of-Thought Prompting Elicits Reasoning in Large Language Models", NeurIPS 2022
- Kojima et al., "Large Language Models are Zero-Shot Reasoners", NeurIPS 2022
- DeepSeek-AI, "DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning", 2025
