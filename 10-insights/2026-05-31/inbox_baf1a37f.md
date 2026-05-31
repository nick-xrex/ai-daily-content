---
id: inbox_baf1a37f
date: 2026-05-31
source_ref: "[[00-inbox/2026-05-31/1801-rtk-releases-dev-0-43-0-rc-254-57f4]]"
title: "dev-0.43.0-rc.254"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.254
source: rtk-releases
published_at: 2026-05-31T15:40:58+00:00
fetched_at: 2026-05-31T18:08:30.432759+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK dev-0.43.0-rc.254 修複 `filter_markdown_body()` 無聲失敗問題。原先當 PR/issue body 僅含徽章、圖片、HTML 註解時，view 會直接略過 body 區段，用户無法察覺內容曾存在但被濾除。修復後，body 被濾空時顯示 fallback note「(body contained only badges/images/comments)」。PR view 和 Issue view 都適用，新增 4 個回歸測試（含 PR 徽章、Issue 純註解、raw empty 等邊界）以確保正確行為。"
key_points:
  - "過濾後 body 為空但原始 body 非空時，顯示 fallback note；避免用户困惑內容遺失"
  - "PR view 和 Issue view 都有此改進，涵蓋徽章、圖片、HTML 註解三種情況"
  - "新增 4 個回歸測試確保沒有誤判（real content 時不顯示 fallback、raw empty 時也不顯示）"
tags: [ux-improvement, markdown-filter, gh-integration]
topics: []
importance: 1
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.43.0-rc.254

RTK dev-0.43.0-rc.254 修複 `filter_markdown_body()` 無聲失敗問題。原先當 PR/issue body 僅含徽章、圖片、HTML 註解時，view 會直接略過 body 區段，用户無法察覺內容曾存在但被濾除。修復後，body 被濾空時顯示 fallback note「(body contained only badges/images/comments)」。PR view 和 Issue view 都適用，新增 4 個回歸測試（含 PR 徽章、Issue 純註解、raw empty 等邊界）以確保正確行為。

### 重點
- 過濾後 body 為空但原始 body 非空時，顯示 fallback note；避免用户困惑內容遺失
- PR view 和 Issue view 都有此改進，涵蓋徽章、圖片、HTML 註解三種情況
- 新增 4 個回歸測試確保沒有誤判（real content 時不顯示 fallback、raw empty 時也不顯示）

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.254)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

fix(gh): show fallback note when PR/issue body is filtered to empty 

 When `filter_markdown_body()` strips a PR or issue body to empty
 (body contained only badges, images, HTML comments, or horizontal
 rules), `format_pr_view` and `format_issue_view` previously skipped
 the body section silently. Users had no indication that body content
 had been present and filtered. 

 Now both views emit a fallback note when the filtered body is empty
 but the raw body was not: 

 PR view: (body contained only badges/images/comments)
 Issue view: Description: (body contained only badges/images/comments) 

 The 4 added tests cover:
 - PR body with only badges/images/comments -&gt; fallback note appears
 - PR body with real content -&gt; no fallback note (sanity)
 - PR body empty (raw) -&gt; no fallback note (no signal to give)
 - Issue body badges-only -&gt; fallback note appears 

 Closes #235 

 Co-authored-by: polaminggkub-debug &lt;polaminggkub-debug@users.noreply.github.com&gt;

</details>