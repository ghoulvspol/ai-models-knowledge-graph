---
title: "ARC-AGI"
aliases: ["ARC", "Abstraction and Reasoning Corpus"]
---

# ARC-AGI

ARC-AGI（Abstraction and Reasoning Corpus for Artificial General Intelligence）是由 [[François Chollet]]（Keras 创始人）于 2019 年设计的抽象推理评测，旨在测试 AI 系统的通用智能。

## 设计理念

ARC-AGI 的核心理念与其他评测根本不同：
- **不是记忆测试**：每道题都是全新的模式
- **不是规模测试**：更大模型不自动获得更好表现
- **测试核心智能**：从少量示例中归纳规则并应用
- **人类基线**：人类可以轻松解决大部分题目，但 AI 系统长期表现不佳

## 评测设计

- **题目数量**：400 道（公开评估集 100 题）
- **格式**：输入-输出网格变换
- **任务**：从 2-3 个输入-输出示例中归纳规则，应用到新输入
- **评估**：精确匹配输出网格

## 顶级表现（2025）

| 系统 | ARC-AGI-1 得分 | 方法 |
|------|---------------|------|
| OpenAI o3 (high) | ~88% | 推理 + 搜索 |
| ARC Prize 2024 冠军 | ~55% | 专用程序合成 |
| [[GPT-4o]] | ~5% | 纯语言模型 |
| 人类基线 | ~85% | 从少量示例推理 |

## ARC-AGI-2

2025 年推出的新版本，难度大幅提升：
- 更复杂的模式和变换
- 推理模型（如 o3）的得分也显著下降
- 继续挑战 AI 系统的极限

## 意义

ARC-AGI 的独特价值在于：
- **智力测试**：被认为是衡量 AI "真正智能"的基准
- **规模定律的反例**：更大模型不一定更擅长 ARC-AGI
- **推动新方法**：催生了程序合成、[[Chain of Thought]] 等新方向
- **François Chollet** 的智能定义：高效获取新技能的能力

## 行业影响

ARC-AGI 挑战了"规模即智能"的观点：
- [[OpenAI]] o3 的高分是 2024 年 AI 领域的重大突破
- 推动了对 AI 推理能力本质的讨论
- ARC Prize 基金会提供百万美元奖金激励研究

## 学术引用

Chollet, F. "On the Measure of Intelligence." arXiv 2019. 引用量超过 2000 次。
