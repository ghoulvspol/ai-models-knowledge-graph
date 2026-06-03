---
title: "DeepSeek"
aliases: ["深度求索", "DeepSeek AI"]
---

# DeepSeek

DeepSeek（深度求索）是中国 AI 研究公司，由量化基金幻方量化（High-Flyer）于 2023 年创立。公司以极高的训练效率和开源策略震惊全球 AI 行业，被称为"AI 界的拼多多"。

## 核心模型

### DeepSeek V3

- 671B 参数 [[MoE]] 架构，激活参数仅 37B
- 在 [[MMLU]]、[[HumanEval]] 等主流评测中接近 [[GPT-4o]] 水平
- 训练成本仅约 550 万美元（对比 GPT-4 的 1 亿美元+）
- 采用 Multi-head Latent Attention（MLA）和 DeepSeekMoE 架构创新

### DeepSeek R1

- 专注推理能力的模型，在 [[MATH]]、[[Codeforces]] 等评测中表现突出
- 采用纯 [[RLHF]]（强化学习）训练推理能力，无需监督微调
- 开源了模型权重和训练方法，推动推理模型民主化
- 在 [[Arena]] 排名中位居前列

## 技术创新

| 创新 | 说明 |
|------|------|
| MLA 注意力机制 | 降低 KV Cache 显存占用，提升推理效率 |
| DeepSeekMoE | 更细粒度的专家划分和负载均衡策略 |
| FP8 训练 | 业界首批大规模 FP8 混合精度训练 |
| 多 token 预测 | 同时预测多个未来 token，提升训练效率 |
| GRPO | Group Relative Policy Optimization，简化 [[RLHF]] 流程 |

## 行业影响

DeepSeek 的出现对全球 AI 产业格局产生重大冲击：
- **算力叙事重塑**：证明高效算法可大幅降低对 [[NVIDIA]] 高端 GPU 的依赖
- **开源冲击**：对 [[OpenAI]] 等闭源商业模式形成挑战
- **中国 AI 信心**：证明中国团队在前沿 AI 研究中的竞争力
- **训练效率范式**：推动行业从"堆算力"转向"拼效率"

## 创始人

梁文锋，幻方量化创始人，浙江大学信号处理专业背景。幻方量化管理资产超百亿元人民币，拥有约 1 万张 [[NVIDIA]] A100/H800 GPU 集群。
