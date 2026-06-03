---
title: "Anthropic"
aliases: ["anthropic"]
---

# Anthropic

Anthropic 是一家专注于 [[AI Safety]] 的人工智能公司，由 [[Dario Amodei]]（CEO）和 [[Daniela Amodei]]（总裁）于 2021 年创立。公司总部位于旧金山，员工超过 1000 人。

## 创始背景

核心团队来自 [[OpenAI]]，包括前研究副总裁 Dario Amodei、[[Jan Leike]]、[[Chris Olah]] 等。离开原因是对 OpenAI 安全研究优先级的分歧。公司获得了 [[Google]]、[[Amazon]]（累计投资 80 亿美元）等支持。

## Claude 模型系列

- **Claude 1**（2023.3）：首个商用模型
- **Claude 2**（2023.7）：更长上下文，改进安全性
- **Claude 3**（2024.3）：Haiku/Sonnet/Opus 三级体系
- **[[Claude Opus 4]]**（2025）：旗舰推理模型
- **Claude Sonnet 4**（2025）：性价比最优模型

## 核心技术

### Constitutional AI（[[Constitutional AI]]）

Anthropic 的标志性对齐方法，通过一组"宪法原则"指导模型行为，减少对人类标注的依赖。该方法结合 [[RLHF]] 和 [[DPO]] 的思想，让 AI 自我批评和修正。

### 可解释性研究

[[Chris Olah]] 领导的团队在神经网络可解释性方面取得突破，包括：
- 特征方向（Feature Directions）研究
- 稀疏自编码器用于模型解释
- 电路级分析（Circuits-level analysis）

## 商业模式

- **API 优先**：通过 Claude API 向企业提供服务
- **Claude Pro**：面向消费者的订阅服务
- **Amazon Bedrock**：通过 AWS 分发 Claude 模型
- **[[Google]] Cloud**：通过 Vertex AI 提供服务

## 竞争定位

Anthropic 以"安全优先"为品牌差异化，在企业级市场与 [[OpenAI]] 竞争。Claude 系列在长上下文处理（200K tokens）、代码生成、指令遵循等方面表现优异，在 [[Arena]] 排名中持续位居前列。
