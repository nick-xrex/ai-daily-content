---
id: inbox_113aa3f4
date: 2026-04-22
source_ref: "[[00-inbox/.../inbox_113aa3f4]]"
title: "v2.1.117"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.117
source: claude-code-releases
published_at: 2026-04-22T00:04:40+00:00
fetched_at: 2026-04-22T02:32:50.740502+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 發布 v2.1.117，包含多項核心功能改進。支援透過環境變數 CLAUDE_CODE_FORK_SUBAGENT=1 在外部構建中啟用 forked subagents；agent frontmatter 的 mcpServers 現已透過 --agent 參數為主線程代理 session 加載；改進 /model 命令使選擇在重啟後持續生效，啟動標頭顯示模型來源；/resume 命令在重新讀取前主動提示摘要大型老化 session。本機構建在 macOS 和 Linux 上以內置 bfs 和 ugrep 替代 Glob 和 Grep 工具，加速搜尋；修正 Opus 4.7 context window 計算誤差（原誤為 200K，實為 1M），解決自動壓縮過早的問題。此外，修正 WebFetch 在超大型 HTML 頁面上掛起、OAuth token 刷新、MCP 連線序列化等多項 bug。"
key_points:
  - "Native 構建：Glob/Grep 改用內置 bfs/ugrep，省去工具往返，加快搜尋速度"
  - "Opus 4.7 修正：Context window 誤算 200K→1M，解決自動壓縮過早和 /context 百分比虛高問題"
  - "Plugin 依賴管理：缺失依賴現自動從配置的市場安裝，blockedMarketplaces/strictKnownMarketplaces 設定於安裝/更新/刷新時強制執行"
tags: [claude-code, performance, build-optimization, plugin-management, oauth-fix]
topics: [foundation_models.claude]
importance: 4
novelty: 3
insight_quality: 4
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.117

Claude Code 發布 v2.1.117，包含多項核心功能改進。支援透過環境變數 CLAUDE_CODE_FORK_SUBAGENT=1 在外部構建中啟用 forked subagents；agent frontmatter 的 mcpServers 現已透過 --agent 參數為主線程代理 session 加載；改進 /model 命令使選擇在重啟後持續生效，啟動標頭顯示模型來源；/resume 命令在重新讀取前主動提示摘要大型老化 session。本機構建在 macOS 和 Linux 上以內置 bfs 和 ugrep 替代 Glob 和 Grep 工具，加速搜尋；修正 Opus 4.7 context window 計算誤差（原誤為 200K，實為 1M），解決自動壓縮過早的問題。此外，修正 WebFetch 在超大型 HTML 頁面上掛起、OAuth token 刷新、MCP 連線序列化等多項 bug。

### 重點
- Native 構建：Glob/Grep 改用內置 bfs/ugrep，省去工具往返，加快搜尋速度
- Opus 4.7 修正：Context window 誤算 200K→1M，解決自動壓縮過早和 /context 百分比虛高問題
- Plugin 依賴管理：缺失依賴現自動從配置的市場安裝，blockedMarketplaces/strictKnownMarketplaces 設定於安裝/更新/刷新時強制執行

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.117)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v2.1.117

<h2>What's changed</h2>
<ul>
<li>Forked subagents can now be enabled on external builds by setting <code>CLAUDE_CODE_FORK_SUBAGENT=1</code></li>
<li>Agent frontmatter <code>mcpServers</code> are now loaded for main-thread agent sessions via <code>--agent</code></li>
<li>Improved <code>/model</code>: selections now persist across restarts even when the project pins a different model, and the startup header shows when the active model comes from a project or managed-settings pin</li>
<li>The <code>/resume</code> command now offers to summarize stale, large sessions before re-reading them, matching the existing <code>--resume</code> behavior</li>
<li>Faster startup when both local and claude.ai MCP servers are configured (concurrent connect now default)</li>
<li><code>plugin install</code> on an already-installed plugin now installs any missing dependencies instead of stopping at "already installed"</li>
<li>Plugin dependency errors now say "not installed" with an install hint, and <code>claude plugin marketplace add</code> now auto-resolves missing dependencies from configured marketplaces</li>
<li>Managed-settings <code>blockedMarketplaces</code> and <code>strictKnownMarketplaces</code> are now enforced on plugin install, update, refresh, and autoupdate</li>
<li>Advisor Tool (experimental): dialog now carries an "experimental" label, learn-more link, and startup notification when enabled; sessions no longer get stuck with "Advisor tool result content could not be processed" errors on every prompt and <code>/compact</code></li>
<li>The <code>cleanupPeriodDays</code> retention sweep now also covers <code>~/.claude/tasks/</code>, <code>~/.claude/shell-snapshots/</code>, and <code>~/.claude/backups/</code></li>
<li>OpenTelemetry: <code>user_prompt</code> events now include <code>command_name</code> and <code>command_source</code> for slash commands; <code>cost.usage</code>, <code>token.usage</code>, <code>api_request</code>, and <code>api_error</code> now include an <code>effort</code> attribute when the model supports effort levels. Custom/MCP command names are redacted unless <code>OTEL_LOG_TOOL_DETAILS=1</code> is set</li>
<li>Native builds on macOS and Linux: the <code>Glob</code> and <code>Grep</code> tools are replaced by embedded <code>bfs</code> and <code>ugrep</code> available through the Bash tool — faster searches without a separate tool round-trip (Windows and npm-installed builds unchanged)</li>
<li>Windows: cached <code>where.exe</code> executable lookups per process for faster subprocess launches</li>
<li>Default effort for Pro/Max subscribers on Opus 4.6 and Sonnet 4.6 is now <code>high</code> (was <code>medium</code>)</li>
<li>Fixed Plain-CLI OAuth sessions dying with "Please run /login" when the access token expires mid-session — the token is now refreshed reactively on 401</li>
<li>Fixed <code>WebFetch</code> hanging on very large HTML pages by truncating input before HTML-to-markdown conversion</li>
<li>Fixed a crash when a proxy returns HTTP 204 No Content — now surfaces a clear error instead of a <code>TypeError</code></li>
<li>Fixed <code>/login</code> having no effect when launched with <code>CLAUDE_CODE_OAUTH_TOKEN</code> env var and that token expires</li>
<li>Fixed prompt-input undo (<code>Ctrl+_</code>) doing nothing immediately after typing, and skipping a state on each undo step</li>
<li>Fixed <code>NO_PROXY</code> not being respected for remote API requests when running under Bun</li>
<li>Fixed rare spurious escape/return triggers when key names arrive as coalesced text over slow connections</li>
<li>Fixed SDK <code>reload_plugins</code> reconnecting all user MCP servers serially</li>
<li>Fixed Bedrock application-inference-profile requests failing with 400 when backed by Opus 4.7 with thinking disabled</li>
<li>Fixed MCP <code>elicitation/create</code> requests auto-cancelling in print/SDK mode when the server finishes connecting mid-turn</li>
<li>Fixed subagents running a different model than the main agent incorrectly flagging file reads with a malware warning</li>
<li>Fixed idle re-render loop when background tasks are present, reducing memory growth on Linux</li>
<li>[VSCode] Fixed "Manage Plugins" panel breaking when multiple large marketplaces are configured</li>
<li>Fixed Opus 4.7 sessions showing inflated <code>/context</code> percentages and autocompacting too early — Claude Code was computing against a 200K context window instead of Opus 4.7's native 1M</li>
</ul>

</details>