---
id: inbox_9a0624fa
date: 2026-07-28
source_ref: "[[00-inbox/.../inbox_9a0624fa]]"
title: "Stop Blaming the Model: TTFT Is an Architecture Budget"
url: https://medium.com/@kedemtomerpt/stop-blaming-the-model-ttft-is-an-architecture-budget-80726b98371e?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-07-28T12:31:02+00:00
fetched_at: 2026-07-29T03:45:07.726663+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "文章論證 TTFT（首個 token 延遲）不應單純歸咎於模型，而是整個架構設計的權衡預算。核心觀點：「首個 token 出現前的每一個同步決策都在消耗使用者無法回收的時間」。暗示 TTFT 最佳化需從系統架構層面重新審視系統設計選擇（如快取策略、序列化開銷、I/O 排程），而非只聚焦模型推理速度。完整分析框架無法確認。"
key_points:
  - "TTFT 是架構層級的系統預算問題，不是模型能力的直接函數"
  - "首個 token 前的同步決策（包括編排、驗證、轉碼）直接增加使用者感知延遲，成本無法補償"
  - "系統設計者需從『預算』角度重新評估 TTFT，權衡功能完整性與響應速度"
tags: [ttft, llm-latency, system-architecture, optimization]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Stop Blaming the Model: TTFT Is an Architecture Budget

文章論證 TTFT（首個 token 延遲）不應單純歸咎於模型，而是整個架構設計的權衡預算。核心觀點：「首個 token 出現前的每一個同步決策都在消耗使用者無法回收的時間」。暗示 TTFT 最佳化需從系統架構層面重新審視系統設計選擇（如快取策略、序列化開銷、I/O 排程），而非只聚焦模型推理速度。完整分析框架無法確認。

### 重點
- TTFT 是架構層級的系統預算問題，不是模型能力的直接函數
- 首個 token 前的同步決策（包括編排、驗證、轉碼）直接增加使用者感知延遲，成本無法補償
- 系統設計者需從『預算』角度重新評估 TTFT，權衡功能完整性與響應速度

**原文：** [medium-tag-llm](https://medium.com/@kedemtomerpt/stop-blaming-the-model-ttft-is-an-architecture-budget-80726b98371e?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

---large_language_models-5"
author: "Tomer Kedem"
published_at: 2026-07-28T12:31:02+00:00
fetched_at: 2026-07-28T22:53:09.669679+00:00
content_hash: "84957c7a325b856fc67a047d38b3635a4d7113a033762141b91fcf7b30122317"
lang: en
caption_quality: None
raw: true
topics: []
---

# Stop Blaming the Model: TTFT Is an Architecture Budget

Every synchronous decision before the first token spends time your user cannot get back Continue reading on Medium »

</details>