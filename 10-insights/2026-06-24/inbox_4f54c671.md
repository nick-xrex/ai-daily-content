---
id: inbox_4f54c671
date: 2026-06-24
source_ref: "[[00-inbox/.../inbox_4f54c671]]"
title: "simonw/browser-compat-db"
url: https://simonwillison.net/2026/Jun/24/browser-compat-db/#atom-everything
source: simon-willison
published_at: 2026-06-24T23:59:03+00:00
fetched_at: 2026-06-29T02:00:52.058242+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 將 Mozilla 的 browser-compat-data 倉庫（包含完整瀏覽器相容性資料）轉換為約 66MB 的 SQLite 資料庫。過程使用 Claude Code (Opus 4.8) 生成 sqlite-utils 轉換腳本，Codex Desktop (GPT-5.5) 建立 GitHub Actions 工作流實現自動化構建與發佈。資料庫託管於 GitHub 倉庫（而非 releases）以獲得開放 CORS 跨域標頭支援，可用 Datasette Lite 進行線上互動探索。該專案受 Mozilla 新發佈的 MDN MCP 服務啟發。"
key_points:
  - "使用 Claude Code (Opus 4.8) 與 Codex (GPT-5.5) 的 AI 輔助程式設計：自動生成資料轉換與 CI/CD 工作流程"
  - "GitHub orphan 分支託管策略：繞過 releases 的 CORS 限制，在倉庫檔案層提供開放跨域存取"
  - "66MB SQLite 資料庫涵蓋完整瀏覽器相容性資訊，可透過 Datasette Lite 進行互動查詢與探索"
tags: [ai-assisted-programming, datasette-lite, sqlite, github-actions, mdn]
topics: [foundation_models.claude, foundation_models.gpt, agents.mcp]
importance: 3
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## simonw/browser-compat-db

Simon Willison 將 Mozilla 的 browser-compat-data 倉庫（包含完整瀏覽器相容性資料）轉換為約 66MB 的 SQLite 資料庫。過程使用 Claude Code (Opus 4.8) 生成 sqlite-utils 轉換腳本，Codex Desktop (GPT-5.5) 建立 GitHub Actions 工作流實現自動化構建與發佈。資料庫託管於 GitHub 倉庫（而非 releases）以獲得開放 CORS 跨域標頭支援，可用 Datasette Lite 進行線上互動探索。該專案受 Mozilla 新發佈的 MDN MCP 服務啟發。

### 重點
- 使用 Claude Code (Opus 4.8) 與 Codex (GPT-5.5) 的 AI 輔助程式設計：自動生成資料轉換與 CI/CD 工作流程
- GitHub orphan 分支託管策略：繞過 releases 的 CORS 限制，在倉庫檔案層提供開放跨域存取
- 66MB SQLite 資料庫涵蓋完整瀏覽器相容性資訊，可透過 Datasette Lite 進行互動查詢與探索

**原文：** [simon-willison](https://simonwillison.net/2026/Jun/24/browser-compat-db/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# simonw/browser-compat-db

simonw/browser-compat-db 
Inspired by Mozilla's new MDN MCP service - source code here - I decided to try converting their comprehensive mdn/browser-compat-data repository full of browser compatibility data into a SQLite database. 
 This new GitHub repo includes a Claude Code for web (Opus 4.8) generated script for doing that using sqlite-utils . 
 I wanted the resulting ~66MB SQLite database to be available via the GitHub CDN with open CORS headers. GitHub releases don't have those, but any file stored in a regular GitHub repository does - so I had Codex Desktop (GPT-5.5) build a GitHub Actions workflow that builds the database and then force-pushes it to a db "orphan" branch. 
 You can download the resulting database from here , and since it's hosted with open CORS headers you can also explore it with Datasette Lite .

 Tags: github , mozilla , projects , github-actions , datasette-lite , ai-assisted-programming , model-context-protocol , mdn

</details>