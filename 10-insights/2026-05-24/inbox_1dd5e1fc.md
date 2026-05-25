---
id: inbox_1dd5e1fc
date: 2026-05-24
source_ref: "[[00-inbox/2026-05-24/0011-simon-willison-datasette-1-0a30-a29a]]"
title: "datasette 1.0a30"
url: https://simonwillison.net/2026/May/24/datasette/#atom-everything
source: simon-willison
published_at: 2026-05-24T23:52:37+00:00
fetched_at: 2026-05-25T00:16:55.584151+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Datasette 1.0a30 alpha 版本新增可自訂的「Jump to...」菜單功能。用戶可在 latest.datasette.io 中按下 / 鍵啟動菜單。新版本引入 jump_items_sql() plugin hook，允許第三方插件向搜尋集合中新增自訂項目，大幅擴展菜單的擴展性。此功能為 Datasette 邁向 1.0 穩定版本的重要里程碑。"
key_points:
  - "版本 1.0a30：新增 Jump to... 菜單，按 / 快速啟動"
  - "插件 API：jump_items_sql() 允許插件註冊自訂搜尋項目"
  - "線上試用：latest.datasette.io 已上線試驗版本"
tags: [datasette, plugin-hooks, ui-feature, alpha-release]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette 1.0a30

Datasette 1.0a30 alpha 版本新增可自訂的「Jump to...」菜單功能。用戶可在 latest.datasette.io 中按下 / 鍵啟動菜單。新版本引入 jump_items_sql() plugin hook，允許第三方插件向搜尋集合中新增自訂項目，大幅擴展菜單的擴展性。此功能為 Datasette 邁向 1.0 穩定版本的重要里程碑。

### 重點
- 版本 1.0a30：新增 Jump to... 菜單，按 / 快速啟動
- 插件 API：jump_items_sql() 允許插件註冊自訂搜尋項目
- 線上試用：latest.datasette.io 已上線試驗版本

**原文：** [simon-willison](https://simonwillison.net/2026/May/24/datasette/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette 1.0a30 
 The big new feature in this alpha is a new customizable "Jump to..." menu, described in detail in The extensible "Jump to" menu in Datasette 1.0a30 on the Datasette blog. You can try it out by hitting / on latest.datasette.io - it looks like this: 
 
 The new jump_items_sql() plugin hook allows plugins to add their own items to the set that's searched by the plugin. 
 
 
 Tags: projects , datasette , annotated-release-notes

</details>