---
id: inbox_5c0454e6
date: 2026-07-07
source_ref: "[[00-inbox/.../inbox_5c0454e6]]"
title: "Node.js 26: Temporal API Enabled by Default, V8 14.6, and a Round of Deprecations"
url: https://www.infoq.com/news/2026/07/nodejs-26-temporal/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-07-07T06:51:00+00:00
fetched_at: 2026-07-08T01:06:17.435732+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Node.js 26 正式發布，主要更新包括：Temporal API 默認啟用（解決 JavaScript 日期時間處理的多年痛點）、V8 引擎升級至 14.6、Undici HTTP 客戶端升級至 8.0。該版本移除了多個棄用的舊 API，NODE_MODULE_VERSION 發生變更，開發者需要檢視依賴包的兼容性。Node.js 26 作為當前版本（Current），將維持 6 個月後進入長期支持（LTS）。"
key_points:
  - "Temporal API 默認啟用是 JavaScript 日期時間 API 的重大升級，改進了原生 Date 對象的局限"
  - "V8 14.6 和 Undici 8.0 帶來性能和 HTTP 協議支持的持續優化"
  - "NODE_MODULE_VERSION 變更要求檢視並可能重新編譯原生模塊依賴"
tags: [nodejs-26, temporal-api, v8-14.6, undici-8.0]
topics: []
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Node.js 26: Temporal API Enabled by Default, V8 14.6, and a Round of Deprecations

Node.js 26 正式發布，主要更新包括：Temporal API 默認啟用（解決 JavaScript 日期時間處理的多年痛點）、V8 引擎升級至 14.6、Undici HTTP 客戶端升級至 8.0。該版本移除了多個棄用的舊 API，NODE_MODULE_VERSION 發生變更，開發者需要檢視依賴包的兼容性。Node.js 26 作為當前版本（Current），將維持 6 個月後進入長期支持（LTS）。

### 重點
- Temporal API 默認啟用是 JavaScript 日期時間 API 的重大升級，改進了原生 Date 對象的局限
- V8 14.6 和 Undici 8.0 帶來性能和 HTTP 協議支持的持續優化
- NODE_MODULE_VERSION 變更要求檢視並可能重新編譯原生模塊依賴

**原文：** [infoq-main](https://www.infoq.com/news/2026/07/nodejs-26-temporal/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Node.js 26: Temporal API Enabled by Default, V8 14.6, and a Round of Deprecations

Node.js 26 has been released, featuring the Temporal API enabled by default, an updated V8 engine to version 14.6, and the Undici HTTP client upgraded to 8.0. The release also removes deprecated legacy APIs. Developers should note migration points related to NODE_MODULE_VERSION changes. Node.js 26 is current for six months before entering long-term support. By Daniel Curtis

</details>