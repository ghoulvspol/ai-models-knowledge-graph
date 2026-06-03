---
title: "HellaSwag"
aliases: ["hellaswag"]
---

# HellaSwag

HellaSwag 是评估大语言模型常识推理能力的评测基准，由 Zellers 等人于 2019 年提出。题目要求模型从四个选项中选择最合理的句子续写。

## 评测概述

- **题目数量**：约 10,000 道（验证集 10,042 题）
- **任务**：给定场景描述，选择最合理的续写
- **干扰项生成**：使用 Adversarial Filtering 生成高迷惑性干扰项
- **人类基线**：约 95.6%（机器最初仅 ~34%）

## 题目示例

给定：*"A man is sitting on a roof. He..."*

正确选项应该是常识上最合理的续写，而不是看似相关但逻辑不通的选项。

## 顶级模型表现（2025）

| 模型 | HellaSwag 得分 | 机构 |
|------|---------------|------|
| [[GPT-4o]] | ~95% | [[OpenAI]] |
| [[Claude Opus 4]] | ~95% | [[Anthropic]] |
| [[Gemini 2.5 Pro]] | ~95% | [[Google DeepMind]] |
| [[DeepSeek V3]] | ~94% | [[DeepSeek]] |

*注：顶级模型已接近人类水平，评测区分度下降*

## 技术特点

| 特性 | 说明 |
|------|------|
| Adversarial Filtering | 自动生成高迷惑性干扰项 |
| ActivityNet 数据 | 视频描述转文本，增加真实性 |
| 常识推理 | 测试日常场景的合理性判断 |
| 人类对比 | 提供人类基线对比 |

## 历史意义

HellaSwag 在 AI 评测历史上的重要地位：
- 2019 年提出时，最好模型仅约 34%，人类 95%
- 到 2024 年，顶级模型已超过 95%
- 见证了大语言模型常识推理能力的飞速提升
- 已被"解决"，区分度不足

## 局限性

- 选择题格式限制评估深度
- 顶级模型已接近人类水平，区分度下降
- 常识推理的评估范围有限
- 催生了更难的评测（如 [[WinoGrande]]、[[TruthfulQA]]）

## 学术引用

Zellers, R., et al. "HellaSwag: Can a Machine Really Finish Your Sentence?" ACL 2019. 引用量超过 3000 次。
