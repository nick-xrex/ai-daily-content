---
id: inbox_beabc781
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1t9fy74/how_does_llamaserver_pick_which_moe_experts_go_on/"
author: "/u/we_are_mammals"
published_at: 2026-05-10T19:11:08+00:00
fetched_at: 2026-05-11T01:50:43.431078+00:00
content_hash: "1541c5a2465e853df9f71af9461d87161eaa9e90fef159f3b993b76686180f8a"
lang: en
caption_quality: None
raw: true
topics: []
---

# How does llama-server pick which MoE experts go on the GPU and which stay on the CPU?

If you are using a MoE model that does not fully fit in your GPU, some of the experts must stay on the CPU. Putting the experts that you will actually need on the GPU will give you GPU inference speeds. But guessing entirely incorrectly will only give you CPU inference speeds. Guessing well is probably easy -- the experts you most commonly used before are the ones that you'll probably need. But I wonder if llama-server uses heuristics like this? &#32; submitted by &#32; /u/we_are_mammals [link] &#32; [comments]