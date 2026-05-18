---
id: inbox_b7f381b7
source: infoq-architecture
source_type: rss
url: "https://www.infoq.com/news/2026/05/pinterest-cpu-zombies-bottleneck/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design"
author: "Mark Silvester"
published_at: 2026-05-14T10:00:00+00:00
fetched_at: 2026-05-14T18:18:22.258396+00:00
content_hash: "a019724f90af45b152d0e94b03bfec25836453010bc1cef059edca6292964330"
lang: en
caption_quality: None
raw: true
topics: []
---

# Pinterest Engineers Eliminate CPU Zombies to Resolve Production Bottlenecks

Pinterest identified and resolved CPU starvation issues that affected machine learning training jobs on its Kubernetes-based platform, PinCompute. The engineers traced the problem to an unused Amazon ECS agent, which caused memory cgroup leaks. By disabling the agent, they stabilised performance. This case illustrates the importance of understanding system defaults for effective troubleshooting. By Mark Silvester