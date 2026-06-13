---
id: inbox_cd934704
date: 2026-06-13
source_ref: "[[00-inbox/.../inbox_cd934704]]"
title: "v13.6.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.6.0
source: claude-mem-releases
published_at: 2026-06-13T01:13:24+00:00
fetched_at: 2026-06-13T04:10:04.850639+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v13.6.0 添加歷史遙測回填功能，使增長指標擴展回遙測存在前的時期。在首次 worker 啟動時執行一次性回填：聚集每個安裝的日常活動匯總（觀察/會話/摘要/提示計數、觀察類型分解、會話結果、subagent 計數、壓縮 token）到 PostHog，標籤 backfilled: true。遵守同意門控（DO_NOT_TRACK、CLAUDE_MEM_TELEMETRY=0、opt-out），運行一次/install 且失敗重試（確定性 UUID 去重複）。支援 CLAUDE_MEM_TELEMETRY_DEBUG=1 乾運行模式檢查負載。"
key_points:
  - "一次性歷史回填：聚集安裝首次活躍日期至升級日期間的日常計數，僅含匿名聚集（無標題、提示、文件內容）"
  - "隱私保護設計：遵守同意門控、幂等重試（確定性 UUID）、opt-in 前回填防止洩露、乾運行模式用於除錯"
  - "資料品質防衛：舊紀元標準化和損壞行警衛防止壞時間戳進入歷史記錄，部分天數不發送"
tags: [claude-mem, telemetry, privacy, analytics, historical-backfill]
topics: [foundation_models.claude]
importance: 2
novelty: 2
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.6.0

claude-mem v13.6.0 添加歷史遙測回填功能，使增長指標擴展回遙測存在前的時期。在首次 worker 啟動時執行一次性回填：聚集每個安裝的日常活動匯總（觀察/會話/摘要/提示計數、觀察類型分解、會話結果、subagent 計數、壓縮 token）到 PostHog，標籤 backfilled: true。遵守同意門控（DO_NOT_TRACK、CLAUDE_MEM_TELEMETRY=0、opt-out），運行一次/install 且失敗重試（確定性 UUID 去重複）。支援 CLAUDE_MEM_TELEMETRY_DEBUG=1 乾運行模式檢查負載。

### 重點
- 一次性歷史回填：聚集安裝首次活躍日期至升級日期間的日常計數，僅含匿名聚集（無標題、提示、文件內容）
- 隱私保護設計：遵守同意門控、幂等重試（確定性 UUID）、opt-in 前回填防止洩露、乾運行模式用於除錯
- 資料品質防衛：舊紀元標準化和損壞行警衛防止壞時間戳進入歷史記錄，部分天數不發送

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.6.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v13.6.0

📊 Historical Telemetry Backfill 
 claude-mem's growth metrics now extend back before telemetry existed. On the first worker start after this upgrade, each install performs a one-time backfill of anonymized daily activity rollups into PostHog via historical-migration ingestion — so installs-over-time, reconstructed WAU/MAU, and cohort retention reflect real usage history instead of starting at the telemetry ship date. 
 What gets sent 
 Anonymous counts only — never titles, prompts, file contents, or project names: 
 
 One profile-less historical_activity event per active day: observation/session/summary/prompt counts, observation-type breakdown, session outcomes, platform buckets, subagent counts, and compression discovery-token totals — all tagged backfilled: true 
 One install_inferred event carrying the install's first active date, drawn from trustworthy session timestamps 
 
 Privacy &amp; safety 
 
 Honors the exact same consent gates as live telemetry: DO_NOT_TRACK , CLAUDE_MEM_TELEMETRY=0 , and telemetry.json opt-out. Opting out before your first post-upgrade worker start prevents the backfill entirely; a later opt-in still backfills. 
 Runs once per install , latched by a completion marker written only after confirmed delivery — failed sends retry on the next worker start, and deterministic event uuids make retries duplicate-safe. 
 CLAUDE_MEM_TELEMETRY_DEBUG=1 dry-runs the full payload to stderr without sending anything. 
 Legacy epoch normalization and corrupt-row guards keep bad timestamps out of the historical record; partial days are never shipped. 
 
 Full disclosure documented at docs.claude-mem.ai/telemetry . 
 PR : #2912

</details>