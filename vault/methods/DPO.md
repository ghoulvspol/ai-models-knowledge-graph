---
title: "DPO"
aliases: ["Direct Preference Optimization"]
---

# DPO

DPO（Direct Preference Optimization）是 [[RLHF]] 的简化替代方案，由 Rafailov 等人于 2023 年提出。它直接从人类偏好数据优化语言模型，无需训练奖励模型和运行强化学习。

## 核心思想

DPO 的关键洞察：
- RLHF 的奖励模型可以被解析求解
- 偏好优化可以转化为简单的分类损失
- 无需 PPO 等复杂的强化学习算法

## 数学公式

DPO 损失函数：
```
L_DPO = -E[(log σ(β · (log π(y_w|x)/π_ref(y_w|x) - log π(y_l|x)/π_ref(y_l|x))))]
```

其中：
- π 是待优化的策略模型
- π_ref 是参考模型
- y_w 是人类偏好的回答
- y_l 是人类不偏好的回答
- β 控制偏离参考模型的程度

## 与 RLHF 的对比

| 特性 | [[RLHF]] | DPO |
|------|---------|-----|
| 奖励模型 | 需要单独训练 | 不需要 |
| 强化学习 | PPO 算法 | 无需 |
| 训练稳定性 | 较难调参 | 更稳定 |
| 计算成本 | 较高 | 较低 |
| 效果 | 长期验证 | 接近 RLHF |
| 实现复杂度 | 较高 | 较简单 |

## 应用实例

| 模型 | DPO 应用 |
|------|---------|
| Zephyr | HuggingFace 的 DPO 训练模型 |
| Llama 3（[[Meta AI]]） | 使用 DPO 进行对齐 |
| [[Qwen 3]]（[[Alibaba]]） | DPO + RLHF 混合训练 |
| Tulu 2 | AI2 的 DPO 训练模型 |

## 变体与改进

- **IPO**：Identity Preference Optimization，解决 DPO 的过拟合问题
- **KTO**：Kahneman-Tversky Optimization，只需二元反馈（好/坏）
- **ORPO**：Odds Ratio Preference Optimization，无需参考模型
- **SimPO**：Simple Preference Optimization，进一步简化

## 行业影响

DPO 的出现降低了对齐训练的门槛：
- 开源社区可以更容易地进行模型对齐
- 减少了对昂贵的人类标注和计算资源的需求
- 推动了开源对齐模型的发展

## 学术引用

Rafailov, R., et al. "Direct Preference Optimization: Your Language Model is Secretly a Reward Model." NeurIPS 2023. 引用量超过 3000 次。
