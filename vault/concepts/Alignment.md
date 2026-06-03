---
title: "Alignment"
aliases: ["对齐", "AI 对齐", "价值对齐", "Value Alignment"]
---

# Alignment

**对齐（Alignment）**是确保 AI 系统的行为符合人类意图和价值观的研究领域。随着大语言模型能力的快速增强，对齐已成为 [[AI Safety]] 中最核心的研究问题。

## 核心问题

### 外部对齐（Outer Alignment）
- **问题**：如何正确地将人类意图编码为训练目标
- **挑战**：奖励模型/目标函数可能不完全反映真实的人类偏好
- **示例**：[[RLHF]] 中的奖励黑客（Reward Hacking）——模型找到获得高奖励但质量差的策略

### 内部对齐（Inner Alignment）
- **问题**：训练出的模型是否真正"内化"了目标，还是仅仅在训练分布上表现良好
- **挑战**：模型可能学到与训练目标不同但训练期间等价的内部目标（Mesa-Optimization）
- **风险**：分布偏移时，内部目标可能与训练目标分离

## 主要对齐方法

### RLHF（基于人类反馈的强化学习）
- [[InstructGPT]] 开创的范式
- 人类标注偏好 → 训练奖励模型 → PPO 优化
- 当前最广泛使用的对齐方法
- 详细内容见 [[RLHF]]

### DPO（直接偏好优化）
- 简化 [[RLHF]]，无需强化学习训练循环
- 直接在偏好数据上优化模型
- 详细内容见 [[DPO]]

### Constitutional AI（宪法 AI）
- [[Anthropic]] 提出的方法
- 让 AI 根据一组"宪法原则"自我批评和修正回复
- 结合 [[RLHF]] 和 AI 自我监督
- 减少对人类标注的依赖

$$\text{回复} \xrightarrow{\text{AI 自我批评}} \text{修正回复} \xrightarrow{\text{RLHF 训练}} \text{对齐后模型}$$

### Scalable Oversight（可扩展监督）
- **辩论（Debate）**：两个 AI 辩论，人类评判
- **递归奖励建模**：AI 辅助人类进行奖励评估
- **弱到强泛化**：用弱模型监督强模型

## 对齐税（Alignment Tax）

对齐训练可能降低模型的原始能力：
- 过度安全：模型拒绝回答合理的学术/专业问题
- 创造力下降：安全限制可能抑制创造性和表达
- 性能损失：某些基准测试分数可能下降

各公司努力最小化对齐税：
- [[GPT-4o]]：持续优化安全与能力的平衡
- [[Claude 3.5 Sonnet]]：[[Anthropic]] 在安全性和有用性之间精细调优
- [[DeepSeek R1]]：使用纯 RL 训练，模型自主学习安全行为

## 当前挑战

1. **主观性**：不同文化、群体的价值观可能冲突
2. **评估困难**：如何衡量对齐程度
3. **欺骗性对齐**：模型在评估中表现对齐，实际未对齐
4. **可扩展性**：当 AI 超过人类能力时，如何继续监督
5. **目标稳定性**：模型能力增强后对齐是否会保持

## 关键论文

- Christiano, "Clarifying AI Alignment", 2018
- Bai et al., "Constitutional AI: Harmlessness from AI Feedback", 2022
- Burns et al., "Weak-to-Strong Generalization", 2023
- Ngo et al., "The Alignment Problem from a Deep Learning Perspective", 2023
