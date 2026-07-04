---
id: inbox_19b1b0ec
date: 2026-07-03
source_ref: "[[00-inbox/2026-07-03/0116-infoq-architecture-cloudflare-details-unified-data-platform-9e45]]"
title: "Cloudflare Details Unified Data Platform Where Billing Workloads Account for 53% of Queries"
url: https://www.infoq.com/news/2026/07/cloudflare-unified-data-platform/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-07-03T14:29:00+00:00
fetched_at: 2026-07-04T01:27:24.403293+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Cloudflare 公開內部統一數據平台 Town Lake 與 AI 分析代理 Skipper，該平台處理約 91K 計費查詢（佔比 53%），同時涵蓋運營、安全及業務數據。使用 Trino、Iceberg、R2、DataHub 構建 lakehouse 架構，支持跨系統治理分析與自然語言查詢。該案例展示 lakehouse 在混合工作負載中的實踐應用。"
key_points:
  - "Town Lake lakehouse 架構：使用 Trino + Iceberg + R2 + DataHub，支持多域數據統一查詢與治理"
  - "Skipper AI 代理：統一計費、運營、安全、業務四大類數據的自然語言訪問入口"
  - "91K 計費查詢佔總查詢 53%，說明計費數據分析是核心工作負載"
tags: [unified-data-platform, lakehouse-architecture, ai-analytics, billing-analytics, trino-iceberg]
topics: [agents.mcp]
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Cloudflare Details Unified Data Platform Where Billing Workloads Account for 53% of Queries

Cloudflare 公開內部統一數據平台 Town Lake 與 AI 分析代理 Skipper，該平台處理約 91K 計費查詢（佔比 53%），同時涵蓋運營、安全及業務數據。使用 Trino、Iceberg、R2、DataHub 構建 lakehouse 架構，支持跨系統治理分析與自然語言查詢。該案例展示 lakehouse 在混合工作負載中的實踐應用。

### 重點
- Town Lake lakehouse 架構：使用 Trino + Iceberg + R2 + DataHub，支持多域數據統一查詢與治理
- Skipper AI 代理：統一計費、運營、安全、業務四大類數據的自然語言訪問入口
- 91K 計費查詢佔總查詢 53%，說明計費數據分析是核心工作負載

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/07/cloudflare-unified-data-platform/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Cloudflare details Town Lake, an internal unified data platform, and Skipper, an AI analytics agent unifying access to operational, billing, security, and business data. The platform processed ~91K billing queries, with billing forming majority usage. Built on a lakehouse architecture using Trino, Iceberg, R2, and DataHub, it enables governed cross-system analytics and natural language access. By Leela Kumili

</details>