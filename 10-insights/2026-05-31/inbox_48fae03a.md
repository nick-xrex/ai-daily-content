---
id: inbox_48fae03a
date: 2026-05-31
source_ref: "[[00-inbox/2026-05-31/1801-rtk-releases-dev-0-43-0-rc-251-4783]]"
title: "dev-0.43.0-rc.251"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.251
source: rtk-releases
published_at: 2026-05-31T14:37:52+00:00
fetched_at: 2026-05-31T18:08:30.438397+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK dev-0.43.0-rc.251 修複 Claude Code 專案路徑編碼，在 provider 層 sanitize 更多字符。此修復確保特殊字符的專案路徑能正確編碼，避免初始化或查詢失敗。"
key_points:
  - "project path 編碼時 sanitize 更多字符，避免邊界情況導致編碼故障"
tags: [path-encoding, sanitization, claude-code]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.43.0-rc.251

RTK dev-0.43.0-rc.251 修複 Claude Code 專案路徑編碼，在 provider 層 sanitize 更多字符。此修復確保特殊字符的專案路徑能正確編碼，避免初始化或查詢失敗。

### 重點
- project path 編碼時 sanitize 更多字符，避免邊界情況導致編碼故障

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.251)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Merge pull request #2172 from KuSh/2150-encode_project_path 

 fix(provider): sanatize more chars when encoding claude code project pathes

</details>