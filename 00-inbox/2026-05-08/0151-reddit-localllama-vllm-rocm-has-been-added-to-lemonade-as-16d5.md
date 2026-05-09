---
id: inbox_096d7e5f
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t7g70j/vllm_rocm_has_been_added_to_lemonade_as_an/"
author: "/u/jfowers_amd"
published_at: 2026-05-08T18:21:15+00:00
fetched_at: 2026-05-09T01:51:59.611640+00:00
content_hash: "16d55da86a297536dad5d24d0446116dca551f728b248735e16533d66a9703fb"
lang: en
caption_quality: None
raw: true
topics: []
---

# vLLM ROCm has been added to Lemonade as an experimental backend

vLLM has the ability to run .safetensors LLMs before they are converted to GGUF and represents a new engine to explore. I personally had never tried it out until u/krishna2910-amd/ u/mikkoph and u/sa1sr1 made it as easy as running llama.cpp in Lemonade: lemonade backends install vllm:rocm lemonade run Qwen3.5-0.8B-vLLM This is an experimental backend for us in the sense that the essentials are implemented, but there are known rough edges. We want the community's feedback to see where and how far we should take this. If you find it interesting, please let us know your thoughts! Quick start guide: https://lemonade-server.ai/news/vllm-rocm.html GitHub: https://github.com/lemonade-sdk/lemonade Discord: https://discord.gg/5xXzkMu8Zk &#32; submitted by &#32; /u/jfowers_amd [link] &#32; [comments]