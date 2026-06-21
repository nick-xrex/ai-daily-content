---
id: inbox_214d8fb5
date: 2026-06-20
source_ref: "[[00-inbox/.../inbox_214d8fb5]]"
title: "dev-0.43.0-rc.283"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.283
source: rtk-releases
published_at: 2026-06-20T15:24:28+00:00
fetched_at: 2026-06-21T02:29:07.636893+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK dev-0.43.0-rc.283：Vitest reporter 修復。Vitest 是現代的 JavaScript/TypeScript 測試框架，支援多種 reporter 以自訂測試結果輸出格式（如 JSON、HTML、TAP 等）。此 RC 版本修正 Vitest 外掛的關鍵 bug：明確指定的 reporters 配置在某些情況下被遺漏，導致使用者的測試結果無法按預期輸出。此修復通過 reporter passthrough 機制確保使用者配置被正確保留，提高測試工作流的可靠性。"
key_points:
  - "Vitest reporter passthrough 修復，保留明確指定的 reporters"
  - "確保自訂測試結果輸出格式配置被正確傳遞"
tags: [rtk, vitest, testing, bugfix]
topics: []
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.43.0-rc.283

RTK dev-0.43.0-rc.283：Vitest reporter 修復。Vitest 是現代的 JavaScript/TypeScript 測試框架，支援多種 reporter 以自訂測試結果輸出格式（如 JSON、HTML、TAP 等）。此 RC 版本修正 Vitest 外掛的關鍵 bug：明確指定的 reporters 配置在某些情況下被遺漏，導致使用者的測試結果無法按預期輸出。此修復通過 reporter passthrough 機制確保使用者配置被正確保留，提高測試工作流的可靠性。

### 重點
- Vitest reporter passthrough 修復，保留明確指定的 reporters
- 確保自訂測試結果輸出格式配置被正確傳遞

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.283)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# dev-0.43.0-rc.283

Merge pull request #2294 from jsiu93/fix/vitest-reporter-passthrough 

 fix(vitest): preserve explicit reporters

</details>