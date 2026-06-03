---
title: "AI Safety"
aliases: ["AI 安全", "人工智能安全", "机器学习安全"]
---

# AI Safety

**AI 安全（AI Safety）**是研究如何确保人工智能系统按预期运行、避免产生危害的学科领域。随着大模型能力的快速增强，AI 安全已成为学术界和工业界最关注的研究方向之一。

## 研究分类

### 短期安全问题
- **[[Hallucination|幻觉]]**：模型生成不准确信息
- **有害内容**：生成暴力、歧视、违法内容
- **隐私泄露**：模型记忆并泄露训练数据中的个人信息
- **对抗攻击**：通过精心构造的输入绕过安全限制

### 长期安全问题
- **[[Alignment|对齐]]问题**：如何确保 AI 的目标与人类意图一致
- **能力失控**：超人类 AI 系统可能产生不可预见的行为
- **欺骗行为**：AI 系统学会隐藏真实能力或意图
- **权力集中**：少数实体垄断超强 AI 能力

## 主要研究方向

### 对齐研究（Alignment）
- [[RLHF]]：基于人类反馈的强化学习
- [[DPO]]：直接偏好优化
- [[Constitutional AI]]：[[Anthropic]] 提出的宪法 AI 方法
- 可扩展监督（Scalable Oversight）：如何监督比人类更聪明的系统

### 安全评估
- 红队测试（Red Teaming）：模拟攻击者评估模型漏洞
- 安全基准测试：标准化的安全评估框架
- 能力评估：评估模型的危险能力（如 CBRN 知识、网络攻击能力）

### 可解释性（Interpretability）
- 理解模型内部的决策机制
- 机械可解释性（Mechanistic Interpretability）：逐层分析神经网络
- [[Anthropic]] 在此方向投入大量研究资源

### 鲁棒性
- 对抗样本防御
- 分布外检测
- 不确定性量化

## 各公司的安全实践

### [[OpenAI]]
- 成立专门的 Safety 团队（经历多次重组）
- 准备框架（Preparedness Framework）评估模型风险等级
- 发布安全系统卡片（System Card）记录模型的安全特性
- 使用 RLHF 进行安全对齐

### [[Anthropic]]
- 以"安全优先"作为公司核心理念
- [[Constitutional AI]] 方法论
- 负责任扩展政策（Responsible Scaling Policy）
- AI 安全级别（ASL）分级框架
- 可解释性研究领先

### [[Google DeepMind]]
- DeepMind Safety Research 专门团队
- Scalable Oversight 研究
- Frontier Model Forum 成员

### [[Meta AI]]
- 开源模型安全策略（通过开放审查提升安全性）
- Llama Guard 安全分类器
- 红队测试和安全评估

## AI 安全级别框架

[[Anthropic]] 提出的 ASL（AI Safety Levels）框架：

| 级别 | 描述 | 要求 |
|------|------|------|
| ASL-1 | 无显著风险 | 标准安全措施 |
| ASL-2 | 与 2024 年模型相当 | 基础安全对齐 + 监控 |
| ASL-3 | 显著提升的危险能力 | 严格安全措施 + 限制部署 |
| ASL-4+ | 超人类风险能力 | 前所未有的安全级别 |

## 关键机构

- **MIRI（Machine Intelligence Research Institute）**：早期 AI 安全研究
- **Alignment Research Center（ARC）**：对齐评估
- **Center for AI Safety（CAIS）**：AI 安全公共倡导
- **Frontier Model Forum**：行业自律组织

## 关键论文

- Amodei et al., "Concrete Problems in AI Safety", 2016
- Hendrycks et al., "Unsolved Problems in ML Safety", 2022
- Anthropic, "Core Views on AI Safety", 2023
