---
id: inbox_d75ce0a0
date: 2026-07-13
source_ref: "[[00-inbox/2026-07-13/2231-claude-mem-releases-v13-11-0-ec3d]]"
title: "v13.11.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.11.0
source: claude-mem-releases
published_at: 2026-07-13T04:01:10+00:00
fetched_at: 2026-07-14T00:19:08.367859+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Memory (claude-mem) v13.11.0 退役獨立的 cloud-sync.mjs daemon，改採 worker 內建同步機制——每次本地寫入觸發背景 flusher（1.5 秒防抖合併連續寫入），分頁刷新至 cmem.ai（200 行/2MB 單頁、30 秒逾時、指數退避重試）。新增 GET /api/sync/status 查詢待同步行數、最後刷新時間、錯誤狀態；新增 /cloud-sync skill 管理遷移與舊 daemon 退役。修復 prompt→session mapping 漏洞（原先記錄落後無法解析 session id），schema v40 自修復（迴溯重推所有先前上傳的 prompt）；縮窄競態條件窗口（per-row timestamp guard 防止 mis-key）。遷移完全自動且向後兼容，既存獨立 daemon 用戶在升級後首次運行 /cloud-sync 自動遷移；未配置同步的安裝不受影響。"
key_points:
  - "Worker 內建同步取代獨立 daemon，降低運維複雜度與部署負擔"
  - "CloudSync flusher：1.5s 防抖、200 行/2MB 分頁、30s 逾時、指數退避重試"
  - "修復 prompt session mapping 與競態條件（per-row timestamp guard）"
tags: [claude-mem, cloud-sync, worker, architecture]
topics: [foundation_models.claude]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.11.0

Claude Memory (claude-mem) v13.11.0 退役獨立的 cloud-sync.mjs daemon，改採 worker 內建同步機制——每次本地寫入觸發背景 flusher（1.5 秒防抖合併連續寫入），分頁刷新至 cmem.ai（200 行/2MB 單頁、30 秒逾時、指數退避重試）。新增 GET /api/sync/status 查詢待同步行數、最後刷新時間、錯誤狀態；新增 /cloud-sync skill 管理遷移與舊 daemon 退役。修復 prompt→session mapping 漏洞（原先記錄落後無法解析 session id），schema v40 自修復（迴溯重推所有先前上傳的 prompt）；縮窄競態條件窗口（per-row timestamp guard 防止 mis-key）。遷移完全自動且向後兼容，既存獨立 daemon 用戶在升級後首次運行 /cloud-sync 自動遷移；未配置同步的安裝不受影響。

### 重點
- Worker 內建同步取代獨立 daemon，降低運維複雜度與部署負擔
- CloudSync flusher：1.5s 防抖、200 行/2MB 分頁、30s 逾時、指數退避重試
- 修復 prompt session mapping 與競態條件（per-row timestamp guard）

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.11.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Worker-native cloud sync (PR #3182 ) 
 The standalone cloud-sync.mjs daemon is retired. The worker now syncs memories itself — every local write nudges a background flusher that drains unsynced rows to cmem.ai, with no separate process to install or babysit. 
 New: 
 
 CloudSync flusher: write-site nudges, 1.5s debounce coalescing write bursts, single-flight flush, 200-row/2MB pages, 30s request timeout, capped exponential backoff on failure 
 GET /api/sync/status — pending counts per kind, last flush time, last error 
 /cloud-sync skill — status checks, first-run credential migration from the legacy .cloud-sync.env , daemon retirement, and worker restart runbook 
 
 Fixed: 
 
 Prompts now join through sdk_sessions to push their real memory_session_id / project instead of an unresolvable fallback — cloud-side prompt-to-session views (Summary ⇄ Prompt toggle, Replay) can now actually find their prompt 
 Schema v40 self-repair: on upgrade, every previously-synced prompt (including ones uploaded by the legacy daemon) is re-queued and re-pushed through the fixed mapper; a backfill lane header suppresses realtime broadcast storms during that re-push 
 Closed a race where a session's memory id registering while its prompt's upload was still in flight could leave that prompt permanently mis-keyed in the cloud — the stamp is now guarded per row and re-pushes with the corrected mapping instead 
 
 Migration: fully automatic and backward compatible. Existing standalone cloud-sync users are migrated on first /cloud-sync run after upgrading; installs with no cloud sync configured are unaffected.

</details>