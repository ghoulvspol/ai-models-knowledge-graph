---
title: "MoE"
aliases: ["混合专家模型", "Mixture of Experts", "稀疏混合专家", "SMoE"]
---

# MoE

**混合专家模型（Mixture of Experts, MoE）**是一种稀疏激活架构，通过在每个输入 token 上只激活部分"专家"子网络，实现以远低于总参数量的计算成本获得大模型的容量优势。

## 核心原理

MoE 层替换标准 [[Transformer]] 中的 FFN 层，包含：

1. **多个专家网络（Experts）**：每个专家是一个独立的 FFN
2. **门控网络（Router/Gate）**：为每个输入 token 选择 Top-K 个专家

$$y = \sum_{i=1}^{N} g_i(x) \cdot E_i(x), \quad g(x) = \text{TopK}(\text{softmax}(W_g \cdot x))$$

其中 $g_i$ 是门控权重，$E_i$ 是第 $i$ 个专家的输出，通常 $K \in \{1, 2, 4\}$。

**关键区别**：
- **总参数量**：包含所有专家的参数（如 DeepSeek V3 总参数 671B）
- **激活参数量**：每个 token 实际使用的参数（如 DeepSeek V3 每 token 激活 37B）

## 主流模型采用情况

| 模型 | 总参数 | 激活参数 | 专家数 | Top-K |
|------|--------|---------|--------|-------|
| Mixtral 8x7B | 47B | 13B | 8 | 2 |
| [[DeepSeek V3]] | 671B | 37B | 256+1 | 8 |
| [[DeepSeek R1]] | 671B | 37B | 256+1 | 8 |
| [[Llama 4 Scout]] | 109B | 17B | 128 | 1 |
| [[Qwen 3]] 235B | 235B | 22B | 128 | 8 |
| [[Grok 3]] | ~314B | ~86B | 未公开 | 未公开 |

## 技术挑战

### 负载均衡
- **问题**：门控网络可能倾向于选择少数专家，导致其他专家"饿死"
- **解决方案**：辅助损失（Auxiliary Loss）鼓励均匀分配，[[DeepSeek V3]] 采用无辅助损失的负载均衡策略

### 通信开销
- 分布式训练中，专家分布在不同 GPU 上，token 路由需要跨设备通信
- 采用专家并行（Expert Parallelism）和流水线策略优化

### 训练不稳定
- 路由决策的离散性可能导致梯度不稳定
- 使用 Jittering、Z-Loss 等技术缓解

## DeepSeek 的创新

[[DeepSeek]] 在 MoE 架构上做出多项创新：
- **细粒度专家**：将大专家拆分为更多小专家，提高组合灵活性
- **共享专家**：部分专家对所有 token 激活，确保基础能力
- **无辅助损失负载均衡**：通过动态偏置项实现平衡，不损失模型质量

## 与 Dense 模型的对比

| 维度 | Dense 模型 | MoE 模型 |
|------|-----------|---------|
| 训练效率 | 标准 | 更高（相同质量用更少计算） |
| 推理效率 | 与参数量成正比 | 仅与激活参数量相关 |
| 内存需求 | 低 | 高（需加载全部专家） |
| 代表 | [[Claude Opus 4]], [[GPT-4.1]] | [[DeepSeek V3]], [[Qwen 3]] |

## 关键论文

- Shazeer et al., "Outrageously Large Neural Networks: The Sparsely-Gated Mixture-of-Experts Layer", ICLR 2017
- Jiang et al., "Mixtral of Experts", 2024
- DeepSeek-AI, "DeepSeek-V3 Technical Report", 2024
