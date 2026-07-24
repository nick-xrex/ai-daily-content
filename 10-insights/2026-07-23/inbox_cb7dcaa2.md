---
id: inbox_cb7dcaa2
date: 2026-07-23
source_ref: "[[00-inbox/2026-07-23/0149-infoq-main-expedia-uses-ai-driven-service-telemetry-402b]]"
title: "Expedia Uses AI Driven Service Telemetry Analyzer to Accelerate Incident Investigation"
url: https://www.infoq.com/news/2026/07/expedia-ai-observability-star/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-07-23T14:15:00+00:00
fetched_at: 2026-07-24T02:03:40.130975+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Expedia 集團內部開發了 STAR（Service Telemetry Analyzer），一個 AI 輔助的可觀測性平台用於加速生產事件調查。STAR 技術棧包含 FastAPI、Datadog、Celery、Redis 和 Langfuse，形成典型的微服務異步架構。系統採用結構化工作流將服務遙測和 LLM 推理深度整合，自動分析異常信號並生成根本原因評估（RCA）。關鍵設計亮點是保持工程師在決策迴路中，LLM 負責分析層而工程師保留回應決策權。此案例展示了 LLM + 可觀測性融合的實踐方向，驗證了生成式 AI 在運維加速上的具體價值。```mermaid
graph LR
    A[Datadog Telemetry] -->|Service Metrics| B[STAR<br/>Service Telemetry Analyzer]
    B -->|Process| C[LLM Reasoning]
    C -->|Generate| D[RCA Report]
    D -->|Review & Act| E[Engineer Decision]
    F[FastAPI] -.->|API Server| B
    G[Celery + Redis] -.->|Task Queue| B
    H[Langfuse] -.->|Monitoring| C
    style B fill:#4A90E2
    style C fill:#F5A623
    style E fill:#7ED321
```"
key_points:
  - "STAR 整合 Datadog 遙測和 LLM：結構化工作流自動分析異常、生成 RCA"
  - "技術棧：FastAPI + Datadog + Celery + Redis + Langfuse，典型的異步微服務可觀測性架構"
  - "人機協作設計：LLM 負責推理層，工程師保留事件回應決策權，降低誤導風險"
tags: [expedia, observability, incident-investigation, llm-ops, structured-workflows]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Expedia Uses AI Driven Service Telemetry Analyzer to Accelerate Incident Investigation

Expedia 集團內部開發了 STAR（Service Telemetry Analyzer），一個 AI 輔助的可觀測性平台用於加速生產事件調查。STAR 技術棧包含 FastAPI、Datadog、Celery、Redis 和 Langfuse，形成典型的微服務異步架構。系統採用結構化工作流將服務遙測和 LLM 推理深度整合，自動分析異常信號並生成根本原因評估（RCA）。關鍵設計亮點是保持工程師在決策迴路中，LLM 負責分析層而工程師保留回應決策權。此案例展示了 LLM + 可觀測性融合的實踐方向，驗證了生成式 AI 在運維加速上的具體價值。```mermaid
graph LR
    A[Datadog Telemetry] -->|Service Metrics| B[STAR<br/>Service Telemetry Analyzer]
    B -->|Process| C[LLM Reasoning]
    C -->|Generate| D[RCA Report]
    D -->|Review & Act| E[Engineer Decision]
    F[FastAPI] -.->|API Server| B
    G[Celery + Redis] -.->|Task Queue| B
    H[Langfuse] -.->|Monitoring| C
    style B fill:#4A90E2
    style C fill:#F5A623
    style E fill:#7ED321
```

### 重點
- STAR 整合 Datadog 遙測和 LLM：結構化工作流自動分析異常、生成 RCA
- 技術棧：FastAPI + Datadog + Celery + Redis + Langfuse，典型的異步微服務可觀測性架構
- 人機協作設計：LLM 負責推理層，工程師保留事件回應決策權，降低誤導風險

**原文：** [infoq-main](https://www.infoq.com/news/2026/07/expedia-ai-observability-star/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Expedia Group has introduced STAR, an internal AI-assisted observability platform that helps engineers investigate production incidents using service telemetry and LLMs. Built with FastAPI, Datadog, Celery, Redis, and Langfuse, STAR follows structured workflows to analyze telemetry, generate root cause assessments, and support incident response while keeping engineers in the loop. By Leela Kumili

</details>