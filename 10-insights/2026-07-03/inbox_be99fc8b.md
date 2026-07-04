---
id: inbox_be99fc8b
date: 2026-07-03
source_ref: "[[00-inbox/2026-07-03/0115-claude-code-releases-v2-1-200-0b2f]]"
title: "v2.1.200"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.200
source: claude-code-releases
published_at: 2026-07-03T16:52:33+00:00
fetched_at: 2026-07-04T01:20:23.355393+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.200 包含多項重要修復和改進。權限模式默認值從 \"default\" 改為 \"manual\"，要求用戶顯式授權，提升安全性。AskUserQuestion 對話框從自動繼續改為可通過 /config 配置空閒超時，增強用戶控制。後台會話的多個關鍵問題得到修復，包括睡眠/喚醒後停止、重複運行被取消的任務、守護進程狀態損壞等。MCP 服務器配置問題和屏幕閱讀器支持也得到改進，包括符號標籤簡化和表格格式優化。"
key_points:
  - "權限模式默認改為 \"manual\"，需顯式授權（安全性提升）"
  - "修復後台會話在系統睡眠/喚醒後停止的關鍵問題，改善穩定性"
  - "屏幕閱讀器支持改進：裝飾字形隱藏、符號縮短、表格格式優化"
tags: [claude-code, permission-mode, background-session, a11y]
topics: []
importance: 4
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.200

Claude Code v2.1.200 包含多項重要修復和改進。權限模式默認值從 "default" 改為 "manual"，要求用戶顯式授權，提升安全性。AskUserQuestion 對話框從自動繼續改為可通過 /config 配置空閒超時，增強用戶控制。後台會話的多個關鍵問題得到修復，包括睡眠/喚醒後停止、重複運行被取消的任務、守護進程狀態損壞等。MCP 服務器配置問題和屏幕閱讀器支持也得到改進，包括符號標籤簡化和表格格式優化。

### 重點
- 權限模式默認改為 "manual"，需顯式授權（安全性提升）
- 修復後台會話在系統睡眠/喚醒後停止的關鍵問題，改善穩定性
- 屏幕閱讀器支持改進：裝飾字形隱藏、符號縮短、表格格式優化

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.200)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Changed AskUserQuestion dialogs to no longer auto-continue by default; opt into an idle timeout via /config 
 Changed the "default" permission mode to "Manual" across the CLI, --help , VS Code, and JetBrains; --permission-mode manual and "defaultMode": "manual" are accepted alongside default 
 Fixed a crash at startup when disabledMcpServers or enabledMcpServers in .claude.json is set to a non-array value 
 Fixed background sessions silently stopping mid-turn after sleep/wake or when reopening a stalled session 
 Fixed background sessions re-running a turn cancelled with Esc after a stall respawn 
 Fixed background agents never starting again after a crash left a stale daemon.lock whose PID the OS reused 
 Fixed background-agent daemon handover so a reinstalled older build can no longer take over the daemon; build recency is now judged by the version's embedded build timestamp 
 Fixed background-agent roster issues: transient corruption permanently disabling orphan cleanup, older binaries not preserving fields written by newer versions, and socket auth tokens being stripped during daemon restarts 
 Fixed subagents cut off by a rate limit before producing any text output returning an empty result instead of failing cleanly 
 Fixed control bytes from background-agent output reaching the terminal in the agent view 
 Fixed claude agents --plugin-dir &lt;dir&gt; not showing the plugin's agents and skills in the agent view when the flag is placed after agents 
 Fixed project-scoped plugins not loading correctly from git worktrees of the same repository 
 Fixed /mcp server list not tracking focus for screen readers and magnifiers 
 Fixed voice dictation showing a misleading "Voice connection failed" message when a recording captures no audio 
 Fixed rendering flicker under tmux 3.4+ by enabling synchronized terminal output 
 Improved screen-reader output: decorative glyphs are now hidden, transcript symbols read as short labels, and nested tables read as Header: value. lines 
 Improved the install script to explain when installation is killed by the system running out of memory

</details>