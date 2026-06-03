---
title: "Pre-training"
aliases: ["预训练", "自监督预训练", "大规模预训练"]
---

# Pre-training

**预训练（Pre-training）**是在大规模无标注数据上训练 [[Foundation Model|基础模型]] 的过程。通过学习海量文本中的统计规律，模型获得通用的语言理解和生成能力，成为后续 [[Fine-tuning|微调]] 和 [[Post-training|后训练]] 的基础。

## 训练目标

### 因果语言建模（Causal Language Modeling）
所有自回归模型（[[GPT-4o]]、[[Claude 3.5 Sonnet]]、[[DeepSeek V3]]）使用的目标：

$$\mathcal{L}_{\text{CLM}} = -\sum_{t=1}^{T} \log P(x_t | x_1, \ldots, x_{t-1}; \theta)$$

模型学习预测序列中的下一个 token。

### 掩码语言建模（Masked Language Modeling）
BERT 系列使用的目标，随机掩码输入中的 token，让模型预测被掩码的内容。

### 填充目标（Fill-in-the-Middle）
部分模型（如 Code Llama）训练时加入中间填充能力，支持代码补全场景。

## 训练数据

### 数据来源
| 来源 | 规模 | 质量 | 代表数据集 |
|------|------|------|-----------|
| 网页爬取 | 数万亿 token | 参差不齐 | Common Crawl, C4 |
| 书籍 | 数千亿 token | 高 | Books3, Gutenberg |
| 代码 | 数千亿 token | 高 | GitHub, The Stack |
| 学术论文 | 数百亿 token | 很高 | arXiv, S2ORC |
| 百科 | 数百亿 token | 高 | Wikipedia |
| 对话 | 数百亿 token | 中等 | Reddit, StackOverflow |

### 数据处理流程
1. **去重**：MinHash、SimHash 等去除近似重复文档
2. **过滤**：去除低质量、有害、个人隐私内容
3. **质量评分**：使用分类器或启发式规则评估质量
4. **混合调配**：按比例混合不同来源的数据
5. **[[Tokenization|分词]]**：将文本转为 token 序列

### 数据规模

| 模型 | 训练 Token 数 | 数据来源多样性 |
|------|-------------|---------------|
| GPT-3 | 300B | 中等 |
| LLaMA | 1.4T | 高 |
| [[Llama 4 Scout]] | 30T+ | 非常高 |
| [[DeepSeek V3]] | 14.8T | 高 |
| [[Qwen 3]] | 36T+ | 非常高 |

## 训练基础设施

### 计算需求
- [[Scaling Laws|缩放定律]] 预测：$C \approx 6ND$（$N$ 为参数量，$D$ 为 token 数）
- [[DeepSeek V3]]（671B 参数，14.8T tokens）：约 $6 \times 671B \times 14.8T \approx 6 \times 10^{25}$ FLOPs
- 使用 2048 张 [[NVIDIA]] H800 GPU，训练约 2 个月

### 分布式训练
- **数据并行**：每个 GPU 处理不同的数据批次
- **张量并行**：将单层的矩阵运算切分到多个 GPU
- **流水线并行**：将不同层分配到不同 GPU
- **专家并行**：[[MoE]] 模型的专家分布在不同 GPU
- **FSDP / ZeRO**：优化器状态、梯度、参数的分布式存储

### 训练稳定性
- **Loss Spike**：训练损失突然飙升，需要回退到之前的检查点
- **梯度裁剪**：限制梯度范数防止爆炸
- **学习率调度**：Warmup + Cosine Decay
- [[DeepSeek V3]] 使用 FP8 训练降低计算成本约 40%

## 数据墙问题

高质量文本数据是否即将耗尽？

- 人类产生的高质量文本估计约 10-20T tokens
- 当前最大模型已接近这个规模
- **解决方案**：合成数据、多模态数据、数据增强、推理时数据

## 关键论文

- Kaplan et al., "Scaling Laws for Neural Language Models", 2020
- Hoffmann et al., "Training Compute-Optimal Large Language Models" (Chinchilla), 2022
- Touvron et al., "LLaMA: Open and Efficient Foundation Language Models", 2023
- DeepSeek-AI, "DeepSeek-V3 Technical Report", 2024
