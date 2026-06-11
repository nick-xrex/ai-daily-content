---
id: inbox_955d628e
date: 2026-06-10
source_ref: "[[00-inbox/2026-06-10/2359-infoq-main-microsoft-open-sources-postgresql-extens-768a]]"
title: "Microsoft Open-Sources PostgreSQL Extension for In-Database Durable Execution"
url: https://www.infoq.com/news/2026/06/postgresql-pg-durable/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-06-10T20:00:00+00:00
fetched_at: 2026-06-11T00:02:51.211174+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Microsoft 開源 pg_durable，一個 PostgreSQL 擴展，使耐久工作流能直接在數據庫內運行，無需外部編排系統。此設計將工作流狀態管理整合到數據庫層，減少架構複雜度，特別適合需要長期運行和自動故障恢復的應用場景。"
key_points:
  - "工具：pg_durable PostgreSQL 擴展（Microsoft 開源）"
  - "核心能力：在數據庫內本地執行耐久工作流（In-Database Durable Execution）"
  - "架構優勢：消除外部編排系統依賴、簡化部署複雜度"
tags: [postgresql, durable-execution, workflow-orchestration, database]
topics: []
importance: 4
novelty: 4
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Microsoft Open-Sources PostgreSQL Extension for In-Database Durable Execution

Microsoft 開源 pg_durable，一個 PostgreSQL 擴展，使耐久工作流能直接在數據庫內運行，無需外部編排系統。此設計將工作流狀態管理整合到數據庫層，減少架構複雜度，特別適合需要長期運行和自動故障恢復的應用場景。

### 重點
- 工具：pg_durable PostgreSQL 擴展（Microsoft 開源）
- 核心能力：在數據庫內本地執行耐久工作流（In-Database Durable Execution）
- 架構優勢：消除外部編排系統依賴、簡化部署複雜度

**原文：** [infoq-main](https://www.infoq.com/news/2026/06/postgresql-pg-durable/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Recently open-sourced by Microsoft, pg_durable is a PostgreSQL extension that enables durable workflows to run natively inside the database, eliminating the need for external orchestration systems. By Sergio De Simone

</details>