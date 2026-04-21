---
id: inbox_840ae1ee
source: claude-code-releases
source_type: rss
url: "https://github.com/anthropics/claude-code/releases/tag/v2.1.111"
author: "ashwin-ant"
published_at: 2026-04-16T15:18:45+00:00
fetched_at: 2026-04-21T01:58:16.050397+00:00
content_hash: "91ae6d5b01b9fd49475358cecc22573b3f35645b2769360adb7627469acb75bc"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.1.111

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