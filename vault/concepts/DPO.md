---
title: "DPO"
aliases: ["直接偏好优化", "Direct Preference Optimization"]
---

# DPO

**DPO（Direct Preference Optimization，直接偏好优化）**是一种简化 [[Alignment|对齐]] 训练的方法，通过直接在偏好数据上优化语言模型，避免了 [[RLHF]] 中复杂的强化学习训练循环。

## 核心思想

DPO 的关键洞察是：**RLHF 的最优解可以用封闭形式表达**，从而将 RL 问题转化为简单的分类问题。

标准 [[RLHF]] 的目标函数：

$$\max_{\pi_\theta} \mathbb{E}_{x, y \sim \pi_\theta} [r(x, y)] - \beta D_{\text{KL}}(\pi_\theta \| \pi_{\text{ref}})$$

其最优策略的封闭形式为：

$$\pi^*(y|x) = \frac{1}{Z(x)} \pi_{\text{ref}}(y|x) \exp\left(\frac{1}{\beta} r(x, y)\right)$$

DPO 反解出隐式奖励：

$$r(x, y) = \beta \log \frac{\pi_\theta(y|x)}{\pi_{\text{ref}}(y|x)} + \beta \log Z(x)$$

## DPO 损失函数

将隐式奖励代入 Bradley-Terry 偏好模型，得到 DPO 损失：

$$\mathcal{L}_{\text{DPO}} = -\mathbb{E}_{(x, y_w, y_l)} \left[ \log \sigma\left(\beta \log \frac{\pi_\theta(y_w|x)}{\pi_{\text{ref}}(y_w|x)} - \beta \log \frac{\pi_\theta(y_l|x)}{\pi_{\text{ref}}(y_l|x)}\right) \right]$$

其中 $y_w$ 是偏好回复，$y_l$ 是非偏好回复，$\beta$ 控制偏离参考策略的程度。

## DPO vs RLHF

| 维度 | [[RLHF]]（PPO） | DPO |
|------|----------------|-----|
| 训练复杂度 | 高（需训练奖励模型 + RL 循环） | 低（仅需偏好数据对） |
| 超参数调优 | 困难（PPO 稳定性差） | 简单 |
| 内存需求 | 高（需同时加载策略、参考、奖励模型） | 较低 |
| 在线数据 | 需要 | 不需要（离线数据即可） |
| 理论等价性 | 标准方法 | 在理想条件下等价 |

## DPO 的变体

1. **IPO（Identity Preference Optimization）**：修正 DPO 在偏好数据有噪声时的过拟合问题
2. **KTO（Kahneman-Tversky Optimization）**：仅需二元反馈（好/坏），无需配对数据
3. **SimPO**：使用序列平均对数概率作为隐式奖励，无需参考模型
4. **ORPO（Odds Ratio Preference Optimization）**：将 SFT 和偏好优化合并为单一目标

## 实际应用

DPO 及其变体已被广泛采用：
- [[Llama 4 Scout]]：Meta 的 Llama 系列使用 DPO 进行对齐
- [[Qwen 3]]：结合 DPO 和 RLHF 进行训练
- [[DeepSeek V3]]：在 SFT 之后使用 DPO 进行对齐
- [[Phi-4]]：[[Microsoft]] 的小型模型也采用 DPO

## 局限性

- **离线方法**：无法像 RLHF 那样从模型自身的采样中学习
- **分布偏移**：训练数据的分布可能与模型生成的分布不匹配
- **奖励黑客**：隐式奖励可能被利用，尤其在 $\beta$ 设置不当时
- **质量上限**：受限于偏好数据的质量，无法超越标注者的水平

## 关键论文

- Rafailov et al., "Direct Preference Optimization: Your Language Model is Secretly a Reward Model", NeurIPS 2023
- Azar et al., "A General Theoretical Paradigm to Understand Learning from Human Feedback" (IPO), 2023
- Ethayarajh et al., "KTO: Model Alignment as Prospect Theoretic Optimization", 2024
