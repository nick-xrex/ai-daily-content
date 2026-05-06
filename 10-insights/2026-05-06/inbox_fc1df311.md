---
id: inbox_fc1df311
date: 2026-05-06
source_ref: "[[00-inbox/2026-05-06/1251-medium-tag-claude-why-claude-keeps-ignoring-your-instructi-91c0]]"
title: "Why Claude Keeps Ignoring Your Instructions (and the 4-Line Fix)"
url: https://medium.com/@danielvalev/why-claude-keeps-ignoring-your-instructions-and-the-4-line-fix-1920ffa5bd19?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-05-06T12:01:01+00:00
fetched_at: 2026-05-06T12:59:44.729104+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Daniel Valev 發現大型 CLAUDE.md 文件降低 Claude 的指令依從性，因為模型有「可靠追蹤指令的上限」。他建議將文件限制在 200 行以內，只保留 4 個核心部分：(1) 構建與測試命令，(2) 單一關鍵約束（原因性敘述），(3) Git 工作流規範，(4) 完成定義。刪掉代碼風格規則（交給 linter）、架構文檔（用 @path 引用）、工作流特定指令（改放到 .claude/skills/ 資料夾）。最終精煉的檔案通常為 22 行，每行都防止特定類型的錯誤。"
key_points:
  - "CLAUDE.md 應限制 200 行以內，用「構建命令、關鍵約束、Git 工作流、完成定義」4 部分結構化"
  - "避免加入代碼風格規則（由 linter 執行）、架構文檔（用 @path 引用）、工作流指令（移至 .claude/skills/）"
  - "每一行都應防止一個具體錯誤類型，精煉版本通常為 22 行左右"
tags: [claude-code, CLAUDE.md, instruction-following, workflow]
topics: []
importance: 4
novelty: 3
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Why Claude Keeps Ignoring Your Instructions (and the 4-Line Fix)

Daniel Valev 發現大型 CLAUDE.md 文件降低 Claude 的指令依從性，因為模型有「可靠追蹤指令的上限」。他建議將文件限制在 200 行以內，只保留 4 個核心部分：(1) 構建與測試命令，(2) 單一關鍵約束（原因性敘述），(3) Git 工作流規範，(4) 完成定義。刪掉代碼風格規則（交給 linter）、架構文檔（用 @path 引用）、工作流特定指令（改放到 .claude/skills/ 資料夾）。最終精煉的檔案通常為 22 行，每行都防止特定類型的錯誤。

### 重點
- CLAUDE.md 應限制 200 行以內，用「構建命令、關鍵約束、Git 工作流、完成定義」4 部分結構化
- 避免加入代碼風格規則（由 linter 執行）、架構文檔（用 @path 引用）、工作流指令（移至 .claude/skills/）
- 每一行都應防止一個具體錯誤類型，精煉版本通常為 22 行左右

**原文：** [medium-tag-claude](https://medium.com/@danielvalev/why-claude-keeps-ignoring-your-instructions-and-the-4-line-fix-1920ffa5bd19?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<div class="medium-feed-item"><p class="medium-feed-image"><a href="https://medium.com/@danielvalev/why-claude-keeps-ignoring-your-instructions-and-the-4-line-fix-1920ffa5bd19?source=rss------claude-5"><img src="https://cdn-images-1.medium.com/max/1254/1*eiD8snwCOF0flTG6Kum-TA.png" width="1254" /></a></p><p class="medium-feed-snippet">Most developers treat CLAUDE.md like a config dump. Here&#x2019;s why that&#x2019;s killing your sessions &#x2014; and the minimal structure that actually works</p><p class="medium-feed-link"><a href="https://medium.com/@danielvalev/why-claude-keeps-ignoring-your-instructions-and-the-4-line-fix-1920ffa5bd19?source=rss------claude-5">Continue reading on Medium »</a></p></div>

</details>