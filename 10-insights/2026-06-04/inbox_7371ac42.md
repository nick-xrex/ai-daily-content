---
id: inbox_7371ac42
date: 2026-06-04
source_ref: "[[00-inbox/.../inbox_7371ac42]]"
title: "v2.1.163"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.163
source: claude-code-releases
published_at: 2026-06-04T21:52:51+00:00
fetched_at: 2026-06-11T00:28:36.581607+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.163 發佈，包含版本管理、Plugin 列表、Hook 擴展等 6 項新功能與 11 項重要修復。新功能方面：(1) requiredMinimumVersion/MaximumVersion 強制版本範圍，超出範圍時拒絕啟動；(2) /plugin list 命令支援 --enabled/--disabled 篩選；(3) /btw 新增「c」快捷鍵複製 markdown；(4) Hooks 可返回 additionalContext 保持對話進行；(5) 新增 $ 逃逸語法；(6) stdio MCP servers 接收 CLAUDE_CODE_SESSION_ID。修復項涵蓋後台命令掛起、Windows 權限、Bash 臨時目錄、Hook 模式匹配、終端對齐等關鍵穩定性問題，並優化後台更新機制避免冷啟動延遲。"
key_points:
  - "新增 requiredMinimumVersion/MaximumVersion 機制強制用户升級/回退到允許版本範圍"
  - "Hook 改進：Stop 與 SubagentStop hooks 可回傳 additionalContext 進行反饋而不觸發錯誤"
  - "11 項 bug fixes 涵蓋 Windows EEXIST、Bazel EDR 保護、背景命令掛起、許可規則應用延遲、終端輸入失響等"
  - "背景 agent session 現可後台自動更新至新版本，無需冷啟動等待"
tags: [claude-code, v2.1.163, version-management, mcp-servers, reliability]
topics: [foundation_models.claude]
importance: 4
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.163

Claude Code v2.1.163 發佈，包含版本管理、Plugin 列表、Hook 擴展等 6 項新功能與 11 項重要修復。新功能方面：(1) requiredMinimumVersion/MaximumVersion 強制版本範圍，超出範圍時拒絕啟動；(2) /plugin list 命令支援 --enabled/--disabled 篩選；(3) /btw 新增「c」快捷鍵複製 markdown；(4) Hooks 可返回 additionalContext 保持對話進行；(5) 新增 $ 逃逸語法；(6) stdio MCP servers 接收 CLAUDE_CODE_SESSION_ID。修復項涵蓋後台命令掛起、Windows 權限、Bash 臨時目錄、Hook 模式匹配、終端對齐等關鍵穩定性問題，並優化後台更新機制避免冷啟動延遲。

### 重點
- 新增 requiredMinimumVersion/MaximumVersion 機制強制用户升級/回退到允許版本範圍
- Hook 改進：Stop 與 SubagentStop hooks 可回傳 additionalContext 進行反饋而不觸發錯誤
- 11 項 bug fixes 涵蓋 Windows EEXIST、Bazel EDR 保護、背景命令掛起、許可規則應用延遲、終端輸入失響等
- 背景 agent session 現可後台自動更新至新版本，無需冷啟動等待

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.163)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v2.1.163

What's changed 
 
 Added requiredMinimumVersion and requiredMaximumVersion managed settings — Claude Code refuses to start if its version is outside the allowed range and directs the user to an approved version 
 Added /plugin list command to list installed plugins, with --enabled / --disabled filters 
 Added a "c to copy" shortcut to /btw that copies the raw markdown answer to the clipboard, preserving formatting when pasted elsewhere 
 Hooks: Stop and SubagentStop hooks can now return hookSpecificOutput.additionalContext to give Claude feedback and keep the turn going without being labeled a hook error 
 Skills: added \$ escape syntax to include a literal $ before a digit in command bodies 
 stdio MCP servers now receive the same CLAUDE_CODE_SESSION_ID as hooks/Bash on --resume 
 Fixed claude -p hanging forever after its final result when a backgrounded command never exits — background shells are now stopped ~5s after the result once stdin closes 
 Fixed claude -p failing with "ANTHROPIC_API_KEY required" on Bedrock/Vertex/Foundry when CI=true and no Anthropic API key is set 
 Fixed bash commands failing under bazel and EDR-protected Go workflows: $TMPDIR was overridden to /tmp/claude-{uid} for all commands instead of only sandboxed ones (regression in 2.1.154) 
 Fixed Bash commands failing on Windows with "EEXIST: file already exists" on the session-env directory when it has the read-only attribute or is inside OneDrive 
 Fixed org-managed permission rules not applying for the entire session when the managed settings fetch completed during startup on a fresh config directory 
 Fixed background sessions in claude agents losing their running background tasks when reattached after a Claude Code update 
 Fixed terminal misalignment and a multi-second hang when exiting the agent view by pressing Esc 
 Fixed clicking Stop on a background-task chip in the desktop app not clearing the chip when the underlying process was already gone 
 Fixed keyboard input becoming permanently unresponsive after a paste operation whose end marker is dropped by the terminal 
 Fixed hook if: "Bash(...)" conditions firing on every Bash command containing $() or $VAR ; the pattern now matches against commands inside subshells and backticks too 
 Fixed deny rules on home-directory paths (e.g. Read(~/Desktop/**) ) not blocking Bash commands that reference the path via $HOME 
 Fixed a stray "(no content)" line left in the transcript after closing panel dialogs like /mcp and /plugins 
 Background agent sessions now update to a new Claude Code version in the background, so opening a session after an update no longer waits on a cold restart 
 Clearer descriptions for built-in commands and skills in the / menu 
 The subscription-switch suggestion now shows in the startup announcement slot instead of a toast 
 claude agents dispatching from the state-grouped view now starts the session in the directory the agent view was opened from

</details>