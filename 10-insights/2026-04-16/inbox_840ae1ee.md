---
id: inbox_840ae1ee
date: 2026-04-16
source_ref: "[[00-inbox/2026-04-16/0158-claude-code-releases-v2-1-111-91ae]]"
title: "v2.1.111"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.111
source: claude-code-releases
published_at: 2026-04-16T15:18:45+00:00
fetched_at: 2026-04-21T02:00:53.044171+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.111 於 2026 年 4 月 16 日發布，這是重大功能版本，主要推出 Claude Opus 4.7 xhigh 努力等級。Max 訂閱戶現可使用 Opus 4.7 auto mode，並透過 /effort 滑桿調整速度與智能平衡；xhigh 等級介於 high 與 max 之間。新增 /less-permission-prompts 技能掃描常見唯讀指令自動提議白名單，/ultrareview 啟用雲端並行多代理程式碼審查。/theme 增加「Auto (match terminal)」自動配對終端深淺模式。Windows 上 PowerShell 工具逐漸推出，Linux/macOS 可透過環境變數啟用。計畫檔名改為基於提示內容生成（如 fix-auth-race-snug-otter.md），提升可追蹤性。修復 /resume 大型會話、Tab 補全、MCP 逾時等 25+ 項問題。"
key_points:
  - "Claude Opus 4.7 xhigh 努力等級推出，Max 訂閱戶可用 auto mode 搭配 Opus 4.7"
  - "/ultrareview 支援雲端並行代理程式碼審查，可直接審查 GitHub PR"
  - "/less-permission-prompts 技能掃描安全白名單；計畫檔名由提示內容生成"
tags: [claude-code, opus-4-7, features, ultrareview, agents]
topics: [foundation_models.claude, agents.mcp]
importance: 5
novelty: 5
deep_dive_candidate: true
deep_dive_approved: false
---

## v2.1.111

Claude Code v2.1.111 於 2026 年 4 月 16 日發布，這是重大功能版本，主要推出 Claude Opus 4.7 xhigh 努力等級。Max 訂閱戶現可使用 Opus 4.7 auto mode，並透過 /effort 滑桿調整速度與智能平衡；xhigh 等級介於 high 與 max 之間。新增 /less-permission-prompts 技能掃描常見唯讀指令自動提議白名單，/ultrareview 啟用雲端並行多代理程式碼審查。/theme 增加「Auto (match terminal)」自動配對終端深淺模式。Windows 上 PowerShell 工具逐漸推出，Linux/macOS 可透過環境變數啟用。計畫檔名改為基於提示內容生成（如 fix-auth-race-snug-otter.md），提升可追蹤性。修復 /resume 大型會話、Tab 補全、MCP 逾時等 25+ 項問題。

