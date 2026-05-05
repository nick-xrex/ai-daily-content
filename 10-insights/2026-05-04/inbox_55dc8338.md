---
id: inbox_55dc8338
date: 2026-05-04
source_ref: "[[00-inbox/2026-05-04/0819-claude-code-releases-v2-1-128-b36e]]"
title: "v2.1.128"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.128
source: claude-code-releases
published_at: 2026-05-04T23:01:47+00:00
fetched_at: 2026-05-05T08:22:46.214337+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.128 發布包含多項功能改進與 bug 修復。核心改動包括：`/mcp` 命令現顯示已連接伺服器的工具計數及標記零工具伺服器；`EnterWorktree` 修復為從本地 HEAD 而非 `origin/<預設分支>` 創建分支，防止未推送提交遺失；修復平行 Bash 工具調用中讀取命令（grep、git diff、ls）失敗不再取消兄弟調用；`--plugin-dir` 新增 .zip 外掛支持；MCP 伺服器重新連接時改進工具列表通告避免重複。另修復焦點模式切換、拖放圖片掛起、vim 空格鍵行為等多個 UX 問題。"
key_points:
  - "`EnterWorktree` 修復：從本地 HEAD 創建分支而非遠端預設分支，保留未推送提交"
  - "`/mcp` 命令增添工具計數顯示與零工具伺服器標記，改進伺服器診斷"
  - "修復平行 Bash 工具調用中讀取命令失敗會取消兄弟調用的問題"
tags: [claude-code, mcp, bug-fixes, tooling, workspace-management]
topics: [agents.mcp]
importance: 3
novelty: 2
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.128

Claude Code v2.1.128 發布包含多項功能改進與 bug 修復。核心改動包括：`/mcp` 命令現顯示已連接伺服器的工具計數及標記零工具伺服器；`EnterWorktree` 修復為從本地 HEAD 而非 `origin/<預設分支>` 創建分支，防止未推送提交遺失；修復平行 Bash 工具調用中讀取命令（grep、git diff、ls）失敗不再取消兄弟調用；`--plugin-dir` 新增 .zip 外掛支持；MCP 伺服器重新連接時改進工具列表通告避免重複。另修復焦點模式切換、拖放圖片掛起、vim 空格鍵行為等多個 UX 問題。

### 重點
- `EnterWorktree` 修復：從本地 HEAD 創建分支而非遠端預設分支，保留未推送提交
- `/mcp` 命令增添工具計數顯示與零工具伺服器標記，改進伺服器診斷
- 修復平行 Bash 工具調用中讀取命令失敗會取消兄弟調用的問題

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.128)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<h2>What's changed</h2>
<ul>
<li>Bare <code>/color</code> (no args) now picks a random session color</li>
<li><code>/mcp</code> now shows the tool count for connected servers and flags servers that connected with 0 tools</li>
<li><code>--plugin-dir</code> now accepts <code>.zip</code> plugin archives in addition to directories</li>
<li><code>--channels</code> now works with console (API key) authentication — console orgs with managed settings must set <code>channelsEnabled: true</code> to enable</li>
<li>Updated <code>/model</code> picker: collapsed duplicate Opus 4.7 entries, and current Opus now shows as "Opus" instead of "Opus 4.7"</li>
<li>Subprocesses (Bash, hooks, MCP, LSP) no longer inherit <code>OTEL_*</code> environment variables, so OTEL-instrumented apps run via the Bash tool no longer pick up the CLI's own OTLP endpoint</li>
<li>MCP: <code>workspace</code> is now a reserved server name — existing servers with that name will be skipped with a warning</li>
<li>Reconnecting MCP servers no longer flood the conversation with full tool-name lists on every reconnect — re-announced tools are summarized by server prefix</li>
<li>SDK hosts now receive a persistent <code>localSettings</code> suggestion for Bash permission prompts, so "Always allow" writes to <code>.claude/settings.local.json</code></li>
<li><code>EnterWorktree</code> now creates the new branch from local HEAD as documented, instead of <code>origin/&lt;default-branch&gt;</code> — unpushed commits are no longer dropped</li>
<li>Auto mode: when the classifier can't evaluate an action, the error now includes a hint (retry, <code>/compact</code>, or run with <code>--debug</code>)</li>
<li>Fixed focus mode briefly dimming the previous response when submitting a new prompt</li>
<li>Fixed stray "4;0;" desktop notification on every <code>/exit</code> in Kitty and other terminals that interpret OSC 9 as a notification</li>
<li>Fixed Remote Control showing an empty "Opening your options…" message on rate limit instead of actionable upsell options</li>
<li>Fixed drag-and-drop image upload hanging on "Pasting text…" when the image read fails</li>
<li>Fixed crash loop when piping very large input (&gt;10 MB) to <code>claude -p</code> via stdin</li>
<li>Fixed long URLs not being individually clickable on every wrapped row in fullscreen mode</li>
<li>Fixed <code>/plugin</code> Components panel showing "Marketplace 'inline' not found" for plugins loaded via <code>--plugin-dir</code></li>
<li>Fixed MCP tool results dropping images when the server returns both structured content and content blocks</li>
<li>Fixed fenced code blocks inside list items carrying leading whitespace into the clipboard on copy-paste</li>
<li>Fixed tab navigation in <code>/config</code> stranding focus — the tab header now stays focused so arrows and Esc keep working</li>
<li>Fixed markdown link labels being lost on terminals without OSC 8 hyperlink support — links now render as <code>label (url)</code> instead of just the URL</li>
<li>Fixed sessions on 1M-context models with a smaller autocompact window being falsely blocked with "Prompt is too long" before reaching the actual API limit</li>
<li>Fixed parallel shell tool calls: a failing read-only command (grep, git diff, ls) no longer cancels sibling calls</li>
<li>Fixed banner showing "with X effort" on models that don't support effort</li>
<li>Fixed <code>/fast</code> on 3P providers fuzzy-matching to an unrelated skill instead of showing "not available"</li>
<li>Fixed Bedrock default model resolving to <code>global.*</code> instead of the region-appropriate prefix</li>
<li>Fixed vim mode: <code>Space</code> in NORMAL mode now moves the cursor right, matching standard vi/vim behavior</li>
<li>Fixed terminal progress indicator (OSC 9;4) flickering off between tool calls — stays visible across the full turn</li>
<li>Fixed <code>/rename</code> without args failing on resumed sessions whose last entry is a compact boundary</li>
<li>Fixed stale "remote-control is active" status lines from prior sessions appearing after <code>--resume</code>/<code>--continue</code></li>
<li>Fixed stale <code>installed_plugins.json</code> entries pointing at deleted cache directories polluting PATH</li>
<li>Fixed MCP stdio servers receiving corrupted arguments when <code>CLAUDE_CODE_SHELL_PREFIX</code> is set and an argument contains spaces or shell metacharacters</li>
<li>Fixed sub-agent progress summaries missing the prompt cache (~3× <code>cache_creation</code> reduction)</li>
<li>Fixed <code>/plugin update</code> never detecting new versions of npm-sourced plugins</li>
<li>Fixed sub-agent summaries firing repeatedly while a sub-agent's transcript is static, capping worst-case token cost on idle sub-agents</li>
<li>Headless <code>--output-format stream-json</code>: <code>init.plugin_errors</code> now includes <code>--plugin-dir</code> load failures in addition to dependency demotions</li>
</ul>

</details>