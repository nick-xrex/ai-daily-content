---
id: inbox_fa33ae71
date: 2026-05-04
source_ref: "[[00-inbox/.../inbox_fa33ae71]]"
title: "Agent Skills"
url: https://addyosmani.com/blog/agent-skills/
source: hackernews
published_at: 2026-05-04T21:40:42+00:00
fetched_at: 2026-05-07T01:51:06.063535+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Addison Osmani 介紹 Agent Skills 開源專案（27K GitHub stars），提出透過強制工作流讓 AI coding agents 遵循高級工程師實踐。核心觀察：資深工程師的工作大多不在 diff 中（規格、設計文件、測試、程式碼評審），但 AI agents 預設跳過這些環節直奔「完成」。Agent Skills 包含 20 項技能，組織為 6 個 SDLC 階段（/spec 規格 → /plan 規劃 → /build 構建 → /test 驗證 → /review 評審 → /ship 交付），對應任何成熟工程組織的標準。核心原則「Process over prose」：可執行的工作流（含檢查點和退出條件）比長篇參考文檔更能驅動 AI 執行。"
key_points:
  - "Process over prose：工作流（步驟 + 檢查點 + 退出條件）比文檔更能驅動 AI；anti-rationalization tables 列舉常見藉口強制遵循流程"
  - "6 階段標準 SDLC：複雜功能激活 11+ 技能，小型修復 3 個；每階段都有可驗證的交付物（規格文件、測試、設計決策文檔）"
  - "資深工程核心工作：最重要的工作（設計、測試、審查、scope discipline）預設不顯示在 diff，AI 必須被強制執行以避免生產事故"
tags: [ai-coding-agents, sdlc, engineering-practices, workflows, agent-skills]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## Agent Skills

Addison Osmani 介紹 Agent Skills 開源專案（27K GitHub stars），提出透過強制工作流讓 AI coding agents 遵循高級工程師實踐。核心觀察：資深工程師的工作大多不在 diff 中（規格、設計文件、測試、程式碼評審），但 AI agents 預設跳過這些環節直奔「完成」。Agent Skills 包含 20 項技能，組織為 6 個 SDLC 階段（/spec 規格 → /plan 規劃 → /build 構建 → /test 驗證 → /review 評審 → /ship 交付），對應任何成熟工程組織的標準。核心原則「Process over prose」：可執行的工作流（含檢查點和退出條件）比長篇參考文檔更能驅動 AI 執行。

### 重點
- Process over prose：工作流（步驟 + 檢查點 + 退出條件）比文檔更能驅動 AI；anti-rationalization tables 列舉常見藉口強制遵循流程
- 6 階段標準 SDLC：複雜功能激活 11+ 技能，小型修復 3 個；每階段都有可驗證的交付物（規格文件、測試、設計決策文檔）
- 資深工程核心工作：最重要的工作（設計、測試、審查、scope discipline）預設不顯示在 diff，AI 必須被強制執行以避免生產事故

**原文：** [hackernews](https://addyosmani.com/blog/agent-skills/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Agent Skills

</details>