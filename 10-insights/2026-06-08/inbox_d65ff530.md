---
id: inbox_d65ff530
date: 2026-06-08
source_ref: "[[00-inbox/2026-06-08/1801-medium-tag-claude-claude-code-skills-vs-agents-knowing-whi-3fdb]]"
title: "Claude Code — Skills vs Agents: Knowing Which One to Use (Part 5)"
url: https://simran-kahlon.medium.com/claude-code-skills-vs-agents-knowing-which-one-to-use-part-5-61f7591b50bf?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-06-08T16:45:40+00:00
fetched_at: 2026-06-08T18:20:12.438418+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 生態中 Skills 與 Agents 的功能差異和適用場景對比。Skills 初始只載入名稱和描述到上下文（按需展開完整指令），在同一 session 內執行，適合重複性流程（安全審查清單、提交訊息格式化）；Agents 每次執行都新建隔離上下文窗口，自攜完整系統提示，適合多步驟複雜任務和平行執行。兩者可互補：Agent 可觸發 Skills，Skills 執行定義程序，Agents 處理探索。"
key_points:
  - "上下文載入差異：Skills 延遲載入（名稱/描述佔用少量 token），Agents 隔離上下文（完整系統提示總是全部載入）"
  - "場景選擇：Skills 優先用於輕量重複流程（描述清晰、執行穩定），Agents 用於需獨立判斷、多步驟探索的複雜任務"
  - "配置差異：Skills 用 allowed-tools，Agents 用 tools；Agents 需 permissionMode 且 model 應用總是開啟，Skills 僅在 context: fork 時啟用"
tags: [claude-code, skills, agents, workflow]
topics: [agents.mcp]
importance: 4
novelty: 2
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## Claude Code — Skills vs Agents: Knowing Which One to Use (Part 5)

Claude Code 生態中 Skills 與 Agents 的功能差異和適用場景對比。Skills 初始只載入名稱和描述到上下文（按需展開完整指令），在同一 session 內執行，適合重複性流程（安全審查清單、提交訊息格式化）；Agents 每次執行都新建隔離上下文窗口，自攜完整系統提示，適合多步驟複雜任務和平行執行。兩者可互補：Agent 可觸發 Skills，Skills 執行定義程序，Agents 處理探索。

### 重點
- 上下文載入差異：Skills 延遲載入（名稱/描述佔用少量 token），Agents 隔離上下文（完整系統提示總是全部載入）
- 場景選擇：Skills 優先用於輕量重複流程（描述清晰、執行穩定），Agents 用於需獨立判斷、多步驟探索的複雜任務
- 配置差異：Skills 用 allowed-tools，Agents 用 tools；Agents 需 permissionMode 且 model 應用總是開啟，Skills 僅在 context: fork 時啟用

**原文：** [medium-tag-claude](https://simran-kahlon.medium.com/claude-code-skills-vs-agents-knowing-which-one-to-use-part-5-61f7591b50bf?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

This is Part 5 of the series &#x201c;Claude Code, The Way Nobody Told You.&#x201d; &#x25c0; Part 4: Claude Code is an Agent Continue reading on Medium »

</details>