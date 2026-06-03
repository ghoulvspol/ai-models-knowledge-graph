---
title: "RLHF"
aliases: ["基于人类反馈的强化学习", "Reinforcement Learning from Human Feedback"]
---

# RLHF

**RLHF（Reinforcement Learning from Human Feedback，基于人类反馈的强化学习）**是当前大语言模型 [[Alignment]] 的核心技术，通过训练奖励模型来指导语言模型生成更符合人类偏好的输出。

## 核心流程

RLHF 分为三个阶段：

### 阶段一：监督微调（SFT）
在高质量的指令-回复数据上对 [[Pre-training|预训练]] 模型进行 [[Fine-tuning|微调]]，得到 SFT 模型。

### 阶段二：奖励模型训练（Reward Model Training）
- 人类标注者对同一 prompt 的多个回复进行排序
- 训练奖励模型 $r_\phi(x, y)$ 学习人类偏好
- 使用 Bradley-Terry 模型：

$$\mathcal{L}_{\text{RM}} = -\mathbb{E}_{(x, y_w, y_l)} \left[ \log \sigma(r_\phi(x, y_w) - r_\phi(x, y_l)) \right]$$

其中 $y_w$ 是被偏好的回复，$y_l$ 是不被偏好的回复。

### 阶段三：强化学习优化（PPO）
使用 Proximal Policy Optimization（PPO）算法优化语言模型：

$$\mathcal{L}_{\text{PPO}} = \mathbb{E}_{x, y \sim \pi_\theta} \left[ r_\phi(x, y) - \beta \cdot D_{\text{KL}}(\pi_\theta \| \pi_{\text{ref}}) \right]$$

KL 散度惩罚项防止模型偏离参考策略太远，避免"奖励黑客"（Reward Hacking）。

## InstructGPT：RLHF 的开创者

[[OpenAI]] 2022 年发表的 InstructGPT 论文首次将 RLHF 应用于大语言模型：

- 基座模型：GPT-3（175B）
- 人类标注员数量：约 40 人
- 结果：1.3B 的 InstructGPT 在人类评估中优于 175B 的 GPT-3
- 这一成果直接催生了 [[ChatGPT]] 的发布

## 现代应用

几乎所有主流模型都使用 RLHF 或其变体：
- [[GPT-4o]]、[[GPT-4.1]]：OpenAI 的 RLHF 方法论持续迭代
- [[Claude 3.5 Sonnet]]、[[Claude Opus 4]]：[[Anthropic]] 结合 [[Constitutional AI]] 使用 RLHF
- [[DeepSeek R1]]：在 RL 阶段采用 GRPO（Group Relative Policy Optimization）
- [[Qwen 3]]：使用 DPO + RLHF 混合训练

## RLHF 的挑战

1. **标注成本高**：需要大量高质量人类标注
2. **奖励模型脆弱**：可能被"欺骗"，生成奖励高但质量差的回复
3. **对齐税（Alignment Tax）**：RLHF 可能降低模型在某些基准上的原始能力
4. **主观性**：不同标注者的偏好可能不一致

## RLHF 的变体与替代

| 方法 | 特点 | 代表使用 |
|------|------|---------|
| 标准 RLHF | PPO + 奖励模型 | InstructGPT, [[GPT-4o]] |
| [[DPO]] | 无需奖励模型 | [[Llama 4 Scout]], [[Qwen 3]] |
| RLHF-AIF | [[Constitutional AI]] + RLHF | Claude 系列 |
| GRPO | 分组相对策略优化 | [[DeepSeek R1]] |
| KTO | 仅需二元反馈 | 部分开源模型 |

## 关键论文

- Ouyang et al., "Training language models to follow instructions with human feedback" (InstructGPT), 2022
- Christiano et al., "Deep Reinforcement Learning from Human Preferences", NeurIPS 2017
- Schulman et al., "Proximal Policy Optimization Algorithms", 2017
