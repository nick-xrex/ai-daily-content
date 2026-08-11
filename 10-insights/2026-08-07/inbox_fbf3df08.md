---
id: inbox_fbf3df08
date: 2026-08-07
source_ref: "[[00-inbox/.../inbox_fbf3df08]]"
title: "v0.45.0"
url: https://github.com/rtk-ai/rtk/releases/tag/v0.45.0
source: rtk-releases
published_at: 2026-08-07T09:48:20+00:00
fetched_at: 2026-08-11T01:19:12.683320+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK v0.45.0 於 2026-08-07 發布。新功能包括針對 Mistral Vibe CLI 的透明 hook 支援及多行區塊重寫能力。Bug 修復聚焦於 hook 配置的自癒機制：修復 RTK 自身舊版 camelCase entry（同時保留用戶配置）、修復 Copilot hook 配置的雙模式 schema 過時問題，以及阻止 Copilot 在命令未配置時默許決定權限。這些改進提升了 hook 系統的穩定性與用戶配置的完整性。"
key_points:
  - "Mistral Vibe CLI 透明 hook 支援；多行區塊重寫功能（d480f1e、3044911）"
  - "Hook 自癒機制：舊版 camelCase entry 修復同時保留用戶配置（db31da9）；Copilot 雙模式 schema 過時修復（d1f7139）"
  - "權限管理改進：阻止 Copilot 未配置命令時默許決定權限（#8722378）"
tags: [rtk, hook-system, copilot-integration]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v0.45.0

RTK v0.45.0 於 2026-08-07 發布。新功能包括針對 Mistral Vibe CLI 的透明 hook 支援及多行區塊重寫能力。Bug 修復聚焦於 hook 配置的自癒機制：修復 RTK 自身舊版 camelCase entry（同時保留用戶配置）、修復 Copilot hook 配置的雙模式 schema 過時問題，以及阻止 Copilot 在命令未配置時默許決定權限。這些改進提升了 hook 系統的穩定性與用戶配置的完整性。

### 重點
- Mistral Vibe CLI 透明 hook 支援；多行區塊重寫功能（d480f1e、3044911）
- Hook 自癒機制：舊版 camelCase entry 修復同時保留用戶配置（db31da9）；Copilot 雙模式 schema 過時修復（d1f7139）
- 權限管理改進：阻止 Copilot 未配置命令時默許決定權限（#8722378）

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/v0.45.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v0.45.0

0.45.0 (2026-08-07) 
 Features 
 
 hooks: add transparent hook support for Mistral Vibe CLI ( d480f1e ) 
 rewrite: rewrite multiline blocks ( 3044911 ) 
 
 Bug Fixes 
 
 hooks: heal only rtk's own legacy camelCase entry, keep user config ( db31da9 ) 
 hooks: self-heal stale dual-schema Copilot hook config ( d1f7139 ) 
 hooks: stop Copilot from silently deciding permission on unconfigured commands ( 8722378 )

</details>