---
id: inbox_40357b9c
date: 2026-05-17
source_ref: "[[00-inbox/2026-05-17/0308-reddit-localllama-m5-vs-dgx-spark-vs-strix-halo-vs-rtx-600-efdb]]"
title: "M5 vs DGX Spark vs Strix Halo vs RTX 6000"
url: https://www.reddit.com/r/LocalLLaMA/comments/1tfzsd6/m5_vs_dgx_spark_vs_strix_halo_vs_rtx_6000/
source: reddit-localllama
published_at: 2026-05-17T19:49:13+00:00
fetched_at: 2026-05-18T03:15:00.000702+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者進行 3 天硬件性能基準測試，對比 M5 MacBook、DGX Spark、Strix Halo 和 RTX 6000 在本地 LLM 推理中的表現。根據測試，RTX 6000 內存帶寬 ~1,800 GB/s，M5 約 600 GB/s，Spark/Strix 約 256 GB/s；在成本效益方面，高配 M5 MacBook 性能明顯超越 DGX Spark（帶寬快 2 倍+）。散熱上，MacBook 穩定在 80°C、長時間運行良好，但高負載噪音大如遊戲筆電；EVO X2 則散熱欠佳。測試數據已發布 GitHub，涵蓋 tokens/秒 性能指標，後續加入 MLX 和不同推理後端影響分析。"
key_points:
  - "RTX 6000 內存帶寬 ~1,800 GB/s，M5 MacBook ~600 GB/s，DGX Spark ~256 GB/s；M5 在同等記憶體成本下快 2 倍+"
  - "MacBook 長時間穩定於 80°C、噪音類似遊戲筆電；EVO X2 散熱問題；Tokens/秒性能與帶寬曲線高度相關"
  - "開源基準測試已上 GitHub，後續納入 MLX、不同推理後端（含 Strix Halo 專用優化）對效能影響"
tags: [hardware-benchmark, local-inference, apple-silicon, memory-bandwidth, tokens-per-second]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## M5 vs DGX Spark vs Strix Halo vs RTX 6000

開發者進行 3 天硬件性能基準測試，對比 M5 MacBook、DGX Spark、Strix Halo 和 RTX 6000 在本地 LLM 推理中的表現。根據測試，RTX 6000 內存帶寬 ~1,800 GB/s，M5 約 600 GB/s，Spark/Strix 約 256 GB/s；在成本效益方面，高配 M5 MacBook 性能明顯超越 DGX Spark（帶寬快 2 倍+）。散熱上，MacBook 穩定在 80°C、長時間運行良好，但高負載噪音大如遊戲筆電；EVO X2 則散熱欠佳。測試數據已發布 GitHub，涵蓋 tokens/秒 性能指標，後續加入 MLX 和不同推理後端影響分析。

### 重點
- RTX 6000 內存帶寬 ~1,800 GB/s，M5 MacBook ~600 GB/s，DGX Spark ~256 GB/s；M5 在同等記憶體成本下快 2 倍+
- MacBook 長時間穩定於 80°C、噪音類似遊戲筆電；EVO X2 散熱問題；Tokens/秒性能與帶寬曲線高度相關
- 開源基準測試已上 GitHub，後續納入 MLX、不同推理後端（含 Strix Halo 專用優化）對效能影響

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1tfzsd6/m5_vs_dgx_spark_vs_strix_halo_vs_rtx_6000/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hey guys, super simple. There have been a lot of online debates about the new M5 Macs vs DGX Sparks vs Strix Halo vs dedicated GPUs etc. So I put them all in a room with good power and cooling and ran everything in parallel with standardized tests for the past 3 days, and published everything to a repo. A lot of it isn’t a big surprise when you just think about headline numbers and fundamentals. An RTX6000 has a memory bandwidth speed of ~1,800 gb/s vs ~600 for the M5 vs ~256 for the Spark and Strix. Tokens per second per piece of hardware follows that math and curve pretty well. For the price point, and assuming you are ecosystem agnostic, the maxed out M5 is genuinely legit and very aggressively outperforms the DGX Spark. Again, not really a surprise when you look at their memory bandwidth speeds (2x+ memory bandwidth speeds on the M5 with the same total unified memory). Second thing worth noting was also probably no surprise but the EVO X2 thermals were an issue with extended runs. The MacBook actually surprised me with how well it held up thermally more than anything. It ran for a few days and cruised in the 80c range. I will say this though, it sounds like a normal gaming laptop when it cooks. There’s a bit of propaganda going on when people say “quiet” with these. You ramp up an M5 MacBook Pro to cook with local AI and it turns into a blow dryer like every other laptop that’s ever tried to cook with local AI. It’s built like an aircraft carrier and performs really well for what it is, but you will 100% know it’s working when it runs lol. I’m now swapping back ends and adding data for things like MLX on Mac, different hosting backends on Strix Halo, etc. for how they all impact performance and outputs. The RTX6000 is not the same as the RTX5090 just so the obvious police don’t grab me, but there are a lot of similarities between cards that could make this data useful for someone debating a 5090 PC vs these other machines. Either way, repo enclosed, hope this helps provide some raw data and numbers for future discussions and debates: https://github.com/Light-Heart-Labs/MMBT-Messy-Model-Bench-Tests/tree/main/hardware-tests &#32; submitted by &#32; /u/Signal_Ad657 [link] &#32; [comments]

</details>