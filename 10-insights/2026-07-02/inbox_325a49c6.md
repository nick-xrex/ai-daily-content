---
id: inbox_325a49c6
date: 2026-07-02
source_ref: "[[00-inbox/2026-07-02/0115-claude-code-releases-v2-1-199-3750]]"
title: "v2.1.199"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.199
source: claude-code-releases
published_at: 2026-07-02T23:35:18+00:00
fetched_at: 2026-07-04T01:20:23.357714+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.199 修復了多個影響工作流的問題。斜杠技能堆疊調用現在可同時加載最多 5 個技能（之前僅加載第一個），提高了工作流靈活性。SSL/TLS 證書錯誤處理改進，立即失敗並顯示修復提示，避免浪費重試次數。流式響應在 API 中部出錯後現在保留部分輸出，減少信息丟失。後台代理修復了 Linux 自殺崩潰、SSH macOS 啟動失敗、內存不足診斷等問題。"
key_points:
  - "斜杠技能堆疊最多 5 個（/skill-a /skill-b），提高工作流效率"
  - "SSL/TLS 錯誤立即失敗並顯示修復提示，避免浪費重試次數"
  - "後台代理修復 Linux 自殺崩潰、SSH 啟動失敗、內存不足診斷等問題"
tags: [claude-code, skill-stacking, ssl-error, background-agent]
topics: []
importance: 3
novelty: 2
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.199

Claude Code v2.1.199 修復了多個影響工作流的問題。斜杠技能堆疊調用現在可同時加載最多 5 個技能（之前僅加載第一個），提高了工作流靈活性。SSL/TLS 證書錯誤處理改進，立即失敗並顯示修復提示，避免浪費重試次數。流式響應在 API 中部出錯後現在保留部分輸出，減少信息丟失。後台代理修復了 Linux 自殺崩潰、SSH macOS 啟動失敗、內存不足診斷等問題。

### 重點
- 斜杠技能堆疊最多 5 個（/skill-a /skill-b），提高工作流效率
- SSL/TLS 錯誤立即失敗並顯示修復提示，避免浪費重試次數
- 後台代理修復 Linux 自殺崩潰、SSH 啟動失敗、內存不足診斷等問題

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.199)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Stacked slash-skill invocations like /skill-a /skill-b do XYZ now load all leading skills (up to 5), not just the first 
 Fixed SSL certificate errors (TLS-inspecting proxies, missing NODE_EXTRA_CA_CERTS , expired certs) burning retries before showing actionable guidance — they now fail immediately with the fix hint 
 Fixed streaming responses being discarded when the API emits a mid-stream overloaded/server error after partial output — the partial is now kept with an incomplete-response notice 
 Fixed subagents cut off by a rate limit or server error silently failing instead of returning their partial work to the parent 
 Fixed subagents reporting API errors (e.g. usage limit reached) as successful results — the error is now reported to the parent agent 
 Fixed the background-agent daemon on Linux killing itself and every running agent every ~50 seconds after an unclean shutdown left a corrupted worker record 
 Fixed background agents failing to cold-start over SSH on macOS with "Could not switch to audit session" (regression in 2.1.196) 
 Fixed claude stop being silently undone when it raced a background-agent respawn — the respawn now honors the stop 
 Fixed background job progress indicators stalling for minutes while the job ran long commands 
 Fixed background sessions on memory-starved machines showing a generic error — they now indicate low memory and suggest freeing resources 
 Fixed remote sessions briefly flapping between Working and Idle in the agent view when a background agent completes 
 Fixed idle subagents vanishing from the agent panel while other subagents were still working; surplus idle agents now collapse into an expandable summary row 
 Fixed typing /model or /fast while viewing a subagent silently opening the lead's model picker — a notice now explains the command applies to the lead 
 Fixed SessionStart , Setup , and SubagentStart hooks silently hiding stderr when exiting with code 2 — the error is now shown in the transcript 
 Fixed claude --dangerously-skip-permissions daemon &lt;subcommand&gt; being treated as a chat prompt instead of running the subcommand 
 Fixed SendMessage silently misrouting when a re-spawned agent reuses a previous agent's name — the tool now detects the mismatch and asks the caller to retarget 
 Fixed opening or resuming a session with no new messages needlessly growing the transcript file 
 Fixed backgrounding a session with ← or /background dropping its /color from the agent view row 
 Fixed resetting a corrupted config file from the startup recovery dialog destroying it unrecoverably — it now backs up the file first 
 Fixed Claude in Chrome repeatedly opening the reconnect page when sessions run from different builds or config directories 
 Fixed plan mode not prompting for state-changing browser tool calls; read-only browser_batch calls are now correctly auto-allowed 
 Transient server rate-limit errors (429s unrelated to your usage limit) are now retried automatically with backoff for subscribers instead of failing the turn 
 CLAUDE_CODE_RETRY_WATCHDOG now raises the default retry count for non-capacity transient errors to 300 and lifts the cap of 15 on CLAUDE_CODE_MAX_RETRIES 
 claude agents session rows now show pull-request links as bare #N without the redundant "PR" label

</details>