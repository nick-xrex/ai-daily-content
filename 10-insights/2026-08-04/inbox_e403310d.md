---
id: inbox_e403310d
date: 2026-08-04
source_ref: "[[00-inbox/2026-08-04/0144-claude-code-releases-v2-1-222-9306]]"
title: "v2.1.222"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.222
source: claude-code-releases
published_at: 2026-08-04T22:39:55+00:00
fetched_at: 2026-08-05T01:50:02.491027+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.222 發布多項安全性和穩定性修復。核心改進包括：worktree 隔離現在一致應用於所有工作階段類型，防止子代理執行破壞性 git 操作；MCP 伺服器用量計算改為只計算實際消耗工具結果的請求，而非後續所有回合；代理任務間的 SendMessage 現通過權限分類器評估提升安全性。此版本修復 20+ 個問題，涵蓋 PreToolUse 繞過限制、org-restricted model alias 降層、HTTPS 代理後端流閒置逾時、以及 claude.ai 連接器誤判授權狀態等議題。移除 ultraplan 功能並強化遠端控制自動啟動限制。"
key_points:
  - "Worktree 隔離 + 子代理 git 限制一致應用於所有工作階段類型，防止檔案編輯和 Bash 的破壞性操作"
  - "MCP 伺服器用量追蹤改進：只計算實際消耗工具結果的請求，避免誤計後續回合（解決計費過高）"
  - "SendMessage 代理間通訊現通過權限分類器評估，背景代理任務的 PreToolUse 不再繞過工具限制"
tags: [claude-code, agent-safety, mcp-integration, security-hardening, isolation]
topics: [agents.mcp]
importance: 4
novelty: 2
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.222

Claude Code v2.1.222 發布多項安全性和穩定性修復。核心改進包括：worktree 隔離現在一致應用於所有工作階段類型，防止子代理執行破壞性 git 操作；MCP 伺服器用量計算改為只計算實際消耗工具結果的請求，而非後續所有回合；代理任務間的 SendMessage 現通過權限分類器評估提升安全性。此版本修復 20+ 個問題，涵蓋 PreToolUse 繞過限制、org-restricted model alias 降層、HTTPS 代理後端流閒置逾時、以及 claude.ai 連接器誤判授權狀態等議題。移除 ultraplan 功能並強化遠端控制自動啟動限制。

### 重點
- Worktree 隔離 + 子代理 git 限制一致應用於所有工作階段類型，防止檔案編輯和 Bash 的破壞性操作
- MCP 伺服器用量追蹤改進：只計算實際消耗工具結果的請求，避免誤計後續回合（解決計費過高）
- SendMessage 代理間通訊現通過權限分類器評估，背景代理任務的 PreToolUse 不再繞過工具限制

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.222)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Fixed worktree-isolated sessions and their subagents being able to run destructive git commands against the main checkout; isolation now applies to file edits and Bash in every session type 
 Fixed PreToolUse auto-allow hooks bypassing tool restrictions in background agent tasks (summaries, compaction, renames) 
 Fixed /usage-credits on Team and Enterprise showing "you've already sent a usage credit request" for members whose earlier request was dismissed, blocking them from sending a new one 
 Fixed the startup connectivity check hanging and then failing behind an HTTPS proxy; it now uses the same proxy-aware transport as API requests and times out with a clear message 
 Fixed "Connection closed mid-response" errors being reported on responses that had actually completed 
 Fixed /usage overattributing usage to MCP servers: a server's share now reflects only the requests that actually consumed its tool results, instead of every turn after any call to it 
 Fixed sessions not linking to pull requests created after the branch was pushed, including through the GitHub REST API 
 Fixed org-restricted model: opus -style subagent and teammate family aliases dropping to the parent model instead of stepping down to the newest org-allowed model in the family 
 Fixed stream idle timeout firing on custom ANTHROPIC_BASE_URL gateways despite server keep-alive pings arriving on the wire 
 Fixed claude.ai connectors being falsely marked as needing authorization when the session token is invalid — they now show a /login hint instead 
 Fixed tool errors not being displayed for tools no longer available locally, for example after an MCP server is removed 
 Fixed SendMessage rejecting a long summary — it now truncates instead, so sends no longer fail on a character limit 
 Fixed the spinner's effort label in a subagent's transcript view showing the session's effort level instead of the subagent's own effort: setting 
 Fixed rare crashes when a file watcher hit a filesystem error or during file-watcher teardown 
 Fixed screen readers re-reading the whole input line on every backspace in --ax-screen-reader mode — end-of-line deletions now echo just the deleted characters 
 Fixed host model-selection keys not taking precedence over a stale on-disk managed-settings.json when CLAUDE_CODE_PROVIDER_MANAGED_BY_HOST is set 
 Improved auto mode safety: messages sent to other agent sessions via SendMessage are now evaluated by the permission classifier before dispatch 
 Improved the refusal when Claude tries to invoke a skill with disable-model-invocation : Claude is now told to ask you to run the skill instead of replicating its workflow 
 Improved the /diff view, the Remote Control workspace diff, and file-edit diffs in Claude Code on the web sessions to use raw git blob content, ignoring workspace-configured diff drivers and textconv 
 Changed Remote Control auto-start so repo-local settings ( .claude/settings.json or .claude/settings.local.json ) can no longer turn it on (they can still turn it off); enable it at user scope via /config 
 Removed ultraplan feature

</details>