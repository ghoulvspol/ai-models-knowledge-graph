---
title: "RLHF"
aliases: ["Reinforcement Learning from Human Feedback"]
---

# RLHF

RLHF（Reinforcement Learning from Human Feedback）是将人类偏好反馈用于训练 AI 模型的核心方法。它是 [[OpenAI]] ChatGPT、[[Anthropic]] Claude 等产品成功的关键技术。

## 核心流程

RLHF 的标准三阶段流程：

### 1. 监督微调（SFT）

在人工编写的高质量对话数据上对预训练模型进行 [[Fine-tuning]]。

### 2. 奖励模型训练

- 人类标注者对模型输出进行排序（A 比 B 好）
- 训练奖励模型（Reward Model）预测人类偏好
- 奖励模型作为后续强化学习的信号源

### 3. 强化学习优化

使用 PPO（Proximal Policy Optimization）等算法，以奖励模型为信号优化语言模型。关键技巧包括：
- KL 散度惩罚，防止模型偏离太远
- Value Head 估计状态价值
- 广义优势估计（GAE）

## 关键人物

- **[[Jan Leike]]**：[[OpenAI]] 超级对齐团队，RLHF 对齐研究
- **[[Dario Amodei]]**：推动 RLHF 在 [[Anthropic]] 的应用
- **[[Alec Radford]]**：GPT 系列预训练为 RLHF 提供基础

## 应用实例

| 模型 | RLHF 应用 |
|------|----------|
| ChatGPT（[[OpenAI]]） | 最早大规模应用 RLHF 的产品 |
| Claude（[[Anthropic]]） | 结合 [[Constitutional AI]] 的 RLHF |
| Llama 2（[[Meta AI]]） | 开源 RLHF 训练流程 |
| [[DeepSeek R1]] | 纯 RL 训练推理能力（无 SFT） |

## 优势与挑战

| 优势 | 挑战 |
|------|------|
| 对齐人类偏好 | 人类标注成本高 |
| 减少有害输出 | 奖励模型可能被欺骗 |
| 提升有用性 | 标注者偏见 |
| 广泛验证有效 | 训练不稳定 |

## 与 DPO 的关系

[[DPO]]（Direct Preference Optimization）是 RLHF 的简化替代方案，直接从偏好数据优化模型，无需单独训练奖励模型和运行强化学习。

## 学术引用

Ouyang, L., et al. "Training language models to follow instructions with human feedback." NeurIPS 2022. 引用量超过 10,000 次。
