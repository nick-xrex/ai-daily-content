---
id: inbox_e9ebc89f
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tdns1i/used_over_a_million_tokens_in_three_separate/"
author: "/u/Jorlen"
published_at: 2026-05-15T06:20:08+00:00
fetched_at: 2026-05-15T18:34:22.440578+00:00
content_hash: "93a1a38669130fc8dbe6e355e32bc7847fce07048aa916d9006a063c50c0fef7"
lang: en
caption_quality: None
raw: true
topics: []
---

# Used over a million tokens in three separate sessions to test Qwen 3.6 35b (new Multi-token Prediction version)

In my opinion, MTP models are 100% game changer for local LLMs. In terms of speed, I was getting around 1.5x the tok/sec of previous tests. The project was a test - building a full iterative step-by-step pygame; a small mystery dungeon-style game. At first I set 100-200k context and raised it to 300k. This is at KV Q8_0 quant. Edit: I was wrong, I had mistakenly left it at q4_0. I will redo tests tomorrow with Q8. I use VSCodium and Roo. The idea was to see how far I can push the context window and measure (by feel) if a large context window with a multi-file project slows it down too much to be effective. Model used: Qwen3.6-35B-A3B-UD-Q5_K_S (MTP version) - link OS/Software: Ubuntu 24.04 - Vulkan - To use MTP I had to use a docker version of the MTP prototype of llama.cpp server (image: havenoammo/llama:vulkan-server) My current window is 300k context but I feel like I can go even higher as my VRAM used is 28.3gb / 32gb. Likely 400k is viable (with the 35B MoE model that is). GPU: Asus Radeon R9700 AI Pro card (32gb RDNA 4 card) Just want to shoot my appreciation for the local LLM community and everyone responsible for enabling us to run these kinds of powerful models at home. Amazing when I think where we were just a year ago. I am having a blast exploring all this tech and every day that I learn something new, it just leaves me astounded. EDIT: Switched to the Qwen 3.6 27b model (non-MoE) as I was running into issues with the MoE model when deep in context sessoin (200k ish). Will update results. &#32; submitted by &#32; /u/Jorlen [link] &#32; [comments]