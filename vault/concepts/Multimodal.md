---
title: "Multimodal"
aliases: ["多模态", "多模态模型", "Multimodal Model"]
---

# Multimodal

**多模态（Multimodal）**指能够处理和生成多种数据类型（文本、图像、音频、视频）的 AI 模型。多模态能力已成为当代大模型的标准配置。

## 技术架构

### 视觉-语言模型

主流方案使用**视觉编码器 + 连接层 + [[Transformer]] 解码器**：

1. **视觉编码器**：通常使用 ViT（Vision Transformer）或 CLIP 视觉编码器处理图像
2. **连接层（Connector）**：将视觉 token 映射到语言模型的嵌入空间
   - 线性投影（LLaVA 方案）
   - Q-Former（BLIP-2 方案）
   - Perceiver Resampler（Flamingo 方案）
3. **语言模型**：处理融合后的多模态 token 序列

### 音频处理
- **Whisper 架构**：音频 → Mel 频谱图 → 编码器 → 文本
- **端到端方案**：直接将音频 token 输入语言模型（如 Gemini）

### 视频理解
- 采样关键帧 → 视觉编码 → 时间建模
- 主要挑战：长视频的时间推理和帧间关系建模

## 主流多模态模型

| 模型 | 文本 | 图像理解 | 图像生成 | 音频 | 视频 |
|------|------|---------|---------|------|------|
| [[GPT-4o]] | ✅ | ✅ | ✅（DALL-E） | ✅ | ✅ |
| [[Claude 3.5 Sonnet]] | ✅ | ✅ | ❌ | ❌ | ❌ |
| [[Gemini 2.5 Pro]] | ✅ | ✅ | ✅（Imagen） | ✅ | ✅ |
| [[Qwen 3]] | ✅ | ✅ | ❌ | ✅ | ✅ |
| [[DeepSeek V3]] | ✅ | ✅（VL 版） | ❌ | ❌ | ❌ |

## 关键技术突破

### CLIP（Contrastive Language-Image Pre-training）
- [[OpenAI]] 2021 年提出，通过对比学习连接文本和图像
- 建立了图像-文本的共享嵌入空间
- 成为后续多模态模型的视觉编码基础

### GPT-4V（2023）
- 首个大规模商用的多模态大模型
- 支持图像理解和视觉问答
- 推动了多模态能力的商业化应用

### GPT-4o 的原生多模态
- "o" 代表 "omni"，统一处理文本、音频、图像
- 音频理解延迟低至 232ms（接近人类对话反应速度）
- 摆弃了传统语音助手的级联架构（ASR → LLM → TTS）

## 应用场景

1. **文档理解**：OCR + 布局分析 + 语义理解
2. **视觉问答**：回答关于图像内容的问题
3. **代码生成**：从设计稿/截图生成代码
4. **医疗影像**：辅助诊断和报告生成
5. **自动驾驶**：多传感器融合理解和决策
6. **内容创作**：文本描述 → 图像/视频生成

## 技术挑战

- **模态对齐**：不同模态的语义空间如何有效对齐
- **幻觉问题**：多模态模型在视觉理解上容易产生 [[Hallucination|幻觉]]
- **计算成本**：处理高分辨率图像和长视频的计算需求巨大
- **评估困难**：缺乏统一的多模态评估基准

## 关键论文

- Radford et al., "Learning Transferable Visual Models From Natural Language Supervision" (CLIP), 2021
- Liu et al., "Visual Instruction Tuning" (LLaVA), NeurIPS 2023
- Alayrac et al., "Flamingo: a Visual Language Model for Few-Shot Learning", NeurIPS 2022
