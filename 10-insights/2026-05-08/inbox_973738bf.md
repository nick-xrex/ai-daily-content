---
id: inbox_973738bf
date: 2026-05-08
source_ref: "[[00-inbox/2026-05-08/0151-reddit-localllama-z-lab-released-gemma-4-26b-a4b-it-dflash-4457]]"
title: "z-lab released gemma-4-26B-A4B-it-DFlash. Anybody tried it yet?"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t79ayh/zlab_released_gemma426ba4bitdflash_anybody_tried/
source: reddit-localllama
published_at: 2026-05-08T14:18:09+00:00
fetched_at: 2026-05-09T02:07:45.177638+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Z-lab 發布 Gemma 4 26B DFlash 版本，引入新的推測解碼技術。DFlash 相比既有的 MTP（多令牌預測）優勢在於：採用更快的並行塊擴散，更重要的是引入有狀態架構（可跨迭代保持上下文緩衝、KV 快取位置、RoPE 偏移狀態），理論上應隨著上下文增長而性能更穩定。反觀 MTP 無狀態設計會面臨 KV 快取膨脹問題導致性能衰減。目前僅 vLLM 支援，llama.cpp 尚未適配；提問者尤其好奇其在稀疏模型（Gemma 4 26B、Qwen 3.6 35B）上的實際推理加速幅度。"
key_points:
  - "DFlash 有狀態設計可跨迭代保持 KV 快取和 RoPE 位置，應比無狀態 MTP 在長上下文場景更優"
  - "DFlash 採用更快的並行塊擴散相比 MTP，且有狀態性應減緩 KV 快取膨脹導致的性能衰減"
  - "Gemma 4 26B DFlash 目前僅 vLLM 支援，llama.cpp 支援狀態未知，實際在稀疏模型上的性能增益待實測"
tags: [gemma-4, dflash, speculative-decoding, mtp-comparison, vllm, kv-cache]
topics: []
importance: 3
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## z-lab released gemma-4-26B-A4B-it-DFlash. Anybody tried it yet?

Z-lab 發布 Gemma 4 26B DFlash 版本，引入新的推測解碼技術。DFlash 相比既有的 MTP（多令牌預測）優勢在於：採用更快的並行塊擴散，更重要的是引入有狀態架構（可跨迭代保持上下文緩衝、KV 快取位置、RoPE 偏移狀態），理論上應隨著上下文增長而性能更穩定。反觀 MTP 無狀態設計會面臨 KV 快取膨脹問題導致性能衰減。目前僅 vLLM 支援，llama.cpp 尚未適配；提問者尤其好奇其在稀疏模型（Gemma 4 26B、Qwen 3.6 35B）上的實際推理加速幅度。

### 重點
- DFlash 有狀態設計可跨迭代保持 KV 快取和 RoPE 位置，應比無狀態 MTP 在長上下文場景更優
- DFlash 採用更快的並行塊擴散相比 MTP，且有狀態性應減緩 KV 快取膨脹導致的性能衰減
- Gemma 4 26B DFlash 目前僅 vLLM 支援，llama.cpp 支援狀態未知，實際在稀疏模型上的性能增益待實測

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t79ayh/zlab_released_gemma426ba4bitdflash_anybody_tried/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Past few days, its all been about MTPs. Somehow people missed out the fact that Z lab released the Dflash for Gemma4 26B a couple of days ago. As far as my understanding goes, Dflash should be a better alternative than MTP because of faster parallel block diffusion drafting and the fact that it is stateful (it can have a persistent state across iterations for context buffers, KV cache positions, and RoPE offsets). This basically should mean that dflash should be drastically better as the session extends and context grows. MTP should technically degrade faster because the kv cache will start balooning faster. I am very curious though how much of a speed difference does dflash bring to sparse models like Gemma 4 26B and Qwen 3.6 35B. Unfortunately, I can't test it since it's vllm only . Anybody tried using this? Any significant gains in speed? And what's the state of dflash support over lcpp? Are we any close? &#32; submitted by &#32; /u/PaceZealousideal6091 [link] &#32; [comments]

</details>