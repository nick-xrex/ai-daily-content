---
id: inbox_d3ef654f
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t7kyju/got_mtp_turboquant_running_qwen3627b_80_ts_at/"
author: "/u/indrasmirror"
published_at: 2026-05-08T21:15:59+00:00
fetched_at: 2026-05-09T01:51:59.651049+00:00
content_hash: "a08c3cdd25c6864710e3e8712d9f347d2169d618149fce75efa04a1522e1db3b"
lang: en
caption_quality: None
raw: true
topics: []
---

# Got MTP + TurboQuant running — Qwen3.6-27B -- 80+ t/s at 262K context on a single RTX 4090

So I've been messing around trying to get MTP working alongside TBQ4_0 (TurboQuant's lossless 4.25 bpv KV cache) on Qwen3.6-27B for my own use. So after a day of vibecoding I think I may have gotten something viable. Went from about 43 t/s when I first got it compiling to 80-87 t/s after optimizing. With MTP draft acceptance around 73% on top of that. Running on: - RTX 4090 24GB - Qwen3.6-27B-Heretic-v2 Q4_K_M with grafted MTP heads - 262K context, TBQ4_0 KV cache, MTP draft 3 - Ubuntu 24.04, CUDA 12.x I'm not a professional or anything so there's probably room for improvement, but it works and the output quality seems solid. The fork's buildable if anyone wants to try it or poke holes in the approach: https://github.com/Indras-Mirror/llama.cpp-mtp Got Deepseek to write up the technical details here if anyone's curious about the kernel architecture: https://indrasmirror.au/blog-mtp-shared-tensors-200k.html &#32; submitted by &#32; /u/indrasmirror [link] &#32; [comments]