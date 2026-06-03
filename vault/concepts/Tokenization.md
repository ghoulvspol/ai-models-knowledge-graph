---
title: "Tokenization"
aliases: ["分词", "分词技术", "子词分词", "BPE", "WordPiece"]
---

# Tokenization

**分词（Tokenization）**是将原始文本转换为模型可处理的离散 token 序列的过程。分词方案直接影响模型的词汇表大小、多语言能力和推理效率。

## 主要分词算法

### BPE（Byte Pair Encoding）
- 最广泛使用的分词算法
- **原理**：从单字符开始，迭代合并最高频的相邻字符对
- **优点**：无 OOV（Out-of-Vocabulary）问题，开放词汇表
- **使用模型**：[[GPT-4o]]、[[GPT-4.1]]、[[Llama 4 Scout]]、[[DeepSeek V3]]

**训练过程**：
1. 将训练语料拆分为单字符
2. 统计所有相邻字符对的频率
3. 合并频率最高的字符对为新 token
4. 重复步骤 2-3 直到达到目标词汇表大小

### WordPiece
- Google 开发，用于 BERT
- 基于似然最大化选择合并操作（而非纯频率）
- 使用 `##` 前缀标记子词续接

### SentencePiece
- [[Google DeepMind]] 开发，语言无关的分词
- 直接在原始文本（含空格）上训练，无需预分词
- 支持 BPE 和 Unigram 两种子算法
- **使用模型**：[[Gemini 2.5 Pro]]、T5

### Byte-level BPE
- 在字节级别而非字符级别应用 BPE
- 能处理任意 Unicode 文本，无需 UNK token
- [[GPT-4o]] 和 [[DeepSeek V3]] 使用此方案

## 词汇表大小

| 模型 | 词汇表大小 | 分词方法 |
|------|-----------|---------|
| GPT-2 | 50,257 | Byte-level BPE |
| LLaMA | 32,000 | SentencePiece BPE |
| [[Llama 4 Scout]] | 128,000 | Byte-level BPE |
| [[GPT-4o]] | ~100,000 | Byte-level BPE |
| [[DeepSeek V3]] | 128,000+ | Byte-level BPE |
| [[Qwen 3]] | 151,643 | Byte-level BPE |

## Token 效率

不同分词方案对同一文本产生不同数量的 token：

- 英文：1 个 token ≈ 4 个字符 ≈ 0.75 个单词
- 中文：1 个汉字通常 = 1-2 个 token（取决于词汇表的中文覆盖）
- 代码：1 个 token ≈ 2-3 个字符（关键字和符号通常有专用 token）

更大的词汇表通常对非英语语言更友好，但增加了嵌入层的参数量。

## 多语言分词挑战

- **低资源语言**：词汇表中占比小，同一语义需要更多 token
- **中日韩（CJK）**：字符级别的压缩效率不如拉丁文
- **形态丰富语言**（如土耳其语、芬兰语）：一个词可能需要多个 token

[[Qwen 3]] 和 [[DeepSeek V3]] 等模型专门优化了中文分词效率。

## 分词对模型能力的影响

1. **数学能力**：数字的分词方式影响算术推理（如 "123" 是一个 token 还是三个）
2. **代码生成**：缩进和符号的分词影响代码质量
3. **多语言能力**：词汇表的语言覆盖决定跨语言性能
4. **推理效率**：token 数量直接影响推理成本和延迟

## 关键论文

- Sennrich et al., "Neural Machine Translation of Rare Words with Subword Units" (BPE), ACL 2016
- Kudo & Richardson, "SentencePiece: A simple and language independent subword tokenizer and detokenizer", EMNLP 2018
- Radford et al., "Language Models are Unsupervised Multitask Learners" (GPT-2 Byte-level BPE), 2019
