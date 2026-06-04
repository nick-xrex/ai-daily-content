---
id: inbox_531493bc
date: 2026-06-03
source_ref: "[[00-inbox/.../inbox_531493bc]]"
title: "dev-0.43.0-rc.260"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.260
source: rtk-releases
published_at: 2026-06-03T15:27:23+00:00
fetched_at: 2026-06-04T00:52:41.734629+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK v0.43.0-rc.260 候選版本發布，修復 git 模組在處理多位元字符時的 panic 崩潰。此修復確保提交訊息包含非 ASCII 字符（如中文、日文、表情符號等）時系統穩定運行。"
key_points:
  - "RTK v0.43.0-rc.260 修復 git commit 多位元字符 panic"
  - "支援提交訊息中的多語言和特殊字符"
  - "PR #1266: fix panic on multibyte chars in commit output"
tags: [rtk, bug-fix, git, release-candidate]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.43.0-rc.260

RTK v0.43.0-rc.260 候選版本發布，修復 git 模組在處理多位元字符時的 panic 崩潰。此修復確保提交訊息包含非 ASCII 字符（如中文、日文、表情符號等）時系統穩定運行。

### 重點
- RTK v0.43.0-rc.260 修復 git commit 多位元字符 panic
- 支援提交訊息中的多語言和特殊字符
- PR #1266: fix panic on multibyte chars in commit output

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.260)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# dev-0.43.0-rc.260

Merge pull request #1266 from shalk/fix/commit-multibyte-panic-rebased 

 fix(git): fix panic on multibyte chars in commit output

</details>