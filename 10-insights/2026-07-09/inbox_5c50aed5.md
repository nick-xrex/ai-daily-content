---
id: inbox_5c50aed5
date: 2026-07-09
source_ref: "[[00-inbox/2026-07-09/2207-gitnexus-releases-rc-950c0a7b93b2f863c062ddd5c0342cb2bb2b9-4b41]]"
title: "rc/950c0a7b93b2f863c062ddd5c0342cb2bb2b9eaf: fix(web): improve repository dropdown search (#2381)"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F950c0a7b93b2f863c062ddd5c0342cb2bb2b9eaf
source: gitnexus-releases
published_at: 2026-07-09T08:42:47+00:00
fetched_at: 2026-07-10T00:16:22.087619+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus commit 950c0a7 針對 web UI repository dropdown 元件進行了多項增強。新增的功能包括使下拉選單可滾動，以及按名稱搜尋過濾倉庫的能力。列表渲染邏輯也進行了改進，現在使用 path 作為每一列的 key。這些改動提升了大型倉庫列表的使用體驗和性能。此 commit 已納入 v1.6.10-rc.12 版本。"
key_points:
  - "Repository dropdown 新增可滾動功能，改善大型倉庫列表的可用性"
  - "新增按名稱搜尋功能，使用者可快速篩選 repository"
  - "改進列表渲染邏輯，使用 path 作為 key 提升效能與穩定性"
tags: [gitnexus, web-ui, ux-improvement, repository-management]
topics: []
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## rc/950c0a7b93b2f863c062ddd5c0342cb2bb2b9eaf: fix(web): improve repository dropdown search (#2381)

GitNexus commit 950c0a7 針對 web UI repository dropdown 元件進行了多項增強。新增的功能包括使下拉選單可滾動，以及按名稱搜尋過濾倉庫的能力。列表渲染邏輯也進行了改進，現在使用 path 作為每一列的 key。這些改動提升了大型倉庫列表的使用體驗和性能。此 commit 已納入 v1.6.10-rc.12 版本。

### 重點
- Repository dropdown 新增可滾動功能，改善大型倉庫列表的可用性
- 新增按名稱搜尋功能，使用者可快速篩選 repository
- 改進列表渲染邏輯，使用 path 作為 key 提升效能與穩定性

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F950c0a7b93b2f863c062ddd5c0342cb2bb2b9eaf)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

fix(web): make repo dropdown scrollable 
 
 
 fix(web): add repository dropdown search 
 
 
 fix(web): filter repositories by name only 
 
 
 fix(web): key repository rows by path 
 
 
 chore(web): apply prettier formatting 
 
 
 chore(web): apply ci autofix formatting 
 
 
 
 Co-authored-by: Gergő Magyar gergomagyar@icloud.com

</details>