---
id: inbox_29314e0b
date: 2026-06-03
source_ref: "[[00-inbox/.../inbox_29314e0b]]"
title: "Article: Two Misconfigurations That Caused Spark OOM Failures on Kubernetes"
url: https://www.infoq.com/articles/spark-oom-kubernetes-misconfigurations/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-06-03T09:00:00+00:00
fetched_at: 2026-06-04T00:54:44.714293+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "遷移 Spark 管道到 Azure Kubernetes Service 後，兩個基礎設施配置產生破壞性的互動：spark.kubernetes.local.dirs.tmpfs=true 將 shuffle spill 導向 RAM 而非磁碟，而 hard podAffinity 規則強制所有 executor 在單一節點上運行。這兩個設置共同造成重複的 OOM kills，且標準診斷工具難以檢測到根本原因。該案例揭示了配置參數間的隱蔽互作用如何導致災難性故障。"
key_points:
  - "spark.kubernetes.local.dirs.tmpfs=true 將 shuffle spill 導向 RAM（而非磁碟），加劇記憶體壓力"
  - "Hard podAffinity 規則強制所有 executor 在單一節點，加重節點負擔"
  - "配置間互動導致 OOM 問題隱蔽，標準 Kubernetes 診斷工具難以發現根本原因"
tags: [spark, kubernetes, oom-failure, misconfiguration, azure-aks]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Article: Two Misconfigurations That Caused Spark OOM Failures on Kubernetes

遷移 Spark 管道到 Azure Kubernetes Service 後，兩個基礎設施配置產生破壞性的互動：spark.kubernetes.local.dirs.tmpfs=true 將 shuffle spill 導向 RAM 而非磁碟，而 hard podAffinity 規則強制所有 executor 在單一節點上運行。這兩個設置共同造成重複的 OOM kills，且標準診斷工具難以檢測到根本原因。該案例揭示了配置參數間的隱蔽互作用如何導致災難性故障。

### 重點
- spark.kubernetes.local.dirs.tmpfs=true 將 shuffle spill 導向 RAM（而非磁碟），加劇記憶體壓力
- Hard podAffinity 規則強制所有 executor 在單一節點，加重節點負擔
- 配置間互動導致 OOM 問題隱蔽，標準 Kubernetes 診斷工具難以發現根本原因

**原文：** [infoq-architecture](https://www.infoq.com/articles/spark-oom-kubernetes-misconfigurations/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Article: Two Misconfigurations That Caused Spark OOM Failures on Kubernetes

After migrating Spark pipelines to Azure Kubernetes Service, two infrastructure settings interacted destructively: spark.kubernetes.local.dirs.tmpfs=true backed shuffle spill with RAM instead of disk, and a hard podAffinity rule forced all executors onto one node. Together, they caused repeated OOM kills invisible to standard diagnostics. By Pranav Bhasker

</details>