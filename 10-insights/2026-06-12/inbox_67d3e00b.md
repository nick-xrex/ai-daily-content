---
id: inbox_67d3e00b
date: 2026-06-12
source_ref: "[[00-inbox/2026-06-12/0336-infoq-main-slack-eliminates-ssh-in-emr-pipelines-mi-68e6]]"
title: "Slack Eliminates SSH in EMR Pipelines, Migrates 700+ Jobs to Rest-Based Architecture"
url: https://www.infoq.com/news/2026/06/slack-ssh-rest-quarry-migration/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-06-12T14:39:00+00:00
fetched_at: 2026-06-13T03:45:42.198499+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Slack 完成資料平台現代化，將 EMR pipelines 中的 700+ Airflow operators 從 SSH 執行遷移至基於 REST 的 Quarry 新架構。本次遷移消除了直接的 SSH 存取，同時改善安全性、可靠性和可觀測性，並實現了伺服器端 job 生命週期管理。Slack 的這次大規模遷移展示了如何系統性地現代化資料基礎設施。"
key_points:
  - "遷移 700+ Airflow operators 從 SSH 到 REST-driven Quarry 架構"
  - "消除直接 SSH 存取，改善安全性與可觀測性"
  - "實現伺服器端 job 生命週期管理，提高系統可靠性"
tags: [slack, emr-migration, rest-architecture, data-platform]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Slack Eliminates SSH in EMR Pipelines, Migrates 700+ Jobs to Rest-Based Architecture

Slack 完成資料平台現代化，將 EMR pipelines 中的 700+ Airflow operators 從 SSH 執行遷移至基於 REST 的 Quarry 新架構。本次遷移消除了直接的 SSH 存取，同時改善安全性、可靠性和可觀測性，並實現了伺服器端 job 生命週期管理。Slack 的這次大規模遷移展示了如何系統性地現代化資料基礎設施。

### 重點
- 遷移 700+ Airflow operators 從 SSH 到 REST-driven Quarry 架構
- 消除直接 SSH 存取，改善安全性與可觀測性
- 實現伺服器端 job 生命週期管理，提高系統可靠性

**原文：** [infoq-main](https://www.infoq.com/news/2026/06/slack-ssh-rest-quarry-migration/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Slack modernized its data platform by replacing SSH based execution in Amazon EMR pipelines with a REST driven orchestration layer called Quarry. The migration covered 700 plus Airflow operators, improving security, reliability, and observability while eliminating direct SSH access across production clusters and enabling a server side job lifecycle model. By Leela Kumili

</details>