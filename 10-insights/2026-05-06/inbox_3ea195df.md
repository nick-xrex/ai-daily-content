---
id: inbox_3ea195df
date: 2026-05-06
source_ref: "[[00-inbox/2026-05-06/1001-claude-code-releases-v2-1-129-5f83]]"
title: "v2.1.129"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.129
source: claude-code-releases
published_at: 2026-05-06T01:40:18+00:00
fetched_at: 2026-05-06T10:06:04.953812+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.129 帶來多項功能與修復：新增 --plugin-url 旗標支援從 URL 載入 plugin zip、CLAUDE_CODE_FORCE_SYNC_OUTPUT 環境變數強制同步輸出、CLAUDE_CODE_PACKAGE_MANAGER_AUTO_UPDATE 自動更新機制；調整 plugin manifests 要求 themes/monitors 宣告在 \"experimental\" 下；將 Gateway /v1/models discovery 改為 opt-in；修正 Ctrl+R 歷史查詢預設行為；第三方部署不再顯示 Anthropic 專屬 spinner tips；新增 skillOverrides 設定模式；改進 OTel 指標計算 MCP 工具創建的 PR；並修復 15+ 個 UX 與後端問題如 /clear 上下文重設、permission dialog 期間狀態丟失等。"
key_points:
  - "新增 --plugin-url 標誌與環境變數支援 (CLAUDE_CODE_FORCE_SYNC_OUTPUT、CLAUDE_CODE_PACKAGE_MANAGER_AUTO_UPDATE)，擴展 plugin 載入彈性"
  - "Gateway 模型發現改為 opt-in，plugin 實驗性功能規範化，提高企業與第三方部署相容性"
  - "修復 OAuth 認證競態、prompt cache TTL 降級、skillOverrides 無效、MCP tool PR 計數等多項核心問題"
tags: [claude-code, features, bug-fixes, plugins, observability]
topics: [foundation_models.claude]
importance: 4
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.129

Claude Code v2.1.129 帶來多項功能與修復：新增 --plugin-url 旗標支援從 URL 載入 plugin zip、CLAUDE_CODE_FORCE_SYNC_OUTPUT 環境變數強制同步輸出、CLAUDE_CODE_PACKAGE_MANAGER_AUTO_UPDATE 自動更新機制；調整 plugin manifests 要求 themes/monitors 宣告在 "experimental" 下；將 Gateway /v1/models discovery 改為 opt-in；修正 Ctrl+R 歷史查詢預設行為；第三方部署不再顯示 Anthropic 專屬 spinner tips；新增 skillOverrides 設定模式；改進 OTel 指標計算 MCP 工具創建的 PR；並修復 15+ 個 UX 與後端問題如 /clear 上下文重設、permission dialog 期間狀態丟失等。

### 重點
- 新增 --plugin-url 標誌與環境變數支援 (CLAUDE_CODE_FORCE_SYNC_OUTPUT、CLAUDE_CODE_PACKAGE_MANAGER_AUTO_UPDATE)，擴展 plugin 載入彈性
- Gateway 模型發現改為 opt-in，plugin 實驗性功能規範化，提高企業與第三方部署相容性
- 修復 OAuth 認證競態、prompt cache TTL 降級、skillOverrides 無效、MCP tool PR 計數等多項核心問題

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.129)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<h2>What's changed</h2>
<ul>
<li>Added <code>--plugin-url &lt;url&gt;</code> flag to fetch a plugin <code>.zip</code> archive from a URL for the current session</li>
<li>Added <code>CLAUDE_CODE_FORCE_SYNC_OUTPUT=1</code> env var to force-enable synchronized output on terminals that auto-detection misses (e.g. Emacs <code>eat</code>)</li>
<li>Added <code>CLAUDE_CODE_PACKAGE_MANAGER_AUTO_UPDATE</code>: when set on Homebrew or WinGet installations, Claude Code runs the upgrade command in the background and prompts to restart</li>
<li>Plugin manifests: <code>themes</code> and <code>monitors</code> should now be declared under <code>"experimental": { ... }</code>. Top-level declarations still work but <code>claude plugin validate</code> will warn</li>
<li>Gateway <code>/v1/models</code> discovery for the <code>/model</code> picker is now opt-in via <code>CLAUDE_CODE_ENABLE_GATEWAY_MODEL_DISCOVERY=1</code> (was automatic in 2.1.126–2.1.128)</li>
<li>Ctrl+R history picker now defaults to searching all prompts across all projects, matching pre-2.1.124 behavior. Press Ctrl+S to narrow to the current project or session</li>
<li>Third-party deployments (Bedrock, Vertex, Foundry, or <code>ANTHROPIC_BASE_URL</code> gateway) no longer see spinner tips pointing at first-party Anthropic surfaces</li>
<li><code>skillOverrides</code> setting now works: <code>off</code> hides from model and <code>/</code>, <code>user-invocable-only</code> hides from model only, <code>name-only</code> collapses description</li>
<li>The <code>claude_code.pull_request.count</code> OTel metric now counts PRs/MRs created via MCP tools, not just shell commands</li>
<li>Policy refusal error messages now include the API Request ID for easier support debugging</li>
<li>Fixed API errors with unrecognized 400 status codes showing raw JSON instead of the underlying error message</li>
<li>Fixed <code>/clear</code> not resetting the terminal tab title after a conversation</li>
<li>Fixed session title chip from <code>/rename</code> disappearing while a permission or other dialog is active</li>
<li>Fixed agent panel below the prompt being hidden when subagents are running (regression in 2.1.122)</li>
<li>Fixed external-editor handoff (Ctrl+G) blanking the conversation history above the prompt</li>
<li>Fixed <code>/context</code> dumping its rendered ASCII visualization grid into the conversation, wasting ~1.6k tokens per call</li>
<li>Fixed <code>/agents</code> Library list arrow-key navigation: the highlighted agent now stays visible when the list exceeds the viewport</li>
<li>Fixed <code>/branch</code> success message not including the new branch's session id for <code>/resume</code></li>
<li>Fixed bold headers with keycap/ZWJ/skin-tone emoji losing trailing characters in fullscreen mode</li>
<li>Fixed server-managed settings policy not applying for enterprise/team users whose stored OAuth credentials lacked the <code>user:inference</code> scope</li>
<li>Fixed OAuth refresh race after wake-from-sleep that could log out all running sessions</li>
<li>Fixed 1-hour prompt cache TTL being silently downgraded to 5 minutes</li>
<li>Fixed cache-miss warning appearing spuriously after <code>/clear</code> or compaction when changing <code>/effort</code> or <code>/model</code></li>
<li>Fixed <code>Bash(mkdir *)</code>, <code>Bash(touch *)</code> and similar allow rules not being honored for in-project paths</li>
<li>Fixed <code>deniedMcpServers</code> patterns with a <code>*://</code> scheme wildcard not matching mixed-case hostnames</li>
<li>Fixed harmless WebSocket warning being logged as an error in <code>--debug</code> during voice mode</li>
<li>[VSCode] Fixed <code>/clear</code> not clearing the conversation context and displayed transcript</li>
</ul>

</details>