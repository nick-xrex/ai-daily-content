---
id: inbox_b3dad8d9
date: 2026-05-31
source_ref: "[[00-inbox/2026-05-31/1801-infoq-ai-ml-duckdb-quack-client-server-protocol-over-5f20]]"
title: "DuckDB Quack: Client/Server Protocol over HTTP for Multi-User Analytics"
url: https://www.infoq.com/news/2026/05/duckdb-quack-protocol/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering
source: infoq-ai-ml
published_at: 2026-05-31T11:17:00+00:00
fetched_at: 2026-05-31T18:09:32.591873+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "DuckDB 正式推出 Quack 協議，一個基於 HTTP 的遠程協議，支援多個 DuckDB 實例透過網絡連接並共享同一資料庫。此舉標誌著 DuckDB 架構的重大轉變，從原本主要用於本地和嵌入式場景，擴展到支援真正的客戶端-伺服器多用戶分散式模式。Quack 協議的推出讓 DuckDB 可適用於更廣泛的企業多用戶分析場景。"
key_points:
  - "Quack 協議：基於 HTTP 的新遠程協議，支援網絡訪問"
  - "多用戶能力：多個 DuckDB 實例可共享同一資料庫，超越嵌入式限制"
  - "架構轉變：從本地嵌入式資料庫擴展至客戶端-伺服器分散式模式"
tags: [duckdb, quack, client-server, http, analytics]
topics: []
importance: 3
novelty: 4
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## DuckDB Quack: Client/Server Protocol over HTTP for Multi-User Analytics

DuckDB 正式推出 Quack 協議，一個基於 HTTP 的遠程協議，支援多個 DuckDB 實例透過網絡連接並共享同一資料庫。此舉標誌著 DuckDB 架構的重大轉變，從原本主要用於本地和嵌入式場景，擴展到支援真正的客戶端-伺服器多用戶分散式模式。Quack 協議的推出讓 DuckDB 可適用於更廣泛的企業多用戶分析場景。

### 重點
- Quack 協議：基於 HTTP 的新遠程協議，支援網絡訪問
- 多用戶能力：多個 DuckDB 實例可共享同一資料庫，超越嵌入式限制
- 架構轉變：從本地嵌入式資料庫擴展至客戶端-伺服器分散式模式

**原文：** [infoq-ai-ml](https://www.infoq.com/news/2026/05/duckdb-quack-protocol/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

DuckDB has recently announced Quack, a new remote protocol over HTTP that lets multiple DuckDB instances connect to and work with the same database over a network. The protocol introduces client-server capabilities to a database that was previously mostly local and embedded. By Renato Losio

</details>