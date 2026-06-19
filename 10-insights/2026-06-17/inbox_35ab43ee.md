---
id: inbox_35ab43ee
date: 2026-06-17
source_ref: "[[00-inbox/2026-06-17/2200-claude-code-releases-v2-1-181-a7a7]]"
title: "v2.1.181"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.181
source: claude-code-releases
published_at: 2026-06-17T22:07:41+00:00
fetched_at: 2026-06-18T22:04:31.663593+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 發布 v2.1.181，新增 /config key=value 語法支援即時設定調整，升級 Bun runtime 到 1.4 以提升執行效能。改善長段落流媒體顯示（行行出現而非等待換行）、API 連線中斷自動重試、MCP OAuth 視覺風格、以及沙箱 Apple Events 權限選項。修復超過 30 項 bug，包括 prompt caching 在自訂 ANTHROPIC_BASE_URL 和 Foundry 的問題、網路磁碟和雲同步資料夾的檔案截斷、macOS Spotlight reindexing 導致 TUI 凍結、以及長運行 session 遺失歷史記錄等關鍵問題。"
key_points:
  - "新增 /config 語法支援實時設定調整（thinking/model 等），適用於互動式、-p 模式和遠端控制"
  - "升級 Bun runtime 至 1.4，改善流媒體顯示從等待換行改為行行出現"
  - "修復 prompt caching 在 custom base URL 和 Foundry 的 attestation token 問題、網路磁碟檔案截斷、macOS TUI 凍結等 30+ 項關鍵 bug"
tags: [claude-code, version-release, bug-fixes, performance-improvement]
topics: [foundation_models.claude]
importance: 4
novelty: 2
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.181

Claude Code 發布 v2.1.181，新增 /config key=value 語法支援即時設定調整，升級 Bun runtime 到 1.4 以提升執行效能。改善長段落流媒體顯示（行行出現而非等待換行）、API 連線中斷自動重試、MCP OAuth 視覺風格、以及沙箱 Apple Events 權限選項。修復超過 30 項 bug，包括 prompt caching 在自訂 ANTHROPIC_BASE_URL 和 Foundry 的問題、網路磁碟和雲同步資料夾的檔案截斷、macOS Spotlight reindexing 導致 TUI 凍結、以及長運行 session 遺失歷史記錄等關鍵問題。

### 重點
- 新增 /config 語法支援實時設定調整（thinking/model 等），適用於互動式、-p 模式和遠端控制
- 升級 Bun runtime 至 1.4，改善流媒體顯示從等待換行改為行行出現
- 修復 prompt caching 在 custom base URL 和 Foundry 的 attestation token 問題、網路磁碟檔案截斷、macOS TUI 凍結等 30+ 項關鍵 bug

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.181)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added /config key=value syntax to set any setting from the prompt (e.g. /config thinking=false ) — works in interactive, -p , and Remote Control 
 Added sandbox.allowAppleEvents opt-in setting that lets sandboxed commands send Apple Events on macOS 
 Added CLAUDE_CLIENT_PRESENCE_FILE environment variable: point it at a marker file to suppress mobile push notifications while you're at the machine 
 Upgraded the bundled Bun runtime to 1.4 
 Improved streaming of long paragraphs: text now appears line-by-line instead of waiting for the first line break 
 Improved auto-retry: API connection drops mid-thinking now automatically retry instead of showing "Connection closed while thinking" 
 Improved the subagent panel: idle subagents auto-hide after 30s, the list caps at 5 rows with scroll hints, and keyboard hints now show in the footer 
 Improved the MCP OAuth browser page to match Claude Code's visual style and auto-close on success 
 Changed fullscreen mode URL opening to require Cmd+click (macOS) / Ctrl+click, matching native terminal behavior 
 Changed the Improved N memories line to no longer list individual files outside verbose mode 
 Fixed prompt caching not reading on custom ANTHROPIC_BASE_URL and on Foundry due to a per-request attestation token changing every turn 
 Fixed Write/Edit producing 0-byte or truncated files on network drives and cloud-synced folders 
 Fixed open , osascript , and browser-based auth flows failing with error -600 on macOS by adding the Apple Events entitlement 
 Fixed a startup regression (~120ms per launch in fresh environments, introduced in 2.1.169): the first prompt no longer waits for the managed-settings fetch when no MCP servers are configured 
 Fixed startup blocking with a blank terminal for up to 15 seconds when the account settings fetch is slow on a degraded network 
 Fixed startup crash ( TypeError: Cannot read properties of null ) when .claude.json contains corrupted null project entries 
 Fixed macOS TUI freezing at session start (Ctrl+C unresponsive) when Spotlight is busy reindexing 
 Fixed long-running idle sessions losing their history when another Claude Code process ran the 30-day transcript cleanup 
 Fixed foreground subagents spawning unbounded nested chains; they now respect the same 5-level depth limit as background subagents 
 Fixed /recap and conversation forks using the previous model immediately after a model switch 
 Fixed subagent "Thinking" duration showing the parent agent's elapsed time instead of the subagent's own 
 Fixed subagents blocked on a nested agent showing a ticking elapsed time instead of "waiting" in the agent panel 
 Fixed the API retry indicator ("Retrying in 0s · attempt N/10") staying on screen after the retry succeeded 
 Fixed AWS awsCredentialExport credentials with a short remaining lifetime causing credential refreshes every minute, and now accepts the JSON shape from aws configure export-credentials 
 Fixed claude mcp get / list showing ✓ Connected when tools/list fails; they now show ! Connected · tools fetch failed with the error detail 
 Fixed /remote-control leaving a stale "connecting..." line; it now confirms in the transcript once connected 
 Fixed ExitWorktree refusing to remove a clean worktree with "Could not verify worktree state" when bare git cannot be resolved on Windows 
 Fixed settings changes (such as /effort or /model ) failing with ENOENT when ~/.claude/settings.json is a relative symlink under a symlinked ~/.claude 
 Fixed IDE selection line numbers in context reminders being off by one (IntelliJ and VS Code) 
 Fixed Ctrl+C in fullscreen after a native terminal selection (modifier+drag) overwriting the clipboard with the app's prior selection 
 Fixed Ctrl+V showing "No image found in clipboard" instead of pasting when the clipboard contains text 
 Fixed agent creation failing with "EEXIST: file already exists" when the agents directory already exists (Windows/OneDrive) 
 Fixed AskUserQuestion preview content being cut off at the dialog edge instead of word-wrapping 
 Fixed AskUserQuestion multi-select questions silently dropping a typed "Other" free-text answer when submitting 
 Fixed /stats "Most active day" and daily token chart dates showing one day early in UTC-negative timezones 
 Fixed /copy and copy-on-select on Linux not detecting a clipboard utility installed after Claude Code started 
 Fixed tab-indented code rendering with incorrect indentation in the Write (create-file) preview 
 Fixed user prompts queued mid-turn not showing a full-width background highlight in the transcript 
 Fixed the activity spinner's pulse dwelling on the wrong glyph size in Ghostty

</details>