---
id: inbox_f5c76558
date: 2026-04-23
source_ref: "[[00-inbox/2026-04-23/0246-claude-code-releases-v2-1-118-bcce]]"
title: "v2.1.118"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.118
source: claude-code-releases
published_at: 2026-04-23T00:42:21+00:00
fetched_at: 2026-04-24T02:49:52.851106+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.118 發布，主要更新包括 Vim visual mode（v 視覺模式、V 視覺行模式）、合併 `/cost` 和 `/stats` 為統一的 `/usage` 指令；新增自訂主題系統可在 `~/.claude/themes/` 建立、編輯或透過 plugins 散佈；hooks 系統擴展支援 MCP tool 直接呼叫 (`type: \"mcp_tool\"`)；新增 `DISABLE_UPDATES` 環境變數完全阻止更新；WSL on Windows 支援繼承 Windows 側管理設定；修復多項 MCP OAuth 問題（token 過期、scope 重新同意、refresh race condition、macOS keychain 競爭）與 plugin 重新解析等，共 30+ 項 bug 修正。"
key_points:
  - "Vim visual mode (v/V) 加入視覺回饋與選區操作；合併 `/cost`+`/stats` 為 `/usage` 統一成本顯示"
  - "自訂主題系統支援 `~/.claude/themes/` 手編 JSON 或透過 plugins 散佈；hooks 可直接呼叫 MCP tools"
  - "修復 MCP OAuth 複雜問題：缺 `expires_in` 導致每小時重認証、macOS keychain race condition、refresh 無 cross-process lock、token 撤銷前過期等"
tags: [claude-code-release, vim-visual-mode, custom-themes, mcp-oauth-fixes, hook-mcp]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.118

Claude Code v2.1.118 發布，主要更新包括 Vim visual mode（v 視覺模式、V 視覺行模式）、合併 `/cost` 和 `/stats` 為統一的 `/usage` 指令；新增自訂主題系統可在 `~/.claude/themes/` 建立、編輯或透過 plugins 散佈；hooks 系統擴展支援 MCP tool 直接呼叫 (`type: "mcp_tool"`)；新增 `DISABLE_UPDATES` 環境變數完全阻止更新；WSL on Windows 支援繼承 Windows 側管理設定；修復多項 MCP OAuth 問題（token 過期、scope 重新同意、refresh race condition、macOS keychain 競爭）與 plugin 重新解析等，共 30+ 項 bug 修正。

### 重點
- Vim visual mode (v/V) 加入視覺回饋與選區操作；合併 `/cost`+`/stats` 為 `/usage` 統一成本顯示
- 自訂主題系統支援 `~/.claude/themes/` 手編 JSON 或透過 plugins 散佈；hooks 可直接呼叫 MCP tools
- 修復 MCP OAuth 複雜問題：缺 `expires_in` 導致每小時重認証、macOS keychain race condition、refresh 無 cross-process lock、token 撤銷前過期等

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.118)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<h2>What's changed</h2>
<ul>
<li>Added vim visual mode (<code>v</code>) and visual-line mode (<code>V</code>) with selection, operators, and visual feedback</li>
<li>Merged <code>/cost</code> and <code>/stats</code> into <code>/usage</code> — both remain as typing shortcuts that open the relevant tab</li>
<li>Create and switch between named custom themes from <code>/theme</code>, or hand-edit JSON files in <code>~/.claude/themes/</code>; plugins can also ship themes via a <code>themes/</code> directory</li>
<li>Hooks can now invoke MCP tools directly via <code>type: "mcp_tool"</code></li>
<li>Added <code>DISABLE_UPDATES</code> env var to completely block all update paths including manual <code>claude update</code> — stricter than <code>DISABLE_AUTOUPDATER</code></li>
<li>WSL on Windows can now inherit Windows-side managed settings via the <code>wslInheritsWindowsSettings</code> policy key</li>
<li>Auto mode: include <code>"$defaults"</code> in <code>autoMode.allow</code>, <code>autoMode.soft_deny</code>, or <code>autoMode.environment</code> to add custom rules alongside the built-in list instead of replacing it</li>
<li>Added a "Don't ask again" option to the auto mode opt-in prompt</li>
<li>Added <code>claude plugin tag</code> to create release git tags for plugins with version validation</li>
<li><code>--continue</code>/<code>--resume</code> now find sessions that added the current directory via <code>/add-dir</code></li>
<li><code>/color</code> now syncs the session accent color to claude.ai/code when Remote Control is connected</li>
<li>The <code>/model</code> picker now honors <code>ANTHROPIC_DEFAULT_*_MODEL_NAME</code>/<code>_DESCRIPTION</code> overrides when using a custom <code>ANTHROPIC_BASE_URL</code> gateway</li>
<li>When auto-update skips a plugin due to another plugin's version constraint, the skip now appears in <code>/doctor</code> and the <code>/plugin</code> Errors tab</li>
<li>Fixed <code>/mcp</code> menu hiding OAuth Authenticate/Re-authenticate actions for servers configured with <code>headersHelper</code>, and HTTP/SSE MCP servers with custom headers being stuck in "needs authentication" after a transient 401</li>
<li>Fixed MCP servers whose OAuth token response omits <code>expires_in</code> requiring re-authentication every hour</li>
<li>Fixed MCP step-up authorization silently refreshing instead of prompting for re-consent when the server's <code>insufficient_scope</code> 403 names a scope the current token already has</li>
<li>Fixed an unhandled promise rejection when an MCP server's OAuth flow times out or is cancelled</li>
<li>Fixed MCP OAuth refresh proceeding without its cross-process lock under contention</li>
<li>Fixed macOS keychain race where a concurrent MCP token refresh could overwrite a freshly-refreshed OAuth token, causing unexpected "Please run /login" prompts</li>
<li>Fixed OAuth token refresh failing when the server revokes a token before its local expiry time</li>
<li>Fixed credential save crash on Linux/Windows corrupting <code>~/.claude/.credentials.json</code></li>
<li>Fixed <code>/login</code> having no effect in a session launched with <code>CLAUDE_CODE_OAUTH_TOKEN</code> — the env token is now cleared so disk credentials take effect</li>
<li>Fixed unreadable text in the "new messages" scroll pill and <code>/plugin</code> badges</li>
<li>Fixed plan acceptance dialog offering "auto mode" instead of "bypass permissions" when running with <code>--dangerously-skip-permissions</code></li>
<li>Fixed agent-type hooks failing with "Messages are required for agent hooks" when configured for events other than <code>Stop</code> or <code>SubagentStop</code></li>
<li>Fixed <code>prompt</code> hooks re-firing on tool calls made by an agent-hook verifier subagent</li>
<li>Fixed <code>/fork</code> writing the full parent conversation to disk per fork — now writes a pointer and hydrates on read</li>
<li>Fixed Alt+K / Alt+X / Alt+^ / Alt+_ freezing keyboard input</li>
<li>Fixed connecting to a remote session overwriting your local <code>model</code> setting in <code>~/.claude/settings.json</code></li>
<li>Fixed typeahead showing "No commands match" error when pasting file paths that start with <code>/</code></li>
<li>Fixed <code>plugin install</code> on an already-installed plugin not re-resolving a dependency installed at the wrong version</li>
<li>Fixed unhandled errors from file watcher on invalid paths or fd exhaustion</li>
<li>Fixed Remote Control sessions getting archived on transient CCR initialization blips during JWT refresh</li>
<li>Fixed subagents resumed via <code>SendMessage</code> not restoring the explicit <code>cwd</code> they were spawned with</li>
</ul>

</details>