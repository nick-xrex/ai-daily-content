---
id: inbox_7c99dda2
date: 2026-05-11
source_ref: "[[00-inbox/2026-05-11/0113-reddit-localllama-500k-context-on-48gb-vram-21tok-s-coding-4947]]"
title: "500k context on 48gb VRAM!! - 21tok/s (coding)"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tag1ks/500k_context_on_48gb_vram_21toks_coding/
source: reddit-localllama
published_at: 2026-05-11T20:49:36+00:00
fetched_at: 2026-05-12T01:21:05.064194+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者發現並驗證 Nemotron-3-Super-64B-A12B-Math-REAP-GGUF 模型，在 48GB VRAM 上支援 500k token context window，編碼任務下達 21 tokens/sec。儘管該模型為數學特化版本，但在 agentic coding（多輪推理 + 工具調用）工作流中表現出乎預期，已用於實際項目開發一週，驗證了長 context 在消費級硬體上的實現方案。"
key_points:
  - "Nemotron-3-Super-64B-A12B 量化版在 48GB VRAM 支援 500k context，編碼速度 21 tokens/sec"
  - "數學特化模型在 agentic coding 意外適配，超越預期效能"
  - "長 context 在消費級硬體實現，量化和 MoE 架構共同作用"
tags: [nemotron-64b, 500k-context, agentic-coding, long-context]
topics: []
importance: 3
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## 500k context on 48gb VRAM!! - 21tok/s (coding)

開發者發現並驗證 Nemotron-3-Super-64B-A12B-Math-REAP-GGUF 模型，在 48GB VRAM 上支援 500k token context window，編碼任務下達 21 tokens/sec。儘管該模型為數學特化版本，但在 agentic coding（多輪推理 + 工具調用）工作流中表現出乎預期，已用於實際項目開發一週，驗證了長 context 在消費級硬體上的實現方案。

### 重點
- Nemotron-3-Super-64B-A12B 量化版在 48GB VRAM 支援 500k context，編碼速度 21 tokens/sec
- 數學特化模型在 agentic coding 意外適配，超越預期效能
- 長 context 在消費級硬體實現，量化和 MoE 架構共同作用

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tag1ks/500k_context_on_48gb_vram_21toks_coding/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I found this model hiding in the corner of huggingface: https://huggingface.co/Max-and-Omnis/Nemotron-3-Super-64B-A12B-Math-REAP-GGUF Looks to be tuned specifically for math but i thought i'd give it a try since i cant run the full 120b nemotron super and it seem to hold up like a champ in agentic coding for some odd reason. been using it to code all my projects for a week now its amazing. Wouldnt dream of having 500k tokens on my potato dual TITAN RTX. If you do happen to try it drop a cmment on your experience with it where did it break what usecase did u use it for ETC. &#32; submitted by &#32; /u/Express_Quail_1493 [link] &#32; [comments]

</details>