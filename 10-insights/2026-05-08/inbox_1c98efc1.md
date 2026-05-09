---
id: inbox_1c98efc1
date: 2026-05-08
source_ref: "[[00-inbox/2026-05-08/0151-reddit-localllama-you-can-do-cuda-inference-on-an-apple-si-6ad2]]"
title: "You can do CUDA inference on an Apple Silicon Mac with PCI Passthrough"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t7cqg9/you_can_do_cuda_inference_on_an_apple_silicon_mac/
source: reddit-localllama
published_at: 2026-05-08T16:20:42+00:00
fetched_at: 2026-05-09T02:26:09.325370+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "用户改编QEMU实现在Apple Silicon Mac上通过GPU PCI Passthrough运行Linux VM以执行CUDA推理。项目重点探讨虚拟化GPU穿透的技术挑战，并提供游戏和AI推理的性能基准数据。这为本地模型推理提供了在Apple硬件上的另一条技术路径。"
key_points:
  - "通过QEMU + PCI Passthrough在Apple Silicon macOS中虚拟化CUDA执行环境"
  - "包含游戏和AI推理的性能benchmark，量化GPU通过虚拟化的实际成本"
  - "技术方案解决了Apple Silicon原生不支持CUDA的限制"
tags: [cuda-inference, apple-silicon, gpu-passthrough, qemu, virtualization]
topics: []
importance: 3
novelty: 4
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## You can do CUDA inference on an Apple Silicon Mac with PCI Passthrough

用户改编QEMU实现在Apple Silicon Mac上通过GPU PCI Passthrough运行Linux VM以执行CUDA推理。项目重点探讨虚拟化GPU穿透的技术挑战，并提供游戏和AI推理的性能基准数据。这为本地模型推理提供了在Apple硬件上的另一条技术路径。

### 重點
- 通过QEMU + PCI Passthrough在Apple Silicon macOS中虚拟化CUDA执行环境
- 包含游戏和AI推理的性能benchmark，量化GPU通过虚拟化的实际成本
- 技术方案解决了Apple Silicon原生不支持CUDA的限制

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t7cqg9/you_can_do_cuda_inference_on_an_apple_silicon_mac/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I have been working on a project to adapt QEMU, running on macOS, to support passing through a GPU into a Linux VM. I wrote this post walking through some of the interesting challenges there, along with benchmarks. The post focuses a lot on gaming, but there are AI benchmarks there as well. &#32; submitted by &#32; /u/scottjgo [link] &#32; [comments]

</details>