---
title: "Emergent Abilities"
aliases: ["涌现能力", "涌现", "Emergent Abilities", "规模涌现"]
---

# Emergent Abilities

**涌现能力（Emergent Abilities）**是指大语言模型在达到一定规模后突然展现出的、在小模型中不存在的能力。这一现象被认为是 [[Scaling Laws|缩放定律]] 最令人兴奋但也最具争议的发现之一。

## 核心概念

Wei et al. 2022 年在论文 *"Emergent Abilities of Large Language Models"* 中正式定义：

> 涌现能力是指在小模型中不存在、但在大模型中出现的能力。这种能力不是通过简单插值或外推预测的。

**关键特征**：
- **突变性**：不是渐进提升，而是在特定规模"突然"出现
- **不可预测性**：无法从小模型的表现外推
- **规模依赖**：需要达到临界规模才会涌现

## 涌现能力实例

### Chain of Thought 推理
- [[Chain of Thought]] 提示在小模型（<10B）上几乎无效
- 在模型规模超过 ~100B 后突然变得有效
- 是最经典的涌现能力案例

### 指令遵循
- 小模型难以理解和遵循复杂指令
- 大模型可以自然理解零样本指令
- [[Fine-tuning|指令微调]] 进一步增强此能力

### 多步数学推理
- 小模型在多位数算术上接近随机
- 大模型可以进行复杂的多步数学推理
- [[o1]]、[[DeepSeek R1]] 将此能力推到新高度

### 代码生成
- 小模型生成的代码通常无法运行
- 大模型可以生成复杂的、可执行的代码
- [[GPT-4o]]、[[Claude 3.5 Sonnet]] 在编程任务上接近人类水平

### 多语言能力
- 小模型主要掌握训练数据中占主导的语言
- 大模型对低资源语言也能表现出一定的能力

## 争议与反思

### "涌现是幻觉"论点
Schaeffer et al. 2023 年论文 *"Are Emergent Abilities of Large Language Models a Mirage?"* 提出：

- 涌现可能是**评估指标**造成的假象
- 使用**连续指标**（而非离散准确率）时，性能提升是平滑的
- 即：模型能力是连续提升的，但二元评估（正确/错误）看起来像突然涌现

**例**：数学题得分从 0% 到 100% 是渐进的，但"完全正确率"（所有步骤正确）看起来是突变的。

### 支持涌现的论点
- 即使单个能力是渐进的，**能力组合**可能产生质变
- 某些能力确实存在明确的临界点
- [[DeepSeek R1]] 发现纯 RL 训练可以激发涌现推理行为

## 与 [[Foundation Model]] 的关系

涌现能力是 [[Foundation Model|基础模型]] 的核心价值之一：
- 预训练过程中自然涌现多种能力
- 通过 [[Prompt Engineering|提示]] 可以激活不同能力
- [[Fine-tuning|微调]] 和 [[RLHF|对齐]] 进一步增强涌现能力

## 对研究和实践的影响

1. **模型选择**：可能需要更大模型才能获得关键能力
2. **评估方法**：需要更细致的评估来发现涌现能力
3. **安全研究**：危险能力也可能涌现（见 [[AI Safety]]）
4. **成本考量**：涌现能力的规模阈值决定最低可用模型大小

## 关键论文

- Wei et al., "Emergent Abilities of Large Language Models", TMLR 2022
- Schaeffer et al., "Are Emergent Abilities of Large Language Models a Mirage?", NeurIPS 2023
- Ganguli et al., "Predictability and Surprise in Large Generative Models", 2022
