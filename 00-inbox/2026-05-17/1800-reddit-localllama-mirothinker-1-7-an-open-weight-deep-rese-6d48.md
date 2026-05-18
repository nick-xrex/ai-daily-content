---
id: inbox_d2e6544b
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tfsmov/mirothinker17_an_openweight_deep_research_agent/"
author: "/u/MiroMindAI"
published_at: 2026-05-17T15:26:43+00:00
fetched_at: 2026-05-17T18:00:47.180765+00:00
content_hash: "6d4844c1fbdf1a2e5ca59a51d7db5459c97dcc6e6f8e5c9145af9ec9720fcc8f"
lang: en
caption_quality: None
raw: true
topics: []
---

# MiroThinker-1.7, an open-weight deep research agent (Qwen3 MoE base) — mini is 30B/3B active, curious what tok/s people get on consumer hardware

As usual, disclosure first: I'm on the team that built this. Our MiroThinker-1.7-deepresearch and 1.7-mini-deepresearch API went live, mini is a deep research agent built on Qwen3 MoE (30B total, 3B active for mini). Weights on HuggingFace: huggingface.co/miromind-ai/MiroThinker-1.7 Posting here because the open-weight agent conversation mostly happens in this sub and I'd genuinely like feed because commenting in reddit and discussing did get me some feedback, but it was actually not enough. Tried to load a github APP on our DC server to get PR notified faster but realized there was actually not enough and one was a promo. Benchmarks (arxiv Table 1, cherry-picked to fit a table but full comparison in paper): Model BrowseComp BrowseComp-ZH HLE-Text GAIA xbench-DS SEAL-0 MiroThinker-1.7 74.0 75.3 42.9 82.7 62.0 53.0 MiroThinker-1.7-mini (30B/3B active) 67.9 72.3 36.4 80.3 57.2 48.2 Qwen3.5-397B 78.6 70.3 48.3 – – 46.9 DeepSeek-V3.2 67.6 65.0 40.8 – – 49.5 GPT-5 (closed, for context) 54.9 65.0 35.2 76.4 75.0 51.4 Two things I'd specifically want this sub to push back on: The mini model is only 3B active params — anyone tried running it locally yet? Curious what tok/s people are getting on consumer hardware. Our context management (sliding window K=5 + episode restarts) is opinionated. If you've run long-context agents locally you probably have opinions on this. Paper: arXiv:2603.15726 See y'all in the comments, will reply tomorrow~ please don't downvote me, for a genuinely good open-source project we ARE not getting enough dev feedback and Reddit has been a good source so far. &#32; submitted by &#32; /u/MiroMindAI [link] &#32; [comments]