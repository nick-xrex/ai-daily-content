---
id: inbox_40a247d0
date: 2026-06-15
source_ref: "[[00-inbox/2026-06-15/2200-simon-willison-datasette-apps-0-1a3-0f40]]"
title: "datasette-apps 0.1a3"
url: https://simonwillison.net/2026/Jun/15/datasette-apps-2/#atom-everything
source: simon-willison
published_at: 2026-06-15T20:25:07+00:00
fetched_at: 2026-06-19T22:10:15.809157+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "datasette-apps 0.1a3 發布，修復兩項重要權限問題。第一項修復（#27）：未授予 create-app 權限的用戶不再能夠建立應用。第二項修復（#29）：應用編輯/刪除權限規則已統一為——私有應用僅所有者可修改，公開應用則遵循 Datasette 常規權限系統。"
key_points:
  - "修復 #27：create-app 權限檢查補強，防止未授權用戶建立應用"
  - "修復 #29：編輯/刪除權限規則統一——私有應用限所有者，公開應用使用系統權限"
  - "權限一致性提升確保多用戶環境的安全"
tags: [datasette-apps, release, bug-fix, permissions]
topics: []
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-apps 0.1a3

datasette-apps 0.1a3 發布，修復兩項重要權限問題。第一項修復（#27）：未授予 create-app 權限的用戶不再能夠建立應用。第二項修復（#29）：應用編輯/刪除權限規則已統一為——私有應用僅所有者可修改，公開應用則遵循 Datasette 常規權限系統。

### 重點
- 修復 #27：create-app 權限檢查補強，防止未授權用戶建立應用
- 修復 #29：編輯/刪除權限規則統一——私有應用限所有者，公開應用使用系統權限
- 權限一致性提升確保多用戶環境的安全

**原文：** [simon-willison](https://simonwillison.net/2026/Jun/15/datasette-apps-2/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-apps 0.1a3 
 
 
 Fixed a bug where users without the create-app permission could still create apps. #27 
 Fixed a bug where it was impossible to grant permission to edit an app to users who were not the app's owner. The rules for edit/delete are now the same as view: if the app is private only the owner can modify it, otherwise permission is controlled by Datasette's regular permission system. #29 
 
 
 
 
 Tags: datasette

</details>