---
id: inbox_64a7b953
source: infoq-main
source_type: rss
url: "https://www.infoq.com/articles/spark-oom-kubernetes-misconfigurations/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global"
author: "Pranav Bhasker"
published_at: 2026-06-03T09:00:00+00:00
fetched_at: 2026-06-03T18:13:48.974375+00:00
content_hash: "e7cbf06b07b29607a52d5bdc6e6c9fc9d2745ec5c1b32ec4e4a03fe89815076b"
lang: en
caption_quality: None
raw: true
topics: []
---

# Article: Two Misconfigurations That Caused Spark OOM Failures on Kubernetes

After migrating Spark pipelines to Azure Kubernetes Service, two infrastructure settings interacted destructively: spark.kubernetes.local.dirs.tmpfs=true backed shuffle spill with RAM instead of disk, and a hard podAffinity rule forced all executors onto one node. Together, they caused repeated OOM kills invisible to standard diagnostics. By Pranav Bhasker