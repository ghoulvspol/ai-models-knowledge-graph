---
title: "Pre-training"
aliases: ["预训练", "pretraining"]
---

# Pre-training

Pre-training（预训练）是在大规模无标注数据上训练基础语言模型的过程。它是所有大语言模型的第一步，赋予模型通用的语言理解和生成能力。

## 预训练范式

### 自回归预训练（Autoregressive）

- 从左到右预测下一个 token
- 代表：GPT 系列（[[OpenAI]]）、Llama（[[Meta AI]]）
- 训练目标：最大化下一个 token 的概率
- 适合生成任务

### 掩码语言模型（MLM）

- 随机遮盖部分 token，预测被遮盖的内容
- 代表：BERT（[[Google]]）
- 训练目标：理解上下文关系
- 适合理解任务

### 编码器-解码器

- 编码器处理输入，解码器生成输出
- 代表：T5（[[Google]]）、BART
- 适合序列到序列任务

## 训练数据

| 数据集 | 规模 | 来源 |
|--------|------|------|
| Common Crawl | PB 级 | 网页抓取 |
| RedPajama | ~1.2T tokens | 多源混合 |
| FineWeb | ~15T tokens | HuggingFace |
| DCLM | 数万亿 tokens | 数据过滤 |

## 训练基础设施

大规模预训练需要：
- **GPU 集群**：数千到数万张 [[NVIDIA]] GPU
- **分布式训练**：数据并行、模型并行、流水线并行
- **训练框架**：Megatron-LM、DeepSpeed、FSDP
- **成本**：GPT-4 预训练估计成本约 1 亿美元

## Scaling Laws（[[Scaling Laws]]）

预训练的核心规律：
- 模型性能与参数量、数据量、计算量呈幂律关系
- 最优训练策略：Chinchilla 比例（参数:数据 ≈ 1:20）
- [[DeepSeek V3]] 挑战了传统 Scaling Laws，以更低成本达到高性能

## 预训练的未来

- **数据墙**：高质量文本数据即将耗尽
- **合成数据**：使用 AI 生成训练数据
- **多模态预训练**：文本、图像、音频、视频联合训练
- **高效训练**：[[DeepSeek]] 证明的低成本训练路径

## 关键人物

- [[Alec Radford]]：GPT 预训练范式的建立者
- [[Ilya Sutskever]]：推动"规模即智能"的研究方向
- [[Ashish Vaswani]]：[[Transformer]] 架构的发明者
