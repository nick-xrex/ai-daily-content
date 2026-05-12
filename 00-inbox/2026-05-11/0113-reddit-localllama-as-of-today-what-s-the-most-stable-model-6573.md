---
id: inbox_e06138d5
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t9p4oe/as_of_today_whats_the_most_stable_model_to_run_on/"
author: "/u/mr_tolkien"
published_at: 2026-05-11T01:35:08+00:00
fetched_at: 2026-05-12T01:13:59.605580+00:00
content_hash: "65736b4177a87f3b6cc7be29872d886a1807ea53afd093db563f9410c17552ec"
lang: en
caption_quality: None
raw: true
topics: []
---

# As of today, what's the *most stable* model to run on a 32Gb RAM Mac w/ 256k context?

Hey everyone, I've been playing around with Gemma4 and Qwen3.6 on my 32Gb Macbook Pro M2 Max since their release but I'm struggling at finding: The best software to run it (oMLX, llama.cpp, ...) The best model + quant to pick The best settings for agentic workflows I have tried literal hundreds of settings but I always face the same issues: Stability sucks, at some points the server just dies Crashes happen when context gets *actually* used so it needs stress tests for validation, which are long and flaky Often getting cache misses in agentic workflows bringing latency up to minutes Now there's also MTP, Turboquants, big developments on the MLX side... I'm lost. My llama.cpp .ini file can be seen here . My use-case is summarization and notes organizations as I'd want to use a local model for a memory system. So my question is simple: as of today, early May 2026, what is the most reliable and stable way to run one of the ~30b models with 256k context for agentic workflows on a Mac with 32Gb of RAM? &#32; submitted by &#32; /u/mr_tolkien [link] &#32; [comments]