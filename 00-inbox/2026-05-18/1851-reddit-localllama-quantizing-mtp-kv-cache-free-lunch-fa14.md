---
id: inbox_76531bb9
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tgk9y6/quantizing_mtp_kv_cache_free_lunch/"
author: "/u/legit_split_"
published_at: 2026-05-18T11:52:58+00:00
fetched_at: 2026-05-18T18:51:02.610856+00:00
content_hash: "fa140412b1324e9d63637900623a0d99964adb2eba760b81f5bec582d4d25998"
lang: en
caption_quality: None
raw: true
topics: []
---

# Quantizing MTP KV Cache = free lunch?

With the MTP llama.cpp implementation in the Qwen3.6/3.5 models more VRAM is required for the MTP layer. However, many people don't realize this layer comes with its own KV cache which can also be quantized: -cache-type-k-draft q8_0 -cache-type-v-draft q8_0 edit: This is NOT quantizing the main KV Cache of the model So is it free lunch thus allowing us to fit slightly more context? From a short benchmark on Qwen3.6-27B-Q8_0 it certainly seems so: --spec-type draft-mtp --spec-draft-n-max 3 Aggregate: { &quot;n_requests&quot;: 9, &quot;total_predicted&quot;: 1404, &quot;total_draft&quot;: 1302, &quot;total_draft_accepted&quot;: 957, &quot;aggregate_accept_rate&quot;: 0.735, &quot;wall_s_total&quot;: 49.46 } --spec-type draft-mtp --spec-draft-n-max 3 -cache-type-k-draft q8_0 -cache-type-v-draft q8_0 Aggregate: { &quot;n_requests&quot;: 9, &quot;total_predicted&quot;: 1404, &quot;total_draft&quot;: 1302, &quot;total_draft_accepted&quot;: 957, &quot;aggregate_accept_rate&quot;: 0.735, &quot;wall_s_total&quot;: 49.32 } Also tested with tensor parallelism: -sm tenor --spec-type draft-mtp --spec-draft-n-max 3 Aggregate: { &quot;n_requests&quot;: 9, &quot;total_predicted&quot;: 1404, &quot;total_draft&quot;: 1294, &quot;total_draft_accepted&quot;: 959, &quot;aggregate_accept_rate&quot;: 0.7411, &quot;wall_s_total&quot;: 38.42 } -sm tensor --spec-type draft-mtp --spec-draft-n-max 3 -cache-type-k-draft q8_0 -cache-type-v-draft q8_0 Aggregate: { &quot;n_requests&quot;: 9, &quot;total_predicted&quot;: 1404, &quot;total_draft&quot;: 1294, &quot;total_draft_accepted&quot;: 959, &quot;aggregate_accept_rate&quot;: 0.7411, &quot;wall_s_total&quot;: 38.29 } Let me know if I'm coping or if you have other experiences. Tested on 2xMi50 32GBs @ PCIe 4.0 x 8 &#32; submitted by &#32; /u/legit_split_ [link] &#32; [comments]