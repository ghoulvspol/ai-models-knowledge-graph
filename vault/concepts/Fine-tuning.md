---
title: "Fine-tuning"
aliases: ["微调", "模型微调", "Fine-tuning", "参数高效微调", "PEFT"]
---

# Fine-tuning

**微调（Fine-tuning）**是在 [[Pre-training|预训练]] 模型的基础上，使用特定任务或领域的数据继续训练，使模型适应特定应用场景的技术。

## 微调类型

### 全参数微调（Full Fine-tuning）
- 更新模型的所有参数
- 效果最好但计算成本最高
- 需要大量 GPU 内存（70B 模型需要 ~8x A100 80GB）
- 容易过拟合小数据集

### 参数高效微调（PEFT）
仅更新少量参数，大幅降低计算和内存成本：

#### LoRA（Low-Rank Adaptation）
最流行的 PEFT 方法，在权重矩阵旁边添加低秩分解：

$$W' = W + \Delta W = W + BA$$

其中 $B \in \mathbb{R}^{d \times r}$，$A \in \mathbb{R}^{r \times k}$，$r \ll \min(d, k)$。

**参数效率**：原始参数 7B → LoRA 可训练参数仅 ~10M（r=8）

#### QLoRA（Quantized LoRA）
- 将基础模型量化为 4-bit（NF4 格式）
- 在量化后的模型上应用 LoRA
- 70B 模型可在单张 48GB GPU 上微调
- Dettmers et al. 2023 年提出

#### 其他 PEFT 方法

| 方法 | 原理 | 参数效率 |
|------|------|---------|
| Prefix Tuning | 在输入前添加可训练前缀 | 极高 |
| Adapter | 在 Transformer 层间插入小型模块 | 高 |
| Prompt Tuning | 仅优化连续 prompt 向量 | 极高 |
| IA3 | 缩放激活值 | 极高 |
| DoRA | 分解 LoRA 的幅度和方向 | 高 |

## 微调数据

### 指令微调（Instruction Tuning）
- 格式：`(instruction, input, output)` 三元组
- 使模型遵循指令而非仅仅续写文本
- 代表数据集：Alpaca、ShareGPT、OpenAssistant

### 对话微调
- 多轮对话格式
- 包含系统提示（system prompt）和用户/助手交替
- 训练模型的对话能力

### RLHF 微调
- 先 SFT（监督微调），再 [[RLHF]] / [[DPO]] 优化
- 使模型更符合人类偏好

## 微调平台与工具

| 工具 | 特点 |
|------|------|
| Hugging Face TRL | 支持 SFT、DPO、RLHF |
| Axolotl | 简化微调配置 |
| LLaMA-Factory | 支持多种模型和方法 |
| Unsloth | 2x 微调加速，减少内存 |

## 实践建议

1. **优先尝试 LoRA**：性价比最高，通常能达到全参数微调 90%+ 的效果
2. **学习率**：LoRA 使用 1e-4 到 2e-4，全参数微调使用 1e-5 到 5e-5
3. **数据质量 > 数据数量**：1000 条高质量数据优于 10000 条低质量数据
4. **评估**：微调后在目标任务上评估，关注过拟合
5. **合并权重**：LoRA 权重可合并回原模型，推理时无额外开销

## 关键论文

- Hu et al., "LoRA: Low-Rank Adaptation of Large Language Models", ICLR 2022
- Dettmers et al., "QLoRA: Efficient Finetuning of Quantized Language Models", NeurIPS 2023
- Wei et al., "Finetuned Language Models Are Zero-Shot Learners" (Flan), ICLR 2022
