---
id: inbox_8b56d032
date: 2026-04-28
source_ref: "[[00-inbox/2026-04-28/0658-reddit-claudeai-compared-11-popular-claude-code-workflow-6bbb]]"
title: "Compared 11 popular Claude Code workflow systems in one table — here&#39;s the canonical pipeline of each"
url: https://www.reddit.com/r/ClaudeAI/comments/1sybpya/compared_11_popular_claude_code_workflow_systems/
source: reddit-claudeai
published_at: 2026-04-28T19:34:01+00:00
fetched_at: 2026-04-29T07:28:48.555359+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitHub 用戶發布完整比較表分析 11 種流行 Claude Code 開發工作流，將每個方法論的標準管線結構視覺化。表格以顏色編碼：黃色標籤表示子迴圈（任務級／故事級／驗證迴圈），藍色標籤表示頂層步驟，使工作流差異清晰可見。研究發現管線長度差異極大：OpenSpec 採最簡潔 3 步模式，BMAD 則需 12 步細緻流程，涵蓋範疇從輕量級漸進式到重流程驗證密集型。開發者核心發現：管線長度本身成為方法論的「個性特質」，反映各團隊對規劃密度、自動化強度和驗證嚴格性的不同偏好。完整比較表及來源資訊發佈於 https://github.com/shanraisshan/claude-code-best-practice。"
key_points:
  - "11 工作流管線長度跨度：OpenSpec 3 步 vs BMAD 12 步，展示方法論設計選擇的關鍵差異"
  - "工作流分類標記：黃色子迴圈 vs 藍色頂層步驟，使流程架構結構化可視化，便於選型對比"
  - "「管線長度即性格」發現：選擇工作流反映團隊對規劃密度、自動化比例、驗證強度的價值取捨"
tags: [claude-code, workflows, methodology-comparison, pipeline-architecture, best-practices]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Compared 11 popular Claude Code workflow systems in one table — here's the canonical pipeline of each

GitHub 用戶發布完整比較表分析 11 種流行 Claude Code 開發工作流，將每個方法論的標準管線結構視覺化。表格以顏色編碼：黃色標籤表示子迴圈（任務級／故事級／驗證迴圈），藍色標籤表示頂層步驟，使工作流差異清晰可見。研究發現管線長度差異極大：OpenSpec 採最簡潔 3 步模式，BMAD 則需 12 步細緻流程，涵蓋範疇從輕量級漸進式到重流程驗證密集型。開發者核心發現：管線長度本身成為方法論的「個性特質」，反映各團隊對規劃密度、自動化強度和驗證嚴格性的不同偏好。完整比較表及來源資訊發佈於 https://github.com/shanraisshan/claude-code-best-practice。

### 重點
- 11 工作流管線長度跨度：OpenSpec 3 步 vs BMAD 12 步，展示方法論設計選擇的關鍵差異
- 工作流分類標記：黃色子迴圈 vs 藍色頂層步驟，使流程架構結構化可視化，便於選型對比
- 「管線長度即性格」發現：選擇工作流反映團隊對規劃密度、自動化比例、驗證強度的價值取捨

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1sybpya/compared_11_popular_claude_code_workflow_systems/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/ClaudeAI/comments/1sybpya/compared_11_popular_claude_code_workflow_systems/"> <img alt="Compared 11 popular Claude Code workflow systems in one table — here's the canonical pipeline of each" src="https://preview.redd.it/6cop4xrmgzxg1.png?width=640&amp;crop=smart&amp;auto=webp&amp;s=e626f83103c4c3791e154c2521b144bbb561d204" title="Compared 11 popular Claude Code workflow systems in one table — here's the canonical pipeline of each" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>Mapped the canonical pipeline of 11 popular Claude Code workflow systems side-by-side. Yellow tags = sub-loops (repeat per task / per story / until verified); blue = top-level steps. Pipeline length turns out to be a personality trait — OpenSpec ships in 3 steps, BMAD runs 12.</p> <p>Full table + sources: <a href="https://github.com/shanraisshan/claude-code-best-practice#%EF%B8%8F-development-workflows">https://github.com/shanraisshan/claude-code-best-practice#%EF%B8%8F-development-workflows</a></p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/shanraisshan"> /u/shanraisshan </a> <br /> <span><a href="https://i.redd.it/6cop4xrmgzxg1.png">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1sybpya/compared_11_popular_claude_code_workflow_systems/">[comments]</a></span> </td></tr></table>

</details>