---
id: inbox_1c647b5e
date: 2026-08-07
source_ref: "[[00-inbox/.../inbox_1c647b5e]]"
title: "Presentation: Rewriting All of Spotify&#39;s Code Base, All the Time"
url: https://www.infoq.com/presentations/spotify-ai-codebase-migration-agent/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-08-07T11:00:00+00:00
fetched_at: 2026-08-11T01:20:53.148860+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Spotify 開發 Honk 代理進行艦隊級代碼庫遷移，涉及數千個工程倉庫的複雜重構。Jo Kelly-Fenton 和 Aleksandar Mitic 分享的核心架構洞察：（1）分離 CI 驗證與 AI agents 決策迴圈，避免驗證瓶頸卡住規劃；（2）處理自動 PR 生成的大規模並行化；（3）跨倉庫標準化推動。展示企業規模 AI 代理的關鍵設計模式。"
key_points:
  - "Honk 核心架構：分離 CI 驗證與 AI agent 迴圈，解決並行 PR 生成瓶頸"
  - "規模化策略：跨數千倉庫標準化推動，需重新設計 agent 調度和驗證模式"
  - "框架洞察：CI 作非同步驗證層、agent 專注規劃與生成，二者解耦避免阻塞"
tags: [spotify-honk, codebase-migration, large-scale-automation, ai-agents, ci-cd]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Presentation: Rewriting All of Spotify's Code Base, All the Time

Spotify 開發 Honk 代理進行艦隊級代碼庫遷移，涉及數千個工程倉庫的複雜重構。Jo Kelly-Fenton 和 Aleksandar Mitic 分享的核心架構洞察：（1）分離 CI 驗證與 AI agents 決策迴圈，避免驗證瓶頸卡住規劃；（2）處理自動 PR 生成的大規模並行化；（3）跨倉庫標準化推動。展示企業規模 AI 代理的關鍵設計模式。

### 重點
- Honk 核心架構：分離 CI 驗證與 AI agent 迴圈，解決並行 PR 生成瓶頸
- 規模化策略：跨數千倉庫標準化推動，需重新設計 agent 調度和驗證模式
- 框架洞察：CI 作非同步驗證層、agent 專注規劃與生成，二者解耦避免阻塞

**原文：** [infoq-main](https://www.infoq.com/presentations/spotify-ai-codebase-migration-agent/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Presentation: Rewriting All of Spotify's Code Base, All the Time

Jo Kelly-Fenton and Aleksandar Mitic explain how Spotify created "Honk," an AI coding agent, to handle complex fleet-wide codebase migrations. They share key architectural insights on decoupling CI verification runtimes from AI agents, dealing with automated pull request bottlenecks, and driving aggressive standardization across thousands of engineering repositories. By Jo Kelly-Fenton, Aleksandar Mitic

</details>