---
id: inbox_c1db6be7
date: 2026-07-03
source_ref: "[[00-inbox/2026-07-03/0115-rtk-releases-dev-0-44-0-rc-307-0ee4]]"
title: "dev-0.44.0-rc.307"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.44.0-rc.307
source: rtk-releases
published_at: 2026-07-03T13:29:02+00:00
fetched_at: 2026-07-04T01:22:28.303217+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK dev-0.44.0-rc.307 修復 git stash show 命令行為，改用緊湊顯示模式而非強制使用 -p 標記，提升命令執行靈活性與輸出可讀性。"
key_points:
  - "git stash show 移除強制 -p 標記限制，轉為緊湊顯示模式"
tags: [git, bugfix]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.44.0-rc.307

RTK dev-0.44.0-rc.307 修復 git stash show 命令行為，改用緊湊顯示模式而非強制使用 -p 標記，提升命令執行靈活性與輸出可讀性。

### 重點
- git stash show 移除強制 -p 標記限制，轉為緊湊顯示模式

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.44.0-rc.307)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Merge pull request #2801 from rtk-ai/fix/git-stash-show-diffstat 

 fix(git): compact git stash show instead of forcing -p

</details>