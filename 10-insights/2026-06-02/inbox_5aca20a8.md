---
id: inbox_5aca20a8
date: 2026-06-02
source_ref: "[[00-inbox/2026-06-02/0029-claude-code-releases-v2-1-160-e49e]]"
title: "v2.1.160"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.160
source: claude-code-releases
published_at: 2026-06-02T02:10:25+00:00
fetched_at: 2026-06-03T00:34:01.714524+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.160 強化安全守門與多平台穩定性，共 26 項修復。核心安全改進：acceptEdits 模式對 build 配置（.npmrc/.yarnrc/bunfig.toml）寫入前提示，shell 啟動檔案（.zshenv/.bash_login）寫入前亦有警告，MCP 命令密鑰脫敏不再輸出。背景會話恢復修復、Windows 響應性改進、CJK IME 支援、vim p 命令修正、「workflow」重命名為「ultracode」。此版本著重供應鏈安全與跨平台體驗，降低無意間執行惡意配置的風險。"
key_points:
  - "敏感檔案寫入前提示機制：build config、shell startup 檔案寫入需明確確認，防供應鏈攻擊"
  - "MCP 命令出力脫敏：credentials、URL secrets、${VAR} 參考均不展開，避免密鑰意外洩露"
  - "多平台穩定性：Windows 響應性改善、WSL 剪貼板修復、背景會話恢復、CJK IME 支援"
tags: [claude-code, security-hardening, safe-defaults, multi-platform, release]
topics: [foundation_models.claude]
importance: 4
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.160

Claude Code v2.1.160 強化安全守門與多平台穩定性，共 26 項修復。核心安全改進：acceptEdits 模式對 build 配置（.npmrc/.yarnrc/bunfig.toml）寫入前提示，shell 啟動檔案（.zshenv/.bash_login）寫入前亦有警告，MCP 命令密鑰脫敏不再輸出。背景會話恢復修復、Windows 響應性改進、CJK IME 支援、vim p 命令修正、「workflow」重命名為「ultracode」。此版本著重供應鏈安全與跨平台體驗，降低無意間執行惡意配置的風險。

### 重點
- 敏感檔案寫入前提示機制：build config、shell startup 檔案寫入需明確確認，防供應鏈攻擊
- MCP 命令出力脫敏：credentials、URL secrets、${VAR} 參考均不展開，避免密鑰意外洩露
- 多平台穩定性：Windows 響應性改善、WSL 剪貼板修復、背景會話恢復、CJK IME 支援

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.160)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added a prompt before writing to shell startup files ( .zshenv , .zlogin , .bash_login ) and ~/.config/git/ , which could otherwise lead to unintended command execution 
 acceptEdits mode now prompts before writing build-tool config files that grant code execution ( .npmrc , .yarnrc* , bunfig.toml , .bazelrc , .pre-commit-config.yaml , .devcontainer/ , etc.) 
 Edit no longer requires a separate Read after viewing a file with grep : single-file grep / egrep / fgrep commands now satisfy the read-before-edit check 
 Fixed copy-on-select not writing to the Windows clipboard on WSL — now uses PowerShell interop instead of OSC 52, which terminals like MobaXterm don't support 
 Fixed restoring a completed session from claude agents dropping chat history and re-running the original prompt 
 Fixed background sessions re-attached after overnight retire losing their conversation and re-running the original prompt 
 Fixed claude --bg occasionally failing with "socket missing" when the background daemon was cold-starting on a loaded machine 
 Fixed an issue on Windows where the directory a background session was started in could not be deleted after claude rm until the background daemon exited 
 Fixed background agents that resumed work being shown under Completed in the agents list 
 Fixed claude agents freezing for several seconds when returning to the session list due to the auto-updater re-checking on every exit 
 Fixed Esc, arrow keys, and typing becoming unresponsive on Windows when attached to a background session or in the agent view while the host is under heavy CPU load 
 Fixed background agents emitting terminal sync-output markers to terminals that don't support them (Apple Terminal, tmux), causing render artifacts when entering a running agent 
 Fixed mouse wheel scrolling prompt history instead of the transcript right after opening a session from the agents list 
 Fixed CJK IME composition appearing at the bottom-left of the screen instead of at the input caret in the claude agents view 
 Fixed valid file:///C:/... links being rewritten to a broken path on Windows terminals with hyperlink support 
 Fixed voice mode failing to connect when the project directory or branch name contains non-ASCII or special characters 
 Fixed the auto mode unavailability message on third-party providers (Bedrock/Vertex/Foundry) to point to the CLAUDE_CODE_ENABLE_AUTO_MODE opt-in instead of incorrectly blaming the model 
 Fixed /effort ultracode incorrectly blaming the dynamic workflows setting when the model cannot run xhigh; ultracode is no longer offered on models that do not support it 
 Fixed model-not-found errors suggesting --model when running via the SDK or other hosts where the CLI flag doesn't apply 
 Fixed Claude's past replies disappearing from scrollback when resuming a brief mode session with brief mode turned off 
 Fixed vim mode p pasting on the line below instead of at the cursor when the register was yanked with v$ 
 Improved performance of opening recently-inactive background agent sessions in claude agents 
 Improved auto mode classifier latency by reducing reasoning on routine actions, lowering the chance of "could not evaluate this action" blocks 
 Improved background-session teardown ( claude rm / stop , idle reap) to send SIGTERM to running shell subprocesses before SIGKILL, so cleanup handlers run 
 Removed CLAUDE_CODE_OPUS_4_6_FAST_MODE_OVERRIDE ; the environment variable is now a no-op 
 Removed the JetBrains plugin install suggestion from startup 
 Renamed the dynamic-workflow trigger keyword from workflow to ultracode . The word "workflow" no longer triggers a run; asking for one in your own words still works. The trigger keyword is highlighted in violet in the prompt input

</details>