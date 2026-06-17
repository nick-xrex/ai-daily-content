---
id: inbox_8f08fe47
date: 2026-06-17
source_ref: "[[00-inbox/2026-06-17/2200-infoq-main-ai-agent-identity-and-permission-challen-1c85]]"
title: "AI Agent Identity and Permission Challenges: How Uber and Auth0 Are Rethinking Access Control"
url: https://www.infoq.com/news/2026/06/ai-agent-identity-uber-auth0/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-06-17T12:15:00+00:00
fetched_at: 2026-06-17T22:06:59.638959+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Uber 公開了多代理 AI 工作流中的身份傳播架構，旨在代理委派工作和呼叫內部工具時保留使用者上下文、追蹤代理來源、實施 scoped 存取權限。Auth0 呼應此觀點，強調 AI 代理的權限管理應基於三原則：委托授權（delegated authority）、scoped credentials、和明確的人工批准邊界。該案例研究反映業界對多代理系統身份管理的共同認識，對構建安全、可審計的多代理企業系統具有實踐參考價值。"
key_points:
  - "Uber 架構三要素：使用者上下文保留、代理溯源追蹤、scoped 存取權限"
  - "Auth0 權限模型：委托授權、scoped credentials、人工批准邊界"
  - "工業應用：多代理系統身份與權限管理的最佳實踐"
tags: [agent-identity, multi-agent-workflow, access-control, delegated-authority]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## AI Agent Identity and Permission Challenges: How Uber and Auth0 Are Rethinking Access Control

Uber 公開了多代理 AI 工作流中的身份傳播架構，旨在代理委派工作和呼叫內部工具時保留使用者上下文、追蹤代理來源、實施 scoped 存取權限。Auth0 呼應此觀點，強調 AI 代理的權限管理應基於三原則：委托授權（delegated authority）、scoped credentials、和明確的人工批准邊界。該案例研究反映業界對多代理系統身份管理的共同認識，對構建安全、可審計的多代理企業系統具有實踐參考價值。

### 重點
- Uber 架構三要素：使用者上下文保留、代理溯源追蹤、scoped 存取權限
- Auth0 權限模型：委托授權、scoped credentials、人工批准邊界
- 工業應用：多代理系統身份與權限管理的最佳實踐

**原文：** [infoq-main](https://www.infoq.com/news/2026/06/ai-agent-identity-uber-auth0/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Uber recently described an internal architecture for propagating identity across multi-agent AI workflows. The design aims to perserve user context, agent provenance, and scoped access as agents delegate work and call internal tools. The case study aligns with Auth0’s view that AI agents need permissions based on delegated authority, scoped credentials, and explicit human approval boundaries. By Eran Stiller

</details>