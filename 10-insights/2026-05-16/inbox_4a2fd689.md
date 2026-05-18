---
id: inbox_4a2fd689
date: 2026-05-16
source_ref: "[[00-inbox/.../inbox_4a2fd689]]"
title: "Ran the same models across Strix Halo, RTX 3090, and RTX 5070 because I wanted my own numbers"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tf9iyk/ran_the_same_models_across_strix_halo_rtx_3090/
source: reddit-localllama
published_at: 2026-05-16T23:57:06+00:00
fetched_at: 2026-05-18T04:11:13.928489+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者對 Strix Halo、RTX 3090、RTX 5070 進行 55 次推論基準測試，涵蓋 5 個後端與 0.35B–35B 模型。發現記憶體頻寬為解碼速度主要限制；RTX 5070（12GB GDDR7, Vulkan）在 12GB 內模型上超越 RTX 3090（24GB GDDR6X, CUDA），例如 Gemma-3-4B 達 156.6 vs 142.0 tok/s。量化權衡：Q2 到 Q6 範圍 1.6x；Q4 為最佳點。推論模型因隱藏推論內容通道而看似 5 倍慢。發現 q4_0 量化用於草稿 KV 快取可節省 VRAM 且品質無損。完整資料公開在 calebcoffie.com/benchmarks。"
key_points:
  - "RTX 5070 (12GB GDDR7, Vulkan) 在同一尺度模型上勝過 RTX 3090：Gemma-4-E4B chat 124.3 vs 118.4 tok/s、LFM2-8B-A1B 336.1 vs 318.7 tok/s"
  - "量化曲線：Q2 比 Q4 快 ~14% 但質量下降；Q6 比 Q4 慢 ~28% 但質量提升，Q2-Q6 整體 1.6x 跨度"
  - "推論模型隱藏推論內容計入解碼速度但不在使用者可見回覆；MoE 路由使 Strix 純 CPU 達 5–9 tok/s（Gemma-4-26B-A4B）"
tags: [benchmark, inference-speed, quantization, vram, rtx-5070, rtx-3090, memory-bandwidth]
topics: []
importance: 5
novelty: 5
insight_quality: 5
insight_type: data-point
deep_dive_candidate: true
deep_dive_approved: false
---

## Ran the same models across Strix Halo, RTX 3090, and RTX 5070 because I wanted my own numbers

開發者對 Strix Halo、RTX 3090、RTX 5070 進行 55 次推論基準測試，涵蓋 5 個後端與 0.35B–35B 模型。發現記憶體頻寬為解碼速度主要限制；RTX 5070（12GB GDDR7, Vulkan）在 12GB 內模型上超越 RTX 3090（24GB GDDR6X, CUDA），例如 Gemma-3-4B 達 156.6 vs 142.0 tok/s。量化權衡：Q2 到 Q6 範圍 1.6x；Q4 為最佳點。推論模型因隱藏推論內容通道而看似 5 倍慢。發現 q4_0 量化用於草稿 KV 快取可節省 VRAM 且品質無損。完整資料公開在 calebcoffie.com/benchmarks。

### 重點
- RTX 5070 (12GB GDDR7, Vulkan) 在同一尺度模型上勝過 RTX 3090：Gemma-4-E4B chat 124.3 vs 118.4 tok/s、LFM2-8B-A1B 336.1 vs 318.7 tok/s
- 量化曲線：Q2 比 Q4 快 ~14% 但質量下降；Q6 比 Q4 慢 ~28% 但質量提升，Q2-Q6 整體 1.6x 跨度
- 推論模型隱藏推論內容計入解碼速度但不在使用者可見回覆；MoE 路由使 Strix 純 CPU 達 5–9 tok/s（Gemma-4-26B-A4B）

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tf9iyk/ran_the_same_models_across_strix_halo_rtx_3090/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Ran the same models across Strix Halo, RTX 3090, and RTX 5070 because I wanted my own numbers

I kept seeing inference-speed claims for these models and wanting an apples-to-apples comparison on the hardware I actually have. So I built a harness and a public page that dumps every run as YAML. The dataset: 55 runs, three rigs, five backends (rocm, vulkan, cpu, cuda, vllm-cuda), models from 0.35B (LFM2.5) through 35B-A3B (Qwen3.5 MoE). Workloads: short-prompt chat, long-context RAG, codegen long-output, and an agent shape at concurrency 1 and 4. Three measured iterations after one warmup, temperature 0, VRAM-fit verified before each run. A few patterns from the data: Memory bandwidth runs the show for decode. The RTX 5070 (12 GiB GDDR7, Vulkan) actually beats the RTX 3090 (24 GiB GDDR6X, CUDA) on every model that fits in 12 GiB: Gemma-3-4b chat: 5070 = 156.6 vs 3090 = 142.0 tok/s Gemma-4-E4B chat: 5070 = 124.3 vs 3090 = 118.4 tok/s LFM2-8B-A1B chat: 5070 = 336.1 vs 3090 = 318.7 tok/s The 3090 wins decisively in the 14-31B band where the model fits in 24 GiB but not 12 GiB: Gemma-4-26B-A4B chat: 3090 = 100.5 | Strix ROCm = 43.7 | Strix Vulkan = 47.7 tok/s Qwen3.6-27B chat: 3090 = 21.1 | Strix ROCm = 11.2 | Strix Vulkan = 11.6 tok/s Strix Vulkan is often a hair faster than Strix ROCm on the same hardware/model. Biggest gap I saw was Gemma-4-26B-A4B at +9% (43.7 → 47.7). Some models are basically tied. Probably a gfx1151 kernel tuning gap on the bundled ROCm build; haven't dug in. Quant cost on the 3090 for Qwen3.6-27B chat: Q2_K = 24.0 Q3_K_M = 20.5 Q4_K_M = 21.1 Q5_K_M = 18.6 Q6_K = 15.3 tok/s Q2 to Q6 is a 1.6x range. Q4 is the sweet spot. Q2 buys you ~14% over Q4 in exchange for the quality hit; Q6 costs ~28% for the quality bump. Surprised the curve isn't steeper. Reasoning models look ~5x slower than they actually are if you only watch output tok/s. Qwen3.5/3.6 stream most output through a hidden reasoning_content channel that counts in the decode rate but isn't part of the user-visible answer. Worth knowing when picking a coding assistant. CPU on Strix is not nothing. Gemma-4-26B-A4B MoE runs at ~5-9 tok/s on pure CPU thanks to unified memory + active-param routing. Not fast, but usable for batch work where you don't need the GPU. Site has every run plus the rest of the models if you want to dig: https://calebcoffie.com/benchmarks . Methodology and the rest of the writeup: https://calebcoffie.com/blog/introducing-open-weight-model-benchmarks . Things I know I haven't done: vLLM on Strix (lemonade's backend-readiness timeout kills the FP8 autotune; fix queued) &amp; the 70-130B Strix-only models (queued for v2). I don't own a 4090/5080/5090, so those aren't represented; the writeup has a back-of-envelope bandwidth extrapolation. Not trying to replace existing benchmark sites. Just wanted another data point for my own setup and figured the same combo of rigs would be useful to someone else. Happy to be wrong on methodology if anyone spots a flaw. &#32; submitted by &#32; /u/C_Coffie [link] &#32; [comments]

</details>