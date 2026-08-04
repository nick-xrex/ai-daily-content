---
id: inbox_cb3a8359
date: 2026-08-03
source_ref: "[[00-inbox/.../inbox_cb3a8359]]"
title: "Quoting David Crawshaw&#39;s prompt"
url: https://simonwillison.net/2026/Aug/3/david-crawshaw/#atom-everything
source: simon-willison
published_at: 2026-08-03T16:15:27+00:00
fetched_at: 2026-08-04T01:52:41.994984+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "David Crawshaw 撰寫的自動化提示詞展示使用代理自動化軟體維護的實務模式。該提示指示建立夜間 cron 任務執行指定動作序列：獲取上游程式庫變更、將本地變更變基至最新版本、驗證軟體運作正常、最後以新版本替換當前版本。此模式結合了版本控制（fetch + rebase）、自動化測試驗證與部署三環節。示範如何利用代理串聯工作流進行持續集成與自動部署，減少手動介入。該提示詞可套用於本地開發環境維護、依賴更新自動化等場景。"
key_points:
  - "Cron + 代理工作流自動化軟體維護序列：fetch upstream → rebase local → verify → replace"
  - "結合版本控制與自動化測試驗證，實現無人值守軟體更新"
  - "可應用於本地環境維護、依賴更新自動化等實務場景"
tags: [prompt-engineering, automation, agent-workflow, software-maintenance, ci-cd]
topics: []
importance: 2
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Quoting David Crawshaw's prompt

David Crawshaw 撰寫的自動化提示詞展示使用代理自動化軟體維護的實務模式。該提示指示建立夜間 cron 任務執行指定動作序列：獲取上游程式庫變更、將本地變更變基至最新版本、驗證軟體運作正常、最後以新版本替換當前版本。此模式結合了版本控制（fetch + rebase）、自動化測試驗證與部署三環節。示範如何利用代理串聯工作流進行持續集成與自動部署，減少手動介入。該提示詞可套用於本地開發環境維護、依賴更新自動化等場景。

### 重點
- Cron + 代理工作流自動化軟體維護序列：fetch upstream → rebase local → verify → replace
- 結合版本控制與自動化測試驗證，實現無人值守軟體更新
- 可應用於本地環境維護、依賴更新自動化等實務場景

**原文：** [simon-willison](https://simonwillison.net/2026/Aug/3/david-crawshaw/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Quoting David Crawshaw's prompt

Set up a nightly cron job that executes the prompt: fetch upstream changes to the &lt;software&gt; and rebase all local changes on top of upstream. Check that the software works as intended and replace the current version. 
 &mdash; David Crawshaw&#x27;s prompt , Devtools must be open source 

 Tags: prompt-engineering , coding-agents , generative-ai , ai , llms , open-source

</details>