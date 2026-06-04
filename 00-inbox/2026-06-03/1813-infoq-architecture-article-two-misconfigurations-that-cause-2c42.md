---
id: inbox_29314e0b
source: infoq-architecture
source_type: rss
url: "https://www.infoq.com/articles/spark-oom-kubernetes-misconfigurations/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design"
author: "Pranav Bhasker"
published_at: 2026-06-03T09:00:00+00:00
fetched_at: 2026-06-03T18:13:50.533980+00:00
content_hash: "2c42f6df0b5b1457983c9ffa60996cb55efee78fe12a8cad8b8cbbb6315c097e"
lang: en
caption_quality: None
raw: true
topics: []
---

# Article: Two Misconfigurations That Caused Spark OOM Failures on Kubernetes

After migrating Spark pipelines to Azure Kubernetes Service, two infrastructure settings interacted destructively: spark.kubernetes.local.dirs.tmpfs=true backed shuffle spill with RAM instead of disk, and a hard podAffinity rule forced all executors onto one node. Together, they caused repeated OOM kills invisible to standard diagnostics. By Pranav Bhasker