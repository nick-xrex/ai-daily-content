---
id: inbox_e9ebc89f
date: 2026-05-15
source_ref: "[[00-inbox/.../inbox_e9ebc89f]]"
title: "Used over a million tokens in three separate sessions to test Qwen 3.6 35b (new Multi-token Prediction version)"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tdns1i/used_over_a_million_tokens_in_three_separate/
source: reddit-localllama
published_at: 2026-05-15T06:20:08+00:00
fetched_at: 2026-05-18T03:56:37.271526+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "用戶在本地運行 Qwen 3.6 35B MTP 版本進行百萬令牌級別測試，報告推理速度相較前代提升約 1.5 倍。在 RDNA4 32GB GPU 上，使用 KV Q4_0 量化可穩定支持 300k 上下文窗口，用戶估計仍有進一步擴展空間（400k 可能可行）。該測試展現了多令牌預測對本地推理效率的實際加速效果。"
key_points:
  - "MTP 速度提升：Qwen 3.6 35B MTP 版本推理速度 ~1.5x 於前代版本"
  - "300k 上下文本地運行：RDNA4 32GB GPU 穩定支持，VRAM 占用 28.3GB/32GB，400k 估計可行"
  - "KV 量化友好性：KV Q4_0 量化下仍保持高速推理能力"
tags: [mtp-inference, local-llm, context-window]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Used over a million tokens in three separate sessions to test Qwen 3.6 35b (new Multi-token Prediction version)

用戶在本地運行 Qwen 3.6 35B MTP 版本進行百萬令牌級別測試，報告推理速度相較前代提升約 1.5 倍。在 RDNA4 32GB GPU 上，使用 KV Q4_0 量化可穩定支持 300k 上下文窗口，用戶估計仍有進一步擴展空間（400k 可能可行）。該測試展現了多令牌預測對本地推理效率的實際加速效果。

### 重點
- MTP 速度提升：Qwen 3.6 35B MTP 版本推理速度 ~1.5x 於前代版本
- 300k 上下文本地運行：RDNA4 32GB GPU 穩定支持，VRAM 占用 28.3GB/32GB，400k 估計可行
- KV 量化友好性：KV Q4_0 量化下仍保持高速推理能力

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tdns1i/used_over_a_million_tokens_in_three_separate/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Used over a million tokens in three separate sessions to test Qwen 3.6 35b (new Multi-token Prediction version)

In my opinion, MTP models are 100% game changer for local LLMs. In terms of speed, I was getting around 1.5x the tok/sec of previous tests. The project was a test - building a full iterative step-by-step pygame; a small mystery dungeon-style game. At first I set 100-200k context and raised it to 300k. This is at KV Q8_0 quant. Edit: I was wrong, I had mistakenly left it at q4_0. I will redo tests tomorrow with Q8. I use VSCodium and Roo. The idea was to see how far I can push the context window and measure (by feel) if a large context window with a multi-file project slows it down too much to be effective. Model used: Qwen3.6-35B-A3B-UD-Q5_K_S (MTP version) - link OS/Software: Ubuntu 24.04 - Vulkan - To use MTP I had to use a docker version of the MTP prototype of llama.cpp server (image: havenoammo/llama:vulkan-server) My current window is 300k context but I feel like I can go even higher as my VRAM used is 28.3gb / 32gb. Likely 400k is viable (with the 35B MoE model that is). GPU: Asus Radeon R9700 AI Pro card (32gb RDNA 4 card) Just want to shoot my appreciation for the local LLM community and everyone responsible for enabling us to run these kinds of powerful models at home. Amazing when I think where we were just a year ago. I am having a blast exploring all this tech and every day that I learn something new, it just leaves me astounded. EDIT: Switched to the Qwen 3.6 27b model (non-MoE) as I was running into issues with the MoE model when deep in context sessoin (200k ish). Will update results. &#32; submitted by &#32; /u/Jorlen [link] &#32; [comments]

</details>