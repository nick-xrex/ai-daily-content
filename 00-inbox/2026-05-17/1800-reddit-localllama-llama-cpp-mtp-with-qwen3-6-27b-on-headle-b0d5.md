---
id: inbox_0c7e7647
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tfilwx/llamacpp_mtp_with_qwen36_27b_on_headless_rtx_3090/"
author: "/u/cleversmoke"
published_at: 2026-05-17T07:31:41+00:00
fetched_at: 2026-05-17T18:00:47.136536+00:00
content_hash: "b0d51da055cf752b4e766c84ad90ccec6c59026691118ca05be10a0b54b7c960"
lang: en
caption_quality: None
raw: true
topics: []
---

# Llama.cpp MTP with Qwen3.6 27B on Headless RTX 3090

Saw some posts around PP being slower, so they were cautious on trying it. Here's a real-world datapoint. Settings: Headless RTX 3090 24G OpenCode Model unsloth's Qwen3.6-27B-MTP-Q4_K_M.gguf 128k context q8_0 kv cache --spec-draft-n-max: 3 --draft-p-min: 0 Use Cases: Research task that uses ~85,000 tokens Coding task that uses ~85,000 tokens. Without MTP (llama.cpp:server-cuda13-b9174): PP: 1,050 tok/s TG: 27 toks/s Total time to complete 85k tokens: ~39 mins With MTP (latest master fork): PP: 600 tok/s (down 42%) TG: 50 tok/s (up 85%) Total time to complete 85k tokens: ~23 mins (1.7x faster or 41% reduction) A 41% time savings is quite huge, so unless you're PP heavy, I'd recommend giving MTP a try on your use cases! I have it on a dual agent set-up so your total processing times may be better since I have another critic agent check the main agent's work. &#32; submitted by &#32; /u/cleversmoke [link] &#32; [comments]