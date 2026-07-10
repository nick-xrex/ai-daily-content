---
id: inbox_125202ad
source: infoq-main
source_type: rss
url: "https://www.infoq.com/news/2026/07/alloydb-ai-proxy-models/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global"
author: "Steef-Jan Wiggers"
published_at: 2026-07-09T08:00:00+00:00
fetched_at: 2026-07-09T22:09:55.040447+00:00
content_hash: "6f23f8fab169db321bad9da4fe82d711aa2c68e9e2879973ba23b4cc9083f9cd"
lang: en
caption_quality: None
raw: true
topics: []
---

# AlloyDB Ships Proxy Models That Replace LLM Calls with Local Inference inside the Database

Google shipped AlloyDB AI functions GA with a proxy model architecture that trains a lightweight local model from LLM outputs, then runs queries at database speed without external calls. Smart batching delivers 2,400x throughput improvement. The proxy model reaches 100,000 rows per second in preview, but benchmark numbers apply only to ai.if in internal testing. By Steef-Jan Wiggers