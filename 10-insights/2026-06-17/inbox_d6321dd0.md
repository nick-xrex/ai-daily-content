---
id: inbox_d6321dd0
date: 2026-06-17
source_ref: "[[00-inbox/2026-06-17/2200-claude-mem-releases-v13-6-2-41a3]]"
title: "v13.6.2"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.6.2
source: claude-mem-releases
published_at: 2026-06-17T20:24:06+00:00
fetched_at: 2026-06-17T22:04:18.126979+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v13.6.2 發布，主要焦點在大幅降低 telemetry 成本。高頻率的 session_compressed 與 context_injected 事件現合併為 5 分鐘 rollup 窗口（observer_turn_rollup、context_injected_rollup），將每月約 4,500 萬個事件縮減至 2 萬筆 rollup 記錄。此優化預期將 PostHog 帳單從 $7,700/月降至 $10/月，同時透過 outcomes_ok / outcomes_error 分類保留統計完整性。另外修復 Windows CI 環境問題，環境固定為 windows-2022 以支援 node-gyp 對 Visual Studio 2022 的相容性。"
key_points:
  - "Telemetry 事件聚合：4,500 萬事件/月 → 2 萬筆 rollup 記錄"
  - "成本優化：PostHog 帳單 $7,700/月 → $10/月，保留統計完整性"
  - "Windows CI 環境固定為 windows-2022，解決 node-gyp Visual Studio 18 相容性問題"
tags: [claude-mem, telemetry, cost-optimization, observability]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.6.2

claude-mem v13.6.2 發布，主要焦點在大幅降低 telemetry 成本。高頻率的 session_compressed 與 context_injected 事件現合併為 5 分鐘 rollup 窗口（observer_turn_rollup、context_injected_rollup），將每月約 4,500 萬個事件縮減至 2 萬筆 rollup 記錄。此優化預期將 PostHog 帳單從 $7,700/月降至 $10/月，同時透過 outcomes_ok / outcomes_error 分類保留統計完整性。另外修復 Windows CI 環境問題，環境固定為 windows-2022 以支援 node-gyp 對 Visual Studio 2022 的相容性。

### 重點
- Telemetry 事件聚合：4,500 萬事件/月 → 2 萬筆 rollup 記錄
- 成本優化：PostHog 帳單 $7,700/月 → $10/月，保留統計完整性
- Windows CI 環境固定為 windows-2022，解決 node-gyp Visual Studio 18 相容性問題

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.6.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's Changed 
 Telemetry cost reduction ( #2977 ) 
 
 TelemetryBuffer rollup windows — high-volume session_compressed and context_injected events are now aggregated into 5-minute rollup windows ( observer_turn_rollup , context_injected_rollup ) before forwarding to PostHog, replacing ~45M individual events/month with ~20K rollup records. Cuts the projected PostHog bill from ~$7,700/mo to ~$10/mo without losing aggregate shape (counts, sums, averages, top model, per-outcome buckets). 
 Outcome visibility in context_injected_rollup — added outcomes_ok / outcomes_error buckets so a window of 100% failed injections is distinguishable from one of zero-token successes. 
 
 CI 
 
 Windows build pinned to windows-2022 — the windows-latest image moved to windows-2025 (Visual Studio 18), which the bundled node-gyp@11.5.0 can't detect, breaking native tree-sitter rebuilds. Pinned to windows-2022 (VS2022) until node-gyp gains VS18 support. 
 
 Full Changelog : v13.6.1...v13.6.2

</details>