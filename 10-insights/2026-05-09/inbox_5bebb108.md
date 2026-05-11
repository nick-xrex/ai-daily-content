---
id: inbox_5bebb108
date: 2026-05-09
source_ref: "[[00-inbox/.../inbox_5bebb108]]"
title: "Cloudflare Ships Dynamic Workflows, Bringing Durable Execution to Per-Tenant and Per-Agent Code"
url: https://www.infoq.com/news/2026/05/cloudflare-dynamic-workflows/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-05-09T09:31:00+00:00
fetched_at: 2026-05-11T02:13:51.976547+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Cloudflare 發布 Dynamic Workflows，一個 MIT licensed 庫，擴展其 durable execution 引擎以支援每個 tenant、agent 或 request 在執行時使用不同的 workflow 代碼。該方案建立於 Dynamic Workers 之上，能以近零閒置成本服務百萬級獨立 durable workflow。主要應用場景包括 CI/CD 流程和 agent plan 執行，特別適合多租戶平台在不增加計算成本的前提下為每個客戶定製工作流邏輯。"
key_points:
  - "Dynamic Workflows 基於 Dynamic Workers，workflow 代碼可按 tenant/agent/request 在執行時動態變化"
  - "支援百萬級獨立 durable workflow，閒置成本近乎為零（near-zero idle cost）"
  - "應用於 CI/CD 和 agent plan 執行，特別適合多租戶 SaaS 平台"
tags: [cloudflare, durable-execution, multi-tenant, workflow-automation, serverless]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Cloudflare Ships Dynamic Workflows, Bringing Durable Execution to Per-Tenant and Per-Agent Code

Cloudflare 發布 Dynamic Workflows，一個 MIT licensed 庫，擴展其 durable execution 引擎以支援每個 tenant、agent 或 request 在執行時使用不同的 workflow 代碼。該方案建立於 Dynamic Workers 之上，能以近零閒置成本服務百萬級獨立 durable workflow。主要應用場景包括 CI/CD 流程和 agent plan 執行，特別適合多租戶平台在不增加計算成本的前提下為每個客戶定製工作流邏輯。

### 重點
- Dynamic Workflows 基於 Dynamic Workers，workflow 代碼可按 tenant/agent/request 在執行時動態變化
- 支援百萬級獨立 durable workflow，閒置成本近乎為零（near-zero idle cost）
- 應用於 CI/CD 和 agent plan 執行，特別適合多租戶 SaaS 平台

**原文：** [infoq-main](https://www.infoq.com/news/2026/05/cloudflare-dynamic-workflows/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Cloudflare Ships Dynamic Workflows, Bringing Durable Execution to Per-Tenant and Per-Agent Code

Cloudflare released Dynamic Workflows, an MIT-licensed library that extends its durable execution engine so workflow code can differ per tenant, agent, or request at runtime. Built on Dynamic Workers, the library enables platforms to serve millions of unique durable workflows at near-zero idle cost. CI/CD and agent plan execution are the headline use cases. By Steef-Jan Wiggers

</details>