---
id: inbox_fb875434
date: 2026-06-26
source_ref: "[[00-inbox/.../inbox_fb875434]]"
title: "dev-0.43.0-rc.290"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.290
source: rtk-releases
published_at: 2026-06-26T11:30:59+00:00
fetched_at: 2026-06-29T00:57:41.658282+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK dev-0.43.0-rc.290 版本修復了 git commit 命令在失敗時未正確傳播 exit code 的問題，改善了錯誤處理的準確性。此修復確保當 git commit 操作失敗時，外部程式能正確偵測到失敗狀態，而不是誤報成功。這對依賴精確錯誤碼來判斷 git 操作成敗的工具和指令碼至關重要。"
key_points:
  - "RTK dev-0.43.0-rc.290：修復 git commit 失敗時的 exit code 傳播"
  - "確保錯誤狀態被正確回報而非誤報成功"
  - "影響範圍：使用 RTK git 整合的自動化工作流"
tags: [rtk, git, bugfix, exit-code]
topics: []
importance: 2
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.43.0-rc.290

RTK dev-0.43.0-rc.290 版本修復了 git commit 命令在失敗時未正確傳播 exit code 的問題，改善了錯誤處理的準確性。此修復確保當 git commit 操作失敗時，外部程式能正確偵測到失敗狀態，而不是誤報成功。這對依賴精確錯誤碼來判斷 git 操作成敗的工具和指令碼至關重要。

### 重點
- RTK dev-0.43.0-rc.290：修復 git commit 失敗時的 exit code 傳播
- 確保錯誤狀態被正確回報而非誤報成功
- 影響範圍：使用 RTK git 整合的自動化工作流

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.290)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# dev-0.43.0-rc.290

Merge pull request #2496 from hgunduzoglu/fix/git-commit-false-success 

 fix(git): propagate exit code when commit fails instead of reporting ok

</details>