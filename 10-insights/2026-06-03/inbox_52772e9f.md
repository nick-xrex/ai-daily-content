---
id: inbox_52772e9f
date: 2026-06-03
source_ref: "[[00-inbox/.../inbox_52772e9f]]"
title: "dev-0.43.0-rc.259"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.259
source: rtk-releases
published_at: 2026-06-03T14:02:04+00:00
fetched_at: 2026-06-04T00:52:41.735890+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK v0.43.0-rc.259 候選版本發布，修復 grep 命令在文件名或位置參數值相同時發生的命令令牌重複問題。此修復確保搜尋結果輸出格式正確。"
key_points:
  - "RTK v0.43.0-rc.259 修復 grep 令牌重複 bug"
  - "當文件名與位置參數值相同時觸發該問題"
  - "PR #2239: fix(grep) command token duplication in output"
tags: [rtk, bug-fix, grep, release-candidate]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.43.0-rc.259

RTK v0.43.0-rc.259 候選版本發布，修復 grep 命令在文件名或位置參數值相同時發生的命令令牌重複問題。此修復確保搜尋結果輸出格式正確。

### 重點
- RTK v0.43.0-rc.259 修復 grep 令牌重複 bug
- 當文件名與位置參數值相同時觸發該問題
- PR #2239: fix(grep) command token duplication in output

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.259)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# dev-0.43.0-rc.259

Merge pull request #2239 from KuSh/1669-restore_double_dash-fix 

 fix(grep): command token duplication in output withsame value filename or positional arg

</details>