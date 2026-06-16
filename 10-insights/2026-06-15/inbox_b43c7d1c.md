---
id: inbox_b43c7d1c
date: 2026-06-15
source_ref: "[[00-inbox/.../inbox_b43c7d1c]]"
title: "v2.1.178"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.178
source: claude-code-releases
published_at: 2026-06-15T21:35:55+00:00
fetched_at: 2026-06-16T00:43:14.368410+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.178 發布，引入細粒度權限規則、巢狀設定目錄優先解析、改進 subagent 啟動器安全檢查，以及大量 bug 修復。新增 Tool(param:value) 語法支援權限規則中的參數匹配（如 Agent(model:opus) 可阻擋 Opus subagent）。.claude/ 巢狀目錄內的 agent/workflow 配置優先級由到工作目錄的距離決定。改進 auto 模式在 subagent 生成前進行分類器驗證。修復多項 nested skills、MCP 相關問題及 vim/CJK 輸入法相容性。"
key_points:
  - "Permission rules 引入 Tool(param:value) 語法實現參數層級的細粒度控制（如 Agent(model:opus) 可指定阻擋特定模型的 subagent）"
  - "巢狀 .claude/ 目錄：最接近工作目錄的 agent/workflow/output-style 配置優先套用，實現工作區級的本地化覆蓋"
  - "Subagent 啟動前加入分類器驗證，阻止被禁用的操作繞過安全檢查"
tags: [claude-code, permission-system, nested-config, subagent-safety]
topics: []
importance: 3
novelty: 2
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.178

Claude Code v2.1.178 發布，引入細粒度權限規則、巢狀設定目錄優先解析、改進 subagent 啟動器安全檢查，以及大量 bug 修復。新增 Tool(param:value) 語法支援權限規則中的參數匹配（如 Agent(model:opus) 可阻擋 Opus subagent）。.claude/ 巢狀目錄內的 agent/workflow 配置優先級由到工作目錄的距離決定。改進 auto 模式在 subagent 生成前進行分類器驗證。修復多項 nested skills、MCP 相關問題及 vim/CJK 輸入法相容性。

### 重點
- Permission rules 引入 Tool(param:value) 語法實現參數層級的細粒度控制（如 Agent(model:opus) 可指定阻擋特定模型的 subagent）
- 巢狀 .claude/ 目錄：最接近工作目錄的 agent/workflow/output-style 配置優先套用，實現工作區級的本地化覆蓋
- Subagent 啟動前加入分類器驗證，阻止被禁用的操作繞過安全檢查

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.178)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v2.1.178

What's changed 
 
 Added Tool(param:value) syntax for permission rules to match a tool's input parameters (with * wildcard), e.g. Agent(model:opus) to block Opus subagents 
 Skills in nested .claude/skills directories now load when working on files there; on a name clash, the nested skill appears as &lt;dir&gt;:&lt;name&gt; so both stay available 
 Nested .claude/ directories: the agent, workflow, and output-style closest to the working directory now wins when names collide; project-scope workflow saves now target the closest existing .claude/workflows/ 
 Improved auto mode: subagent spawns are now evaluated by the classifier before launch, closing a gap where a subagent could request a blocked action without review 
 Improved /doctor with consistent flat tree layout across all sections, clearer section status icons, and highlighted command names 
 Improved the skill listing truncation warning to show how many skill descriptions are affected 
 Changed the workflow prompt keyword to use a purple shimmer highlight and trigger only on explicit phrases like "run a workflow" or "workflow:", not on any mention of the word 
 Improved Remote Control error messages: connection failures now show a persistent red "/rc failed" indicator in the footer, and the "not yet enabled" error now explains whether it's a gate, a check failure, stale entitlement, or org policy 
 /bug now requires a description before submitting, and no longer uses model-refusal text as the GitHub issue title 
 Fixed a crash (out-of-memory) when the CLI inherits a stale websocket/OAuth file-descriptor environment variable from a parent process 
 Fixed Claude in Chrome silently failing to connect when the OAuth token belongs to a different account than the Claude Code login 
 Fixed nested .claude/skills skills with directory-qualified names being blocked by permission prompts in non-interactive runs 
 Fixed several subagent issues: viewing a subagent's transcript now shows tool results and live progress, messages sent while it finishes its turn are no longer dropped, and backgrounding a running subagent (ctrl+b) no longer restarts it from scratch 
 Fixed claude agents workers failing with 401 Invalid bearer token when the daemon was started from a shell with a custom API gateway via ANTHROPIC_BASE_URL and ANTHROPIC_AUTH_TOKEN 
 Fixed compaction not honoring --fallback-model : compaction now falls back to the configured fallback model chain on overload or model-availability errors 
 Fixed model requests continuing to fail with auth errors after credentials were refreshed outside the session, due to a stale cached request configuration 
 Fixed background sessions created with /bg or ←← after a turn finished showing "Working" forever in the agents list 
 Fixed CLAUDE_CODE_PLUGIN_KEEP_MARKETPLACE_ON_FAILURE=1 preventing fresh marketplace installs from cloning 
 Fixed MCP server-level specs ( mcp__server , mcp__server__* , mcp__* ) in subagent disallowedTools being silently ignored 
 Fixed vim mode undo: u now steps through NORMAL/VISUAL-mode commands one at a time instead of merging commands in quick succession into a single undo step 
 Fixed statusline links with custom URI schemes (e.g. vscode:// ) not opening when clicked in claude agents 
 [VSCode] Fixed pressing Esc to dismiss a CJK IME candidate window canceling the running Claude task

</details>