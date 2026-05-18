---
id: inbox_025fcf80
source: reddit-localllama
source_type: rss
url: "https://www.reddit.com/r/LocalLLaMA/comments/1tdb4ic/a_first_comprehensive_study_of_turboquant/"
author: "/u/MajorZesty"
published_at: 2026-05-14T20:59:45+00:00
fetched_at: 2026-05-15T18:34:22.422025+00:00
content_hash: "696f92c2a82bc39ec08733b07449dbf2d5d1db81ddf201fad4d3cce14e7c6861"
lang: en
caption_quality: None
raw: true
topics: []
---

# A First Comprehensive Study of TurboQuant: Accuracy and Performance

TL;DR from the article: FP8 via --kv-cache-dtype fp8 remains the best default for KV-cache quantization: it provides 2x KV-cache capacity with negligible accuracy loss, while matching BF16 on most performance metrics and substantially improving them in memory-constrained serving scenarios. TurboQuant k8v4 does not provide any significant advantage over FP8: it only provides modest KV-cache savings (2.4x vs 2x) which are not worth the consistent negative impact on throughput and latency metrics. TurboQuant 4bit-nc is likely the most practical TurboQuant variant: it helps under KV-cache memory pressure, but trades the extra capacity for moderate accuracy, latency, and throughput costs. It may still be viable for edge deployments where memory is the dominant constraint. TurboQuant k3v4-nc and 3bit-nc show meaningful accuracy drops, especially on reasoning and very long-context tasks, while also substantially degrading latency and throughput. This makes them poor candidates for production deployments. &#32; submitted by &#32; /u/MajorZesty [link] &#32; [comments]