---
id: inbox_1e1276fc
date: 2026-06-07
source_ref: "[[00-inbox/2026-06-07/1800-rtk-releases-dev-0-42-4-rc-268-6ae3]]"
title: "dev-0.42.4-rc.268"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.42.4-rc.268
source: rtk-releases
published_at: 2026-06-07T13:26:27+00:00
fetched_at: 2026-06-07T18:04:08.532444+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK v0.42.4-rc.268 候選版本發佈，修復了 curl 模組中的二進位檔案傳遞問題。該問題會導致二進位下載（如圖片、壓縮檔）在傳遞過程中發生 UTF-8 編碼損壞，造成檔案無法使用。此次修復實作了 binary passthrough 機制，確保二進位資料在傳遞時不進行任何文字編碼轉換。修復透過 PR #2181 合併（對應 Issue #1087）。對使用 RTK curl 進行二進位下載的用戶來說，這是關鍵的可靠性改善。"
key_points:
  - "修復 curl binary passthrough 導致的 UTF-8 corruption 問題"
  - "v0.42.4-rc.268 候選版本發佈"
  - "PR #2181 合併，對應 Issue #1087"
tags: [rtk, curl, binary-download, utf8, bug-fix]
topics: []
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.42.4-rc.268

RTK v0.42.4-rc.268 候選版本發佈，修復了 curl 模組中的二進位檔案傳遞問題。該問題會導致二進位下載（如圖片、壓縮檔）在傳遞過程中發生 UTF-8 編碼損壞，造成檔案無法使用。此次修復實作了 binary passthrough 機制，確保二進位資料在傳遞時不進行任何文字編碼轉換。修復透過 PR #2181 合併（對應 Issue #1087）。對使用 RTK curl 進行二進位下載的用戶來說，這是關鍵的可靠性改善。

### 重點
- 修復 curl binary passthrough 導致的 UTF-8 corruption 問題
- v0.42.4-rc.268 候選版本發佈
- PR #2181 合併，對應 Issue #1087

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.42.4-rc.268)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Merge pull request #2181 from rtk-ai/fix/curl-binary-passthrough-1087 

 fix(curl): passthrough binary downloads to prevent UTF-8 corruption ( #1087 )

</details>