---
title: "Post-training"
aliases: ["后训练", "后处理训练", "Post-training", "模型对齐训练"]
---

# Post-training

**后训练（Post-training）**是在 [[Pre-training|预训练]] 完成后、模型部署前的一系列训练步骤。后训练的目标是将通用的语言模型转变为安全、有用、符合人类偏好的助手。

## 后训练流程

```
预训练模型 → SFT → RLHF/DPO → 安全加固 → 部署
```

### 阶段一：SFT（Supervised Fine-Tuning，监督微调）

在高质量的指令-回复数据上微调模型：

**数据类型**：
- 单轮指令遵循数据
- 多轮对话数据
- 代码生成和调试数据
- 数学推理数据
- 创意写作数据

**关键因素**：
- 数据质量远比数量重要
- [[Anthropic]] 发现 ~10K 高质量 SFT 样本即可显著提升指令遵循能力
- 多样性很重要：覆盖不同任务类型、难度、语言

### 阶段二：偏好对齐

使用人类偏好数据进一步优化模型：

**[[RLHF]]（标准方案）**：
1. 训练奖励模型
2. 使用 PPO 优化策略模型
3. KL 惩罚防止偏离太远

**[[DPO]]（简化方案）**：
- 直接在偏好数据对上优化
- 无需训练独立的奖励模型
- 训练更稳定，实现更简单

**混合方案**：
- [[DeepSeek V3]]：SFT → DPO
- [[DeepSeek R1]]：SFT → RL（GRPO）
- [[Qwen 3]]：SFT → DPO → RL
- [[Claude Opus 4]]：SFT → [[Constitutional AI]] + RLHF

### 阶段三：安全加固

- **红队测试**：发现并修复安全漏洞
- **安全微调**：在安全相关的数据上进一步训练
- **安全分类器**：训练独立的安全检测模型
- **安全提示**：在系统提示中嵌入安全约束

## 后训练技术演进

| 时期 | 方法 | 代表 | 特点 |
|------|------|------|------|
| 2022 | SFT + RLHF | [[InstructGPT]] | 开创性工作 |
| 2023 | SFT + RLHF | GPT-4, Claude 2 | 规模化应用 |
| 2023 | SFT + DPO | Llama 2, Zephyr | 简化对齐流程 |
| 2024 | SFT + DPO + RL | Llama 3, Qwen 2 | 混合训练策略 |
| 2025 | SFT + GRPO | [[DeepSeek R1]] | 纯 RL 推理涌现 |
| 2025 | 混合推理 | [[Qwen 3]] | 可切换快慢思考 |

## 数据质量工程

后训练的数据质量是决定模型体验的关键：

### 数据收集方式
1. **人工标注**：专业标注员编写高质量回复
2. **AI 辅助**：使用大模型生成初稿，人工审核修正
3. **用户反馈**：从真实用户交互中筛选优质对话
4. **合成数据**：使用更强的模型生成训练数据

### 数据质量标准
- 事实准确性
- 指令遵循度
- 安全性
- 表达质量和格式
- 多样性和覆盖度

## DeepSeek R1 的突破

[[DeepSeek R1]] 证明了一个重要发现：

- 仅通过纯 RL（GRPO），无需 SFT 阶段的推理数据
- 模型可以**自主涌现**出 [[Chain of Thought|长链推理]] 能力
- 推理能力的获得不需要人工设计的推理模板
- 这改变了后训练的范式：从"教模型如何思考"到"让模型自己学会思考"

## 后训练的评估

| 评估维度 | 方法 |
|---------|------|
| 指令遵循 | MT-Bench, AlpacaEval |
| 安全性 | HarmBench, ToxiGen |
| 有用性 | Chatbot Arena (ELO 排名) |
| 推理 | GSM8K, MATH, HumanEval |
| 多语言 | 多语言基准测试 |

## 关键论文

- Ouyang et al., "Training language models to follow instructions with human feedback", 2022
- Rafailov et al., "Direct Preference Optimization", NeurIPS 2023
- DeepSeek-AI, "DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning", 2025
