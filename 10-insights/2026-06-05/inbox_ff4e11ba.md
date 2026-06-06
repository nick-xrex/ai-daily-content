---
id: inbox_ff4e11ba
date: 2026-06-05
source_ref: "[[00-inbox/2026-06-05/1800-rtk-releases-v0-42-2-db69]]"
title: "v0.42.2"
url: https://github.com/rtk-ai/rtk/releases/tag/v0.42.2
source: rtk-releases
published_at: 2026-06-05T11:04:57+00:00
fetched_at: 2026-06-05T18:06:27.743680+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK v0.42.2 發布。此版本修復了三類權限管理問題：(1) 移除檔案重定向的自動允許並限制作用域至 Gemini/Cursor 配置、(2) 阻止自動評估不可評估的命令，改為延遲至主機決定、(3) 實現項目優先的配置查詢邏輯。這些修復強化了權限系統在多編輯器場景下的安全性。"
key_points:
  - "檔案重定向不再自動允許，須明確作用域限制至 Gemini/Cursor"
  - "不可評估命令不再自動許可，改由宿主主機判決"
  - "項目級配置查詢優先於全局配置，改進 Gemini/Cursor 相容性"
tags: [rtk, permissions, security, gemini, cursor]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v0.42.2

RTK v0.42.2 發布。此版本修復了三類權限管理問題：(1) 移除檔案重定向的自動允許並限制作用域至 Gemini/Cursor 配置、(2) 阻止自動評估不可評估的命令，改為延遲至主機決定、(3) 實現項目優先的配置查詢邏輯。這些修復強化了權限系統在多編輯器場景下的安全性。

### 重點
- 檔案重定向不再自動允許，須明確作用域限制至 Gemini/Cursor
- 不可評估命令不再自動許可，改由宿主主機判決
- 項目級配置查詢優先於全局配置，改進 Gemini/Cursor 相容性

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/v0.42.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

0.42.2 (2026-06-05) 
 Bug Fixes 
 
 permissions: &gt;&amp;file redirect no allow + scope Gemini/Cursor config ( ce36297 ) 
 permissions: never auto-allow not evaluable cmds, defer to hosts ( e1bc0bd ) 
 permissions: project-first config lookup for Gemini/Cursor ( 084fa84 )

</details>