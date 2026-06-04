---
id: inbox_64a7b953
date: 2026-06-03
source_ref: "[[00-inbox/.../inbox_64a7b953]]"
title: "Article: Two Misconfigurations That Caused Spark OOM Failures on Kubernetes"
url: https://www.infoq.com/articles/spark-oom-kubernetes-misconfigurations/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-06-03T09:00:00+00:00
fetched_at: 2026-06-04T00:53:33.814253+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "文章分析了 Spark 管道遷移到 Azure Kubernetes Service 後發生的 OOM 故障根本原因。兩個基礎設施配置的相互作用造成問題：spark.kubernetes.local.dirs.tmpfs=true 導致 shuffle spill 使用 RAM 而非磁碟，嚴格的 podAffinity 規則強制所有 executor 在單一節點。此組合導致重複 OOM 殺死，標準診斷工具難以檢測。By Pranav Bhasker"
key_points:
  - "spark.kubernetes.local.dirs.tmpfs=true 配置導致 shuffle spill 使用 RAM，易觸發 OOM"
  - "嚴格 podAffinity 規則強制所有 executor 集中在單一節點，加重記憶體壓力"
  - "兩個配置組合的互動作用導致 OOM，標準 K8s 診斷工具無法檢測"
tags: [spark, kubernetes, oom, configuration, azure-aks, debugging]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Article: Two Misconfigurations That Caused Spark OOM Failures on Kubernetes

文章分析了 Spark 管道遷移到 Azure Kubernetes Service 後發生的 OOM 故障根本原因。兩個基礎設施配置的相互作用造成問題：spark.kubernetes.local.dirs.tmpfs=true 導致 shuffle spill 使用 RAM 而非磁碟，嚴格的 podAffinity 規則強制所有 executor 在單一節點。此組合導致重複 OOM 殺死，標準診斷工具難以檢測。By Pranav Bhasker

### 重點
- spark.kubernetes.local.dirs.tmpfs=true 配置導致 shuffle spill 使用 RAM，易觸發 OOM
- 嚴格 podAffinity 規則強制所有 executor 集中在單一節點，加重記憶體壓力
- 兩個配置組合的互動作用導致 OOM，標準 K8s 診斷工具無法檢測

**原文：** [infoq-main](https://www.infoq.com/articles/spark-oom-kubernetes-misconfigurations/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Article: Two Misconfigurations That Caused Spark OOM Failures on Kubernetes

After migrating Spark pipelines to Azure Kubernetes Service, two infrastructure settings interacted destructively: spark.kubernetes.local.dirs.tmpfs=true backed shuffle spill with RAM instead of disk, and a hard podAffinity rule forced all executors onto one node. Together, they caused repeated OOM kills invisible to standard diagnostics. By Pranav Bhasker

</details>