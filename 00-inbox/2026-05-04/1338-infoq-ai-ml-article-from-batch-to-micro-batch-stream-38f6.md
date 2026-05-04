---
id: inbox_35e25b70
source: infoq-ai-ml
source_type: rss
url: "https://www.infoq.com/articles/micro-batch-streaming-lessons-learned/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering"
author: "Parveen Saini"
published_at: 2026-05-04T11:00:00+00:00
fetched_at: 2026-05-04T13:38:28.400798+00:00
content_hash: "38f67eafb5662882b0a3908aaaad8e2fc8450293b94f8f5bcebb887efcf229b0"
lang: en
caption_quality: None
raw: true
topics: []
---

# Article: From Batch to Micro-Batch Streaming: Lessons Learned the Hard Way in a Delta Index Pipeline

<img src="https://res.infoq.com/articles/micro-batch-streaming-lessons-learned/en/headerimage/micro-batch-streaming-lessons-learned-header-1777381781538.jpg" /><p>This article describes how a production delta-index pipeline migrated from scheduled batch to micro-batch Spark Structured Streaming. It covers why record-level streaming was rejected, how partition-based watermarks replaced fragile S3 completion markers,  overlap-window correctness, and restart-as-design strategies for better predictability in object-store–based ingestion systems.</p> <i>By Parveen Saini</i>