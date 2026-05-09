---
id: inbox_040023df
date: 2026-05-08
source_ref: "[[00-inbox/.../inbox_040023df]]"
title: "Gemma 4 26B Hits 600 Tok/s on One RTX 5090"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t796qe/gemma_4_26b_hits_600_toks_on_one_rtx_5090/
source: reddit-localllama
published_at: 2026-05-08T14:13:52+00:00
fetched_at: 2026-05-09T02:53:47.685506+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "用戶在 RTX 5090 上測試 Gemma 4 26B 搭配 DFlash 推測解碼的性能。在 num_speculative_tokens=13、max_num_batched_tokens=8192 配置下，生成速度從無推測解碼的 228 tok/s 提升至 578 tok/s (E2E latency 從 4455ms 降至 1738ms)，實現 2.56 倍加速。測試表明最佳平均效能設定與最佳服務設定不同：num_speculative_tokens=13 最快，但 max_num_batched_tokens=8192 在尾延遲上更穩定。"
key_points:
  - "Gemma 4 26B + DFlash 在 RTX 5090 上達到 578 tok/s (vs. 228 tok/s baseline)，2.56 倍吞吐加速"
  - "num_speculative_tokens=13 為最佳設定，超過 15 token 反而降速；推測 token 數存在上限而非線性增益"
  - "max_num_batched_tokens 8192 vs 4096 權衡：前者吞吐更高，後者 p95 延遲更優，需根據場景選擇"
tags: [gemma-4-26b, dflash-speculative, vllm, rtx-5090, throughput-tuning]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Gemma 4 26B Hits 600 Tok/s on One RTX 5090

用戶在 RTX 5090 上測試 Gemma 4 26B 搭配 DFlash 推測解碼的性能。在 num_speculative_tokens=13、max_num_batched_tokens=8192 配置下，生成速度從無推測解碼的 228 tok/s 提升至 578 tok/s (E2E latency 從 4455ms 降至 1738ms)，實現 2.56 倍加速。測試表明最佳平均效能設定與最佳服務設定不同：num_speculative_tokens=13 最快，但 max_num_batched_tokens=8192 在尾延遲上更穩定。

### 重點
- Gemma 4 26B + DFlash 在 RTX 5090 上達到 578 tok/s (vs. 228 tok/s baseline)，2.56 倍吞吐加速
- num_speculative_tokens=13 為最佳設定，超過 15 token 反而降速；推測 token 數存在上限而非線性增益
- max_num_batched_tokens 8192 vs 4096 權衡：前者吞吐更高，後者 p95 延遲更優，需根據場景選擇

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t796qe/gemma_4_26b_hits_600_toks_on_one_rtx_5090/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Gemma 4 26B Hits 600 Tok/s on One RTX 5090

I ran a benchmark to see how much DFlash speculative decoding actually helps in vLLM. Setup: GPU: RTX 5090, 32GB VRAM vLLM: 0.19.2rc1 Main model: cyankiwi/gemma-4-26B-A4B-it-AWQ-4bit Draft model: z-lab/gemma-4-26B-A4B-it-DFlash Workload: random dataset, 256 input tokens, 1024 output tokens Concurrency: 1 Request rate: 1 Tested num_speculative_tokens from 0 to 15 The short version: Baseline without DFlash: ~228 output tok/s ~4455 ms mean E2E latency Best practical DFlash setting: num_speculative_tokens=13 max_num_batched_tokens=8192 ~578 output tok/s ~1738 ms mean E2E latency ~2.56x speedup One interesting thing: the fastest average setting was not automatically the best serving setting. num_speculative_tokens=13 with max_num_batched_tokens=4096 had slightly better mean latency, but worse p95. Moving to 8192 gave a cleaner tail. I made a short video showing the setup, script, benchmark method, graphs, and final recommended command: https://youtu.be/S_zbHH5Ycs0 Charts / script / results: https://medium.com/@ttio2tech_28094/3a7ac4f73e5d Curious if others are seeing similar optimal speculative-token counts with DFlash, especially on 4090/5090 or different Gemma/Qwen models. &#32; submitted by &#32; /u/chain-77 [link] &#32; [comments]

</details>