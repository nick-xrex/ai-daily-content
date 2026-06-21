---
id: inbox_f1f50d28
date: 2026-06-20
source_ref: "[[00-inbox/.../inbox_f1f50d28]]"
title: "v13.7.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.7.0
source: claude-mem-releases
published_at: 2026-06-20T07:05:05+00:00
fetched_at: 2026-06-21T02:29:07.635698+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude-Mem v13.7.0：遙測系統全面改進。核心改變包括：(1) 改用 per-session rollups 取代 5 分鐘牆上時間視窗，減少遙測數據量（確認舊版本 raw_session_compressed 在 2 天內下降 75%）；(2) 統一遙測路徑，本地日誌保持完整保真度，遠端遙測自動遮蔽；(3) 同意門控的錯誤追蹤，自動去除家目錄、路徑、DB 連接字符串、Email、API 金鑰等敏感資訊，錯誤訊息限制 500 字符；(4) 新增獨立的遙測錯誤開關 CLAUDE_MEM_TELEMETRY_ERRORS=0。此版本實現從白名單遙測到同意門控的隱私轉向。"
key_points:
  - "Per-session rollups 取代時間視窗，減少遙測量 ~75%（驗證舊版本衰減）"
  - "統一遙測路徑：本地日誌完整，遠端自動遮蔽（家目錄、路徑、DB 密碼、Email、API token）"
  - "同意門控錯誤追蹤 + 獨立開關，遵守 CLAUDE_MEM_TELEMETRY 和 DO_NOT_TRACK"
tags: [claude-mem, telemetry, privacy, observability]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.7.0

Claude-Mem v13.7.0：遙測系統全面改進。核心改變包括：(1) 改用 per-session rollups 取代 5 分鐘牆上時間視窗，減少遙測數據量（確認舊版本 raw_session_compressed 在 2 天內下降 75%）；(2) 統一遙測路徑，本地日誌保持完整保真度，遠端遙測自動遮蔽；(3) 同意門控的錯誤追蹤，自動去除家目錄、路徑、DB 連接字符串、Email、API 金鑰等敏感資訊，錯誤訊息限制 500 字符；(4) 新增獨立的遙測錯誤開關 CLAUDE_MEM_TELEMETRY_ERRORS=0。此版本實現從白名單遙測到同意門控的隱私轉向。

### 重點
- Per-session rollups 取代時間視窗，減少遙測量 ~75%（驗證舊版本衰減）
- 統一遙測路徑：本地日誌完整，遠端自動遮蔽（家目錄、路徑、DB 密碼、Email、API token）
- 同意門控錯誤追蹤 + 獨立開關，遵守 CLAUDE_MEM_TELEMETRY 和 DO_NOT_TRACK

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.7.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v13.7.0

PostHog telemetry overhaul 
 A ground-up rebuild of claude-mem's telemetry — per-session rollups, unified instrumentation, and real (redacted) error tracking. Grounded in live PostHog data: the raw-event volume was confirmed to be legacy-fleet decay (raw session_compressed fell ~75% in two days as installs updated), so this is the proper rebuild, not a hotfix. 
 What's new 
 
 Per-session rollups — observer_turn_rollup is now emitted once per session at session end ( rollup_reason = session_end | worker_shutdown | safety_flush, plus window_seq ) instead of per 5-minute wall-clock window. Memory-bounded with a safety sweep; drains correctly on worker shutdown. 
 Unified instrumentation — a single instrument() path fans out to the local logger (full fidelity) and telemetry (scrubbed/rolled-up). The logger stays telemetry-free. 
 Redacted error tracking — real error messages + trimmed stacks now reach PostHog as $exception events, consent-gated, profile-less, and fingerprint rate-limited. An allow-then-redact scrubber strips home dirs, absolute paths, DB connection-string credentials, URL userinfo, emails, API tokens (sk-/phc-/ghp-/AWS AKIA/JWT), hex, and IPv4; messages cap at 500 chars, stacks at ~2KB. Autocapture is fully redacted (on-disk source context is stripped, never sent). 
 New kill-switch — CLAUDE_MEM_TELEMETRY_ERRORS=0 disables error capture independently of analytics. 
 Docs — telemetry.mdx rewritten to document the new model, the error-tracking opt-in + one-way-door note, and the opt-out switches. 
 
 Privacy 
 This release begins collecting redacted error messages/stacks (a deliberate, consent-gated shift from whitelist-only telemetry). Raw paths, prompts, project names, source code, and model output are still never collected. Opt out of all telemetry with CLAUDE_MEM_TELEMETRY=0 / DO_NOT_TRACK=1 , or errors-only with CLAUDE_MEM_TELEMETRY_ERRORS=0 . 
 🤖 Generated with Claude Code

</details>