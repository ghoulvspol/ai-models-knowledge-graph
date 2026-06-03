---
title: "Scaling Laws"
aliases: ["缩放定律", "缩放法则", "规模定律"]
---

# Scaling Laws

**缩放定律（Scaling Laws）**描述了大语言模型性能如何随模型参数量、数据量和计算量的增长而可预测地提升。这一发现是推动 AI 模型规模爆炸式增长的理论基础。

## Kaplan 缩放定律（2020）

[[OpenAI]] 研究团队在 2020 年发表了开创性论文，发现模型的测试损失与三个因素呈**幂律关系**：

$$L(N) \propto N^{-\alpha_N}, \quad L(D) \propto D^{-\alpha_D}, \quad L(C) \propto C^{-\alpha_C}$$

其中 $N$ 为参数量，$D$ 为数据量，$C$ 为计算量（FLOPs）。

**关键发现**：
- 模型性能随规模增长平滑提升，不存在明显的天花板
- 更大的模型在相同计算预算下更高效（样本效率更高）
- 模型架构细节（宽度/深度比、注意力头数）对性能影响相对较小
- 计算最优策略：模型规模应随计算预算的增加而增大，但数据量增长应相对较少

## Chinchilla 缩放定律（2022）

DeepMind 的 Hoffmann et al. 2022 年发表 *"Training Compute-Optimal Large Language Models"*，修正了 Kaplan 的结论：

**核心观点**：给定计算预算，模型参数量和训练数据量应**等比例增长**。

$$N_{\text{opt}} \propto C^{0.5}, \quad D_{\text{opt}} \propto C^{0.5}$$

| 模型 | 参数量 | 训练 Token 数 | 是否计算最优 |
|------|--------|--------------|-------------|
| Gopher | 280B | 300B | 欠训练（模型过大） |
| Chinchilla | 70B | 1.4T | 计算最优 |
| [[Llama 4 Scout]] | 109B（17B 激活） | 30T+ | 过度训练（推理效率优先） |

**实践启示**：
- Chinchilla 70B 用更少参数超过了 Gopher 280B
- 现代模型（如 Llama 系列）故意"过度训练"以优化推理效率
- [[DeepSeek V3]]、[[Qwen 3]] 等采用 [[MoE]] 架构来平衡训练效率和推理成本

## 对模型发展的影响

缩放定律直接推动了：
1. **算力竞赛**：模型训练从 GPU 级别扩展到万卡集群
2. **[[Foundation Model]] 范式**：预训练大模型 + 下游微调
3. **[[Emergent Abilities]] 的讨论**：某些能力是否仅在特定规模涌现
4. **[[Pre-training]] 数据工程**：高质量数据的收集和清洗成为关键

## 当代争议

- **数据墙**：高质量文本数据是否即将耗尽？合成数据是否可持续？
- **推理时缩放（Inference-Time Scaling）**：[[o1]]、[[DeepSeek R1]] 通过增加推理时计算来提升性能，开辟了新的缩放维度
- **[[MoE]] 缩放**：稀疏激活是否改变了缩放定律的适用条件？

## 关键论文

- Kaplan et al., "Scaling Laws for Neural Language Models", 2020
- Hoffmann et al., "Training Compute-Optimal Large Language Models" (Chinchilla), 2022
- Snell et al., "Scaling LLM Test-Time Compute Optimally can be More Effective than Scaling Model Parameters", 2024
