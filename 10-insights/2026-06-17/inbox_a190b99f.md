---
id: inbox_a190b99f
date: 2026-06-17
source_ref: "[[00-inbox/2026-06-17/2200-infoq-architecture-ai-agent-identity-and-permission-challen-6309]]"
title: "AI Agent Identity and Permission Challenges: How Uber and Auth0 Are Rethinking Access Control"
url: https://www.infoq.com/news/2026/06/ai-agent-identity-uber-auth0/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-06-17T12:15:00+00:00
fetched_at: 2026-06-17T22:11:39.309049+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Uber 發表了內部架構設計，展示如何在多代理 AI 工作流中可靠地傳播用戶身份。該設計的三個核心目標是保留用戶上下文、維護代理來源的可追蹤性，以及實施作用域訪問控制，確保代理在委託工作和調用內部工具時受到適當的權限約束。Auth0 認為 AI 代理需要基於委託權限 (delegated authority)、作用域憑證 (scoped credentials) 和明確人類批准邊界的多層權限機制。此案例研究對於設計安全可控的生產級多代理系統提供了重要的架構參考。"
key_points:
  - "Uber 案例：多代理工作流中的身份傳播與作用域訪問控制架構，保留用戶上下文和代理出處"
  - "Auth0 權限模型三層：委託權限 + 作用域憑證 + 明確人類批准邊界"
  - "實踐意義：代理調用內部工具時需維持正確的用戶上下文和動態權限邊界"
tags: [ai-agent-identity, multi-agent-workflow, access-control, delegation-authority]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## AI Agent Identity and Permission Challenges: How Uber and Auth0 Are Rethinking Access Control

Uber 發表了內部架構設計，展示如何在多代理 AI 工作流中可靠地傳播用戶身份。該設計的三個核心目標是保留用戶上下文、維護代理來源的可追蹤性，以及實施作用域訪問控制，確保代理在委託工作和調用內部工具時受到適當的權限約束。Auth0 認為 AI 代理需要基於委託權限 (delegated authority)、作用域憑證 (scoped credentials) 和明確人類批准邊界的多層權限機制。此案例研究對於設計安全可控的生產級多代理系統提供了重要的架構參考。

### 重點
- Uber 案例：多代理工作流中的身份傳播與作用域訪問控制架構，保留用戶上下文和代理出處
- Auth0 權限模型三層：委託權限 + 作用域憑證 + 明確人類批准邊界
- 實踐意義：代理調用內部工具時需維持正確的用戶上下文和動態權限邊界

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/06/ai-agent-identity-uber-auth0/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Uber recently described an internal architecture for propagating identity across multi-agent AI workflows. The design aims to perserve user context, agent provenance, and scoped access as agents delegate work and call internal tools. The case study aligns with Auth0’s view that AI agents need permissions based on delegated authority, scoped credentials, and explicit human approval boundaries. By Eran Stiller

</details>