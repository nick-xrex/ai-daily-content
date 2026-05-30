---
id: inbox_0c1f1401
date: 2026-05-29
source_ref: "[[00-inbox/2026-05-29/0216-rtk-releases-dev-0-43-0-rc-247-6fa8]]"
title: "dev-0.43.0-rc.247"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.247
source: rtk-releases
published_at: 2026-05-29T11:28:57+00:00
fetched_at: 2026-05-30T02:25:00.429317+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "rtk dev-0.43.0-rc.247：修復 output 被管道時的崩潰。提高 piped output 場景的穩定性。"
key_points:
  - "Output 管道化時崩潰 → 修復異常終止問題"
tags: [rtk, stability, pipe-handling]
topics: []
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.43.0-rc.247

rtk dev-0.43.0-rc.247：修復 output 被管道時的崩潰。提高 piped output 場景的穩定性。

### 重點
- Output 管道化時崩潰 → 修復異常終止問題

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.247)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Merge pull request #1048 from ashwingopalsamy/master 

 fix: prevent crashes when output is piped

</details>