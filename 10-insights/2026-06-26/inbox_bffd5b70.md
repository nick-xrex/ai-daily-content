---
id: inbox_bffd5b70
date: 2026-06-26
source_ref: "[[00-inbox/.../inbox_bffd5b70]]"
title: "dev-0.43.0-rc.289"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.289
source: rtk-releases
published_at: 2026-06-26T10:50:01+00:00
fetched_at: 2026-06-29T00:57:41.664123+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK dev-0.43.0-rc.289 擴展測試覆蓋範圍，新增 git stash list 和 git stash show 命令失敗時的 exit code 傳播測試。此舉進一步加強了 git 子命令的錯誤傳播機制，確保 stash 操作的失敗能被上層工具正確捕捉。"
key_points:
  - "RTK dev-0.43.0-rc.289：新增 git stash 失敗的 exit code 測試覆蓋"
  - "涵蓋 stash list 與 stash show 兩個命令"
  - "持續加強 git 操作的錯誤信號傳播"
tags: [rtk, git, testing, exit-code]
topics: []
importance: 2
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.43.0-rc.289

RTK dev-0.43.0-rc.289 擴展測試覆蓋範圍，新增 git stash list 和 git stash show 命令失敗時的 exit code 傳播測試。此舉進一步加強了 git 子命令的錯誤傳播機制，確保 stash 操作的失敗能被上層工具正確捕捉。

### 重點
- RTK dev-0.43.0-rc.289：新增 git stash 失敗的 exit code 測試覆蓋
- 涵蓋 stash list 與 stash show 兩個命令
- 持續加強 git 操作的錯誤信號傳播

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.289)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# dev-0.43.0-rc.289

Merge pull request #2500 from hgunduzoglu/fix/git-stash-list-show-exi... 

 ...t-code 

 test(git): cover exit-code propagation for git stash list/show failure

</details>