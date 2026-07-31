---
id: inbox_1b71f78e
date: 2026-07-30
source_ref: "[[00-inbox/2026-07-30/2201-ruflo-releases-v3-32-39-codex-hooks-json-pretooluse-ver-97a1]]"
title: "v3.32.39 — Codex hooks.json + PreToolUse verdict compat"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.39
source: ruflo-releases
published_at: 2026-07-30T02:12:29+00:00
fetched_at: 2026-07-30T22:06:30.271249+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.32.39 修復 Codex 編輯器相容性問題。#2855 修復插件清單加載器對未知欄位的拒絕：ruflo-core 和 ruflo-cost-tracker 的 hooks.json 攜帶 _note/_platform_note 文檔欄位，Codex 只接受 description 和 hooks，導致插件加載失敗。修復後將文檔內容摺疊入 description，並添加 CI 防護避免無聲迴歸。#2856 修復 PreToolUse hooks JSON 輸出格式不相容：modify-bash/modify-file 回傳 Cursor 的 {\"permission\":\"allow\"} 格式，但 Codex 更嚴格的 schema 拒絕。通過 turn_id 層級檢查和環境變數雙重驗證強化 Codex 主機檢測。ruflo-core 0.2.5→0.2.6、ruflo-cost-tracker 0.26.2→0.26.3，觸發 Codex 插件緩存失效以取得修復。"
key_points:
  - "Codex 插件清單加載器對 _note/_platform_note 欄位拒絕，摺疊入 description + 添加 CI 防護"
  - "PreToolUse hooks 輸出格式與 Codex 更嚴格 schema 不相容，通過 turn_id 和環境變數雙重驗證"
  - "版本碰撞（0.2.5→0.2.6、0.26.2→0.26.3）觸發 Codex 緩存失效"
tags: [codex-compat, plugin-manifest, pretooluse, hooks-json]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.32.39 — Codex hooks.json + PreToolUse verdict compat

Ruflo v3.32.39 修復 Codex 編輯器相容性問題。#2855 修復插件清單加載器對未知欄位的拒絕：ruflo-core 和 ruflo-cost-tracker 的 hooks.json 攜帶 _note/_platform_note 文檔欄位，Codex 只接受 description 和 hooks，導致插件加載失敗。修復後將文檔內容摺疊入 description，並添加 CI 防護避免無聲迴歸。#2856 修復 PreToolUse hooks JSON 輸出格式不相容：modify-bash/modify-file 回傳 Cursor 的 {"permission":"allow"} 格式，但 Codex 更嚴格的 schema 拒絕。通過 turn_id 層級檢查和環境變數雙重驗證強化 Codex 主機檢測。ruflo-core 0.2.5→0.2.6、ruflo-cost-tracker 0.26.2→0.26.3，觸發 Codex 插件緩存失效以取得修復。

### 重點
- Codex 插件清單加載器對 _note/_platform_note 欄位拒絕，摺疊入 description + 添加 CI 防護
- PreToolUse hooks 輸出格式與 Codex 更嚴格 schema 不相容，通過 turn_id 和環境變數雙重驗證
- 版本碰撞（0.2.5→0.2.6、0.26.2→0.26.3）觸發 Codex 緩存失效

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.39)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Fixes 
 #2855 — Codex's plugin hook-manifest loader accepts only description and hooks at the top level. plugins/ruflo-core/hooks/hooks.json and plugins/ruflo-cost-tracker/hooks/hooks.json carried _note / _platform_note documentation fields, so a fresh Codex install of ruflo-core@ruflo failed to load the plugin at all with unknown field \ _note`, expected `description` or `hooks` . Fixed by folding the doc content into description . Added a permanent CI guard ( scripts/audit-plugin-hooks-cross-platform.mjs`) so this can't regress silently again. 
 #2856 — Once the manifest could load, modify-bash / modify-file PreToolUse hooks always echoed Cursor's {"permission":"allow"} verdict, which Codex's own stricter output schema rejects outright ( hook returned invalid pre-tool-use JSON output ) — verified directly against the real parser ( codex-rs/hooks/src/engine/output_parser.rs ). Hardened Codex-host detection with a turn_id -based fallback alongside the existing PLUGIN_ROOT / PLUGIN_DATA env-var check. 
 ruflo-core bumped 0.2.5 → 0.2.6 and ruflo-cost-tracker 0.26.2 → 0.26.3 so Codex's per-version plugin cache invalidates and picks up the fix rather than serving a stale cached copy indefinitely. 
 PR: #2857 
 Packages 
 `@claude-flow/cli`, `claude-flow`, and `ruflo` are all at 3.32.39 ; `latest`, `alpha`, and `v3alpha` dist-tags all point to it.

</details>