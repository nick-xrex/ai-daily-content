---
id: inbox_1a29fab9
date: 2026-05-19
source_ref: "[[00-inbox/2026-05-19/0019-claude-code-releases-v2-1-145-dff4]]"
title: "v2.1.145"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.145
source: claude-code-releases
published_at: 2026-05-19T21:31:07+00:00
fetched_at: 2026-05-20T00:23:13.951564+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.145 發布，包含 10 多項功能改進與穩定性修復。新增 `claude agents --json` 可匯出 live sessions 供 tmux-resurrect 和狀態列整合；改進 OTEL 分佈式追蹤，Agent tool 跨度現在包含 agent_id 和 parent_agent_id，確保後台 subagent 跨度正確巢狀；狀態列 JSON 輸入加入 GitHub 倉庫與 PR 資訊；/plugin 探索畫面現在顯示 plugin commands、agents、skills、hooks 和 MCP/LSP 伺服器清單；修復權限提示旁路漏洞（裸露的環境變數賦值被不當批准）、MCP 命令錯誤訊息、非 ASCII 特殊字符破壞 Agent Teams、以及多項 UX 固定（task list 隨機排序、PR badge 更新延遲、voice push-to-talk）。Read tool 改進：超大檔案現在返回截斷首頁加「PARTIAL view」提示，而非硬錯誤。"
key_points:
  - "`claude agents --json` 輸出 live sessions，支援 tmux-resurrect 和自訂狀態列"
  - "OTEL tracing 加入 agent_id 和 parent_agent_id，後台 subagent 正確巢狀於 dispatching span"
  - "修復權限提示旁路：裸露的環境變數賦值不再自動批准非白名單變數"
tags: [claude-code, devtools, observability, tracing, ux]
topics: []
importance: 4
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.145

Claude Code v2.1.145 發布，包含 10 多項功能改進與穩定性修復。新增 `claude agents --json` 可匯出 live sessions 供 tmux-resurrect 和狀態列整合；改進 OTEL 分佈式追蹤，Agent tool 跨度現在包含 agent_id 和 parent_agent_id，確保後台 subagent 跨度正確巢狀；狀態列 JSON 輸入加入 GitHub 倉庫與 PR 資訊；/plugin 探索畫面現在顯示 plugin commands、agents、skills、hooks 和 MCP/LSP 伺服器清單；修復權限提示旁路漏洞（裸露的環境變數賦值被不當批准）、MCP 命令錯誤訊息、非 ASCII 特殊字符破壞 Agent Teams、以及多項 UX 固定（task list 隨機排序、PR badge 更新延遲、voice push-to-talk）。Read tool 改進：超大檔案現在返回截斷首頁加「PARTIAL view」提示，而非硬錯誤。

### 重點
- `claude agents --json` 輸出 live sessions，支援 tmux-resurrect 和自訂狀態列
- OTEL tracing 加入 agent_id 和 parent_agent_id，後台 subagent 正確巢狀於 dispatching span
- 修復權限提示旁路：裸露的環境變數賦值不再自動批准非白名單變數

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.145)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added claude agents --json to list live Claude sessions as JSON for scripting (tmux-resurrect, status bars, session pickers) 
 Added agent_id and parent_agent_id attributes to claude_code.tool OTEL spans, and fixed trace parenting so background subagent spans nest under the dispatching Agent tool span 
 Status line JSON input now includes GitHub repo and PR information when detected 
 /plugin Discover and Browse screens now show a plugin's commands, agents, skills, hooks, and MCP/LSP servers before installation 
 claude agents terminal tab title now shows the awaiting-input count so an alt-tabbed window tells you when an agent needs attention 
 Slash command and @-mention suggestion list now supports mouse hover and click in fullscreen mode 
 Stop and SubagentStop hook input now includes background_tasks and session_crons fields 
 Fixed a permission-prompt bypass where bare variable assignments to non-allowlisted environment variables in Bash commands were auto-approved 
 Fixed MCP prompt slash commands showing raw server validation errors when a required argument is omitted — the error now names the missing argument and shows expected usage 
 Fixed the spinner and elapsed-time display freezing until a keypress after the terminal was resized or refocused 
 Fixed the cross-project resume hint failing in default Windows PowerShell 5.1 — Windows now uses ; as the command separator 
 Fixed voice push-to-talk not working in the agent view's reply pane 
 Fixed task lists rendering in random order when several tasks are created at once 
 Fixed stale "Failed to install Anthropic marketplace" banner showing when the marketplace is already installed 
 Fixed the PR badge in the footer not updating immediately after gh pr create and other PR-state-changing commands run in-session 
 Fixed Agent Teams teammates with non-ASCII names failing every API call due to invalid header encoding 
 Fixed /review using a deprecated projectCards GraphQL query that errored on repos with Classic Projects 
 Fixed claude plugin validate not flagging skills: entries that point at a file instead of a directory — the error now suggests the parent directory 
 Fixed an infinite loop where a skill using context: fork could repeatedly re-invoke itself instead of running 
 Improved the Read tool to return a truncated first page with a "PARTIAL view" notice instead of a hard error when a whole-file read exceeds the token limit

</details>