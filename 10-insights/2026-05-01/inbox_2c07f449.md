---
id: inbox_2c07f449
date: 2026-05-01
source_ref: "[[00-inbox/2026-05-01/1257-claude-code-releases-v2-1-126-ecbe]]"
title: "v2.1.126"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.126
source: claude-code-releases
published_at: 2026-05-01T03:11:36+00:00
fetched_at: 2026-05-01T13:00:20.778819+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.126 更新發佈，針對開發者工作流程進行多項改進。核心功能包括：(1) /model 選擇器現支援 Anthropic 相容網關，可列出網關 /v1/models 端點的模型；(2) 新增 `claude project purge [path]` 指令用於刪除專案所有 Claude Code 狀態（含 transcripts、tasks、file history、config），支援 --dry-run、--yes、--interactive、--all 旗標；(3) --dangerously-skip-permissions 旗標可繞過 .claude/、.git/、.vscode/、shell config 等受保護路徑的提示；(4) 安全修復：allowManagedDomainsOnly/allowManagedReadPathsOnly 在高優先級管理設定缺少 sandbox 區塊時被忽略的問題；(5) OAuth 改善：支援在 WSL2、SSH、容器環境中直接貼上 OAuth code。此外修復了 20+ 個影響穩定性的 bug，包括圖像過大導致 session 中斷、Stream idle timeout 誤報、traclpad 過快滾動等。"
key_points:
  - "新 `claude project purge` 指令支援 --dry-run/--yes/--interactive/--all，可完整清除專案狀態而無需手動追蹤"
  - "/model 選擇器支援 Anthropic 相容網關（如 vLLM、ollama），gateway URL 指向 /v1/models 端點自動列舉"
  - "安全修複：managedDomainsOnly/managedReadPathsOnly 被高優先級設定源覆蓋的 sandbox 缺失問題"
tags: [claude-code, developer-tools, oauth-improvements, security-fix, gateway-support]
topics: [foundation_models.claude]
importance: 4
novelty: 3
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.126

Claude Code v2.1.126 更新發佈，針對開發者工作流程進行多項改進。核心功能包括：(1) /model 選擇器現支援 Anthropic 相容網關，可列出網關 /v1/models 端點的模型；(2) 新增 `claude project purge [path]` 指令用於刪除專案所有 Claude Code 狀態（含 transcripts、tasks、file history、config），支援 --dry-run、--yes、--interactive、--all 旗標；(3) --dangerously-skip-permissions 旗標可繞過 .claude/、.git/、.vscode/、shell config 等受保護路徑的提示；(4) 安全修復：allowManagedDomainsOnly/allowManagedReadPathsOnly 在高優先級管理設定缺少 sandbox 區塊時被忽略的問題；(5) OAuth 改善：支援在 WSL2、SSH、容器環境中直接貼上 OAuth code。此外修復了 20+ 個影響穩定性的 bug，包括圖像過大導致 session 中斷、Stream idle timeout 誤報、traclpad 過快滾動等。

