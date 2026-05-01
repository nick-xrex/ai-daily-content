---
id: inbox_423ec68b
date: 2026-04-29
source_ref: "[[00-inbox/2026-04-29/1257-simon-willison-llm-0-32a1-9157]]"
title: "llm 0.32a1"
url: https://simonwillison.net/2026/Apr/29/llm-3/#atom-everything
source: simon-willison
published_at: 2026-04-29T23:52:50+00:00
fetched_at: 2026-05-01T13:03:04.446653+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 的 llm 工具發布 0.32a1 版本，修復了前一版本 0.32a0 中工具調用會話從 SQLite 資料庫讀取時的錯誤。該修復涉及 issue #1426 的問題解決。"
key_points:
  - "修復 tool-calling 會話的 SQLite 反序列化缺陷（issue #1426）"
  - "v0.32a1 為 alpha 版本，持續迭代中"
tags: [llm-cli, bug-fix, sqlite, tool-use]
topics: []
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## llm 0.32a1

Simon Willison 的 llm 工具發布 0.32a1 版本，修復了前一版本 0.32a0 中工具調用會話從 SQLite 資料庫讀取時的錯誤。該修復涉及 issue #1426 的問題解決。

### 重點
- 修復 tool-calling 會話的 SQLite 反序列化缺陷（issue #1426）
- v0.32a1 為 alpha 版本，持續迭代中

**原文：** [simon-willison](https://simonwillison.net/2026/Apr/29/llm-3/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<p><strong>Release:</strong> <a href="https://github.com/simonw/llm/releases/tag/0.32a1">llm 0.32a1</a></p>
    <blockquote>
<ul>
<li>Fixed a bug in 0.32a0 where tool-calling conversations were not correctly reinflated from SQLite. <a href="https://github.com/simonw/llm/issues/1426">#1426</a></li>
</ul>
</blockquote>
    
        <p>Tags: <a href="https://simonwillison.net/tags/llm">llm</a></p>

</details>