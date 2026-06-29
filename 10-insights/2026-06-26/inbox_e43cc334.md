---
id: inbox_e43cc334
date: 2026-06-26
source_ref: "[[00-inbox/.../inbox_e43cc334]]"
title: "dev-0.43.0-rc.288"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.288
source: rtk-releases
published_at: 2026-06-26T09:55:52+00:00
fetched_at: 2026-06-29T00:57:41.665567+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK dev-0.43.0-rc.288 修復了 git status 命令在 compact mode 路徑中失敗時的 exit code 傳播問題。該修復進一步完善了 RTK git 功能的錯誤處理邏輯，使得 git status 的失敗狀態能被明確傳達給呼叫者。"
key_points:
  - "RTK dev-0.43.0-rc.288：修復 git status compact path 中的 exit code 傳播"
  - "針對性解決 compact 模式的錯誤報告缺陷"
  - "確保 git status 失敗被正確信號化"
tags: [rtk, git, bugfix, exit-code]
topics: []
importance: 2
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.43.0-rc.288

RTK dev-0.43.0-rc.288 修復了 git status 命令在 compact mode 路徑中失敗時的 exit code 傳播問題。該修復進一步完善了 RTK git 功能的錯誤處理邏輯，使得 git status 的失敗狀態能被明確傳達給呼叫者。

### 重點
- RTK dev-0.43.0-rc.288：修復 git status compact path 中的 exit code 傳播
- 針對性解決 compact 模式的錯誤報告缺陷
- 確保 git status 失敗被正確信號化

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.288)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# dev-0.43.0-rc.288

Merge pull request #2498 from hgunduzoglu/fix/git-status-compact-exit... 

 ...-code 

 fix(git): propagate exit code on git status failure in compact path

</details>