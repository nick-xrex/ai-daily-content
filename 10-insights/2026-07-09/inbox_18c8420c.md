---
id: inbox_18c8420c
date: 2026-07-09
source_ref: "[[00-inbox/.../inbox_18c8420c]]"
title: "llm 0.31.1"
url: https://simonwillison.net/2026/Jul/9/llm/#atom-everything
source: simon-willison
published_at: 2026-07-09T16:06:15+00:00
fetched_at: 2026-07-10T00:48:24.698947+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "llm 0.31.1 發布，修復 OpenAI Chat Completion endpoints 工具調用 bug (#1521)：當 tool call 帶有空白引數時，會導致某些供應商的 JSON 錯誤。該 bug 在測試 llm-meta-ai 新插件時被發現。"
key_points:
  - "修復 #1521：tool call empty arguments 導致 JSON 解析失敗"
  - "OpenAI Chat Completion 端點工具調用相容性改善"
  - "Bug 發現於 llm-meta-ai 外部整合測試流程"
tags: [llm, bug-fix, openai, tool-calling]
topics: []
importance: 2
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## llm 0.31.1

llm 0.31.1 發布，修復 OpenAI Chat Completion endpoints 工具調用 bug (#1521)：當 tool call 帶有空白引數時，會導致某些供應商的 JSON 錯誤。該 bug 在測試 llm-meta-ai 新插件時被發現。

### 重點
- 修復 #1521：tool call empty arguments 導致 JSON 解析失敗
- OpenAI Chat Completion 端點工具調用相容性改善
- Bug 發現於 llm-meta-ai 外部整合測試流程

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/9/llm/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# llm 0.31.1

Release: llm 0.31.1 
 
 
 Fix for a bug with OpenAI Chat Completion endpoints where a tool call with empty arguments could result in a JSON error from some providers. #1521 
 
 
 This bug came up when I was testing llm-meta-ai . 
 
 
 Tags: llm

</details>