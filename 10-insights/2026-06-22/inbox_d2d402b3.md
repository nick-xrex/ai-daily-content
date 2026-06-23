---
id: inbox_d2d402b3
date: 2026-06-22
source_ref: "[[00-inbox/2026-06-22/2203-claude-code-releases-v2-1-186-cae5]]"
title: "v2.1.186"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.186
source: claude-code-releases
published_at: 2026-06-22T20:37:34+00:00
fetched_at: 2026-06-22T23:23:45.070930+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.186 發布，新增 MCP CLI 認證指令（claude mcp login/logout）、/workflows 狀態篩選、Skills 管理、tmux/iterm2 支援。重要改進包括：bash 指令現在預設自動觸發 Claude 回應（breaking change，可透過 respondToBashCommands: false 停用），修復睡眠喚醒後串流失敗的「Content block not found」及 JSON 解析錯誤、background agent 權限提示改善、Workflow schema 驗證無窮迴圈等 15+ 項 bug。"
key_points:
  - "新增 `claude mcp login/logout` CLI 命令，支援 --no-browser SSH 重導，無需開啟互動式 /mcp 菜單"
  - "bash 命令預設自動觸發 Claude 回應（breaking change：可設定 respondToBashCommands: false 還原舊行為）"
  - "修復睡眠喚醒後的串流崩潰（「Content block not found」/JSON 解析失敗）；background agent 權限提示改為在主會話顯示"
tags: [claude-code, mcp, cli, workflow, bug-fixes]
topics: [agents.mcp]
importance: 4
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.186

Claude Code v2.1.186 發布，新增 MCP CLI 認證指令（claude mcp login/logout）、/workflows 狀態篩選、Skills 管理、tmux/iterm2 支援。重要改進包括：bash 指令現在預設自動觸發 Claude 回應（breaking change，可透過 respondToBashCommands: false 停用），修復睡眠喚醒後串流失敗的「Content block not found」及 JSON 解析錯誤、background agent 權限提示改善、Workflow schema 驗證無窮迴圈等 15+ 項 bug。

### 重點
- 新增 `claude mcp login/logout` CLI 命令，支援 --no-browser SSH 重導，無需開啟互動式 /mcp 菜單
- bash 命令預設自動觸發 Claude 回應（breaking change：可設定 respondToBashCommands: false 還原舊行為）
- 修復睡眠喚醒後的串流崩潰（「Content block not found」/JSON 解析失敗）；background agent 權限提示改為在主會話顯示

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.186)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added claude mcp login &lt;name&gt; and claude mcp logout &lt;name&gt; to authenticate MCP servers from the CLI without opening the interactive /mcp menu, with --no-browser stdin redirect support for completing over SSH 
 Added status filtering (press f ) to the /workflows agent detail view 
 Added a "Skills" section to the /plugin Installed tab 
 Added teammateMode: "iterm2" setting with a warning when auto mode cannot find the it2 CLI 
 Added "Claude Platform on AWS - refresh credentials" option to /login when awsAuthRefresh is configured 
 ! bash commands now trigger Claude to respond to the output automatically; set "respondToBashCommands": false in settings.json to keep the previous context-only behavior 
 Fixed streaming requests failing with "Content block not found" or JSON parse errors after the machine wakes from sleep 
 Fixed subagent transcript scroll position bleeding into the main transcript on exit 
 Fixed background task previews flashing raw tool names before the agent's plan loaded 
 Fixed Chrome tab-group isolation not applying when the in-product permissions gate is off for concurrent CLI sessions 
 Fixed background session recaps being duplicated; the agent's own end-of-turn summary now shows as the recap line 
 Fixed opening a background session from claude agents leaving the previous screen painted behind it 
 Fixed Agent(type) deny rules and Agent(x,y) allowed-types restrictions not being enforced for named subagent spawns 
 Fixed Esc and Ctrl+C not responding while background agents are still running after the main turn ends 
 Fixed misaligned option numbers in permission prompts when the option text overflows 
 Fixed pressing x on a finished subagent in the agent panel not dismissing it 
 Fixed a misleading "MCP server disconnected" notice for intentionally retired tools when resuming older sessions 
 Fixed /plugin Installed showing a "more above" indicator when already scrolled to the top 
 Fixed ~~strikethrough~~ showing literal tildes in assistant messages instead of rendering as strikethrough 
 Fixed --tools allowing feature-gated tools to slip through before flags loaded on a cold first launch 
 Fixed background job status in claude agents showing a stale "needs input" message after replying 
 Fixed a dark-theme flash when opening a background session from claude agents on a light terminal 
 Fixed mouse-selected text staying highlighted after deleting it in claude agents 
 Fixed session cost not showing for usage-based Enterprise and Team subscribers 
 Fixed agent teams: teammates spawned via tmux/pane backends now inherit the leader's --effort level 
 Fixed Workflow agent({schema}) subagents looping forever on repeated schema validation failures instead of aborting after 5 attempts 
 Improved claude mcp get and claude mcp remove to suggest the closest configured server name on a typo and truncate long server lists 
 Improved memory: the agent is now reminded to compact its MEMORY.md index when nearing the size limit 
 Improved skill frontmatter: display-name , default-enabled , fallback , and metadata.* keys now accept kebab-case, snake_case, and camelCase 
 Improved malformed SKILL.md YAML frontmatter handling: loads the skill body with empty metadata instead of failing silently 
 Changed CLAUDE_CODE_MAX_RETRIES to cap at 15; for unattended sessions, use CLAUDE_CODE_RETRY_WATCHDOG instead 
 Changed background subagents to surface permission prompts in the main session instead of auto-denying; the dialog shows which agent is asking, and Esc denies just that tool 
 Changed /review &lt;pr&gt; to use the same review engine as /code-review medium

</details>