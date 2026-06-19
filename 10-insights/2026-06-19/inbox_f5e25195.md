---
id: inbox_f5e25195
date: 2026-06-19
source_ref: "[[00-inbox/2026-06-19/2200-medium-towards-data-science-gpu-resident-top-k-for-agentic-rag-i-bui-598a]]"
title: "GPU-Resident Top-K for Agentic RAG: I Built a CUDA Kernel So My Retrieval Step Would Stop Bouncing Off the GPU"
url: https://towardsdatascience.com/gpu-resident-top-k-for-agentic-rag-i-built-a-cuda-kernel-so-my-retrieval-step-would-stop-bouncing-off-the-gpu/
source: medium-towards-data-science
published_at: 2026-06-19T12:00:00+00:00
fetched_at: 2026-06-19T22:15:29.213835+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Agentic RAG 系統中，向量檢索步驟會頻繁在 GPU 和 CPU 間穿梭，PCIe 傳輸延遲成為隱形瓶頸。作者開發了自訂 CUDA kernel 使向量搜索保持 GPU resident，繞過 CPU，從而達到 microsecond 級尾延遲。這個優化對推理密集的 agent 系統至關重要，減少了每次檢索的上下文切換開銷。該方法展示了針對特定工作流的低階硬體優化如何顯著提升系統效率。"
key_points:
  - "PCIe 傳輸延遲是 agentic RAG 中被忽視的性能瓶頸"
  - "自訂 GPU resident vector search kernel 可達 microsecond 尾延遲"
  - "避免 CPU-GPU 來回傳輸是高效 retrieval 的關鍵優化"
tags: [gpu-optimization, cuda, rag, vector-search, agentic-ai]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## GPU-Resident Top-K for Agentic RAG: I Built a CUDA Kernel So My Retrieval Step Would Stop Bouncing Off the GPU

Agentic RAG 系統中，向量檢索步驟會頻繁在 GPU 和 CPU 間穿梭，PCIe 傳輸延遲成為隱形瓶頸。作者開發了自訂 CUDA kernel 使向量搜索保持 GPU resident，繞過 CPU，從而達到 microsecond 級尾延遲。這個優化對推理密集的 agent 系統至關重要，減少了每次檢索的上下文切換開銷。該方法展示了針對特定工作流的低階硬體優化如何顯著提升系統效率。

### 重點
- PCIe 傳輸延遲是 agentic RAG 中被忽視的性能瓶頸
- 自訂 GPU resident vector search kernel 可達 microsecond 尾延遲
- 避免 CPU-GPU 來回傳輸是高效 retrieval 的關鍵優化

**原文：** [medium-towards-data-science](https://towardsdatascience.com/gpu-resident-top-k-for-agentic-rag-i-built-a-cuda-kernel-so-my-retrieval-step-would-stop-bouncing-off-the-gpu/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The PCIe transfer latency is silently bottlenecking your agentic inference. Here is how building a custom device-resident vector search kernel bypasses the CPU to unlock deterministic microsecond tail latencies. 
 The post GPU-Resident Top-K for Agentic RAG: I Built a CUDA Kernel So My Retrieval Step Would Stop Bouncing Off the GPU appeared first on Towards Data Science .

</details>