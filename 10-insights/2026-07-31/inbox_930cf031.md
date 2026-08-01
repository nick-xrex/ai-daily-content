---
id: inbox_930cf031
date: 2026-07-31
source_ref: "[[00-inbox/2026-07-31/2353-infoq-main-dropbox-integrates-mcp-and-dash-to-close-8a7a]]"
title: "Dropbox Integrates MCP and Dash to Close the Gap Between Security Design and Code Review"
url: https://www.infoq.com/news/2026/07/dropbox-mcp-ai-code-review/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-07-31T14:36:00+00:00
fetched_at: 2026-08-01T04:21:41.856370+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Dropbox 通過整合 Model Context Protocol (MCP) 與其內部知識平台 Dash，在 AI 輔助代碼審查工作流中實現了安全設計上下文的自動注入。該系統在開發者提交 pull request 時主動檢索相關的威脅模型和安全需求文檔，並將這些關鍵上下文提供給 AI 審查工具參考。這樣做的目的是幫助代碼審查員更有效地驗證新代碼實現是否與原始安全設計意圖保持對齊。案例展示了 MCP 在企業代碼治理中的實踐價值，通過自動化知識流通，縮小了架構設計與代碼審查之間的認知差距。InfoQ 對此進行了深入 Q&A 訪談，記錄了該系統的架構設計和實施過程中的核心經驗教訓。"
key_points:
  - "MCP 與 Dash 整合實現安全設計上下文在代碼審查中的自動注入和檢索"
  - "系統在 pull request 時主動拉取威脅模型和安全需求，供 AI 輔助審查驗證實現對齊度"
  - "展示了 MCP 在企業代碼治理中的實踐模式，通過自動化上下文流通改善設計與審查的連結"
tags: [mcp, code-review, security, ai-assisted-review, enterprise-ai]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: true
deep_dive_approved: false
---

## Dropbox Integrates MCP and Dash to Close the Gap Between Security Design and Code Review

Dropbox 通過整合 Model Context Protocol (MCP) 與其內部知識平台 Dash，在 AI 輔助代碼審查工作流中實現了安全設計上下文的自動注入。該系統在開發者提交 pull request 時主動檢索相關的威脅模型和安全需求文檔，並將這些關鍵上下文提供給 AI 審查工具參考。這樣做的目的是幫助代碼審查員更有效地驗證新代碼實現是否與原始安全設計意圖保持對齊。案例展示了 MCP 在企業代碼治理中的實踐價值，通過自動化知識流通，縮小了架構設計與代碼審查之間的認知差距。InfoQ 對此進行了深入 Q&A 訪談，記錄了該系統的架構設計和實施過程中的核心經驗教訓。

### 重點
- MCP 與 Dash 整合實現安全設計上下文在代碼審查中的自動注入和檢索
- 系統在 pull request 時主動拉取威脅模型和安全需求，供 AI 輔助審查驗證實現對齊度
- 展示了 MCP 在企業代碼治理中的實踐模式，通過自動化上下文流通改善設計與審查的連結

**原文：** [infoq-main](https://www.infoq.com/news/2026/07/dropbox-mcp-ai-code-review/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Dropbox has integrated Model Context Protocol (MCP) with its internal knowledge platform, Dash, to surface security design context during AI assisted code reviews. The system retrieves threat models and security requirements for pull requests, helping reviewers validate implementation against design intent. An InfoQ Q&amp;A explores the architecture and key lessons learned. By Leela Kumili

</details>