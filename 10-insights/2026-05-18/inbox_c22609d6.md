---
id: inbox_c22609d6
date: 2026-05-18
source_ref: "[[00-inbox/2026-05-18/0201-reddit-localllama-21-gpu-s-benchmarked-running-a-small-tts-3dfc]]"
title: "21 GPU&#39;s benchmarked running a small TTS model (vram peak: 5GB)"
url: https://www.reddit.com/r/LocalLLaMA/comments/1th2f5w/21_gpus_benchmarked_running_a_small_tts_model/
source: reddit-localllama
published_at: 2026-05-18T21:46:14+00:00
fetched_at: 2026-05-19T02:09:43.207932+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者在 vast.ai 租用 21 款 GPU 運行小型 TTS 模型 OmniVoice（峰值 VRAM 5GB），測試各消費級 GPU 與自家 RTX 3090 的性能表現，計算實時倍速（xRT）數據。以非科學但實用的方式，為用戶選擇 TTS 推理硬體提供參考基準。"
key_points:
  - "21 款 GPU 基準對比，OmniVoice 模型峰值 VRAM 僅 5GB，適合消費級硬體運行"
  - "用實時倍速（xRT）衡量推理速度，基於 3 次運行的小段落 TTS 測試平均值"
  - "涵蓋 RTX 系列、H100 等多型號，幫助用戶評估成本效益"
tags: [tts-inference, gpu-benchmark, consumer-gpu, vram-efficient]
topics: []
importance: 3
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## 21 GPU's benchmarked running a small TTS model (vram peak: 5GB)

作者在 vast.ai 租用 21 款 GPU 運行小型 TTS 模型 OmniVoice（峰值 VRAM 5GB），測試各消費級 GPU 與自家 RTX 3090 的性能表現，計算實時倍速（xRT）數據。以非科學但實用的方式，為用戶選擇 TTS 推理硬體提供參考基準。

### 重點
- 21 款 GPU 基準對比，OmniVoice 模型峰值 VRAM 僅 5GB，適合消費級硬體運行
- 用實時倍速（xRT）衡量推理速度，基於 3 次運行的小段落 TTS 測試平均值
- 涵蓋 RTX 系列、H100 等多型號，幫助用戶評估成本效益

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1th2f5w/21_gpus_benchmarked_running_a_small_tts_model/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I rented different GPUs on vast.ai for a few minutes each to benchmark a small TTS model, OmniVoice, with a peak VRAM usage of about 5 GB. I wanted to see how various mostly consumer GPUs would stack up against my own RTX 3090. This is by no means an extensive or scientific analysis, but I think it gives a rough estimate of how these GPUs perform relative to each other. xRT means times real-time. It shows how much faster than real-time the GPU generates audio. Average of 3 runs of a small paragraph with reference audio provided (voice cloning). &#32; submitted by &#32; /u/urarthur [link] &#32; [comments]

</details>