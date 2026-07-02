---
id: inbox_3ae7d80c
date: 2026-07-01
source_ref: "[[00-inbox/2026-07-01/2224-codex-releases-0-142-5-27b9]]"
title: "0.142.5"
url: https://github.com/openai/codex/releases/tag/rust-v0.142.5
source: codex-releases
published_at: 2026-07-01T01:17:02+00:00
fetched_at: 2026-07-02T00:15:15.457911+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI Codex v0.142.5（Rust 版本）發布，修復了一個日誌安全問題。該版本防止完整的 Responses WebSocket 請求負載被寫入追踪日誌，避免敏感資料外洩。這是一個小幅度的維護版本更新。"
key_points:
  - "防止 WebSocket 請求完整負載被寫入追踪日誌，提升敏感資料保護"
tags: [codex, websocket, logging, security, rust]
topics: [foundation_models.gpt]
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## 0.142.5

OpenAI Codex v0.142.5（Rust 版本）發布，修復了一個日誌安全問題。該版本防止完整的 Responses WebSocket 請求負載被寫入追踪日誌，避免敏感資料外洩。這是一個小幅度的維護版本更新。

### 重點
- 防止 WebSocket 請求完整負載被寫入追踪日誌，提升敏感資料保護

**原文：** [codex-releases](https://github.com/openai/codex/releases/tag/rust-v0.142.5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Bug Fixes 
 
 Prevented full Responses WebSocket request payloads from being written to trace logs. ( #30771 ) 
 
 Changelog 
 Full Changelog: rust-v0.142.4...rust-v0.142.5 
 
 #30771 [codex] Backport websocket trace fix to release/0.142 @dylan-hurd-oai

</details>