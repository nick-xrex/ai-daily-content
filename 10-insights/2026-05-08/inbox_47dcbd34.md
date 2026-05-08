---
id: inbox_47dcbd34
date: 2026-05-08
source_ref: "[[00-inbox/2026-05-08/0737-reddit-claudeai-cli-cowork-or-ide-6bf8]]"
title: "CLI, Cowork, or IDE?"
url: https://www.reddit.com/r/ClaudeAI/comments/1t6yk0d/cli_cowork_or_ide/
source: reddit-claudeai
published_at: 2026-05-08T05:27:03+00:00
fetched_at: 2026-05-08T08:14:45.069428+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Reddit 用戶分享在三種 Claude 介面（CLI、Cowork、VSCode）上的開發體驗對比。起初在 CLI 環境嘗試單一 subagent 執行單一功能開發，但發現此方法不僅耗時冗長，還容易遺漏需求規格。經多次試驗後發現最優工作流：使用 Cowork 實例扮演專案經理、VSCode 實例扮演開發者，兩者透過 Markdown 文件進行非同步協作，使用者手動觸發實例讀取文件，藉此避免過度推送。此雙實例模式結果快速且代碼品質明顯更優。此經驗揭示一個原則：將工作流中的不同認知角色分給專用實例，優於單一全能實例處理所有任務。"
key_points:
  - "CLI 單一 subagent 方式低效易漏規格；Cowork (PM) + VSCode (Dev) 雙實例搭配快速且品質好"
  - "MD 文件非同步協作 + 手動觸發讀取，避免 context 過度推送與角色混亂"
  - "多實例角色化分工符合認知邊界與專業分工原則，優於全能單一實例"
tags: [claude-workflow-orchestration, multi-agent-collaboration, developer-productivity, async-coordination]
topics: [foundation_models.claude]
importance: 3
novelty: 2
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## CLI, Cowork, or IDE?

Reddit 用戶分享在三種 Claude 介面（CLI、Cowork、VSCode）上的開發體驗對比。起初在 CLI 環境嘗試單一 subagent 執行單一功能開發，但發現此方法不僅耗時冗長，還容易遺漏需求規格。經多次試驗後發現最優工作流：使用 Cowork 實例扮演專案經理、VSCode 實例扮演開發者，兩者透過 Markdown 文件進行非同步協作，使用者手動觸發實例讀取文件，藉此避免過度推送。此雙實例模式結果快速且代碼品質明顯更優。此經驗揭示一個原則：將工作流中的不同認知角色分給專用實例，優於單一全能實例處理所有任務。

### 重點
- CLI 單一 subagent 方式低效易漏規格；Cowork (PM) + VSCode (Dev) 雙實例搭配快速且品質好
- MD 文件非同步協作 + 手動觸發讀取，避免 context 過度推送與角色混亂
- 多實例角色化分工符合認知邊界與專業分工原則，優於全能單一實例

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t6yk0d/cli_cowork_or_ide/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What is the best way to use Claude for programming projects? I started out in the CLI and then tried cowork and eventually decided to use the Claude plugin in vscode. I definitely notice I get different results. I found that when I asked CLI Claude to spin up sub agents to develop specific features on my project, it ended up taking a lot of time and often missed specs. Alternatively, I’ve found the best results by having one instance of Claude cowork be my project manager and have another instance of Claude in VScode be the developer. They communicate through writing in MD files and have to be prompted by me to read them. But I’ve found this to be much faster and result in better code. &#32; submitted by &#32; /u/onixmmgo [link] &#32; [comments]

</details>