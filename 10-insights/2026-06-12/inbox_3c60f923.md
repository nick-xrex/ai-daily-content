---
id: inbox_3c60f923
date: 2026-06-12
source_ref: "[[00-inbox/2026-06-12/0336-claude-code-releases-v2-1-175-ef3a]]"
title: "v2.1.175"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.175
source: claude-code-releases
published_at: 2026-06-12T04:23:51+00:00
fetched_at: 2026-06-13T03:40:37.896485+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.175 發佈，新增 enforceAvailableModels 受管設定。啟用時，availableModels 白名單也會限制 Default 模型選擇：如果 Default 解析到被禁止的模型，系統自動回退到第一個允許的模型；用戶或專案設定無法擴寬受管的 availableModels 清單。此設定強化了企業對模型訪問的集中管理能力。"
key_points:
  - "enforceAvailableModels 受管設定：使 availableModels 白名單約束 Default 模型，禁止用戶或專案設定繞過企業限制"
tags: [claude-code-release, model-governance, enterprise-settings, access-control]
topics: []
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.175

Claude Code v2.1.175 發佈，新增 enforceAvailableModels 受管設定。啟用時，availableModels 白名單也會限制 Default 模型選擇：如果 Default 解析到被禁止的模型，系統自動回退到第一個允許的模型；用戶或專案設定無法擴寬受管的 availableModels 清單。此設定強化了企業對模型訪問的集中管理能力。

### 重點
- enforceAvailableModels 受管設定：使 availableModels 白名單約束 Default 模型，禁止用戶或專案設定繞過企業限制

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.175)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added enforceAvailableModels managed setting — when enabled, the availableModels allowlist also constrains the Default model (a Default that would resolve to a disallowed model now falls back to the first allowed model), and user or project settings can no longer widen a managed availableModels list

</details>