---
title: "Hallucination"
aliases: ["幻觉", "模型幻觉", "AI 幻觉", "LLM Hallucination"]
---

# Hallucination

**幻觉（Hallucination）**指大语言模型生成看似合理但实际上不准确、无依据或完全虚构的内容。这是当前 AI 系统最核心的可靠性挑战之一。

## 幻觉类型

### 事实性幻觉（Factual Hallucination）
- **内在矛盾**：生成与已知事实冲突的内容
- **虚构信息**：编造不存在的引用、人物、事件
- **数据错误**：给出错误的数字、日期、统计

### 忠实性幻觉（Faithfulness Hallucination）
- 生成与输入上下文不一致的内容
- 摘要时添加原文没有的信息
- 翻译时引入原文不存在的语义

### 推理幻觉（Reasoning Hallucination）
- 推理过程中的逻辑跳跃
- [[Chain of Thought|思维链]] 中的错误步骤
- 数学计算中的错误结果

## 产生原因

1. **训练数据**：数据中的错误信息被学习和放大
2. **解码策略**：采样温度过高增加随机性
3. **知识截止**：训练数据有时间截止，无法反映最新信息
4. **能力边界**：模型对不确定的知识仍倾向于给出自信的回答
5. **训练目标**：语言模型本质上学习的是"下一个最可能的 token"，而非"正确的事实"

## 缓解方法

### 检索增强（RAG）
- 使用 [[RAG]] 将外部知识库的检索结果注入模型上下文
- 为生成提供事实依据，减少编造
- 局限：检索结果本身可能有误

### 思维链推理
- [[Chain of Thought]] 让模型逐步推理，减少一步到位的错误
- [[DeepSeek R1]]、[[o1]] 等推理模型在数学和逻辑任务上幻觉率更低

### 不确定性校准
- 训练模型识别自身的不确定性
- 在不确定时主动说"我不确定"
- [[Anthropic]] 的 Claude 系列在这方面做得相对较好

### 事实验证
- 生成后再用另一个模型或工具验证
- 交叉引用多个来源
- 使用自动化事实检查工具

### RLHF 对齐
- 通过 [[RLHF]] 训练模型避免编造
- 将"诚实性"作为对齐目标之一
- [[AI Safety|安全]] 研究中的"诚实 AI"方向

## 评估基准

| 基准 | 评估内容 | 特点 |
|------|---------|------|
| TruthfulQA | 常见误解场景 | 测试模型是否重复流行谬误 |
| FActScore | 生成文本的事实密度 | 逐句验证事实准确性 |
| HaluEval | 多种幻觉类型 | 覆盖 QA、对话、摘要场景 |
| SimpleQA | 简单事实查询 | [[OpenAI]] 发布，测试基础事实能力 |

## 不同模型的表现

- [[GPT-4o]]、[[Claude 3.5 Sonnet]] 等顶级模型幻觉率已显著降低，但远未消除
- [[DeepSeek R1]] 的推理链在数学任务上减少幻觉，但在开放问答中仍存在
- 小模型（如 [[Phi-4]]、[[Gemma 3]]）通常幻觉率更高
- [[RAG]] 架构可将幻觉率降低 30-50%（取决于检索质量）

## 关键论文

- Ji et al., "Survey of Hallucination in Natural Language Generation", ACM Computing Surveys, 2023
- Lin et al., "TruthfulQA: Measuring How Models Mimic Human Falsehoods", ACL 2022
- Min et al., "FActScore: Fine-grained Atomic Evaluation of Factual Precision", ACL 2023
