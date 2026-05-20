---
id: inbox_ef86a579
date: 2026-05-19
source_ref: "[[00-inbox/2026-05-19/0019-simon-willison-datasette-llm-0-1a8-eeba]]"
title: "datasette-llm 0.1a8"
url: https://simonwillison.net/2026/May/19/datasette-llm/#atom-everything
source: simon-willison
published_at: 2026-05-19T20:28:16+00:00
fetched_at: 2026-05-20T00:23:13.977611+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "datasette-llm 0.1a8 發布，修復 llm_prompt_context() hook 不完全收集響應鏈的 bug。"
key_points:
  - "修復 hook 在處理多層響應鏈時的不完全收集"
tags: [datasette, llm-cli, bug-fix]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-llm 0.1a8

datasette-llm 0.1a8 發布，修復 llm_prompt_context() hook 不完全收集響應鏈的 bug。

### 重點
- 修復 hook 在處理多層響應鏈時的不完全收集

**原文：** [simon-willison](https://simonwillison.net/2026/May/19/datasette-llm/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-llm 0.1a8 
 
 
 Fix for bug where llm_prompt_context() hook did not fully collect chains of responses. #7

</details>