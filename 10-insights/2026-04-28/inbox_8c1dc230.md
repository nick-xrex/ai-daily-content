---
id: inbox_8c1dc230
date: 2026-04-28
source_ref: "[[00-inbox/2026-04-28/youtube/1257-youtube-ai-engineer-one-login-to-rule-them-all-cross-app-acc-40e5]]"
title: "One Login to Rule Them All: Cross-App Access for MCP — Garrett Galow, WorkOS"
url: https://www.youtube.com/watch?v=EmhRyw6xeT0
source: youtube-ai-engineer
published_at: 2026-04-28T14:00:06+00:00
fetched_at: 2026-05-01T13:18:25.023194+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "WorkOS 產品經理 Garrett Galow 介紹如何解決 MCP 多次登入問題。當前開發者在 Cursor、Anthropic、OpenAI 等應用使用 MCP servers 時，每次授權都需要點擊同意畫面，造成重複困擾；尤其在大型團隊中，數十名開發者頻繁管理授權就變成顯著的生產力問題。WorkOS 提供企業級單點登入（SSO）解決方案，讓用戶通過一次登入即可跨多個 MCP 工具授權，已服務 Anthropic、Cursor、OpenAI 等主要 AI 產品平台。"
key_points:
  - "MCP 目前使用 OAuth，每個 server 需要獨立的同意畫面授權，導致開發者重複手動確認"
  - "企業級多人協作時，同意流程管理成為顯著的工作流摩擦（dozen+ 開發者 × half-dozen MCP servers）"
  - "WorkOS 單點登入方案透過統一授權入口解決此問題，已被業界主流 AI 工具採用"
tags: [mcp-auth, enterprise-dev-ux, sso-integration, developer-platform]
topics: [agents.mcp]
importance: 4
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## One Login to Rule Them All: Cross-App Access for MCP — Garrett Galow, WorkOS

WorkOS 產品經理 Garrett Galow 介紹如何解決 MCP 多次登入問題。當前開發者在 Cursor、Anthropic、OpenAI 等應用使用 MCP servers 時，每次授權都需要點擊同意畫面，造成重複困擾；尤其在大型團隊中，數十名開發者頻繁管理授權就變成顯著的生產力問題。WorkOS 提供企業級單點登入（SSO）解決方案，讓用戶通過一次登入即可跨多個 MCP 工具授權，已服務 Anthropic、Cursor、OpenAI 等主要 AI 產品平台。

### 重點
- MCP 目前使用 OAuth，每個 server 需要獨立的同意畫面授權，導致開發者重複手動確認
- 企業級多人協作時，同意流程管理成為顯著的工作流摩擦（dozen+ 開發者 × half-dozen MCP servers）
- WorkOS 單點登入方案透過統一授權入口解決此問題，已被業界主流 AI 工具採用

**原文：** [youtube-ai-engineer](https://www.youtube.com/watch?v=EmhRyw6xeT0)