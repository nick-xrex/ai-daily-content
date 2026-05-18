---
id: inbox_8ecf74df
source: infoq-main
source_type: rss
url: "https://www.infoq.com/news/2026/05/pinterest-cpu-zombies-bottleneck/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global"
author: "Mark Silvester"
published_at: 2026-05-14T10:00:00+00:00
fetched_at: 2026-05-14T18:18:20.221750+00:00
content_hash: "bd785ec4c8270b6e9635d6054fe33683864ec131ecc04803e2199e4c1bb0cdc9"
lang: en
caption_quality: None
raw: true
topics: []
---

# Pinterest Engineers Eliminate CPU Zombies to Resolve Production Bottlenecks

Pinterest identified and resolved CPU starvation issues that affected machine learning training jobs on its Kubernetes-based platform, PinCompute. The engineers traced the problem to an unused Amazon ECS agent, which caused memory cgroup leaks. By disabling the agent, they stabilised performance. This case illustrates the importance of understanding system defaults for effective troubleshooting. By Mark Silvester