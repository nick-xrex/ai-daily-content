---
id: inbox_48811dde
date: 2026-06-12
source_ref: "[[00-inbox/2026-06-12/0336-claude-code-releases-v2-1-176-7c46]]"
title: "v2.1.176"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.176
source: claude-code-releases
published_at: 2026-06-12T21:53:27+00:00
fetched_at: 2026-06-13T03:40:37.852414+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.176 發佈，包含 30 多項修復和改進。重點包括：session titles 支持多語言生成（基於用戶語言設定）、Bedrock 認證快取改為根據 Expiration 時間而非固定 1 小時、availableModels 強制執行防止環境變數繞過模型禁止清單、Fable 5 auto mode 修復使其回退到最佳 Opus 版本而非失敗、hook path matching 修復支援 Edit(src/**) 等模式、Linux symlink 路徑修復、tmux over SSH 的 copy/paste 修復、Remote Control 的多項連接管理修復、背景 session 狀態和 Windows daemon 等穩定性改進。"
key_points:
  - "Bedrock 認證快取改進：從固定 1 小時改為直到 credential 的 Expiration 時間，減少過期認證問題"
  - "availableModels 強制執行：ANTHROPIC_DEFAULT_*_MODEL 環境變數無法繞過禁止的模型，/fast 指令也拒絕切換到非白名單模型"
  - "Fable 5 auto mode 修復：沒有 Opus 4.8 的組織現在 classifier 會回退到最佳可用 Opus 版本"
tags: [claude-code-release, bug-fixes, remote-control, bedrock-integration, model-selection]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.176

Claude Code v2.1.176 發佈，包含 30 多項修復和改進。重點包括：session titles 支持多語言生成（基於用戶語言設定）、Bedrock 認證快取改為根據 Expiration 時間而非固定 1 小時、availableModels 強制執行防止環境變數繞過模型禁止清單、Fable 5 auto mode 修復使其回退到最佳 Opus 版本而非失敗、hook path matching 修復支援 Edit(src/**) 等模式、Linux symlink 路徑修復、tmux over SSH 的 copy/paste 修復、Remote Control 的多項連接管理修復、背景 session 狀態和 Windows daemon 等穩定性改進。

### 重點
- Bedrock 認證快取改進：從固定 1 小時改為直到 credential 的 Expiration 時間，減少過期認證問題
- availableModels 強制執行：ANTHROPIC_DEFAULT_*_MODEL 環境變數無法繞過禁止的模型，/fast 指令也拒絕切換到非白名單模型
- Fable 5 auto mode 修復：沒有 Opus 4.8 的組織現在 classifier 會回退到最佳可用 Opus 版本

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.176)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Session titles are now generated in the language of your conversation (set the language setting to pin a specific language) 
 Added footerLinksRegexes setting for regex-matched link badges in the footer row, configurable via user or managed settings 
 Improved Bedrock credential caching: credentials from awsCredentialExport are now cached until their Expiration instead of a fixed 1 hour 
 Fixed availableModels enforcement: alias model picks can no longer be redirected to a blocked model via ANTHROPIC_DEFAULT_*_MODEL environment variables, and /fast now refuses to toggle when it would switch to a model outside the allowlist 
 Fixed auto mode failing on Fable 5 for organizations without Opus 4.8 enabled — the classifier now falls back to the best available Opus model 
 Fixed hook if conditions for Read/Edit/Write tool paths: documented patterns like Edit(src/**) , Read(~/.ssh/**) , and Read(.env) now match correctly 
 Fixed Linux sandbox failing to start when .claude/settings.json is a symlink with an absolute target 
 Fixed /copy and mouse-selection copy not reaching the system clipboard inside tmux over SSH, and tmux paste buffer not loading on versions older than 3.2 
 Fixed Remote Control connecting from web/mobile silently switching the session's model 
 Fixed Remote Control disconnect notifications showing a bare numeric code instead of a human-readable reason, and connection failures adding a duplicate line to the conversation transcript 
 Fixed Remote Control sessions not disconnecting when you sign in to a different account 
 Fixed /cd and worktree moves leaving the session reporting the previous directory's git branch 
 Fixed claude agents : pressing back in one window no longer detaches other windows attached to the same session 
 Fixed backgrounded sessions showing "Working" forever when /bg mid-turn had nothing left to continue 
 Fixed background agent search by PR URL: PRs opened during scheduled wakeups or while a job was blocked now appear in claude agents search 
 Fixed the agents view input showing no text cursor on Windows 
 Fixed claude --bg -cn &lt;name&gt; not seeding the session name 
 Fixed background sessions to neutralize Windows network paths in persisted state before respawn 
 Fixed background-session respawn rejecting malformed resume IDs from corrupted state files 
 Fixed the Windows background-service daemon not starting when ~/.claude/daemon has the ReadOnly attribute set 
 Fixed cloud sessions failing with "Could not resolve authentication method" when idle for too long before being claimed 
 Background sessions now show clearer guidance when a window left open across an auto-update can't submit a reply, and claude daemon status explains version-skew behavior

</details>