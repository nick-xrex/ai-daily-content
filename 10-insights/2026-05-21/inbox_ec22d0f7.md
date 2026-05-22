---
id: inbox_ec22d0f7
date: 2026-05-21
source_ref: "[[00-inbox/.../inbox_ec22d0f7]]"
title: "What’s Actually Running When You Run an LLM Locally?"
url: https://medium.com/@rraushan24/whats-actually-running-when-you-run-an-llm-locally-27f673250be2?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-05-21T13:21:22+00:00
fetched_at: 2026-05-22T01:03:03.748669+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "深入 GPU 層級分析本地 LLM 運行時（Ollama、llama.cpp、MLX）。llama.cpp 是基礎，由 Georgi Gerganov 用 C/C++ 編寫，透過量化和 CPU/GPU 卸載實現消費級硬體上的高效推理，支援 Apple Metal、NVIDIA CUDA。Ollama 基於 llama.cpp 但加入容器包裝和管理層。LM Studio、MLX 各有不同定位。作者在 M2 MacBook Pro（32GB）上實測比較，避免雲端抽象，直接測量金屬層、記憶體和效能數據。"
key_points:
  - "llama.cpp（C/C++、by Georgi Gerganov）是推理基礎；透過量化和 CPU/GPU 卸載達成消費級效率；支援 Metal API（Apple）、CUDA（NVIDIA）、CPU 運行"
  - "本地 LLM 生態中 Ollama、LM Studio、llama.cpp、MLX 外觀相似但架構與目標不同；需實測 GPU 行為而非僅看標籤宣傳"
  - "透過推理工程書籍實驗驗證，在單機（M2）上測量實際令牌吞吐量、記憶體使用、CPU/GPU 分布"
tags: [local-llm, ollama, llama-cpp, mlx, inference-engineering]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## What’s Actually Running When You Run an LLM Locally?

深入 GPU 層級分析本地 LLM 運行時（Ollama、llama.cpp、MLX）。llama.cpp 是基礎，由 Georgi Gerganov 用 C/C++ 編寫，透過量化和 CPU/GPU 卸載實現消費級硬體上的高效推理，支援 Apple Metal、NVIDIA CUDA。Ollama 基於 llama.cpp 但加入容器包裝和管理層。LM Studio、MLX 各有不同定位。作者在 M2 MacBook Pro（32GB）上實測比較，避免雲端抽象，直接測量金屬層、記憶體和效能數據。

### 重點
- llama.cpp（C/C++、by Georgi Gerganov）是推理基礎；透過量化和 CPU/GPU 卸載達成消費級效率；支援 Metal API（Apple）、CUDA（NVIDIA）、CPU 運行
- 本地 LLM 生態中 Ollama、LM Studio、llama.cpp、MLX 外觀相似但架構與目標不同；需實測 GPU 行為而非僅看標籤宣傳
- 透過推理工程書籍實驗驗證，在單機（M2）上測量實際令牌吞吐量、記憶體使用、CPU/GPU 分布

**原文：** [medium-tag-llm](https://medium.com/@rraushan24/whats-actually-running-when-you-run-an-llm-locally-27f673250be2?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

---large_language_models-5"
author: "Rakesh Raushan"
published_at: 2026-05-21T13:21:22+00:00
fetched_at: 2026-05-21T18:28:33.062229+00:00
content_hash: "0336b9a9a5a7abbb0d4c11eff18a6a7fa02a0248b6b0f89fe6240741e76de5f3"
lang: en
caption_quality: None
raw: true
topics: []
---

# What’s Actually Running When You Run an LLM Locally?

A GPU-level look at Ollama, llama.cpp, and MLX on Apple Silicon Continue reading on Medium »

</details>