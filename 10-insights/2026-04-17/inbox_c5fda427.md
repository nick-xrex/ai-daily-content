---
id: inbox_c5fda427
date: 2026-04-17
source_ref: "[[00-inbox/2026-04-17/0158-claude-code-releases-v2-1-113-8037]]"
title: "v2.1.113"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.113
source: claude-code-releases
published_at: 2026-04-17T19:34:41+00:00
fetched_at: 2026-04-21T02:00:53.040307+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.113 於 2026 年 4 月 17 日發布，包含架構優化與安全加固。CLI 改為生成原生二進位檔（平臺特定可選依賴）而非捆綁 JavaScript，新增 sandbox.network.deniedDomains 設定可阻擋特定域名，全屏模式新增 Shift+↑/↓ 選擇並滾動，Ctrl+A/E 調和 readline 行為。Subagent 卡死現在 10 分鐘後明確失敗，安全機制強化包括 macOS /private/* 危險移除目標、exec 包裹指令檢偵、find -exec -delete 停用。修復 MCP 併發呼叫逾時處理漏洞、多行表格渲染破損。"
key_points:
  - "CLI 改用原生二進位執行（取代 JavaScript 打包），改善啟動效率"
  - "新增 sandbox.network.deniedDomains 設定，允許黑名單域名突破白名單通配"
  - "Subagent 10 分鐘卡死判定改為明確錯誤；安全規則加強對 sudo/env/watch 等 exec 包裹的偵測"
tags: [claude-code, security, performance, mcp, architecture]
topics: [agents.mcp]
importance: 3
novelty: 3
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.113

Claude Code v2.1.113 於 2026 年 4 月 17 日發布，包含架構優化與安全加固。CLI 改為生成原生二進位檔（平臺特定可選依賴）而非捆綁 JavaScript，新增 sandbox.network.deniedDomains 設定可阻擋特定域名，全屏模式新增 Shift+↑/↓ 選擇並滾動，Ctrl+A/E 調和 readline 行為。Subagent 卡死現在 10 分鐘後明確失敗，安全機制強化包括 macOS /private/* 危險移除目標、exec 包裹指令檢偵、find -exec -delete 停用。修復 MCP 併發呼叫逾時處理漏洞、多行表格渲染破損。

### 重點
- CLI 改用原生二進位執行（取代 JavaScript 打包），改善啟動效率
- 新增 sandbox.network.deniedDomains 設定，允許黑名單域名突破白名單通配
- Subagent 10 分鐘卡死判定改為明確錯誤；安全規則加強對 sudo/env/watch 等 exec 包裹的偵測

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.113)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<h2>What's changed</h2>
<ul>
<li>Changed the CLI to spawn a native Claude Code binary (via a per-platform optional dependency) instead of bundled JavaScript</li>
<li>Added <code>sandbox.network.deniedDomains</code> setting to block specific domains even when a broader <code>allowedDomains</code> wildcard would otherwise permit them</li>
<li>Fullscreen mode: Shift+↑/↓ now scrolls the viewport when extending a selection past the visible edge</li>
<li><code>Ctrl+A</code> and <code>Ctrl+E</code> now move to the start/end of the current logical line in multiline input, matching readline behavior</li>
<li>Windows: <code>Ctrl+Backspace</code> now deletes the previous word</li>
<li>Long URLs in responses and bash output stay clickable when they wrap across lines (in terminals with OSC 8 hyperlinks)</li>
<li>Improved <code>/loop</code>: pressing Esc now cancels pending wakeups, and wakeups display as "Claude resuming /loop wakeup" for clarity</li>
<li><code>/extra-usage</code> now works from Remote Control (mobile/web) clients</li>
<li>Remote Control clients can now query <code>@</code>-file autocomplete suggestions</li>
<li>Improved <code>/ultrareview</code>: faster launch with parallelized checks, diffstat in the launch dialog, and animated launching state</li>
<li>Subagents that stall mid-stream now fail with a clear error after 10 minutes instead of hanging silently</li>
<li>Bash tool: multi-line commands whose first line is a comment now show the full command in the transcript, closing a UI-spoofing vector</li>
<li>Running <code>cd &lt;current-directory&gt; &amp;&amp; git …</code> no longer triggers a permission prompt when the <code>cd</code> is a no-op</li>
<li>Security: on macOS, <code>/private/{etc,var,tmp,home}</code> paths are now treated as dangerous removal targets under <code>Bash(rm:*)</code> allow rules</li>
<li>Security: Bash deny rules now match commands wrapped in <code>env</code>/<code>sudo</code>/<code>watch</code>/<code>ionice</code>/<code>setsid</code> and similar exec wrappers</li>
<li>Security: <code>Bash(find:*)</code> allow rules no longer auto-approve <code>find -exec</code>/<code>-delete</code></li>
<li>Fixed MCP concurrent-call timeout handling where a message for one tool call could silently disarm another call's watchdog</li>
<li>Fixed Cmd-backspace / <code>Ctrl+U</code> to once again delete from the cursor to the start of the line</li>
<li>Fixed markdown tables breaking when a cell contains an inline code span with a pipe character</li>
<li>Fixed session recap auto-firing while composing unsent text in the prompt</li>
<li>Fixed <code>/copy</code> "Full response" not aligning markdown table columns for pasting into GitHub, Notion, or Slack</li>
<li>Fixed messages typed while viewing a running subagent being hidden from its transcript and misattributed to the parent AI</li>
<li>Fixed Bash <code>dangerouslyDisableSandbox</code> running commands outside the sandbox without a permission prompt</li>
<li>Fixed <code>/effort auto</code> confirmation — now says "Effort level set to max" to match the status bar label</li>
<li>Fixed the "copied N chars" toast overcounting emoji and other multi-code-unit characters</li>
<li>Fixed <code>/insights</code> crashing with <code>EBUSY</code> on Windows</li>
<li>Fixed exit confirmation dialog mislabeling one-shot scheduled tasks as recurring — now shows a countdown</li>
<li>Fixed slash/@ completion menu not sitting flush against the prompt border in fullscreen mode</li>
<li>Fixed <code>CLAUDE_CODE_EXTRA_BODY</code> <code>output_config.effort</code> causing 400 errors on subagent calls to models that don't support effort and on Vertex AI</li>
<li>Fixed prompt cursor disappearing when <code>NO_COLOR</code> is set</li>
<li>Fixed <code>ToolSearch</code> ranking so pasted MCP tool names surface the actual tool instead of description-matching siblings</li>
<li>Fixed compacting a resumed long-context session failing with "Extra usage is required for long context requests"</li>
<li>Fixed <code>plugin install</code> succeeding when a dependency version conflicts with an already-installed plugin — now reports <code>range-conflict</code></li>
<li>Fixed "Refine with Ultraplan" not showing the remote session URL in the transcript</li>
<li>Fixed SDK image content blocks that fail to process crashing the session — now degrade to a text placeholder</li>
<li>Fixed Remote Control sessions not streaming subagent transcripts</li>
<li>Fixed Remote Control sessions not being archived when Claude Code exits</li>
<li>Fixed <code>thinking.type.enabled is not supported</code> 400 error when using Opus 4.7 via a Bedrock Application Inference Profile ARN</li>
</ul>

</details>
