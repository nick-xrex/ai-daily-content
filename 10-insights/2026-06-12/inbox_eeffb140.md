---
id: inbox_eeffb140
date: 2026-06-12
source_ref: "[[00-inbox/2026-06-12/0336-infoq-architecture-slack-eliminates-ssh-in-emr-pipelines-mi-3155]]"
title: "Slack Eliminates SSH in EMR Pipelines, Migrates 700+ Jobs to Rest-Based Architecture"
url: https://www.infoq.com/news/2026/06/slack-ssh-rest-quarry-migration/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-06-12T14:39:00+00:00
fetched_at: 2026-06-13T03:48:20.838511+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Slack 將其 Amazon EMR 數據管道從基於 SSH 的執行遷移至 REST 驅動的 Quarry 編排層，涉及 700 多個 Airflow operators。此次遷移消除了生產集群上的直接 SSH 訪問，改進了安全性、可靠性與可觀測性，同時啟用了服務端作業生命週期管理。這一從命令執行到聲明式 REST API 的轉變代表了現代數據平台架構的演進方向。

```mermaid
graph TB
    subgraph Before[\"舊架構\"]
        A1[\"Airflow Operator\"]
        A2[\"SSH 直接執行\"]
        A3[\"EMR Cluster\"]
        A1 -->|Direct SSH| A2 -->|Command Exec| A3
    end
    subgraph After[\"新架構 (Quarry)\"]
        B1[\"Airflow Operator\"]
        B2[\"REST API\"]
        B3[\"EMR Cluster\"]
        B1 -->|REST 請求| B2 -->|作業生命週期管理| B3
    end
    Before -.->|700+ operators 遷移| After
```"
key_points:
  - "700+ Airflow operators 遷移至 REST API（Quarry）編排層，消除直接 SSH 訪問風險"
  - "啟用服務端作業生命週期模型，改進可觀測性與故障排除能力"
  - "架構遷移提升安全邊界，代表大規模數據平台現代化方向"
tags: [emr-migration, ssh-to-rest, data-orchestration, airflow, platform-engineering]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Slack Eliminates SSH in EMR Pipelines, Migrates 700+ Jobs to Rest-Based Architecture

Slack 將其 Amazon EMR 數據管道從基於 SSH 的執行遷移至 REST 驅動的 Quarry 編排層，涉及 700 多個 Airflow operators。此次遷移消除了生產集群上的直接 SSH 訪問，改進了安全性、可靠性與可觀測性，同時啟用了服務端作業生命週期管理。這一從命令執行到聲明式 REST API 的轉變代表了現代數據平台架構的演進方向。

```mermaid
graph TB
    subgraph Before["舊架構"]
        A1["Airflow Operator"]
        A2["SSH 直接執行"]
        A3["EMR Cluster"]
        A1 -->|Direct SSH| A2 -->|Command Exec| A3
    end
    subgraph After["新架構 (Quarry)"]
        B1["Airflow Operator"]
        B2["REST API"]
        B3["EMR Cluster"]
        B1 -->|REST 請求| B2 -->|作業生命週期管理| B3
    end
    Before -.->|700+ operators 遷移| After
```

### 重點
- 700+ Airflow operators 遷移至 REST API（Quarry）編排層，消除直接 SSH 訪問風險
- 啟用服務端作業生命週期模型，改進可觀測性與故障排除能力
- 架構遷移提升安全邊界，代表大規模數據平台現代化方向

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/06/slack-ssh-rest-quarry-migration/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Slack modernized its data platform by replacing SSH based execution in Amazon EMR pipelines with a REST driven orchestration layer called Quarry. The migration covered 700 plus Airflow operators, improving security, reliability, and observability while eliminating direct SSH access across production clusters and enabling a server side job lifecycle model. By Leela Kumili

</details>