### 重點
- Claude Opus 4.7 xhigh 努力等級推出，Max 訂閱戶可用 auto mode 搭配 Opus 4.7
- /ultrareview 支援雲端並行代理程式碼審查，可直接審查 GitHub PR
- /less-permission-prompts 技能掃描安全白名單；計畫檔名由提示內容生成

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.111)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<h2>What's changed</h2>
<ul>
<li>Claude Opus 4.7 xhigh is now available! Use /effort to tune speed vs. intelligence</li>
<li>Auto mode is now available for Max subscribers when using Opus 4.7</li>
<li>Added <code>xhigh</code> effort level for Opus 4.7, sitting between <code>high</code> and <code>max</code>. Available via <code>/effort</code>, <code>--effort</code>, and the model picker; other models fall back to <code>high</code></li>
<li><code>/effort</code> now opens an interactive slider when called without arguments, with arrow-key navigation between levels and Enter to confirm</li>
<li>Added "Auto (match terminal)" theme option that matches your terminal's dark/light mode — select it from <code>/theme</code></li>
<li>Added <code>/less-permission-prompts</code> skill — scans transcripts for common read-only Bash and MCP tool calls and proposes a prioritized allowlist for <code>.claude/settings.json</code></li>
<li>Added <code>/ultrareview</code> for running comprehensive code review in the cloud using parallel multi-agent analysis and critique — invoke with no arguments to review your current branch, or <code>/ultrareview &lt;PR#&gt;</code> to fetch and review a specific GitHub PR</li>
<li>Auto mode no longer requires <code>--enable-auto-mode</code></li>
<li>Windows: PowerShell tool is progressively rolling out. Opt in or out with <code>CLAUDE_CODE_USE_POWERSHELL_TOOL</code>. On Linux and macOS, enable with <code>CLAUDE_CODE_USE_POWERSHELL_TOOL=1</code> (requires <code>pwsh</code> on PATH)</li>
<li>Read-only bash commands with glob patterns (e.g. <code>ls *.ts</code>) and commands starting with <code>cd &lt;project-dir&gt; &amp;&amp;</code> no longer trigger a permission prompt</li>
<li>Suggest the closest matching subcommand when <code>claude &lt;word&gt;</code> is invoked with a near-miss typo (e.g. <code>claude udpate</code> → "Did you mean <code>claude update</code>?")</li>
<li>Plan files are now named after your prompt (e.g. <code>fix-auth-race-snug-otter.md</code>) instead of purely random words</li>
<li>Improved <code>/setup-vertex</code> and <code>/setup-bedrock</code> to show the actual <code>settings.json</code> path when <code>CLAUDE_CONFIG_DIR</code> is set, seed model candidates from existing pins on re-run, and offer a "with 1M context" option for supported models</li>
<li><code>/skills</code> menu now supports sorting by estimated token count — press <code>t</code> to toggle</li>
<li><code>Ctrl+U</code> now clears the entire input buffer (previously: delete to start of line); press <code>Ctrl+Y</code> to restore</li>
<li><code>Ctrl+L</code> now forces a full screen redraw in addition to clearing the prompt input</li>
<li>Transcript view footer now shows <code>[</code> (dump to scrollback) and <code>v</code> (open in editor) shortcuts</li>
<li>The "+N lines" marker for truncated long pastes is now a full-width rule for easier scanning</li>
<li>Headless <code>--output-format stream-json</code> now includes <code>plugin_errors</code> on the init event when plugins are demoted for unsatisfied dependencies</li>
<li>Added <code>OTEL_LOG_RAW_API_BODIES</code> environment variable to emit full API request and response bodies as OpenTelemetry log events for debugging</li>
<li>Suppressed spurious decompression, network, and transient error messages that could appear in the TUI during normal operation</li>
<li>Reverted the v2.1.110 cap on non-streaming fallback retries — it traded long waits for more outright failures during API overload</li>
<li>Fixed terminal display tearing (random characters, drifting input) in iTerm2 + tmux setups when terminal notifications are sent</li>
<li>Fixed <code>@</code> file suggestions re-scanning the entire project on every turn in non-git working directories, and showing only config files in freshly-initialized git repos with no tracked files</li>
<li>Fixed LSP diagnostics from before an edit appearing after it, causing the model to re-read files it just edited</li>
<li>Fixed tab-completing <code>/resume</code> immediately resuming an arbitrary titled session instead of showing the session picker</li>
<li>Fixed <code>/context</code> grid rendering with extra blank lines between rows</li>
<li>Fixed <code>/clear</code> dropping the session name set by <code>/rename</code>, causing statusline output to lose <code>session_name</code></li>
<li>Improved plugin error handling: dependency errors now distinguish conflicting, invalid, and overly complex version requirements; fixed stale resolved versions after <code>plugin update</code>; <code>plugin install</code> now recovers from interrupted prior installs</li>
<li>Fixed Claude calling a non-existent <code>commit</code> skill and showing "Unknown skill: commit" for users without a custom <code>/commit</code> command</li>
<li>Fixed 429 rate-limit errors on Bedrock/Vertex/Foundry referencing status.claude.com (it only covers Anthropic-operated providers)</li>
<li>Fixed feedback surveys appearing back-to-back after dismissing one</li>
<li>Fixed bare URLs in bash/PowerShell/MCP tool output being unclickable when the terminal wraps them across lines</li>
<li>Windows: <code>CLAUDE_ENV_FILE</code> and SessionStart hook environment files now apply (previously a no-op)</li>
<li>Windows: permission rules with drive-letter paths are now correctly root-anchored, and paths differing only by drive-letter case are recognized as the same path</li>
</ul>

</details>
