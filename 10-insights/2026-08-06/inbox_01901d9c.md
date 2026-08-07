---
id: inbox_01901d9c
date: 2026-08-06
source_ref: "[[00-inbox/.../inbox_01901d9c]]"
title: "dev-0.45.0-rc.351"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.45.0-rc.351
source: rtk-releases
published_at: 2026-08-06T15:36:05+00:00
fetched_at: 2026-08-07T01:24:19.566047+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK 開發版本 0.45.0-rc.351 新增對 Mistral Vibe CLI 的透明 pre_tool 重寫支援。該功能透過新的 hooks 機制實現，允許在使用 Mistral Vibe CLI 環境中進行工具調用的自動轉換，解決生態系統相容性需求。"
key_points:
  - "RTK 0.45.0-rc.351 新增透明 pre_tool 重寫 hooks，實現 Mistral Vibe CLI 的無縫相容（#3391）"
tags: [mistral-vibe, hooks, tool-rewrite]
topics: []
importance: 3
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.45.0-rc.351

RTK 開發版本 0.45.0-rc.351 新增對 Mistral Vibe CLI 的透明 pre_tool 重寫支援。該功能透過新的 hooks 機制實現，允許在使用 Mistral Vibe CLI 環境中進行工具調用的自動轉換，解決生態系統相容性需求。

### 重點
- RTK 0.45.0-rc.351 新增透明 pre_tool 重寫 hooks，實現 Mistral Vibe CLI 的無縫相容（#3391）

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.45.0-rc.351)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# dev-0.45.0-rc.351

Merge pull request #3391 from xavierpestel-ai/feat/vibe-hook-support 

 feat(hooks): transparent pre_tool rewrite for Mistral Vibe CLI ( closes #800 )

</details>