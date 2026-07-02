---
id: inbox_f141c225
date: 2026-07-01
source_ref: "[[00-inbox/2026-07-01/2223-claude-code-releases-v2-1-198-bd5e]]"
title: "v2.1.198"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.198
source: claude-code-releases
published_at: 2026-07-01T20:45:36+00:00
fetched_at: 2026-07-02T00:15:15.383560+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.198 帶來多項重要功能與修復。Chrome 支持正式上線，Background agents 現可在工作完成時自動 commit、push 並開啟 draft PR，無需停止等待確認。新增 /dataviz 技能提供圖表與儀表板設計指導。Gateway 側添加 Claude Platform on AWS 作為上游提供者，支援模型容錯轉移。Subagents 與上下文壓縮現繼承會話的 extended thinking 配置，提升委派任務品質。此外修復網絡瞬時掉線導致的中止、後台分類器過度請求、task panel 卡住等 15+ bug，並改進 Explore agent 模型繼承（上限 opus）、語法突出、API 重試 UX 等。"
key_points:
  - "Claude in Chrome 正式發布；Background agents 自動完成 commit、push、draft PR 流程"
  - "Subagents 與上下文壓縮繼承會話 extended thinking 配置，改善委派任務品質"
  - "Gateway 新增 Claude Platform on AWS 作為上游提供者，ECONNRESET 瞬時錯誤自動重試"
tags: [claude-code, agent-automation, remote-gateway, chrome-support, extended-thinking]
topics: [foundation_models.claude]
importance: 4
novelty: 3
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.198

Claude Code v2.1.198 帶來多項重要功能與修復。Chrome 支持正式上線，Background agents 現可在工作完成時自動 commit、push 並開啟 draft PR，無需停止等待確認。新增 /dataviz 技能提供圖表與儀表板設計指導。Gateway 側添加 Claude Platform on AWS 作為上游提供者，支援模型容錯轉移。Subagents 與上下文壓縮現繼承會話的 extended thinking 配置，提升委派任務品質。此外修復網絡瞬時掉線導致的中止、後台分類器過度請求、task panel 卡住等 15+ bug，並改進 Explore agent 模型繼承（上限 opus）、語法突出、API 重試 UX 等。

### 重點
- Claude in Chrome 正式發布；Background agents 自動完成 commit、push、draft PR 流程
- Subagents 與上下文壓縮繼承會話 extended thinking 配置，改善委派任務品質
- Gateway 新增 Claude Platform on AWS 作為上游提供者，ECONNRESET 瞬時錯誤自動重試

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.198)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Claude in Chrome is now generally available 
 Added background agent notifications in claude agents — sessions that need input or finish now fire the Notification hook ( agent_needs_input / agent_completed ) 
 Added /dataviz skill for chart and dashboard design guidance with a runnable color-palette validator 
 Gateway: added Claude Platform on AWS (anthropicAws) as an upstream provider; model-not-found responses now advance the failover chain 
 Background agents launched from claude agents now commit, push, and open a draft PR when they finish code work in a worktree, instead of stopping to ask 
 The built-in Explore agent now inherits the main session's model (capped at opus) instead of running on haiku 
 Subagents and context compaction now inherit the session's extended thinking configuration, improving output quality on delegated tasks 
 Fixed brief network drops mid-response aborting the turn — transient errors like ECONNRESET now retry with backoff instead of failing 
 Fixed excessive background classifier requests when sandboxed processes repeatedly accessed the same network host 
 Fixed background tasks in web, desktop, and VS Code task panels getting stuck on "Running" after they finish or after resuming a session 
 Fixed agent teams: a teammate that dies on an API error now reports "failed" to the lead, and messaging a stuck teammate wakes it to retry immediately 
 Fixed the /diff panel not refreshing when you switch branches or commit outside the session 
 Fixed markdown tables overflowing and wrapping their right border when rendered in fullscreen mode 
 Fixed Claude Platform on AWS and Mantle sessions dead-ending with "Please run /login" when the STS token expires — awsAuthRefresh now runs automatically 
 Fixed "no route to host" for local-network hosts in macOS background agent sessions by declaring Local Network entitlements 
 Fixed /desktop failing with "Cannot determine working directory" after entering and exiting a worktree 
 Fixed background agents repeatedly showing "Reconnecting..." every ~52 seconds on macOS while the agents view was open 
 Fixed pressing ← inside claude attach &lt;id&gt; exiting to the shell instead of opening the agent view 
 Fixed claude --bg silently creating an unattachable session when combined with --print / -p ; the conflicting flags are now rejected up front 
 Fixed the workflow progress view dropping the earliest agents from the list while the phase counter stayed correct in SDK and desktop-app sessions 
 Fixed .claude/rules/ conditional rules not loading when the target file is reached via a symlinked path 
 Fixed Cmd+click not opening URLs in fullscreen mode in Warp on macOS 
 Fixed double-click word selection in fullscreen mode to select the entire URL including the scheme 
 Fixed plan mode not auto-allowing read-only tool calls when a session starts in plan mode 
 Fixed /branch deriving its default fork name from the compaction summary instead of the first real prompt 
 Improved focus mode: subagents launched in a turn now appear in its activity summary, and completed background notifications fold into a single count 
 Improved syntax highlighting accuracy in code blocks, diffs, and file previews by upgrading to highlight.js 11 
 Keyboard shortcut hints now show opt/cmd instead of alt/super when connected from a Mac over SSH 
 Improved API retry UX: the error reason is now shown after the second attempt, and a status page link replaces the spinner tip when the API is overloaded 
 /login now opens the sign-in dialog from the claude agents view instead of saying it isn't available 
 Subagents now treat messages from the agent that launched them as normal task direction; an agent's message is still never treated as the user's approval 
 Removed the /agents wizard; ask Claude to create or manage subagents, or edit .claude/agents/ directly

</details>