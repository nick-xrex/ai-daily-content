---
id: inbox_5138ac95
date: 2026-06-05
source_ref: "[[00-inbox/2026-06-05/1800-rtk-releases-dev-0-42-4-rc-267-9059]]"
title: "dev-0.42.4-rc.267"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.42.4-rc.267
source: rtk-releases
published_at: 2026-06-05T16:38:06+00:00
fetched_at: 2026-06-05T18:06:27.766171+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK dev-0.42.4-rc.267 發布重構，移除命令輸出中的裝飾符雜訊。此項改進使命令輸出更清潔、更易於解析，特別適合自動化工具與下游消費者處理。"
key_points:
  - "移除命令過濾輸出中的裝飾符"
tags: [rtk, refactoring, output]
topics: []
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.42.4-rc.267

RTK dev-0.42.4-rc.267 發布重構，移除命令輸出中的裝飾符雜訊。此項改進使命令輸出更清潔、更易於解析，特別適合自動化工具與下游消費者處理。

### 重點
- 移除命令過濾輸出中的裝飾符

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.42.4-rc.267)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Merge pull request #2289 from rtk-ai/refacto/strip-output-decorators 

 refacto(cmds): strip decorator noise from filter output

</details>