### 重點
- 新 `claude project purge` 指令支援 --dry-run/--yes/--interactive/--all，可完整清除專案狀態而無需手動追蹤
- /model 選擇器支援 Anthropic 相容網關（如 vLLM、ollama），gateway URL 指向 /v1/models 端點自動列舉
- 安全修複：managedDomainsOnly/managedReadPathsOnly 被高優先級設定源覆蓋的 sandbox 缺失問題

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.126)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<h2>What's changed</h2>
<ul>
<li>The <code>/model</code> picker now lists models from your gateway's <code>/v1/models</code> endpoint when <code>ANTHROPIC_BASE_URL</code> points at an Anthropic-compatible gateway</li>
<li>
<ul>
<li>Added <code>claude project purge [path]</code> to delete all Claude Code state for a project (transcripts, tasks, file history, config entry) — supports <code>--dry-run</code>, <code>-y/--yes</code>, <code>-i/--interactive</code>, and <code>--all</code></li>
</ul>
</li>
<li><code>--dangerously-skip-permissions</code> now bypasses prompts for writes to <code>.claude/</code>, <code>.git/</code>, <code>.vscode/</code>, shell config files, and other previously-protected paths (catastrophic removal commands still prompt as a safety net)</li>
<li><code>claude auth login</code> now accepts the OAuth code pasted into the terminal when the browser callback can't reach localhost (WSL2, SSH, containers)</li>
<li><code>claude_code.skill_activated</code> OpenTelemetry event now fires for user-typed slash commands and carries a new <code>invocation_trigger</code> attribute (<code>"user-slash"</code>, <code>"claude-proactive"</code>, or <code>"nested-skill"</code>)</li>
<li>Auto mode: the spinner now turns red when a permission check stalls, instead of looking like the tool is running</li>
<li>Host-managed deployments (<code>CLAUDE_CODE_PROVIDER_MANAGED_BY_HOST</code>) no longer auto-disable analytics on Bedrock/Vertex/Foundry</li>
<li>Windows: PowerShell 7 installed via the Microsoft Store, MSI without PATH, or <code>.NET global tool</code> is now detected</li>
<li>Windows: when the PowerShell tool is enabled, Claude now treats PowerShell as the primary shell instead of defaulting to Bash</li>
<li>Read tool: removed the per-file malware-assessment reminder that could cause spurious refusals and "this is not malware" commentary on legacy models</li>
<li><strong>Security:</strong> Fixed <code>allowManagedDomainsOnly</code> / <code>allowManagedReadPathsOnly</code> being ignored when a higher-priority managed-settings source lacked a <code>sandbox</code> block</li>
<li>Fixed pasting an image larger than 2000px breaking the session — images are now downscaled on paste, and oversized images in history are automatically removed and the request retried</li>
<li>Fixed showing the login screen for "OAuth not allowed for organization" errors — now shows guidance to contact your admin</li>
<li>Fixed OAuth login failing with timeout on slow or proxied connections, in IPv6-only devcontainers, and when the browser callback can't reach localhost</li>
<li>Fixed a rare race where a concurrent credential write could clear a valid OAuth refresh token</li>
<li>Fixed API retry countdown sticking at "0s" instead of counting down between attempts</li>
<li>Fixed "Stream idle timeout" error after waking Mac from sleep mid-request</li>
<li>Fixed background and remote sessions falsely aborting with "Stream idle timeout" during long model thinking pauses</li>
<li>Fixed a hang where the assistant could finish thinking but show no output after a run of empty turns</li>
<li>Fixed overly fast trackpad scrolling in Cursor and VS Code 1.92–1.104 integrated terminals</li>
<li>Fixed claude.ai MCP connectors being suppressed by manual servers stuck in needs-auth state</li>
<li>Fixed Japanese/Korean/Chinese text rendering as garbled characters on Windows in no-flicker mode</li>
<li>Fixed <code>Ctrl+L</code> clearing the prompt input — it now only forces a screen redraw, matching readline behavior</li>
<li>Fixed deferred tools (WebSearch, WebFetch, etc.) not being available to skills with <code>context: fork</code> and other subagents on their first turn</li>
<li>Fixed plan-mode tools being unavailable in interactive sessions launched with <code>--channels</code></li>
<li>Fixed <code>/plugin</code> Uninstall reporting "Enabled" instead of "Uninstalled"</li>
<li>Bounded total size of file-modified reminders when a linter touches many files at once</li>
<li>Fixed <code>/remote-control</code> retries appearing stuck on "connecting…" — each retry now shows its result</li>
<li>Fixed Remote Control failure notification not showing the error reason for initial connection failures</li>
<li>Windows: clipboard writes no longer expose copied content in process command-line arguments visible to EDR/SIEM telemetry; also fixes &gt;22KB selections not reaching the clipboard</li>
<li>PowerShell tool: bare <code>--</code> (e.g. <code>git diff -- file</code>) is no longer mis-flagged as the <code>--%</code> stop-parsing token</li>
<li>Fixed Agent SDK hang when the model emits a malformed tool name in a parallel tool call batch</li>
</ul>

</details>