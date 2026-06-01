---
id: inbox_2b2b1a80
date: 2026-05-31
source_ref: "[[00-inbox/2026-05-31/2245-simon-willison-datasette-1-0a32-4e74]]"
title: "datasette 1.0a32"
url: https://simonwillison.net/2026/May/31/datasette/#atom-everything
source: simon-willison
published_at: 2026-05-31T23:23:38+00:00
fetched_at: 2026-06-01T22:52:13.117507+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Datasette 1.0a32 發佈修復兩大類問題。首先修復新增端點 /db/-/execute-write 處理 INSERT ... RETURNING 查詢時的 bug；其次修復 Service Workers 實驗期間發現的 base_url 相關問題。這是穩定性改進版本，確保新功能的可靠性。"
key_points:
  - "修復 INSERT ... RETURNING 透過寫入端點的查詢處理"
  - "解決 Service Workers 集成時的 base_url 路由問題"
tags: [datasette, sql-queries, bug-fix, web-api]
topics: []
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette 1.0a32

Datasette 1.0a32 發佈修復兩大類問題。首先修復新增端點 /db/-/execute-write 處理 INSERT ... RETURNING 查詢時的 bug；其次修復 Service Workers 實驗期間發現的 base_url 相關問題。這是穩定性改進版本，確保新功能的可靠性。

### 重點
- 修復 INSERT ... RETURNING 透過寫入端點的查詢處理
- 解決 Service Workers 集成時的 base_url 路由問題

**原文：** [simon-willison](https://simonwillison.net/2026/May/31/datasette/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette 1.0a32 
 A minor bugfix release. Fixes a bug with INSERT ... RETURNING queries via the new /db/-/execute-write endpoint and a bunch of base_url issues which showed up when I was experimenting with Service Workers yesterday. 
 
 
 Tags: datasette , annotated-release-notes

</details>