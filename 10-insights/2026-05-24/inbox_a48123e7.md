---
id: inbox_a48123e7
date: 2026-05-24
source_ref: "[[00-inbox/2026-05-24/0011-infoq-ai-ml-google-introduces-middleware-architectur-eef9]]"
title: "Google Introduces Middleware Architecture for Genkit Applications"
url: https://www.infoq.com/news/2026/05/google-genkit-middleware/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering
source: infoq-ai-ml
published_at: 2026-05-24T17:55:00+00:00
fetched_at: 2026-05-25T00:18:04.587413+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Google 為開源 Genkit 框架新增 Middleware 功能，在 model 調用、tool 執行和 generation loop 等環節提供可編程的攔截層。這一設計讓開發者無須修改應用核心邏輯，就能在執行時注入可靠性、安全性和編排控制。Middleware 通過標準化的攔截點，使生產 AI 系統能更好地應對複雜的 AI 工作流管理需求。該功能對於構建可追蹤、可控的企業級 AI 應用尤其重要。"
key_points:
  - "Middleware 層支援三個攔截點：model calls、tool execution、generation loops"
  - "無須修改應用程式即可在執行時注入可靠性和安全控制，降低成本"
  - "適用於生產環境中需要細粒度編排和可審計性的 AI 系統"
tags: [genkit, middleware, ai-orchestration, production-ai]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Google Introduces Middleware Architecture for Genkit Applications

Google 為開源 Genkit 框架新增 Middleware 功能，在 model 調用、tool 執行和 generation loop 等環節提供可編程的攔截層。這一設計讓開發者無須修改應用核心邏輯，就能在執行時注入可靠性、安全性和編排控制。Middleware 通過標準化的攔截點，使生產 AI 系統能更好地應對複雜的 AI 工作流管理需求。該功能對於構建可追蹤、可控的企業級 AI 應用尤其重要。

### 重點
- Middleware 層支援三個攔截點：model calls、tool execution、generation loops
- 無須修改應用程式即可在執行時注入可靠性和安全控制，降低成本
- 適用於生產環境中需要細粒度編排和可審計性的 AI 系統

**原文：** [infoq-ai-ml](https://www.infoq.com/news/2026/05/google-genkit-middleware/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Google has introduced Middleware for Genkit, its open-source framework for building AI-powered and agentic applications. The update adds a programmable interception layer around model calls, tool execution, and generation loops, giving developers more control over reliability, safety, and orchestration inside production AI systems. By Robert Krzaczyński

</details>