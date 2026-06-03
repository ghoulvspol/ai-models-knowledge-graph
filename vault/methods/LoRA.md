---
title: "LoRA"
aliases: ["Low-Rank Adaptation", "低秩适配"]
---

# LoRA

LoRA（Low-Rank Adaptation）是一种参数高效的 [[Fine-tuning]] 方法，通过在模型权重矩阵中注入低秩分解矩阵来实现微调。它由 Hu 等人于 2021 年提出，已成为大模型微调的标准方法。

## 核心原理

LoRA 的关键洞察：
- 预训练模型的权重更新矩阵是低秩的
- 可以用两个小矩阵的乘积来近似权重更新
- 仅训练这两个小矩阵，冻结原始模型

数学表达：
```
W' = W + ΔW = W + BA
```
其中：
- W：原始权重矩阵（冻结）
- B ∈ R^(d×r)：低秩矩阵
- A ∈ R^(r×k)：低秩矩阵
- r << min(d, k)：秩远小于原始维度

## 参数效率

以 [[Llama 4 Scout]]（70B）为例：

| 方法 | 可训练参数 | 显存需求 | 效果 |
|------|-----------|---------|------|
| 全参数微调 | 70B (100%) | ~280GB | 最佳 |
| LoRA (r=16) | ~40M (0.06%) | ~16GB | 接近全参数 |
| LoRA (r=64) | ~160M (0.2%) | ~24GB | 非常接近 |
| QLoRA (r=16) | ~40M (0.06%) | ~8GB | 略低于 LoRA |

## 超参数

| 参数 | 说明 | 典型值 |
|------|------|--------|
| r (rank) | 低秩矩阵的秩 | 8, 16, 32, 64 |
| alpha | 缩放因子 | 16, 32 |
| target_modules | 应用 LoRA 的层 | q_proj, v_proj, k_proj |
| dropout | LoRA 层的 dropout | 0.05, 0.1 |

## 变体

| 变体 | 说明 |
|------|------|
| QLoRA | 4-bit 量化 + LoRA，显存需求最低 |
| LoRA+ | 不同学习率给 A 和 B 矩阵 |
| DoRA | 权重分解为方向和大小 |
| AdaLoRA | 自适应秩分配 |
| rsLoRA | 秩稳定缩放 |
| GaLore | 梯度低秩投影 |

## 框架支持

- **HuggingFace PEFT**：最流行的 LoRA 实现
- **LLaMA-Factory**：一站式微调工具
- **Axolotl**：简化微调流程
- **Unsloth**：2x 加速的 LoRA 训练

## 应用场景

- **垂直领域适配**：医疗、法律、金融等
- **多任务学习**：为不同任务训练不同 LoRA
- **个性化**：为用户定制专属模型
- **安全对齐**：[[RLHF]] 和 [[DPO]] 的参数高效版本
- **[[Apple]] Intelligence**：端侧 LoRA 适配

## 学术引用

Hu, E., et al. "LoRA: Low-Rank Adaptation of Large Language Models." ICLR 2022. 引用量超过 15,000 次。
