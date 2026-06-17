---
id: inbox_f8742e24
date: 2026-06-17
source_ref: "[[00-inbox/2026-06-17/2200-medium-tag-claude-stop-wasting-tokens-on-mcps-global-scope-600a]]"
title: "Stop wasting tokens on MCPs: Global Scope vs Project Scope"
url: https://akshatnerella.medium.com/stop-wasting-tokens-on-mcps-global-scope-vs-project-scope-d10ad6a16191?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-06-17T20:59:53+00:00
fetched_at: 2026-06-17T22:15:25.689008+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 用戶若啟用多個全域 MCP 伺服器，即使在不使用這些工具的專案中，也會在每個會話開始時為所有伺服器的工具定義付費（耗用 token）。文章建議透過 `claude mcp list` 和 `/context` 命令審計目前設定，並將不常用的 MCP 伺服器從全域（user scope）改為專案（project scope）範圍，以減少不必要的 token 消耗。例如編輯前端程式碼時若啟用了 Splunk 工具就會白白浪費 token。實作變更後需要重新啟動會話才能生效。"
key_points:
  - "MCP 工具定義在會話初始化時全量載入，即使未使用也計費——單一伺服器可能包含十多個工具，十個伺服器會耗費數萬 token"
  - "全域 scope（user level）在每個專案都載入；改用專案 scope（`.mcp.json`）只在特定 repo 中啟用工具可大幅節省成本"
  - "用 `claude mcp list` 審計、移除重複與未使用伺服器、檢查 SessionStart hooks 是否拖累 context——改變後需新會話生效"
tags: [mcp, token-optimization, claude-code, context-management]
topics: [agents.mcp]
importance: 3
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Stop wasting tokens on MCPs: Global Scope vs Project Scope

Claude Code 用戶若啟用多個全域 MCP 伺服器，即使在不使用這些工具的專案中，也會在每個會話開始時為所有伺服器的工具定義付費（耗用 token）。文章建議透過 `claude mcp list` 和 `/context` 命令審計目前設定，並將不常用的 MCP 伺服器從全域（user scope）改為專案（project scope）範圍，以減少不必要的 token 消耗。例如編輯前端程式碼時若啟用了 Splunk 工具就會白白浪費 token。實作變更後需要重新啟動會話才能生效。

### 重點
- MCP 工具定義在會話初始化時全量載入，即使未使用也計費——單一伺服器可能包含十多個工具，十個伺服器會耗費數萬 token
- 全域 scope（user level）在每個專案都載入；改用專案 scope（`.mcp.json`）只在特定 repo 中啟用工具可大幅節省成本
- 用 `claude mcp list` 審計、移除重複與未使用伺服器、檢查 SessionStart hooks 是否拖累 context——改變後需新會話生效

**原文：** [medium-tag-claude](https://akshatnerella.medium.com/stop-wasting-tokens-on-mcps-global-scope-vs-project-scope-d10ad6a16191?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

If you use Claude Code with a few MCP servers, you&#x2019;re probably paying for all of them in every project, even the ones you don&#x2019;t touch. Continue reading on Medium »

</details>