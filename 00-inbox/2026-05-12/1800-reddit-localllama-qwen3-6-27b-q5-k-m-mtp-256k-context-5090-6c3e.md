---
id: inbox_bda4d58e
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1taz3eu/qwen36_27b_q5_k_m_mtp_256k_context_5090/"
author: "/u/No_Mango7658"
published_at: 2026-05-12T11:43:51+00:00
fetched_at: 2026-05-12T18:00:40.914908+00:00
content_hash: "6c3e7a50aeac0864bddc58c089b9f3c54e188461364a2476e76e63f08f87f403"
lang: en
caption_quality: None
raw: true
topics: []
---

# Qwen3.6 27b q5_k_M MTP - 256k context - 5090

￼Straight to it: llama-server-mtp \ -m ~/models/Qwen3.6-27B-Q5_K_M-mtp.gguf \ --spec-type mtp \ --spec-draft-n-max 3 \ --cache-type-k q8_0 \ --cache-type-v q8_0 \ -np 1 \ -c 262144 \ -ngl 99 \ --host 0.0.0.0 \ --port 8080 Been running this on my desktop 5090 with no issues and no spillover! You will need to install a special version of llamacpp to run Qwen3.6 with MTP: https://github.com/ggml-org/llama.cpp/pull/22673 Edit: 65-75 tps &#32; submitted by &#32; /u/No_Mango7658 [link] &#32; [comments]