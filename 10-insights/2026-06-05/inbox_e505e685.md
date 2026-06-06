---
id: inbox_e505e685
date: 2026-06-05
source_ref: "[[00-inbox/2026-06-05/1800-infoq-main-presentation-platform-teams-enabling-ai-de62]]"
title: "Presentation: Platform Teams Enabling AI - MCP/Multi-Agentic Tools Across Linkedin"
url: https://www.infoq.com/presentations/ai-multi-agentic-tools/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-06-05T12:23:00+00:00
fetched_at: 2026-06-05T18:07:25.850400+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "LinkedIn 工程團隊在 InfoQ 分享大規模 AI 代理部署經驗，揭露透過 MCP（Model Context Protocol）實現多代理協調的平台架構。該團隊已在生產環境中部署編碼、系統觀測（observability）和 UI 測試代理，強調結構化上下文、安全工具和統一編排層的必要性，藉此超越零散的點狀實驗，達成企業級 AI 工具集成的可擴展性。"
key_points:
  - "MCP 為多代理的標準協議，LinkedIn 用其統一編碼、觀測、UI 測試代理的編排"
  - "平台抽象層（類似 Kubernetes 對容器的作用）讓工程師無需重複實現代理集成"
  - "結構化上下文和安全工具是大規模部署的核心（不只是模型能力）"
tags: [mcp, multi-agent, platform-engineering, linkedin, ai-tooling]
topics: [agents.mcp]
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Presentation: Platform Teams Enabling AI - MCP/Multi-Agentic Tools Across Linkedin

LinkedIn 工程團隊在 InfoQ 分享大規模 AI 代理部署經驗，揭露透過 MCP（Model Context Protocol）實現多代理協調的平台架構。該團隊已在生產環境中部署編碼、系統觀測（observability）和 UI 測試代理，強調結構化上下文、安全工具和統一編排層的必要性，藉此超越零散的點狀實驗，達成企業級 AI 工具集成的可擴展性。

### 重點
- MCP 為多代理的標準協議，LinkedIn 用其統一編碼、觀測、UI 測試代理的編排
- 平台抽象層（類似 Kubernetes 對容器的作用）讓工程師無需重複實現代理集成
- 結構化上下文和安全工具是大規模部署的核心（不只是模型能力）

**原文：** [infoq-main](https://www.infoq.com/presentations/ai-multi-agentic-tools/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

LinkedIn’s Karthik Ramgopal and Prince Valluri discuss leveraging AI as a new execution model for large-scale engineering. They explain how to move beyond fragmented implementations by building platform abstractions for orchestration, structured context, and safe tooling like MCP. They share architectural insights from real-world coding, observation, and UI testing agents built at LinkedIn. By Karthik Ramgopal, Prince Valluri

</details>