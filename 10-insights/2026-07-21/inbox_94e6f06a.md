---
id: inbox_94e6f06a
date: 2026-07-21
source_ref: "[[00-inbox/2026-07-21/0015-claude-code-releases-v2-1-217-b8ab]]"
title: "v2.1.217"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.217
source: claude-code-releases
published_at: 2026-07-21T21:35:10+00:00
fetched_at: 2026-07-22T00:21:40.207221+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.217 發布多項穩定性和安全改進。新增 emoji 快速輸入功能（輸入 :heart: 自動轉換為 ❤️）、修復記憶體洩漏問題（MCP 工具輸出截斷時保留完整結果導致洩漏）、修復 Windows 自動更新失敗後遺留 claude.exe 缺失的問題。此版本也修復企業環境設定（mTLS、TLS-verify、OAuth scope、代理）被忽視的問題，強化背景會話隔離（canonicalize symlinked 目錄防止逃逸）。新增並發子代理限制（預設 20 個，CLAUDE_CODE_MAX_CONCURRENT_SUBAGENTS 可調）防止單一訊息無限 fan-out，修改子代理預設不生成嵌套代理以降低複雜度，且 --max-budget-usd 現在能正確停止背景子代理執行。"
key_points:
  - "新增 emoji 快速輸入及並發子代理限制（預設 20）防止無界 fan-out"
  - "修復 MCP 工具輸出截斷導致的記憶體洩漏、Windows 自動更新缺失執行檔、企業 mTLS/TLS/OAuth 設定被忽視"
  - "budget 約束現生效於背景子代理停止，子代理預設不嵌套以穩定複雜度"
tags: [claude-code, memory-leak-fix, agent-concurrency-limit, windows-reliability, enterprise-security]
topics: [foundation_models.claude]
importance: 4
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.217

Claude Code v2.1.217 發布多項穩定性和安全改進。新增 emoji 快速輸入功能（輸入 :heart: 自動轉換為 ❤️）、修復記憶體洩漏問題（MCP 工具輸出截斷時保留完整結果導致洩漏）、修復 Windows 自動更新失敗後遺留 claude.exe 缺失的問題。此版本也修復企業環境設定（mTLS、TLS-verify、OAuth scope、代理）被忽視的問題，強化背景會話隔離（canonicalize symlinked 目錄防止逃逸）。新增並發子代理限制（預設 20 個，CLAUDE_CODE_MAX_CONCURRENT_SUBAGENTS 可調）防止單一訊息無限 fan-out，修改子代理預設不生成嵌套代理以降低複雜度，且 --max-budget-usd 現在能正確停止背景子代理執行。

### 重點
- 新增 emoji 快速輸入及並發子代理限制（預設 20）防止無界 fan-out
- 修復 MCP 工具輸出截斷導致的記憶體洩漏、Windows 自動更新缺失執行檔、企業 mTLS/TLS/OAuth 設定被忽視
- budget 約束現生效於背景子代理停止，子代理預設不嵌套以穩定複雜度

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.217)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added emoji shortcode autocomplete in the prompt input: type :heart: to insert ❤️, or :hea for suggestions — disable with the emojiCompletionEnabled setting 
 Added warnings when transcript writes are failing (e.g. disk full) or when session saving is off due to an inherited environment variable, instead of losing transcripts silently 
 Fixed a memory leak where truncated MCP tool outputs kept the full untruncated result in memory for the rest of the session 
 Fixed Windows auto-update failures that could leave claude.exe missing; failed updates now restore the preserved executable automatically 
 Fixed background session isolation not canonicalizing symlinked working directories, which could let sessions escape their workspace folder 
 Fixed auto-compact never triggering for Claude Opus 4.8 on Bedrock and /compact failing once over the limit 
 Fixed corporate mTLS, TLS-verify, OAuth scope, and proxy settings being ignored in Claude Desktop sessions 
 Fixed screen reader mode's startup announcement being cut off by the first prompt render, and the thinking status row re-rendering every few seconds to update elapsed time and token counts 
 Fixed managed settings that set OTEL_EXPORTER_OTLP_ENDPOINT not governing all signals — lower-scope signal-specific overrides no longer redirect telemetry away from the managed endpoint 
 Fixed --resume / --continue and /resume failing with a TypeError when a transcript has a malformed attachment entry 
 Fixed Remote Control sessions not showing a pending permission prompt or dialog to viewers that connected after it appeared 
 Fixed background shells sometimes becoming impossible to stop after a session is sent to the background ( /background or ← ) or when the session exits on a heavily loaded machine, most visible on Windows 
 Fixed a CLAUDE.md or SKILL.md paths frontmatter value with many brace groups OOM-killing or stalling the CLI at startup — brace expansion is now budget-bounded 
 Fixed the transcript preview sitting flush against the input area when attaching to a starting background session; it now leaves the same one-line gap as the live layout, so the transcript no longer shifts when the session takes over 
 Improved footer PR badge links to be clickable hyperlinks even when terminal support can't be detected (e.g. over ssh/tmux); set FORCE_HYPERLINK=0 to opt out 
 Changed the login-expiry warning to appear 3 days before expiry instead of 5 
 Capped the frontend-design plugin suggestion tip at 3 lifetime impressions instead of repeating indefinitely 
 Added a cap on concurrently-running subagents (default 20, override with CLAUDE_CODE_MAX_CONCURRENT_SUBAGENTS ) so one message can't fan out unbounded background agents 
 Changed subagents to no longer spawn nested subagents by default; set CLAUDE_CODE_MAX_SUBAGENT_SPAWN_DEPTH to allow deeper nesting 
 Fixed --max-budget-usd not stopping background subagents: once the cap is reached, new spawns are denied and running background agents are halted

</details>