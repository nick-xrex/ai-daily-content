---
id: inbox_91d47fcd
date: 2026-05-17
source_ref: "[[00-inbox/.../inbox_91d47fcd]]"
title: "Jackrong/Qwopus3.5-9B-Coder-GGUF · Hugging Face"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tfin40/jackrongqwopus359bcodergguf_hugging_face/
source: reddit-localllama
published_at: 2026-05-17T07:33:35+00:00
fetched_at: 2026-05-18T04:09:16.233483+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Jackrong 發布 Qwopus3.5-9B-Coder，Qwen 3.5 9B dense 架構經過針對性優化，整合 Trace Inversion 數據增強和高品質 Agent Traces，專為代碼寫作、tool calling 和邏輯推理設計。9B dense 被定位為「最佳甜蜜點」——支援 8-bit 精度在標準 16GB RAM 設備（如筆電、Mac mini），實現高性能推理和快速生成。模型卡有完整 benchmark 數據。"
key_points:
  - "9B dense 架構、8-bit 精度在 16GB RAM（筆電、Mac mini）無需高端硬體"
  - "Trace Inversion 數據增強 + Agent Traces 整合，強化結構化邏輯推理與代碼寫作"
  - "針對 agentic coding、tool calling、repository 級任務優化"
tags: [qwen-3.5, coding-model, agentic-ai, trace-inversion, 9b-model]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Jackrong/Qwopus3.5-9B-Coder-GGUF · Hugging Face

Jackrong 發布 Qwopus3.5-9B-Coder，Qwen 3.5 9B dense 架構經過針對性優化，整合 Trace Inversion 數據增強和高品質 Agent Traces，專為代碼寫作、tool calling 和邏輯推理設計。9B dense 被定位為「最佳甜蜜點」——支援 8-bit 精度在標準 16GB RAM 設備（如筆電、Mac mini），實現高性能推理和快速生成。模型卡有完整 benchmark 數據。

### 重點
- 9B dense 架構、8-bit 精度在 16GB RAM（筆電、Mac mini）無需高端硬體
- Trace Inversion 數據增強 + Agent Traces 整合，強化結構化邏輯推理與代碼寫作
- 針對 agentic coding、tool calling、repository 級任務優化

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tfin40/jackrongqwopus359bcodergguf_hugging_face/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Jackrong/Qwopus3.5-9B-Coder-GGUF · Hugging Face

Qwopus3.5-9B-coder is specially optimized and fine-tuned for high-performance 🤖 Agentic Coding, complex Tool Calling, and logical reasoning. 💡 Why the 9B Dense Model? We believe that the 9B dense architecture represents the perfect &quot;sweet spot&quot; for large language models. It runs seamlessly at 8-bit precision on entry-level 16GB RAM devices—such as standard laptops and the Mac mini—making it exceptionally lightweight yet highly versatile. Without requiring expensive hardware, it allows you to achieve excellent performance paired with impressive inference speeds. Simply put, Qwen3.5-9B is currently the best open-source model in its class. 🛠 Training Strategy The fine-tuning process of this model deeply integrates Trace Inversion data augmentation technology with high-quality Agent Traces . This systematic approach not only strengthens the model's ability to solve complex programming tasks, but also greatly improves its logical coherence and accuracy when using various tools. This model is designed specifically for the following goals: 🧩 More structured and stronger logical reasoning capabilities, reducing repetitive thinking 💻 More powerful capabilities in code writing, debugging, and repository-level task processing 🛠 More stable and accurate Tool Calling capabilities for terminal commands, file operations, and browsers 🔁 Better cross-data source distillation alignment Check model card for all benchmarks. With MTP, hope this could be better &amp; faster on ~10GB VRAM. Nice to do Agentic coding while getting good t/s just with 8GB VRAM. &#32; submitted by &#32; /u/pmttyji [link] &#32; [comments]

</details>