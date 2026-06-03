# AI 模型知识图谱

> 2023-2026 大模型技术全景知识图谱 — 覆盖 35+ 模型、25+ 概念、15+ 组织、15+ 人物、15+ 基准、15+ 方法

[![GitHub Pages](https://img.shields.io/badge/GitHub-Pages-blue)](https://ghoulvspol.github.io/ai-models-knowledge-graph/site/)
[![Python 3](https://img.shields.io/badge/Python-3.x-green)](https://python.org)

## 这是什么

一个可漫游的 AI 模型知识图谱网站，把散落在各家官方博客、技术报告、研究论文、Hugging Face 模型卡中的 AI 模型信息，整理成一张可以漫游的知识网络。

覆盖 OpenAI、Anthropic、Google、Meta、阿里、DeepSeek 等主要厂商，从 2023 年 GPT-4 到 2026 年 GPT-5，跨越大模型黄金三年。

## 内容覆盖

| 分类 | 数量 | 说明 |
|------|------|------|
| 模型 | 35+ | GPT、Claude、Gemini、Llama、Qwen、DeepSeek、Mistral、Grok 等 |
| 概念 | 25+ | Transformer、Scaling Laws、MoE、RLHF、DPO、长上下文等 |
| 组织 | 15+ | OpenAI、Anthropic、Google DeepMind、Meta AI、DeepSeek 等 |
| 人物 | 15+ | Sam Altman、Dario Amodei、Ilya Sutskever、Yann LeCun 等 |
| 基准测试 | 15+ | MMLU、HumanEval、GPQA、Arena、SWE-bench 等 |
| 方法 | 15+ | RLHF、DPO、RAG、Fine-tuning、AI Agent 等 |

## 快速开始

### 本地构建

```bash
# 确保安装了依赖
pip install pyyaml markdown

# 构建网站
python3 build_ai_models.py

# 本地预览
cd site && python3 -m http.server 8080
```

### 在线访问

构建后的静态网站在 `site/` 目录，可直接部署到 GitHub Pages。

## 技术栈

- **数据源**：Obsidian 风格 Markdown（YAML frontmatter + wikilinks）
- **构建**：Python 3 + pyyaml + markdown
- **前端**：纯静态 HTML/CSS/JS（无框架依赖）
- **部署**：GitHub Pages

## 特性

- 双向链接：每个页面都有"链接到本页"反向链接面板
- 侧边栏导航：按分类折叠，支持移动端
- 引用计数：热门概念/模型/方法按引用次数排序
- 响应式布局：桌面/平板/手机自适应

## 目录结构

```
ai-models-knowledge-graph/
├── build_ai_models.py    # 构建脚本
├── vault/                # Markdown 源文件
│   ├── 欢迎.md           # 首页
│   ├── models/           # AI 模型
│   ├── concepts/         # 核心概念
│   ├── organizations/    # 核心组织
│   ├── people/           # 关键人物
│   ├── benchmarks/       # 基准测试
│   └── methods/          # 技术方法
├── site/                 # 生成的静态网站（git ignore）
├── assets/               # favicon 等资源
├── README.md
└── .gitignore
```

## License

MIT
