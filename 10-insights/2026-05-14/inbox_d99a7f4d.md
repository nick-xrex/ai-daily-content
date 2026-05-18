---
id: inbox_d99a7f4d
date: 2026-05-14
source_ref: "[[00-inbox/.../inbox_d99a7f4d]]"
title: "v2.1.142"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.142
source: claude-code-releases
published_at: 2026-05-14T22:55:10+00:00
fetched_at: 2026-05-18T03:47:32.558174+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.142 版本發布，新增八個 claude agents flags（--add-dir、--settings、--mcp-config、--plugin-dir、--permission-mode、--model、--effort、--dangerously-skip-permissions），使背景會話配置更靈活。Fast mode 預設升級至 Opus 4.7（改善推理和編碼），可透過環境變數 CLAUDE_CODE_OPUS_4_6_FAST_MODE_OVERRIDE=1 保留舊版。修復多個影響穩定性的關鍵問題：macOS sleep/wake 後 daemon 重連失敗、背景代理與 git worktree 衝突、Windows 網路驅動死鎖。此版本對開發者效率與系統可靠性均有顯著改善。"
key_points:
  - "新增 8 個 agents flags 擴展背景會話配置（--add-dir、--mcp-config、--plugin-dir 等）"
  - "Fast mode 預設升級至 Opus 4.7；環境變數 CLAUDE_CODE_OPUS_4_6_FAST_MODE_OVERRIDE=1 可保留 Opus 4.6"
  - "修復 8+ 個穩定性問題：macOS daemon 重連、git worktree 衝突、Windows 死鎖、daemon 升級後進程清理"
tags: [claude-code, opus-4.7, agents-flags, daemon-fixes, mcp-plugin]
topics: [foundation_models.claude, agents.mcp]
importance: 4
novelty: 3
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.142

Claude Code v2.1.142 版本發布，新增八個 claude agents flags（--add-dir、--settings、--mcp-config、--plugin-dir、--permission-mode、--model、--effort、--dangerously-skip-permissions），使背景會話配置更靈活。Fast mode 預設升級至 Opus 4.7（改善推理和編碼），可透過環境變數 CLAUDE_CODE_OPUS_4_6_FAST_MODE_OVERRIDE=1 保留舊版。修復多個影響穩定性的關鍵問題：macOS sleep/wake 後 daemon 重連失敗、背景代理與 git worktree 衝突、Windows 網路驅動死鎖。此版本對開發者效率與系統可靠性均有顯著改善。

### 重點
- 新增 8 個 agents flags 擴展背景會話配置（--add-dir、--mcp-config、--plugin-dir 等）
- Fast mode 預設升級至 Opus 4.7；環境變數 CLAUDE_CODE_OPUS_4_6_FAST_MODE_OVERRIDE=1 可保留 Opus 4.6
- 修復 8+ 個穩定性問題：macOS daemon 重連、git worktree 衝突、Windows 死鎖、daemon 升級後進程清理

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.142)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v2.1.142

What's changed 
 
 Added new claude agents flags: --add-dir , --settings , --mcp-config , --plugin-dir , --permission-mode , --model , --effort , and --dangerously-skip-permissions to configure dispatched background sessions 
 Fast mode now uses Opus 4.7 by default (previously Opus 4.6). Set CLAUDE_CODE_OPUS_4_6_FAST_MODE_OVERRIDE=1 to pin fast mode to Opus 4.6 
 Plugins with a root-level SKILL.md and no skills/ subdirectory are now surfaced as a skill 
 The /plugin details pane and claude plugin details now show LSP servers a plugin provides 
 /web-setup warns before replacing an existing GitHub App connection 
 Fixed MCP_TOOL_TIMEOUT not raising the per-request fetch timeout for remote HTTP and SSE MCP servers, which capped tool calls at 60 seconds regardless of the configured value 
 Fixed background sessions not recognizing pre-existing git worktrees, blocking Edit while EnterWorktree refused to create a duplicate 
 Fixed background sessions disappearing and daemon reconnect failing after macOS sleep/wake — the daemon now detects clock jumps instead of treating them as elapsed idle time 
 Fixed daemon not exiting cleanly after the binary is upgraded (e.g. brew upgrade ), causing dispatched agents to crash-loop on the deleted path 
 Fixed background agents crash-looping when the Claude-in-Chrome extension is connected without a shared tab 
 Fixed clicking links in an attached claude agents session — the background worker's headless browser shim no longer applies while attached 
 Fixed claude agents "v to open in editor" using the daemon's default editor instead of your shell's $EDITOR / $VISUAL 
 Fixed claude agents deadlocking on Windows with network-drive working directories; Ctrl+C now works during startup 
 Fixed background-color bleed when attaching to a claude agents session from Apple Terminal or other 256-color-only terminals 
 Fixed claude --bg --dangerously-skip-permissions not persisting across retire/wake 
 Fixed session titles being derived from the URL when the first message is a link 
 Fixed redundant set_model requests from remote clients injecting duplicate /model breadcrumbs into the transcript 
 Fixed plugins using skills: ["./"] showing a false "path escapes plugin directory" error 
 Fixed plugin cache cleanup deleting the active plugin version directory when no installation metadata is present 
 Fixed /plugin browse pane showing "0 installs" for newly published plugins 
 Fixed plugin advisories not naming every plugin.json key that shadows a default folder 
 Improved reactive compaction: the first summarize attempt now seeds from the original request's overflow size, avoiding a wasted near-full-context retry 
 Improved hook configuration error: configuring a prompt- or agent-type hook for SessionStart / Setup / SubagentStart now shows a clear "use a command-type hook instead" error 
 Removed stale /model claude-sonnet-4-20250514 suggestion from Usage Policy refusal messages

</details>