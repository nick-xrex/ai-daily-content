---
id: inbox_2e403b8f
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1taihoo/b9109_preemptive_fix_for_mtp_mmproj_fix_soon_it/"
author: "/u/Bulky-Priority6824"
published_at: 2026-05-11T22:20:53+00:00
fetched_at: 2026-05-12T01:13:59.602219+00:00
content_hash: "3b187a05e0ac93e8ac3148d82eddaa90ed9b4f9170cb570d4b0085ed7fbfc95c"
lang: en
caption_quality: None
raw: true
topics: []
---

# B9109: preemptive fix for mtp & mmproj fix soon? It appears so

Summary : spec : process images through the draft context — this directly addresses the mmproj + MTP crash. Previously images (mmproj) couldn't be processed through the speculative/draft context at all. This commit adds that capability. That's the actual fix in progress. server : fix mtmd draft processing — mtmd is the multimodal (mmproj) handler. Explicitly fixing draft processing for multimodal means they know about the crash and are targeting it. spec : support parallel drafts — this is infrastructure for running multiple draft models simultaneously, which is required for MTP to work properly at scale with parallel slots. The combination of all three in one build — multimodal draft fix, parallel draft support, and images through draft context — suggests this is a focused push to get MTP + mmproj working together. PR #22673 might not be far behind. &#32; submitted by &#32; /u/Bulky-Priority6824 [link] &#32; [comments]