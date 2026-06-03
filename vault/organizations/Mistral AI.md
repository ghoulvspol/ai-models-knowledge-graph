---
title: "Mistral AI"
aliases: ["Mistral", "mistral"]
---

# Mistral AI

Mistral AI 是法国 AI 创业公司，由前 [[Meta AI]] 和 [[Google DeepMind]] 研究员于 2023 年创立。公司采用开源与商用并行的"双轨"策略，是欧洲最具影响力的大模型公司。

## 创始团队

- **Arthur Mensch**：CEO，前 DeepMind 研究员
- **Timothée Lacroix**：CTO，前 Meta AI
- **Guillaume Lample**：首席科学家，前 Meta AI，LLaMA 核心作者

## 模型系列

| 模型 | 类型 | 参数规模 | 特点 |
|------|------|---------|------|
| Mistral 7B | 开源 | 7.3B | 滑动窗口注意力，性能超 Llama 2 13B |
| Mixtral 8x7B | 开源 | 46.7B（12.9B 激活） | [[MoE]] 架构，性能超 GPT-3.5 |
| Mixtral 8x22B | 开源 | 176B（39B 激活） | 多语言，64K 上下文 |
| [[Mistral Large 2]] | 商用 | 123B | 多语言，128K 上下文 |
| Mistral Medium | 商用 | 未公开 | 性价比最优 |
| Codestral | 开源 | 22B | 代码专用模型 |

## 技术特色

- **滑动窗口注意力（Sliding Window Attention）**：降低长序列计算复杂度
- **[[MoE]] 架构**：Mixtral 系列验证了 MoE 的高效性
- **分组查询注意力（GQA）**：优化推理效率
- **高效推理**：模型在推理速度和质量之间取得良好平衡

## 商业模式

- **Le Chat**：面向消费者的 AI 助手产品
- **La Plateforme**：企业级 API 服务
- **Mistral on Azure / AWS / GCP**：多云部署
- **开源社区**：模型在 HuggingFace 上开放下载

## 融资与估值

- 2023 年种子轮：1.13 亿美元（欧洲 AI 最大种子轮）
- 2024 年 B 轮：6 亿美元，估值 20 亿欧元
- 投资者包括 [[Microsoft]]、a]16z、光速资本等

## 战略意义

Mistral AI 是欧洲 AI 主权的重要支撑，被视为"欧洲的 [[OpenAI]]"。公司的发展证明了欧洲在全球 AI 竞争中的潜力。
