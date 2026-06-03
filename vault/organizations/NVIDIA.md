---
title: "NVIDIA"
aliases: ["英伟达", "NVDA"]
---

# NVIDIA

NVIDIA 是全球最有价值的半导体公司，由 [[Jensen Huang]] 于 1993 年创立。公司从游戏 GPU 起家，已成为 AI 计算的绝对霸主，市值一度突破 3 万亿美元。

## GPU 产品线

| 产品 | 发布年份 | 定位 | 关键特性 |
|------|---------|------|---------|
| A100 | 2020 | 数据中心旗舰 | 80GB HBM，312 TFLOPS FP16 |
| H100 | 2022 | AI 训练主力 | 80GB HBM3，989 TFLOPS FP16 |
| H200 | 2024 | H100 升级版 | 141GB HBM3e，带宽提升 |
| B200 | 2025 | Blackwell 架构 | 192GB HBM3e，第二代 Transformer Engine |
| GB200 | 2025 | 超级芯片 | Grace CPU + B200 GPU，NVLink 互连 |

## CUDA 生态

CUDA 是 NVIDIA 最深的护城河：
- 超过 400 万开发者
- 所有主流 AI 框架（PyTorch、TensorFlow、JAX）深度依赖 CUDA
- cuDNN、TensorRT、NCCL 等库构成完整 AI 计算栈
- 替代方案（ROCm、oneAPI）生态远未成熟

## AI 训练集群

全球最大的 AI 训练集群几乎都基于 NVIDIA GPU：
- [[OpenAI]] / [[Microsoft]]：数万张 H100 集群
- [[xAI]] Colossus：10 万张 H100
- [[Meta]]：超过 10 万张 A100/H100
- [[Google]]：TPU + GPU 混合集群

## 竞争与挑战

- **[[Google]] TPU**：自研芯片，内部使用为主
- **[[Amazon]] Trainium**：AWS 自研训练芯片
- **AMD MI300X**：性能接近 H100，但生态差距大
- **[[DeepSeek]] 效应**：高效训练可能降低 GPU 需求预期

## CEO

[[Jensen Huang]] 是硅谷任职时间最长的 CEO 之一，以标志性的黑色皮夹克和对 AI 的前瞻性押注闻名。在他的领导下，NVIDIA 从游戏公司转型为 AI 基础设施公司。
