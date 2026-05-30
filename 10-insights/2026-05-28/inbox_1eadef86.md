---
id: inbox_1eadef86
date: 2026-05-28
source_ref: "[[00-inbox/2026-05-28/0216-simon-willison-llm-anthropic-0-25-1-7afb]]"
title: "llm-anthropic 0.25.1"
url: https://simonwillison.net/2026/May/28/llm-anthropic/#atom-everything
source: simon-willison
published_at: 2026-05-28T23:54:56+00:00
fetched_at: 2026-05-30T02:26:17.268512+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "llm-anthropic 工具版本 0.25.1 發布。新增支援 Claude Opus 4.8 模型（claude-opus-4.8），推出 -o fast 選項用於 fast mode（需組織帳戶啟用）。變更：各模型的 max_tokens 預設值改為該模型的最大輸出限制，而非固定 8,192 tokens。"
key_points:
  - "新增模型：Claude Opus 4.8 (claude-opus-4.8)"
  - "新選項：-o fast 1 for fast mode（限有權限的組織）"
  - "預設行為調整：max_tokens 改為模型特定的最大值，而非固定 8,192"
tags: [llm-anthropic, tool-release, claude-opus-4.8]
topics: [foundation_models.claude]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## llm-anthropic 0.25.1

llm-anthropic 工具版本 0.25.1 發布。新增支援 Claude Opus 4.8 模型（claude-opus-4.8），推出 -o fast 選項用於 fast mode（需組織帳戶啟用）。變更：各模型的 max_tokens 預設值改為該模型的最大輸出限制，而非固定 8,192 tokens。

### 重點
- 新增模型：Claude Opus 4.8 (claude-opus-4.8)
- 新選項：-o fast 1 for fast mode（限有權限的組織）
- 預設行為調整：max_tokens 改為模型特定的最大值，而非固定 8,192

**原文：** [simon-willison](https://simonwillison.net/2026/May/28/llm-anthropic/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: llm-anthropic 0.25.1 
 
 
 New model: Claude Opus 4.8 ( claude-opus-4.8 ). 
 New -o fast 1 option for fast mode , for organizations with that feature enabled on their account. 
 Default max_tokens for each model now defaults to that model's maximum output rather than 8,192. #72 
 
 
 See also my notes on Opus 4.8 - I used this new release of llm-anthropic to generate the pelicans.

</details>