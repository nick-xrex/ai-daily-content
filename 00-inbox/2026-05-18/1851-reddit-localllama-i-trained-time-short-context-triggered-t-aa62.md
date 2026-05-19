---
id: inbox_4a854798
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tg90pu/i_trained_time_short_contexttriggered_thinking_on/"
author: "/u/susmitds"
published_at: 2026-05-18T02:14:12+00:00
fetched_at: 2026-05-18T18:51:02.688405+00:00
content_hash: "aa62262e5dd123464e9e4925435ee69e8f85f87fcafb0237b23bd2601d943bbf"
lang: en
caption_quality: None
raw: true
topics: []
---

# I trained TIME: short context-triggered thinking on Qwen model instead of overthinking

Started this as a personal project for my Open-WebUI setup to use. Somehow it ended up as an ACL 2026 paper. Not some lab paper, it is personal solo independent paper that happened. TIME is basically my attempt to train Qwen3 models to think in short bursts wherever the response actually needs it, instead of dumping one giant reasoning block at the start. Not just “make thinking shorter&quot; or “turn thinking on/off per task” or &quot;split thinking to interleaving reasoning for the task&quot; More like: let the model re-think mid-response when context gives it a reason to. The temporal part came in because time is a really clean way to model latent context changes: silence, gaps, stale assumptions, deadlines, timezone shifts, etc. Also, time just matters in a ton of normal conversations. Funny side effect: it also helps with what I think of as the QwQ problem. QwQ was the OG overthinker benchmaxxing model, and the Qwen line still has this vibe where thinking mode can go burn 10k tokens for even trivial stuff like hi. Methods side: QLoRA on Qwen3 4B/8B/14B/32B, four-phase curriculum, Unsloth , vLLM eval, TIMEBench benchmark. Trained locally on my own personal PC: 7950X3D, 128GB RAM, RTX Pro 6000 Blackwell 96GB. All Notebooks and data are available, anyone can replicate it easily (24 GB VRAM good enough upto 14B training, 48 GB good enough for 32B) I intend to do the same on Qwen3.5 and Qwen3.6 later to see if i can reduced overthinking issues. Model uploads are taking time because the merged checkpoints are huge, but datasets, notebooks, scripts, training curriculum, and eval harness are up. Paper : https://arxiv.org/abs/2601.05300v2 TIME repo (Data and Code): https://github.com/The-Coherence-Initiative/TIME TIMEBench repo : https://github.com/The-Coherence-Initiative/TIMEBench &#32; submitted by &#32; /u/susmitds [link] &#32; [comments]