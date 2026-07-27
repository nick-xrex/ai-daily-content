---
id: inbox_b18e5754
date: 2026-07-24
source_ref: "[[00-inbox/2026-07-24/0123-rtk-releases-dev-0-44-0-rc-329-eafd]]"
title: "dev-0.44.0-rc.329"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.44.0-rc.329
source: rtk-releases
published_at: 2026-07-24T09:55:16+00:00
fetched_at: 2026-07-27T01:32:33.014694+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK dev-0.44.0-rc.329 修復了 `uv run` 命令的標準輸出處理。修復確保被執行程序的標準輸出被正確保留，同時恢復內部命令篩選邏輯。使用者執行的外部程序輸出不再被遺失或誤過濾。"
key_points:
  - "修復 uv run 保留程序標準輸出，避免輸出被吞沒"
  - "恢復內部命令過濾機制，確保正確的命令路由"
  - "確保外部程序執行時的輸出完整性和可見性"
tags: [rtk, uv, stdout, io-handling]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.44.0-rc.329

RTK dev-0.44.0-rc.329 修復了 `uv run` 命令的標準輸出處理。修復確保被執行程序的標準輸出被正確保留，同時恢復內部命令篩選邏輯。使用者執行的外部程序輸出不再被遺失或誤過濾。

### 重點
- 修復 uv run 保留程序標準輸出，避免輸出被吞沒
- 恢復內部命令過濾機制，確保正確的命令路由
- 確保外部程序執行時的輸出完整性和可見性

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.44.0-rc.329)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Merge pull request #3061 from rtk-ai/fix/uv-run-preserve-stdout 

 fix(uv): preserve program stdout and restore inner-command filtering

</details>