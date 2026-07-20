---
id: inbox_fab115f0
date: 2026-07-19
source_ref: "[[00-inbox/.../inbox_fab115f0]]"
title: "v2.1.215"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.215
source: claude-code-releases
published_at: 2026-07-19T02:56:01+00:00
fetched_at: 2026-07-20T00:53:12.113253+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.215 發布改變代理自動執行行為。舊版本中 Claude 會自動執行 /verify 和 /code-review 指令，新版本改為等待使用者明確呼叫。此改變讓使用者能夠更細粒度地控制驗證和程式碼審查流程的觸發時機，避免不必要的自動工作。"
key_points:
  - "v2.1.215：/verify 和 /code-review 指令改為按需調用而非自動執行"
tags: [claude-code, product-update, behavior-change]
topics: [foundation_models.claude]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.215

Claude Code v2.1.215 發布改變代理自動執行行為。舊版本中 Claude 會自動執行 /verify 和 /code-review 指令，新版本改為等待使用者明確呼叫。此改變讓使用者能夠更細粒度地控制驗證和程式碼審查流程的觸發時機，避免不必要的自動工作。

### 重點
- v2.1.215：/verify 和 /code-review 指令改為按需調用而非自動執行

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.215)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v2.1.215

What's changed 
 
 Claude no longer runs the /verify and /code-review skills on its own; invoke them with /verify or /code-review when you want them

</details>