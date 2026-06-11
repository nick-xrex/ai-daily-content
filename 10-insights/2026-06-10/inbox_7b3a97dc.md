---
id: inbox_7b3a97dc
date: 2026-06-10
source_ref: "[[00-inbox/.../inbox_7b3a97dc]]"
title: "v2.1.172"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.172
source: claude-code-releases
published_at: 2026-06-10T20:44:15+00:00
fetched_at: 2026-06-11T00:19:45.613643+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.172 發布，引入多項重大功能和修復。最值得注意的新功能是 sub-agents 現在可以遞迴生成自己的 sub-agents，最多支援 5 層深，大幅擴展代理系統的複雜度和自動化潛力。Amazon Bedrock 改進包括支援從 ~/.aws config 自動讀取 AWS region，遵循 AWS SDK 的優先順序邏輯。此版本修復了超過 20 個 bug，其中最關鍵的是修復了 1M context 邊界情況下 session 永久卡頓的問題，現在系統會自動壓縮回標準 context 限制。其他重要修復包括背景 agent 讀取錯誤目錄設定、availableModels 限制失效於 subagent、model ID 重複後綴問題等。性能改進方面，減少了空閒 CPU 使用，改進了 Chrome 工具加載批量化，以及修復了 WebFetch 通配符規則。"
key_points:
  - "Sub-agents 支援遞迴生成最多 5 層深的 sub-agents，擴展代理系統複雜度和自動化潛力"
  - "修復 1M context 無使用額度 session 永久卡頓問題，現自動壓縮回標準 context 限制"
  - "Amazon Bedrock 支援從 ~/.aws config 讀取 region（遵循 AWS SDK 優先順序），availableModels 限制現對 subagent 生效"
tags: [claude-code, sub-agents, bedrock, context-management, bug-fixes]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.172

Claude Code v2.1.172 發布，引入多項重大功能和修復。最值得注意的新功能是 sub-agents 現在可以遞迴生成自己的 sub-agents，最多支援 5 層深，大幅擴展代理系統的複雜度和自動化潛力。Amazon Bedrock 改進包括支援從 ~/.aws config 自動讀取 AWS region，遵循 AWS SDK 的優先順序邏輯。此版本修復了超過 20 個 bug，其中最關鍵的是修復了 1M context 邊界情況下 session 永久卡頓的問題，現在系統會自動壓縮回標準 context 限制。其他重要修復包括背景 agent 讀取錯誤目錄設定、availableModels 限制失效於 subagent、model ID 重複後綴問題等。性能改進方面，減少了空閒 CPU 使用，改進了 Chrome 工具加載批量化，以及修復了 WebFetch 通配符規則。

### 重點
- Sub-agents 支援遞迴生成最多 5 層深的 sub-agents，擴展代理系統複雜度和自動化潛力
- 修復 1M context 無使用額度 session 永久卡頓問題，現自動壓縮回標準 context 限制
- Amazon Bedrock 支援從 ~/.aws config 讀取 region（遵循 AWS SDK 優先順序），availableModels 限制現對 subagent 生效

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.172)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v2.1.172

What's changed 
 
 Sub-agents can now spawn their own sub-agents (up to 5 levels deep) 
 Amazon Bedrock now reads the AWS region from ~/.aws config files when AWS_REGION isn't set, matching AWS SDK precedence; /status shows where the region came from 
 Added a search bar when browsing a marketplace's plugins in /plugin 
 Added model attribute to the claude_code.lines_of_code.count OTEL metric 
 Fixed sessions using 1M context without usage credits getting permanently stuck — the session now automatically compacts back under the standard context limit 
 Fixed a repeating "an image in the conversation could not be processed and was removed" error when the conversation contained multiple images 
 Fixed the agents view keeping a session under Working with a busy spinner for up to 30 seconds after the worker replied 
 Fixed background agents potentially reading another directory's project settings ( .mcp.json approvals, trust) when dispatched onto a pre-warmed worker 
 Fixed background-session attach failing with EAUTH for sessions started on an older version after the daemon auto-updated 
 Fixed a background sub-agent staying stuck as "active" in the agent panel after a nested agent it spawned was stopped 
 Fixed /model suggestions in the claude agents dispatch input rendering with a misleading slash prefix and showing models disabled for your org 
 Fixed availableModels restrictions not being applied to subagent model overrides, the agent dispatch model picker, and the advisor model 
 Fixed availableModels allowlists hiding the /model picker's Opus and Sonnet 1M rows when entries use version-specific IDs like claude-opus-4-8 
 Fixed the /model picker on Bedrock offering models the provider doesn't serve — selecting one silently switched the session model and lit the selection marker on multiple rows 
 Fixed model IDs getting a doubled 1M-context suffix (e.g. [1M][1m] ) when ANTHROPIC_DEFAULT_OPUS_MODEL already includes one 
 Fixed opusplan model setting not shipping with 1M context in plan mode for entitled users; the opusplan[1m] workaround now also correctly switches to Opus in plan mode 
 Fixed WebFetch(domain:*.example.com) wildcard domain rules never matching subdomains in allow, deny, and ask position, and file permission rules with mid-pattern wildcards (e.g. Read(secrets-*/config.json) ) being rejected at startup 
 Fixed up-arrow prompt history showing the main agent's prompts while a subagent's chat tab is open 
 Fixed memory recall not finding mounted team memory stores ( CLAUDE_MEMORY_STORES ) in remote sessions 
 Fixed workflow validation rejecting scripts whose prompt strings or comments merely mention Date.now() / Math.random() 
 Disable mouse tracking on Windows consoles that don't fully support it 
 Fixed the /plugin marketplace list losing its cursor after backing out of a long plugin list, and Esc from the plugin browser returning to the wrong tab 
 Improved performance in long conversations by removing redundant message normalization and avoiding full message-history transforms when streaming tool-use state is unchanged 
 Reduced idle CPU usage: /goal status chip no longer re-renders the terminal at 5 Hz while idle, and fewer UI re-renders while subagents run in parallel 
 Improved Claude in Chrome tool loading: browser tools now load in a single batched call instead of one per tool 
 Improved the non-interactive Usage Policy refusal message to suggest starting a new session or changing your model 
 /code-review now keeps the ultra option visible when you're not signed in to claude.ai, with an explanation that the cloud review requires a claude.ai account 
 Shortened the Remote Control footer indicator to "/rc active" and hid it on narrow terminals 
 Stopped promoting /loop in remote sessions, where pending loops don't keep the container alive 
 [VSCode] Fixed PowerShell tool calls rendering as raw JSON instead of a proper command display and permission dialog, and stripped ANSI escape codes from displayed shell output

</details>