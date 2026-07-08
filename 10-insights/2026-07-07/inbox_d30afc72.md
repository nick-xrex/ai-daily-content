---
id: inbox_d30afc72
date: 2026-07-07
source_ref: "[[00-inbox/.../inbox_d30afc72]]"
title: "v2.1.203"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.203
source: claude-code-releases
published_at: 2026-07-07T21:06:12+00:00
fetched_at: 2026-07-08T00:59:09.632879+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.203 發布，包含 30+ 項 bug 修復和優化。核心修復包括：背景 session 在 daemon token 過期時能自動恢復（防止永久無反應）；修復返回 claude agents 時無聲停止 subagent 的問題，現在能保留其工作成果；解決 macOS 上開啟背景 session 卡 15-20 秒的效能回歸（2.1.196 引入）。多 repo worktree 場景下的隔離修復確保 subagent 在正確 checkout 中執行命令。二進制檔減少 ~7 MB、啟動記憶體 ~7 MB，改進長回應流時的響應速度。此版本特別針對背景 agent 穩定性和 worktree 多 repo 開發的痛點進行深度優化。"
key_points:
  - "背景 session daemon token 過期時現在能自動恢復（原先永久無反應），防止附加/停止/回覆失敗"
  - "修復 macOS 開啟/切換背景 session 的 15-20 秒卡頓，源自誤判低記憶體的回歸問題"
  - "worktree 隔離修復：subagent 在正確 checkout 中執行、嵌套 repo 能被 worktree 正確隔離、工作目錄失效時明確報錯而非 crash-loop"
tags: [session-stability, worktree-isolation, background-agents, performance-tuning, claude-code]
topics: []
importance: 4
novelty: 3
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.203

Claude Code v2.1.203 發布，包含 30+ 項 bug 修復和優化。核心修復包括：背景 session 在 daemon token 過期時能自動恢復（防止永久無反應）；修復返回 claude agents 時無聲停止 subagent 的問題，現在能保留其工作成果；解決 macOS 上開啟背景 session 卡 15-20 秒的效能回歸（2.1.196 引入）。多 repo worktree 場景下的隔離修復確保 subagent 在正確 checkout 中執行命令。二進制檔減少 ~7 MB、啟動記憶體 ~7 MB，改進長回應流時的響應速度。此版本特別針對背景 agent 穩定性和 worktree 多 repo 開發的痛點進行深度優化。

### 重點
- 背景 session daemon token 過期時現在能自動恢復（原先永久無反應），防止附加/停止/回覆失敗
- 修復 macOS 開啟/切換背景 session 的 15-20 秒卡頓，源自誤判低記憶體的回歸問題
- worktree 隔離修復：subagent 在正確 checkout 中執行、嵌套 repo 能被 worktree 正確隔離、工作目錄失效時明確報錯而非 crash-loop

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.203)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v2.1.203

What's changed 
 
 Added a warning when your login is about to expire, so you can re-authenticate before background sessions are interrupted 
 Added a grey ⏸ badge to the footer when in manual permission mode, making the active mode always visible 
 Added the session's additional working directories to MCP roots/list , with notifications/roots/list_changed sent when the set changes 
 Fixed opening or switching background agent sessions on macOS stalling for 15–20 seconds due to a false low-memory detection (regression in 2.1.196) 
 Fixed background sessions becoming permanently unresponsive to attach, replies, and stop when the daemon's session token went stale — the session now recovers automatically 
 Fixed returning to claude agents silently stopping running subagents and re-running the prompt from scratch — their work now carries over 
 Fixed a memory and per-turn CPU regression in interactive sessions: the context-usage indicator no longer re-analyzes the entire transcript after every turn 
 Fixed background agents inheriting a stale PATH from the daemon instead of the dispatching shell, causing missing tools on Windows 
 Fixed background and agent-view sessions dropping a shell-exported ANTHROPIC_BASE_URL , which sent API keys to the default endpoint and failed with 401 
 Fixed Bash failing with "argument list too long" in repos with many git worktrees 
 Fixed worktree-isolated subagents sometimes running shell commands in the parent checkout instead of their own worktree 
 Fixed worktree creation rejecting nested repositories in multi-repo workspaces, leaving background sessions unable to isolate and edit 
 Fixed background agents crash-looping when their working directory was deleted, replaced by a file, or became an invalid path — they now fail once with a clear error 
 Fixed a background daemon auto-upgrade failure silently killing all running background sessions 
 Fixed TaskStop and TaskOutput failing to find background agents spawned by another agent — errors now list running agents by id and description 
 Fixed the claude agents composer discarding your typed message when a slash command isn't available there 
 Fixed the agent list crashing when opening a stopped session whose conversation was already open in another session 
 Fixed background sessions showing "Needs input" in the agent list after the question was already answered 
 Fixed background agent startup failures showing only "exit_with_message" instead of the actual error 
 Fixed background sessions ignoring effortLevel changes in settings.json when forked through the daemon 
 Fixed attached background sessions ignoring CLAUDE_CODE_DISABLE_MOUSE and CLAUDE_CODE_DISABLE_MOUSE_CLICKS opt-outs 
 Fixed /exit incorrectly warning about running background agents after all named agents had completed 
 Fixed background sessions started from a non-git directory unable to edit files when a WorktreeCreate hook was configured 
 Fixed the @ directory picker in claude agents not showing registered git worktrees 
 Fixed background task output on Windows being permanently replaced by an empty file after /clear 
 Fixed content jumping when scrolling up through long transcript history 
 Fixed the terminal flickering and jumping while typing in bash mode when a shell-history suggestion was shown 
 Fixed literal ^[[I / ^[[O escape codes being printed when reattaching to a background session 
 Fixed LSP-only plugins being incorrectly flagged for disuse when their language servers deliver diagnostics or answer navigation requests 
 Improved responsiveness while long responses stream: live-preview updates no longer re-render the whole screen 
 Improved subagent behavior: agents are now less likely to re-delegate their entire task to another subagent 
 Reduced binary size by ~7 MB and startup memory by ~7 MB by loading a large bundled dependency lazily instead of inlining it 
 Changed left arrow to no longer close the background tasks, diff, and workflow detail views — press Esc instead 
 Changed the empty claude agents view to always show the organized sections (Needs input / Working / Completed) with descriptions 
 Removed the startup "claude command missing or broken" warnings — they now appear in /doctor and /status instead 
 Removed a redundant navigation hint from the claude agents footer 
 [VSCode] Added a Settings toggle for "Enable Remote Control for all sessions"

</details>