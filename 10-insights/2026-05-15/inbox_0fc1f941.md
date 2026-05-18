---
id: inbox_0fc1f941
date: 2026-05-15
source_ref: "[[00-inbox/.../inbox_0fc1f941]]"
title: "I have (even faster) DeepSeek V4 Pro at home"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tdpk3f/i_have_even_faster_deepseek_v4_pro_at_home/
source: reddit-localllama
published_at: 2026-05-15T07:59:13+00:00
fetched_at: 2026-05-18T03:59:24.979888+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者在消費級硬體（Epyc 9374F + RTX PRO 6000 Max-Q）上用 ktransformers（sglang + kt-kernel）成功運行 DeepSeek-V4-Pro，並測試 0–131K context depth 的端到端效能。pp512 (prefill) 模式在各 depth 穩定達 45–46 tokens/s，tg32 (token generation) 模式約 7–8 t/s；最長 context 131K 下，預填充吞吐仍維持 45.81 t/s。VRAM 消耗 90.8GB / 97.9GB，GPU 功耗 150W（TG 模式），系統總功耗 400W，peak ~500W。無需模型轉換，直接原始檔案運行；關鍵優化包括 NUMA 配置、tensor split mode，以及 f16 KV cache 防止長文脈迴圈。此設定展示超長文脈模型可在消費級硬體高效本地部署。"
key_points:
  - "DeepSeek-V4-Pro pp512 在 32K–131K context 穩定 45–46 t/s，無衰減；tg32 約 7–8 t/s，顯示 prefill 效率優秀"
  - "VRAM 90.8GB / 97.9GB、GPU 150W (TG)、CPU 400W、peak ~500W 牆面功耗，適合 on-premise 長文脈應用"
  - "ktransformers tensor split + f16 KV cache 防止長 context 迴圈，避免 q8_0 KV cache 在編譯任務中的失敗"
tags: [deepseek-v4, local-inference, ktransformers, benchmarks, context-window]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## I have (even faster) DeepSeek V4 Pro at home

使用者在消費級硬體（Epyc 9374F + RTX PRO 6000 Max-Q）上用 ktransformers（sglang + kt-kernel）成功運行 DeepSeek-V4-Pro，並測試 0–131K context depth 的端到端效能。pp512 (prefill) 模式在各 depth 穩定達 45–46 tokens/s，tg32 (token generation) 模式約 7–8 t/s；最長 context 131K 下，預填充吞吐仍維持 45.81 t/s。VRAM 消耗 90.8GB / 97.9GB，GPU 功耗 150W（TG 模式），系統總功耗 400W，peak ~500W。無需模型轉換，直接原始檔案運行；關鍵優化包括 NUMA 配置、tensor split mode，以及 f16 KV cache 防止長文脈迴圈。此設定展示超長文脈模型可在消費級硬體高效本地部署。

### 重點
- DeepSeek-V4-Pro pp512 在 32K–131K context 穩定 45–46 t/s，無衰減；tg32 約 7–8 t/s，顯示 prefill 效率優秀
- VRAM 90.8GB / 97.9GB、GPU 150W (TG)、CPU 400W、peak ~500W 牆面功耗，適合 on-premise 長文脈應用
- ktransformers tensor split + f16 KV cache 防止長 context 迴圈，避免 q8_0 KV cache 在編譯任務中的失敗

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tdpk3f/i_have_even_faster_deepseek_v4_pro_at_home/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# I have (even faster) DeepSeek V4 Pro at home

