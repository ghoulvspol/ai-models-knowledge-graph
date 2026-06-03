---
title: "Foundation Model"
aliases: ["基础模型", "底座模型", "预训练大模型"]
---

# Foundation Model

**基础模型（Foundation Model）**是在大规模广泛数据上 [[Pre-training|预训练]] 的模型，能够适配各种下游任务。Bommasani et al. 2021 年在斯坦福 HAI 的报告中正式提出这一概念。

## 核心特征

### 规模（Scale）
- 参数量通常在数十亿到数千亿
- 训练数据量达数万亿 token
- 训练计算需要数千到数万 GPU

### 通用性（Generality）
- 单一模型可处理多种任务
- 通过 [[Prompt Engineering|提示]] 或 [[Fine-tuning|微调]] 适配不同场景
- 支持 [[Multimodal|多种模态]]

### 可适配性（Adaptability）
- [[Fine-tuning|微调]]：针对特定任务优化
- [[Prompt Engineering|提示工程]]：通过指令激活能力
- [[RAG]]：结合外部知识扩展能力
- [[AI Agent|Agent]]：作为智能体的核心推理引擎

## 代表性基础模型

### 闭源模型
| 模型 | 开发者 | 参数量 | 特点 |
|------|--------|--------|------|
| [[GPT-4o]] | [[OpenAI]] | 未公开 | 首个大规模商用多模态模型 |
| [[GPT-4.1]] | [[OpenAI]] | 未公开 | 1M 上下文，编码能力强 |
| [[o1]] | [[OpenAI]] | 未公开 | 推理模型先驱 |
| [[o3]] | [[OpenAI]] | 未公开 | 增强推理能力 |
| [[Claude 3.5 Sonnet]] | [[Anthropic]] | 未公开 | 安全对齐领先 |
| [[Claude Opus 4]] | [[Anthropic]] | 未公开 | 最强推理能力 |
| [[Gemini 2.5 Pro]] | [[Google DeepMind]] | 未公开 | 10M 上下文 |

### 开源模型
| 模型 | 开发者 | 参数量 | 特点 |
|------|--------|--------|------|
| [[Llama 4 Scout]] | [[Meta AI]] | 109B (17B 激活) | [[MoE]] 架构，10M 上下文 |
| [[DeepSeek V3]] | [[DeepSeek]] | 671B (37B 激活) | MoE，高性价比 |
| [[DeepSeek R1]] | [[DeepSeek]] | 671B (37B 激活) | 推理模型 |
| [[Qwen 3]] | 阿里 | 235B (22B 激活) | MoE，混合推理 |
| [[Phi-4]] | [[Microsoft]] | 14B | 小型高效 |
| [[Gemma 3]] | [[Google DeepMind]] | 27B | 开源多模态 |

## 技术栈

```
           ┌─────────────────────────┐
           │      应用层              │
           │  Chat / Agent / RAG     │
           ├─────────────────────────┤
           │     适配层               │
           │  Prompt / Fine-tune     │
           │  / RLHF / DPO          │
           ├─────────────────────────┤
           │    基础模型层             │
           │  Transformer / MoE      │
           ├─────────────────────────┤
           │     训练基础设施          │
           │  GPU 集群 / 分布式框架    │
           ├─────────────────────────┤
           │      数据层              │
           │  网页 / 书籍 / 代码      │
           └─────────────────────────┘
```

## 训练范式

1. **[[Pre-training]]**：在海量无标注数据上学习通用表示
2. **[[Post-training]]**：SFT + [[RLHF]]/[[DPO]] 进行对齐
3. **部署优化**：[[Quantization|量化]]、[[Inference|推理优化]]、[[Distillation|蒸馏]]

## 经济学

- 训练成本：GPT-4 估计 $100M+，Gemini Ultra 估计 $100M+
- 推理成本：每百万 token 价格从 $30（GPT-4 2023）降至 $0.07（DeepSeek V3 2025）
- 开源模型改变了定价格局，推动成本持续下降

## 关键论文

- Bommasani et al., "On the Opportunities and Risks of Foundation Models", 2021
- Brown et al., "Language Models are Few-Shot Learners" (GPT-3), NeurIPS 2020
- Touvron et al., "LLaMA: Open and Efficient Foundation Language Models", 2023
