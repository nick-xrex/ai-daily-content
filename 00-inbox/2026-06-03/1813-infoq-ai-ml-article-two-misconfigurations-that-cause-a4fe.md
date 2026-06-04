---
id: inbox_38120d31
source: infoq-ai-ml
source_type: rss
url: "https://www.infoq.com/articles/spark-oom-kubernetes-misconfigurations/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering"
author: "Pranav Bhasker"
published_at: 2026-06-03T09:00:00+00:00
fetched_at: 2026-06-03T18:13:49.718790+00:00
content_hash: "a4fe018f22b0f94a3caadb34a1c9e13f374ca52582a1bc23f34e96ca80173e25"
lang: en
caption_quality: None
raw: true
topics: []
---

# Article: Two Misconfigurations That Caused Spark OOM Failures on Kubernetes

After migrating Spark pipelines to Azure Kubernetes Service, two infrastructure settings interacted destructively: spark.kubernetes.local.dirs.tmpfs=true backed shuffle spill with RAM instead of disk, and a hard podAffinity rule forced all executors onto one node. Together, they caused repeated OOM kills invisible to standard diagnostics. By Pranav Bhasker