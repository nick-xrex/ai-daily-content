---
id: inbox_3f9049c3
date: 2026-06-21
source_ref: "[[00-inbox/.../inbox_3f9049c3]]"
title: "v13.8.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.8.0
source: claude-mem-releases
published_at: 2026-06-21T20:33:47+00:00
fetched_at: 2026-06-22T01:24:07.834927+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v13.8.0 發佈，強化遙測系統以追蹤觀察量及成本指標。observer_turn_rollup 現在聚合每個壓縮週期的 observations_created 及各類型觀察計數（bugfix、discovery、decision、refactor、other），context_injected_rollup 記錄注入的觀察總數與節省的 token 對比，使得成本-per-observation 與觀察類型-by-model 可直接從聚合數據推導。此版本並移除了舊的 fabrication tracking 相關字段，更新了公開遙測文檔。該改進讓使用者能更精細地監測效能和成本效益。"
key_points:
  - "observer_turn_rollup 新增 observations_created 及 obs_type_* 家族聚合，使成本-per-observation 可直接推導"
  - "context_injected_rollup 記錄 total_observations_injected 與 total_tokens_saved_vs_naive，提升快取價值透明度"
  - "廢棄 fabrication tracking，代碼和文檔隨之清理"
tags: [claude-mem, telemetry, observability, metrics]
topics: [foundation_models.claude]
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.8.0

claude-mem v13.8.0 發佈，強化遙測系統以追蹤觀察量及成本指標。observer_turn_rollup 現在聚合每個壓縮週期的 observations_created 及各類型觀察計數（bugfix、discovery、decision、refactor、other），context_injected_rollup 記錄注入的觀察總數與節省的 token 對比，使得成本-per-observation 與觀察類型-by-model 可直接從聚合數據推導。此版本並移除了舊的 fabrication tracking 相關字段，更新了公開遙測文檔。該改進讓使用者能更精細地監測效能和成本效益。

### 重點
- observer_turn_rollup 新增 observations_created 及 obs_type_* 家族聚合，使成本-per-observation 可直接推導
- context_injected_rollup 記錄 total_observations_injected 與 total_tokens_saved_vs_naive，提升快取價值透明度
- 廢棄 fabrication tracking，代碼和文檔隨之清理

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.8.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v13.8.0

Telemetry: observation volume on per-session rollups 
 Carries generation-side observation volume and type mix on the observer_turn_rollup event so cache-value KPIs survive the migration off the legacy per-occurrence session_compressed / context_injected streams. 
 What's new 
 
 observer_turn_rollup now sums observations_created and the obs_type_* family (bugfix / discovery / decision / refactor / other) across every compression turn in a session. Paired with total_cost_usd , this makes cost-per-observation and observation-type-by-model derivable from the rollup alone. 
 context_injected_rollup carries total_observations_injected and total_tokens_saved_vs_naive — context-cache value (observations served × cost/obs) is now derivable from the rollup. 
 scrub.ts whitelist extended for the new aggregate keys; all values are counts/sums only — never names, prompt text, or raw strings. 
 Public telemetry.mdx docs updated to document the new rollup fields. 
 
 Merge notes 
 
 Merged latest main (Ponytail audit, v13.7.1), which removed fabrication tracking; the now-stale fabrication_count / fabricated_count references were dropped from code and docs accordingly. 
 
 Full changes: #3017

</details>