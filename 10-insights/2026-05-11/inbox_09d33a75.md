---
id: inbox_09d33a75
date: 2026-05-11
source_ref: "[[00-inbox/.../inbox_09d33a75]]"
title: "ExLlamaV3 Major Updates!"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t9voxs/exllamav3_major_updates/
source: reddit-localllama
published_at: 2026-05-11T07:05:47+00:00
fetched_at: 2026-05-12T01:39:55.203515+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "ExLlamaV3 推理引擎近期多次迭代，Turboderp 新增 Gemma 4 支援、改進緩存效率，以及 DFlash 加速技術。DFlash 在不同任務上性能提升 1.27–3.00 倍：代理代碼達 2.51 倍、編程達 3.00 倍、翻譯推理達 2.06 倍。同步釋出多個模型的 4.0–4.15 bits-per-weight 量化方案，精度改進幅度達 0%–72.4%。"
key_points:
  - "DFlash 支援帶來 2.51–3.00 倍推理加速（任務相關）"
  - "新增 Gemma 4 支援及改進的 KV 緩存機制"
  - "量化方案涵蓋 Qwen3.5-35B、Trinity-Nano 等，4.00–4.15 bpw 下精度改進 0%–72.4%"
tags: [exllama, dflash, quantization, inference-optimization, local-llm]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## ExLlamaV3 Major Updates!

ExLlamaV3 推理引擎近期多次迭代，Turboderp 新增 Gemma 4 支援、改進緩存效率，以及 DFlash 加速技術。DFlash 在不同任務上性能提升 1.27–3.00 倍：代理代碼達 2.51 倍、編程達 3.00 倍、翻譯推理達 2.06 倍。同步釋出多個模型的 4.0–4.15 bits-per-weight 量化方案，精度改進幅度達 0%–72.4%。

### 重點
- DFlash 支援帶來 2.51–3.00 倍推理加速（任務相關）
- 新增 Gemma 4 支援及改進的 KV 緩存機制
- 量化方案涵蓋 Qwen3.5-35B、Trinity-Nano 等，4.00–4.15 bpw 下精度改進 0%–72.4%

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t9voxs/exllamav3_major_updates/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# ExLlamaV3 Major Updates!

Turboderp has a been on an absolute tear recently, in the endless battle to cram new llamas into smaller, faster boxes. We started off last month with the release of gemma 4 support , and continued with improved caching efficiency . DFlash support came 2 weeks ago with these impressive results: Category Baseline N-gram/suffix DFlash Agentic, code 55.98 t/s 89.58 t/s (1.60x) 140.61 t/s (2.51x) Agentic, curl 54.03 t/s 74.62 t/s (1.38x) 125.94 t/s (2.33x) Coding 59.21 t/s 75.34 t/s (1.27x) 177.67 t/s (3.00x) Creative 59.10 t/s 67.26 t/s (1.13x) 89.19 t/s (1.50x) Creative (reasoning) 59.03 t/s 64.25 t/s (1.09x) 93.54 t/s (1.58x) Translation 58.11 t/s 55.39 t/s (0.95x) 75.73 t/s (1.30x) Translation (reasoning) 58.08 t/s 80.21 t/s (1.38x) 119.43 t/s (2.06x) More model optimization last week, with these improvements: Model 30901 40901 50901 6000 Pro1 50902 6000 Pro2 Qwen3.5-35B-A3B 4.00bpw 5.3% 5.8% 8.6% 10.3% 21.0% 23.5% Qwen3.5-27B 4.00bpw 0.0% 1.9% 8.1% 11.7% 13.1% 15.0% Trinity-Nano 4.15bpw 29.5% 48.6% 52.3% 52.9% 70.5% 72.4% Gemma4-26B-A4B 4.10bpw 3.1% 2.9% 7.8% 9.6% 16.4% 19.2% Gemma4-31B 4.00bpw 4.0% 4.9% 10.0% 8.0% 16.0% 12.0% DFlash model quantization and more bugfixes + efficiency in the last 2 days, and more work on the dev branch already! Come say hi at the exllama discord . &#32; submitted by &#32; /u/Unstable_Llama [link] &#32; [comments]

</details>