Few days ago I posted about my DeepSeek V4 Pro at home - now time for an update. Yesterday I finally managed to run this model in ktransformers (sglang + kt-kernel). I followed the tutorial for DeepSeek V4 Flash and tweaked some options (NUMA, cores) for my hardware (Epyc 9374F + RTX PRO 6000 Max-Q). Then I ran llama-benchy with increasing context depth to check the performance. Results: Depth 0: | model | test | t/s | peak t/s | ttfr (ms) | est_ppt (ms) | e2e_ttft (ms) | |:----------------------------|-------:|-------------:|------------:|----------------:|----------------:|----------------:| | deepseek-ai/DeepSeek-V4-Pro | pp512 | 39.76 ± 0.00 | | 12878.44 ± 0.00 | 12877.59 ± 0.00 | 12878.44 ± 0.00 | | deepseek-ai/DeepSeek-V4-Pro | tg32 | 7.54 ± 0.00 | 8.00 ± 0.00 | | | | Depth 2048: | model | test | t/s | peak t/s | ttfr (ms) | est_ppt (ms) | e2e_ttft (ms) | |:----------------------------|--------------:|-------------:|------------:|----------------:|----------------:|----------------:| | deepseek-ai/DeepSeek-V4-Pro | pp512 @ d2048 | 45.13 ± 0.00 | | 56726.85 ± 0.00 | 56725.93 ± 0.00 | 56726.85 ± 0.00 | | deepseek-ai/DeepSeek-V4-Pro | tg32 @ d2048 | 7.32 ± 0.00 | 8.00 ± 0.00 | | | | Depth 4096: | model | test | t/s | peak t/s | ttfr (ms) | est_ppt (ms) | e2e_ttft (ms) | |:----------------------------|--------------:|-------------:|------------:|-----------------:|-----------------:|-----------------:| | deepseek-ai/DeepSeek-V4-Pro | pp512 @ d4096 | 45.75 ± 0.00 | | 100729.28 ± 0.00 | 100728.46 ± 0.00 | 100729.28 ± 0.00 | | deepseek-ai/DeepSeek-V4-Pro | tg32 @ d4096 | 7.29 ± 0.00 | 8.00 ± 0.00 | | | | Depth 8192: | model | test | t/s | peak t/s | ttfr (ms) | est_ppt (ms) | e2e_ttft (ms) | |:----------------------------|--------------:|-------------:|------------:|-----------------:|-----------------:|-----------------:| | deepseek-ai/DeepSeek-V4-Pro | pp512 @ d8192 | 45.97 ± 0.00 | | 189354.94 ± 0.00 | 189354.03 ± 0.00 | 189354.94 ± 0.00 | | deepseek-ai/DeepSeek-V4-Pro | tg32 @ d8192 | 7.25 ± 0.00 | 8.00 ± 0.00 | | | | Depth 16384: | model | test | t/s | peak t/s | ttfr (ms) | est_ppt (ms) | e2e_ttft (ms) | |:----------------------------|---------------:|-------------:|------------:|-----------------:|-----------------:|-----------------:| | deepseek-ai/DeepSeek-V4-Pro | pp512 @ d16384 | 46.16 ± 0.00 | | 365997.22 ± 0.00 | 365996.26 ± 0.00 | 365997.22 ± 0.00 | | deepseek-ai/DeepSeek-V4-Pro | tg32 @ d16384 | 7.17 ± 0.00 | 8.00 ± 0.00 | | | | Depth 32768: | model | test | t/s | peak t/s | ttfr (ms) | est_ppt (ms) | e2e_ttft (ms) | |:----------------------------|---------------:|-------------:|------------:|-----------------:|-----------------:|-----------------:| | deepseek-ai/DeepSeek-V4-Pro | pp512 @ d32768 | 46.18 ± 0.00 | | 720687.13 ± 0.00 | 720685.67 ± 0.00 | 720687.13 ± 0.00 | | deepseek-ai/DeepSeek-V4-Pro | tg32 @ d32768 | 7.07 ± 0.00 | 8.00 ± 0.00 | | | | Depth 65536: | model | test | t/s | peak t/s | ttfr (ms) | est_ppt (ms) | e2e_ttft (ms) | |:----------------------------|---------------:|-------------:|------------:|------------------:|------------------:|------------------:| | deepseek-ai/DeepSeek-V4-Pro | pp512 @ d65536 | 46.09 ± 0.00 | | 1433019.29 ± 0.00 | 1433016.42 ± 0.00 | 1433019.29 ± 0.00 | | deepseek-ai/DeepSeek-V4-Pro | tg32 @ d65536 | 6.80 ± 0.00 | 7.00 ± 0.00 | | | | Depth 131072: | model | test | t/s | peak t/s | ttfr (ms) | est_ppt (ms) | e2e_ttft (ms) | |:----------------------------|----------------:|-------------:|------------:|------------------:|------------------:|------------------:| | deepseek-ai/DeepSeek-V4-Pro | pp512 @ d131072 | 45.81 ± 0.00 | | 2872297.51 ± 0.00 | 2872296.30 ± 0.00 | 2872297.51 ± 0.00 | | deepseek-ai/DeepSeek-V4-Pro | tg32 @ d131072 | 6.38 ± 0.00 | 7.00 ± 0.00 | | | | During 64k test (that took over 20 min) llama-benchy did not report the result despite sglang finishing processing the request so I aborted the test. I don't know, maybe there is some kind of timeout happening. It appears that llama-benchy simply applies depth settings even to warmup phase, so it processed 64k of context, did warmup, then processed 64k of context again to do the actual test. So --no-warmup to the rescue. Not so fast, it still processed the context twice. Update: I got it, --no-warmup --no-adapt-prompt and depth context is processed only once. This is all running the original model files, no need for conversion. GPU VRAM usage: 90815MiB / 97887MiB GPU power usage: ~100W during PP, ~150W during TG RAM usage: 907.5GB / 1152GB CPU+MB power usage: ~400W &#32; submitted by &#32; /u/fairydreaming [link] &#32; [comments]

</details>