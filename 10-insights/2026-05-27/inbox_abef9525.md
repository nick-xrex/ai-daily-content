---
id: inbox_abef9525
date: 2026-05-27
source_ref: "[[00-inbox/2026-05-27/2344-claude-code-releases-v2-1-152-3c50]]"
title: "v2.1.152"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.152
source: claude-code-releases
published_at: 2026-05-27T01:30:59+00:00
fetched_at: 2026-05-27T23:49:52.839786+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.152 發布，引入 /code-review --fix 命令可將審查建議直接應用到工作樹，支持識別代碼重用、簡化與效率機會。Skills 系統新增 disallowed-tools 前置詞移除特定工具；SessionStart hooks 可啟動 skill 目錄重新掃描（reloadSkills: true）及設定會話標題；新增 MessageDisplay hook 轉換助手訊息輸出。UI 優化包含 Vim 模式增強（NORMAL 模式 / 鍵提供反向歷史搜尋）、思考摘要最少可讀 3 秒並限制 10 行、背景 agent 計數提示優化、模型不可用時自動切換至 fallback 模型。修復 20+ 項 bug 涵蓋插件重複刪除、終端樣式降級、markdown 表格樣式等。"
key_points:
  - "/code-review --fix 可自動應用審查建議至工作樹，檢測代碼重用、簡化和效率改進機會"
  - "Skills 系統新增 disallowed-tools 機制、SessionStart hooks 支持動態 skill 重載（/reload-skills）、MessageDisplay hook；無需重啟會話"
  - "Vim 模式強化、思考摘要可讀性提升（3 秒+、10 行限制）、模型自動切換、20+ bug 修復"
tags: [claude-code, code-review, tooling, ide-improvements, vim-mode]
topics: []
importance: 4
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.152

Claude Code v2.1.152 發布，引入 /code-review --fix 命令可將審查建議直接應用到工作樹，支持識別代碼重用、簡化與效率機會。Skills 系統新增 disallowed-tools 前置詞移除特定工具；SessionStart hooks 可啟動 skill 目錄重新掃描（reloadSkills: true）及設定會話標題；新增 MessageDisplay hook 轉換助手訊息輸出。UI 優化包含 Vim 模式增強（NORMAL 模式 / 鍵提供反向歷史搜尋）、思考摘要最少可讀 3 秒並限制 10 行、背景 agent 計數提示優化、模型不可用時自動切換至 fallback 模型。修復 20+ 項 bug 涵蓋插件重複刪除、終端樣式降級、markdown 表格樣式等。

### 重點
- /code-review --fix 可自動應用審查建議至工作樹，檢測代碼重用、簡化和效率改進機會
- Skills 系統新增 disallowed-tools 機制、SessionStart hooks 支持動態 skill 重載（/reload-skills）、MessageDisplay hook；無需重啟會話
- Vim 模式強化、思考摘要可讀性提升（3 秒+、10 行限制）、模型自動切換、20+ bug 修復

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.152)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 /code-review --fix now applies review findings to your working tree after the review, surfacing reuse, simplification, and efficiency suggestions; /simplify now invokes /code-review --fix 
 Skills and slash commands can now set disallowed-tools in frontmatter to remove tools from the model while the skill is active 
 Added /reload-skills command to re-scan skill directories without restarting the session 
 SessionStart hooks can now return reloadSkills: true to re-scan skill directories, making skills installed by the hook available in the same session 
 SessionStart hooks can now set the session title via hookSpecificOutput.sessionTitle on startup and resume 
 Added a MessageDisplay hook event that lets hooks transform or hide assistant message text as it is displayed 
 Added pluginSuggestionMarketplaces managed setting: admins can allowlist org marketplaces whose plugins may be suggested via context-aware tips 
 claude plugin marketplace remove now accepts --scope user|project|local for symmetry with marketplace add , install , and uninstall 
 Claude Code now switches to your configured --fallback-model for the rest of the session when the primary model is not found, instead of failing every request 
 Auto mode no longer requires opt-in consent 
 Vim mode: / in NORMAL mode now opens reverse history search (like Ctrl+R), matching bash/zsh vi-mode 
 The /usage breakdown now includes large session files; files are scanned with a streaming read so memory usage stays flat 
 Thinking summaries in the collapsed group now stay readable for at least 3 seconds, render as markdown, and cap at 10 lines ( Ctrl+O shows the full thinking) 
 In fullscreen mode, the "Thinking for Ns" indicator now counts up live while the model is thinking, and keeps its value if you interrupt mid-thought 
 Simplified the Workflow tool's inline progress display — live agent counts now show only in the persistent workflow status row below the prompt 
 The post-response timer now shows "Waiting for N background agents/workflows to finish" when backgrounded agents or workflows are still running, and reports the cumulative time once their results are processed 
 Added the session entrypoint as an OpenTelemetry metric attribute ( app.entrypoint , opt-in via OTEL_METRICS_INCLUDE_ENTRYPOINT=true ) 
 Fixed terminal styling degrading in very long sessions by recycling the renderer's style pool 
 Fixed the sandbox-enabled warning not appearing in condensed startup mode — it now shows in every layout 
 Fixed the loading spinner showing "still thinking"/"almost done thinking" while a tool is running, and reset the thinking status to "thinking" after each tool 
 Fixed focus mode showing a spurious "N messages hidden" count on turns with no hidden activity 
 Fixed clicking a link inside an expanded tool result collapsing the section instead of opening the link 
 Fixed markdown table cell borders inheriting the color of inline code, wrapped continuation lines losing their style, and empty header cells showing a label in the narrow-terminal stacked layout 
 Fixed plugin MCP servers with the same command but different environment variables being incorrectly deduplicated 
 Fixed /doctor reporting "marketplace not found" or "plugin not found" for stale enabledPlugins entries referencing removed marketplaces or dropped plugins 
 Fixed plugins that track a git branch silently no longer receiving updates after the plugin registry was rebuilt 
 Fixed remote MCP servers failing to connect in Claude Code Remote sessions when the egress proxy is enabled 
 Fixed the effort-change confirmation dialog appearing when the conversation has no messages or when switching between effort levels that resolve to the same underlying value 
 Fixed the Agent tool description referencing an agent list that is never delivered when running with --bare or with attachments disabled 
 Fixed a background worker crash in claude agents when accepting a stale permission prompt after a subagent was cancelled 
 Fixed cache_creation_input_tokens reporting as 0 in transcript and result usage when the API reports cache writes only via the nested cache_creation breakdown 
 Fixed the PushNotification tool incorrectly reporting "Mobile push not sent (Remote Control inactive)" in SDK-hosted sessions when Remote Control is enabled 
 Fixed sessions getting stuck after a model or login switch left stale thinking-block signatures in history; now stripped proactively with a retry safety-net

</details>