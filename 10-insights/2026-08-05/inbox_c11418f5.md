---
id: inbox_c11418f5
date: 2026-08-05
source_ref: "[[00-inbox/.../inbox_c11418f5]]"
title: "I Shipped Prompt Caching to a WhatsApp Handler and Cached Nothing for a Week"
url: https://medium.com/@hayrikar54/i-shipped-prompt-caching-to-a-whatsapp-handler-and-cached-nothing-for-a-week-380351ad4eb8?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-08-05T19:33:07+00:00
fetched_at: 2026-08-06T00:30:09.899012+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者 Hayrullah Kar 在 WhatsApp handler 中部署了 Claude API 的 prompt caching 功能，卻發現一周內完全沒有命中緩存。Claude 接受了所有 cache_control 指令並收取寫入溢價，但查詢時未返回任何緩存內容。系統無聲失敗，沒有錯誤提示，導致難以偵測。這揭示 Claude prompt caching 在特定應用架構（如消息處理 handler）下的隱性限制，用戶將為無效的緩存成本買單。"
key_points:
  - "Claude prompt caching 在 WhatsApp handler 架構中失效：接受緩存指令但未返回緩存結果，完全無聲失敗"
  - "成本陷阱：系統收取寫入溢價但不提供緩存收益，無錯誤信號警示用戶"
  - "隱含架構限制：緩存可能需要特定的會話/連接持久性，短生命週期的消息 handler 違反此要求"
tags: [claude-api, prompt-caching, whatsapp-integration, production-gotcha]
topics: [foundation_models.claude]
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: true
deep_dive_approved: false
---

## I Shipped Prompt Caching to a WhatsApp Handler and Cached Nothing for a Week

作者 Hayrullah Kar 在 WhatsApp handler 中部署了 Claude API 的 prompt caching 功能，卻發現一周內完全沒有命中緩存。Claude 接受了所有 cache_control 指令並收取寫入溢價，但查詢時未返回任何緩存內容。系統無聲失敗，沒有錯誤提示，導致難以偵測。這揭示 Claude prompt caching 在特定應用架構（如消息處理 handler）下的隱性限制，用戶將為無效的緩存成本買單。

### 重點
- Claude prompt caching 在 WhatsApp handler 架構中失效：接受緩存指令但未返回緩存結果，完全無聲失敗
- 成本陷阱：系統收取寫入溢價但不提供緩存收益，無錯誤信號警示用戶
- 隱含架構限制：緩存可能需要特定的會話/連接持久性，短生命週期的消息 handler 違反此要求

**原文：** [medium-tag-claude](https://medium.com/@hayrikar54/i-shipped-prompt-caching-to-a-whatsapp-handler-and-cached-nothing-for-a-week-380351ad4eb8?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

---claude-5"
author: "Hayrullah Kar"
published_at: 2026-08-05T19:33:07+00:00
fetched_at: 2026-08-05T22:33:14.361890+00:00
content_hash: "a4b862d9f72cde615e4898c62c49eaae672cdf7fb0e706c5563e6685c6c85d4c"
lang: en
caption_quality: None
raw: true
topics: []
---

# I Shipped Prompt Caching to a WhatsApp Handler and Cached Nothing for a Week

Claude accepted every cache_control block, charged me the write premium, and read nothing back. There was no error to find. Continue reading on Medium »

</details>