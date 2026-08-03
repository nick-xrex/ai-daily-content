---
id: inbox_7af95836
date: 2026-08-02
source_ref: "[[00-inbox/.../inbox_7af95836]]"
title: "v13.13.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.13.0
source: claude-mem-releases
published_at: 2026-08-02T17:15:08+00:00
fetched_at: 2026-08-03T00:24:16.713780+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v13.13.0 發布，引入第九種觀察類型「sensitive」用於標記內部資訊洩露風險（內部 URL、未發布計畫、個人細節、商業指標、客戶名稱等）。新類型預設觸發 Telegram 通知，通過環境變數 CLAUDE_MEM_TELEGRAM_TRIGGER_TYPES 設定。本版本同時修正四月以來觀察器提示語中的過時描述，該描述導致 security_alert 和 security_note 被低頻率發出；舊預設安裝自動遷移至「security_alert,sensitive」，客製化設定保持不變，展現向後相容性設計。"
key_points:
  - "claude-mem v13.13.0：新增第九種觀察類型「sensitive」，區分內部敏感資訊洩露風險"
  - "修正四月起的觀察器提示語 bug，導致 security_alert/security_note 低頻率發出"
  - "自動遷移策略：舊預設升級為「security_alert,sensitive」；客製化設定保持不變"
tags: [claude-mem, observation-types, sensitivity-tiering, notifications, information-governance]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.13.0

claude-mem v13.13.0 發布，引入第九種觀察類型「sensitive」用於標記內部資訊洩露風險（內部 URL、未發布計畫、個人細節、商業指標、客戶名稱等）。新類型預設觸發 Telegram 通知，通過環境變數 CLAUDE_MEM_TELEGRAM_TRIGGER_TYPES 設定。本版本同時修正四月以來觀察器提示語中的過時描述，該描述導致 security_alert 和 security_note 被低頻率發出；舊預設安裝自動遷移至「security_alert,sensitive」，客製化設定保持不變，展現向後相容性設計。

### 重點
- claude-mem v13.13.0：新增第九種觀察類型「sensitive」，區分內部敏感資訊洩露風險
- 修正四月起的觀察器提示語 bug，導致 security_alert/security_note 低頻率發出
- 自動遷移策略：舊預設升級為「security_alert,sensitive」；客製化設定保持不變

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.13.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v13.13.0

Sensitive observation type 
 Adds a ninth observation type to the code mode: sensitive — information that isn't quite private, but that you wouldn't want leaking into further content development in the wrong context. Internal URLs, unreleased plans, personal details, business metrics, client or partner names. 
 These fire a Telegram notification by default, the same way security_alert does. 
 Configuring 
 Notifications are controlled by CLAUDE_MEM_TELEGRAM_TRIGGER_TYPES in ~/.claude-mem/settings.json . The default is now security_alert,sensitive . Set the key to any comma-separated list of types, or to an empty string to turn notifications off entirely. 
 Existing installs are migrated automatically: if your trigger list is still the old default of exactly security_alert , it is rewritten to include sensitive . A customized list is left untouched. Without this migration the new type would never have notified on any existing install, because a fresh settings.json is seeded with every default and persisted values win on load. 
 If you had deliberately set your trigger list to exactly security_alert and want it to stay that way, set it to something explicitly different after upgrading — the migration cannot distinguish that case from the seeded default. 
 Also in this release 
 
 Observer prompt fix. The type_guidance prompt still described "6 options" and never listed security_alert or security_note from #2084 . That string is the only type prose the observer model sees — the per-type description fields are never injected into any prompt — so those types have been under-emitted since April. It now enumerates all nine. 
 Corpus filters, the OpenClaw detailed feed, and the weekly-digests legend all recognize the new type. 
 BMP-safe fallback for the new emoji, so injected context can't contribute a surrogate pair (the #2787 failure class). 
 Built plugin artifacts are regenerated, picking up the chroma concurrent-write fix from #3462 that had not yet been built into the shipped bundles. 
 
 Full changelog : v13.12.4...v13.13.0

</details>