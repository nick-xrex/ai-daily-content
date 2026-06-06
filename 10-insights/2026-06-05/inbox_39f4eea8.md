---
id: inbox_39f4eea8
date: 2026-06-05
source_ref: "[[00-inbox/2026-06-05/1800-medium-tag-claude-stop-burning-tokens-on-headers-nobody-ca-08e2]]"
title: "Stop Burning Tokens on Headers Nobody Cares About: A Smarter Burp MCP Extension"
url: https://medium.com/@hammadhassan924/stop-burning-tokens-on-headers-nobody-cares-about-a-smarter-burp-mcp-extension-06b5a34f93da?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-06-05T17:01:10+00:00
fetched_at: 2026-06-05T18:12:11.120297+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "工程師在 PortSwigger MCP 伺服器上層開發 session-variable 層級，過濾掉動態應用安全測試（DAST）中冗餘的 HTTP headers，減少發送給 Claude 等 LLM 的無用 token。實測每次請求的 token 消耗可減少最多 59%。該方案直接適用於 Burp Suite + Claude 工作流，通過上游資訊過濾優化 token 效率和成本。"
key_points:
  - "PortSwigger MCP 上開發 session-variable 層級，智能過濾 HTTP headers"
  - "每次請求減少 token 消耗最多 59%，成本優化顯著"
  - "無需修改核心業務邏輯，直接適配 Burp + Claude 工作流"
tags: [mcp, token-optimization, burp-suite, cost-reduction]
topics: [agents.mcp]
importance: 3
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Stop Burning Tokens on Headers Nobody Cares About: A Smarter Burp MCP Extension

工程師在 PortSwigger MCP 伺服器上層開發 session-variable 層級，過濾掉動態應用安全測試（DAST）中冗餘的 HTTP headers，減少發送給 Claude 等 LLM 的無用 token。實測每次請求的 token 消耗可減少最多 59%。該方案直接適用於 Burp Suite + Claude 工作流，通過上游資訊過濾優化 token 效率和成本。

### 重點
- PortSwigger MCP 上開發 session-variable 層級，智能過濾 HTTP headers
- 每次請求減少 token 消耗最多 59%，成本優化顯著
- 無需修改核心業務邏輯，直接適配 Burp + Claude 工作流

**原文：** [medium-tag-claude](https://medium.com/@hammadhassan924/stop-burning-tokens-on-headers-nobody-cares-about-a-smarter-burp-mcp-extension-06b5a34f93da?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

How we engineered a session-variable layer on top of the PortSwigger MCP server &#x2014; and cut AI token consumption by up to 59% per request. Continue reading on Medium »

</details>