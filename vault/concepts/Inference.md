---
title: "Inference"
aliases: ["推理", "模型推理", "推理优化", "LLM 推理"]
---

# Inference

**推理（Inference）**指使用训练好的模型对新输入生成输出的过程。对于大语言模型，推理优化是降低服务成本、提升用户体验的关键技术。

## 自回归生成原理

大语言模型采用**自回归（Autoregressive）**方式逐 token 生成：

$$P(y_1, y_2, \ldots, y_T | x) = \prod_{t=1}^{T} P(y_t | x, y_1, \ldots, y_{t-1})$$

每生成一个 token 都需要完整的前向传播，这使得推理效率成为核心瓶颈。

## Prefill 与 Decode 阶段

| 阶段 | 操作 | 特点 | 瓶颈 |
|------|------|------|------|
| Prefill | 处理输入 prompt | 并行计算 | 计算密集（Compute-bound） |
| Decode | 逐 token 生成 | 顺序计算 | 内存带宽密集（Memory-bound） |

## 核心优化技术

### KV Cache
- 缓存已计算的 Key 和 Value 向量，避免重复计算
- 将 Decode 阶段的计算从 $O(n^2)$ 降至 $O(n)$
- 内存占用随序列长度线性增长
- 是所有现代推理框架的标配

### 投机解码（Speculative Decoding）
- 使用小型"草稿模型"快速生成多个候选 token
- 大模型一次性验证所有候选 token
- 被接受的 token 直接使用，被拒绝的从该位置重新生成
- 可实现 2-3x 加速，且输出分布与原始模型完全一致

### 批处理优化

**连续批处理（Continuous Batching）**
- 不等一个 batch 全部生成完毕，随时插入新请求
- 显著提升 GPU 利用率
- vLLM 首创，现已成为标准

**PagedAttention**
- 类似操作系统虚拟内存的 KV Cache 管理
- 避免内存碎片，提升内存利用率
- vLLM 的核心创新

### 量化推理
- 使用 [[Quantization|量化]]（INT8/INT4）减少内存占用和计算量
- FP8 推理：[[NVIDIA]] H100 原生支持
- 详见 [[Quantization]]

### 模型并行
- **张量并行（Tensor Parallelism）**：将单层的权重矩阵切分到多个 GPU
- **流水线并行（Pipeline Parallelism）**：将不同层分配到不同 GPU
- **序列并行（Sequence Parallelism）**：将序列维度切分

## 主流推理框架

| 框架 | 特点 | 适用场景 |
|------|------|---------|
| vLLM | PagedAttention，连续批处理 | 高吞吐量服务 |
| TensorRT-LLM | [[NVIDIA]] 官方优化 | 最大化 GPU 性能 |
| TGI | Hugging Face 出品 | 快速部署 |
| llama.cpp | CPU 推理，GGUF 量化 | 消费级硬件 |
| SGLang | 结构化生成优化 | 复杂推理场景 |
| Ollama | 本地一键部署 | 个人使用 |

## 推理成本

模型推理成本持续下降：

| 时间 | 模型 | 价格（$/M tokens） |
|------|------|-------------------|
| 2023.03 | GPT-4 | $30/$60 (input/output) |
| 2024.05 | GPT-4o | $5/$15 |
| 2025.01 | [[DeepSeek V3]] | $0.27/$1.10 |
| 2025.04 | [[GPT-4.1]] | $2/$8 |

## 优化指标

- **TTFT（Time to First Token）**：首 token 延迟，影响用户感知
- **TPS（Tokens per Second）**：生成速度，影响阅读体验
- **Throughput**：每秒处理的总 token 数，影响服务成本
- **Context Length**：支持的最大上下文长度

## 关键论文

- Kwon et al., "Efficient Memory Management for Large Language Model Serving with PagedAttention", SOSP 2023
- Leviathan et al., "Fast Inference from Transformers via Speculative Decoding", ICML 2023
- Leviathan et al., "DRAFT & VERIFY: Lossless Large Language Model Acceleration via Self-Speculative Decoding", 2023
