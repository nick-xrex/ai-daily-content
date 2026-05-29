---
id: inbox_4f091b12
date: 2026-05-28
source_ref: "[[00-inbox/2026-05-28/0000-ruflo-releases-v3-10-5-wizard-init-fixes-0a8a]]"
title: "v3.10.5 — wizard init fixes"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.5
source: ruflo-releases
published_at: 2026-05-28T15:25:50+00:00
fetched_at: 2026-05-29T00:07:13.015465+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.5 修正初始化三項問題：MCP 伺服器金鑰 claude-flow 配置、init 偵測器假陽性、CLAUDE.md 覆蓋前備份。新增 CI 迴歸守衛防止重複。發佈至三個套件（latest/alpha/v3alpha 分發標籤）。"
key_points:
  - "MCP 伺服器金鑰 claude-flow 設定修正"
  - "init 偵測器假陽性修正"
  - "CLAUDE.md 覆蓋前備份邏輯 + CI 迴歸守衛"
tags: [ruflo, bugfix, mcp, init]
topics: [agents.mcp]
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.5 — wizard init fixes

Ruflo v3.10.5 修正初始化三項問題：MCP 伺服器金鑰 claude-flow 配置、init 偵測器假陽性、CLAUDE.md 覆蓋前備份。新增 CI 迴歸守衛防止重複。發佈至三個套件（latest/alpha/v3alpha 分發標籤）。

### 重點
- MCP 伺服器金鑰 claude-flow 設定修正
- init 偵測器假陽性修正
- CLAUDE.md 覆蓋前備份邏輯 + CI 迴歸守衛

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Fixes #2206 (MCP server key claude-flow), #2207 (init detector false-positive), #2208 (CLAUDE.md backup before overwrite). New CI regression guard prevents recurrence. Published to all three packages with latest/alpha/v3alpha dist-tags.

</details>