---
title: "Distillation"
aliases: ["知识蒸馏", "模型蒸馏", "Teacher-Student", "Knowledge Distillation"]
---

# Distillation

**知识蒸馏（Knowledge Distillation）**是一种模型压缩技术，将大型"教师模型"的知识转移到小型"学生模型"中，使学生模型以更少的参数达到接近教师模型的性能。

## 核心原理

教师模型的 softmax 输出包含丰富的"暗知识"（dark knowledge）——不同类别之间的相对关系：

$$\mathcal{L}_{\text{KD}} = \alpha \cdot \mathcal{L}_{\text{CE}}(y, \hat{y}_s) + (1-\alpha) \cdot T^2 \cdot D_{\text{KL}}\left(\frac{\hat{y}_t}{T} \| \frac{\hat{y}_s}{T}\right)$$

其中 $T$ 是温度参数（temperature），$\hat{y}_t$ 和 $\hat{y}_s$ 分别是教师和学生的输出。

**温度的作用**：$T > 1$ 使 softmax 输出更平滑，暴露更多类别间的相对信息。

## 蒸馏方法分类

### Logit 蒸馏（Output-based）
- 学生模型学习匹配教师的输出分布
- 最经典的方法，Hinton et al. 2015 年提出
- 适用于分类和生成任务

### 特征蒸馏（Feature-based）
- 学生模型学习匹配教师的中间层表示
- FitNets、Attention Transfer 等方法
- 需要设计层间映射关系

### 在线蒸馏（Online Distillation）
- 教师和学生同时训练，互相学习
- Deep Mutual Learning 等方法
- 无需预训练好的教师模型

## 在大语言模型中的应用

### 模型压缩
- **Alpaca**：Stanford 从 GPT-3.5 的输出蒸馏训练 LLaMA-7B
- **Vicuna**：从 ShareGPT 对话数据（含 GPT-4 输出）蒸馏
- **Orca**：从 GPT-4 蒸馏推理过程（不仅学答案，还学推理链）

### 能力特化蒸馏
- [[DeepSeek R1]] 的蒸馏实践：将 671B 的推理能力蒸馏到 1.5B-70B 的密集模型
  - DeepSeek-R1-Distill-Qwen-32B：在数学和编程上接近 GPT-4o 级别
  - 蒸馏后的模型继承了长链 [[Chain of Thought|推理]] 能力
- [[Qwen 3]]：从大模型蒸馏到多种尺寸的小模型

### 推理能力蒸馏
- 将大模型的 [[Chain of Thought]] 推理链作为训练数据
- 学生模型不仅学习最终答案，还学习推理过程
- [[DeepSeek R1]] 证明纯蒸馏可以有效传递推理能力

## 蒸馏 vs 其他压缩方法

| 方法 | 原理 | 优势 | 劣势 |
|------|------|------|------|
| 知识蒸馏 | 学习教师输出 | 保持任务性能 | 需要教师模型 |
| [[Fine-tuning\|微调]] | 在特定数据上训练 | 定制化能力强 | 不压缩模型 |
| [[Quantization\|量化]] | 降低数值精度 | 无损或微损 | 精度有限 |
| 剪枝 | 移除不重要的参数 | 直接减少参数 | 可能破坏结构 |

## 法律与伦理问题

- 使用商业模型（如 GPT-4）的输出训练竞品模型是否合法？
- [[OpenAI]] 服务条款禁止使用其输出训练竞品模型
- 开源社区广泛使用蒸馏，但存在灰色地带
- [[DeepSeek]] 被质疑是否使用了 GPT-4 的输出进行蒸馏

## 关键论文

- Hinton et al., "Distilling the Knowledge in a Neural Network", 2015
- Taori et al., "Stanford Alpaca: An Instruction-following LLaMA Model", 2023
- Mukherjee et al., "Orca: Progressive Learning from Complex Explanation Traces of GPT-4", 2023
- DeepSeek-AI, "DeepSeek-R1 Technical Report", 2025
