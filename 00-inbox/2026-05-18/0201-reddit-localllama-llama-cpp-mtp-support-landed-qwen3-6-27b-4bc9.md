---
id: inbox_16ca174b
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tgxau6/llamacpp_mtp_support_landed_qwen36_27b_at_244_on/"
author: "/u/C_Coffie"
published_at: 2026-05-18T19:01:23+00:00
fetched_at: 2026-05-19T02:01:31.464133+00:00
content_hash: "4bc9794aaacf222b1c43b3dd940b0ceb78e8428f4c5d1a3951d22dbddf3d321f"
lang: en
caption_quality: None
raw: true
topics: []
---

# llama.cpp MTP support landed - Qwen3.6 27B at 2.44× on a Strix Halo, 2.17× on a RTX 3090 rig

PR #22673 (commit 4f13cb7) landed MTP speculative decoding in mainline llama.cpp on May 16. I tested it on two separate rigs. Qwen3.6 27B, single-stream chat, temperature 0, median of 5 runs: Strix Halo (Framework Desktop, ROCm 7.0.2): Q4_K_M: 11.7 → 21.2 tok/s (1.81×) Q8_0: 7.4 → 18.1 tok/s (2.44×) Single RTX 3090 @ 450W (CUDA 12.9, driver 590.26): Q4_K_M: 38.7 → 59.5 tok/s (1.54×, n=2) Dual RTX 3090, layer-split: Q8_0: 25.7 → 55.9 tok/s (2.17×, n=3) Qwen3.6 35B-A3B (MoE): Strix Halo: 49.5 → 69.4 tok/s (1.40×) 3090: 120.0 → 148.3 tok/s (1.24×) Enable with --spec-type draft-mtp --spec-draft-n-max N . Output is byte-identical to baseline at the same seed and temperature. MTP helps MoE less because only ~3B of 35B params run per token — each forward pass is already cheap, so saving N-1 of them is a smaller win. Sweet-spot N also depends on the rig: uncapped 3090 prefers n=2 at Q4, capped 3090 and Strix Halo prefer n=3. Couple of follow-ups from the last thread: The 3090 numbers in my earlier post were undercut by an undisclosed 200W cap (breaker-popping issue with 4 cards on one circuit). I re-benched 26 of the 3090 models at 350W and 450W; dense 27-32B models gained +70 to +113%. Writeup with the curve and full table: https://calebcoffie.com/blog/how-much-do-power-limits-affect-llm-benchmark-tok-s Prompt-processing tok/s and prompt-token columns are now on every row of the benchmarks page. MTP writeup with both rigs side-by-side, build commands, and per-shape tables: https://calebcoffie.com/blog/benchmarking-llama-cpp-mtp-on-strix-halo Raw YAML per run: https://github.com/CCoffie/CalebCoffie.com/tree/main/content/benchmarks/runs &#32; submitted by &#32; /u/C_Coffie [link] &#32; [comments]