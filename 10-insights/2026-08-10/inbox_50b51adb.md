---
id: inbox_50b51adb
date: 2026-08-10
source_ref: "[[00-inbox/2026-08-10/2208-infoq-main-canva-shares-s3-based-architecture-for-s-c2c0]]"
title: "Canva Shares S3 Based Architecture for Session Revocation Across Hundreds of Millions of Sessions"
url: https://www.infoq.com/news/2026/08/canva-session-revocation-scale/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-08-10T14:14:00+00:00
fetched_at: 2026-08-11T00:47:34.295430+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Canva 重新設計 session revocation 基礎設施以支援 1 億活躍 sessions。架構運用 Amazon S3 存儲 durable revocation 記錄，並將緊湊的 in-memory indexes 分散到應用網關。此設計改善部署速度、減少數據庫基礎設施需求，並將 revocation cache 記憶體佔用降低 87.5%。"
key_points:
  - "S3 + 分散式 in-memory indexes 架構支援百萬級 session revocation 規模"
  - "記憶體足跡降低 87.5%，減少數據庫查詢負擔"
  - "提升部署速度，降低數據庫基礎設施成本"
tags: [session-management, aws-s3, scalability, distributed-cache]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Canva Shares S3 Based Architecture for Session Revocation Across Hundreds of Millions of Sessions

Canva 重新設計 session revocation 基礎設施以支援 1 億活躍 sessions。架構運用 Amazon S3 存儲 durable revocation 記錄，並將緊湊的 in-memory indexes 分散到應用網關。此設計改善部署速度、減少數據庫基礎設施需求，並將 revocation cache 記憶體佔用降低 87.5%。

### 重點
- S3 + 分散式 in-memory indexes 架構支援百萬級 session revocation 規模
- 記憶體足跡降低 87.5%，減少數據庫查詢負擔
- 提升部署速度，降低數據庫基礎設施成本

**原文：** [infoq-main](https://www.infoq.com/news/2026/08/canva-session-revocation-scale/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Canva redesigned session revocation infrastructure to support 100M active sessions while reducing database lookups. The architecture uses Amazon S3 for durable revocation records and distributes compact, in-memory indexes to application gateways. Canva said the design improved deployment speed, reduced database infrastructure requirements, and cut the revocation cache memory footprint by 87.5%. By Leela Kumili

</details>