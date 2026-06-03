---
title: "Quantization"
aliases: ["量化", "模型量化", "权重量化"]
---

# Quantization

**量化（Quantization）**是降低模型参数数值精度的技术，将浮点数（FP32/FP16）转换为低精度表示（INT8/INT4），以减少内存占用和加速推理，同时尽量保持模型质量。

## 基本原理

将高精度浮点数映射到低精度整数：

$$q = \text{round}\left(\frac{x}{s}\right) + z$$

其中 $s$ 是缩放因子（scale），$z$ 是零点偏移（zero-point），$q$ 是量化后的整数值。

### 对称量化 vs 非对称量化

- **对称量化**：零点 $z = 0$，范围关于零对称
- **非对称量化**：零点 $z \neq 0$，适应非对称分布

## 量化粒度

| 粒度 | 描述 | 精度 | 开销 |
|------|------|------|------|
| Per-tensor | 整个张量共享一组参数 | 最低 | 最小 |
| Per-channel | 每个输出通道一组参数 | 中等 | 中等 |
| Per-group | 每 g 个元素一组参数（如 g=128） | 高 | 较小 |
| Per-token | 每个 token 动态量化 | 最高 | 较大 |

## 主流量化方法

### PTQ（Post-Training Quantization）
训练后量化，无需重新训练：

**GPTQ（2022）**
- 基于近似二阶信息的逐层量化
- 将权重量化到 INT4/INT3
- 需要少量校准数据（128 条即可）
- 适用于 GPU 推理

**AWQ（Activation-aware Weight Quantization）**
- 识别对输出影响最大的权重通道，对其保持更高精度
- INT4 量化下质量优于 GPTQ
- [[NVIDIA]] 研究团队提出

**GGUF/GGML**
- llama.cpp 项目使用的量化格式
- 支持 CPU 推理，适合消费级设备
- 提供 Q2 到 Q8 多种精度选择

### QAT（Quantization-Aware Training）
训练中模拟量化效果，精度更高但需要训练资源。

### FP8 训练
- [[DeepSeek V3]] 使用 FP8 训练，节省约 40% 计算成本
- [[NVIDIA]] H100 原生支持 FP8 运算
- 成为大规模训练的新标准

## 精度与性能对比

| 精度 | 内存（70B 模型） | 速度提升 | 质量损失 |
|------|-----------------|---------|---------|
| FP16 | ~140 GB | 基准 | 无 |
| INT8 | ~70 GB | 1.5-2x | 极小 |
| INT4 | ~35 GB | 2-3x | 轻微 |
| INT3 | ~26 GB | 2-3x | 明显 |
| INT2 | ~18 GB | 3-4x | 显著 |

## INT4 量化实例

以 [[Llama 4 Scout]]（109B）为例：
- FP16：~218 GB → 需要多张 A100
- INT4：~55 GB → 单张 A100 80GB 可运行
- Q4_K_M（GGUF）：~60 GB → 高端消费级 GPU（RTX 4090 24GB + 系统内存）可运行

## 实践建议

1. **优先使用 INT8**：质量损失极小，速度提升明显
2. **INT4 需要评估**：在目标任务上测试质量下降程度
3. **GPTQ 适合 GPU**：AWQ 在某些场景质量更好
4. **GGUF 适合 CPU/边缘设备**：灵活的精度选择
5. **FP8 训练**：大规模训练的新趋势

## 关键论文

- Frantar et al., "GPTQ: Accurate Post-Training Quantization for Generative Pre-trained Transformers", ICLR 2023
- Lin et al., "AWQ: Activation-aware Weight Quantization for LLM Compression and Acceleration", MLSys 2024
- Dettmers et al., "LLM.int8(): 8-bit Matrix Multiplication for Transformers at Scale", NeurIPS 2022
