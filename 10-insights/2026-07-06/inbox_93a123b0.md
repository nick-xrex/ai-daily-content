---
id: inbox_93a123b0
date: 2026-07-06
source_ref: "[[00-inbox/2026-07-06/2254-ruflo-releases-v3-25-2-agentdb-atomic-flushes-backup-au-0df0]]"
title: "v3.25.2 — AgentDB atomic flushes + backup auto-restore (#2584)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.25.2
source: ruflo-releases
published_at: 2026-07-06T02:34:41+00:00
fetched_at: 2026-07-07T00:38:26.155001+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo 3.25.2 修復了 AgentDB（sql.js 資料庫）在併發全映像刷新時導致磁碟映像損壞的問題。核心改進包括原子寫入機制（temp → fsync → rename），透過 writeFileAtomic 和 writeFileRestricted 防止中途中斷或併發寫入造成半寫入狀態。備份自動恢復功能則在本地重建無法修復時，自動從 .swarm/backups/ 目錄恢復最新的 integrity_check=ok 快照，將資料全損轉為自動復原。新增合成撕裂映像測試驗證修復效果（6/6 通過），採取主動防禦、即故即閉的設計哲學。"
key_points:
  - "原子寫入模式（temp → fsync → rename）防止電源中斷或 OOM 造成的半寫入損壞"
  - "備份自動恢復：sqlite3 .recover 無法救援時自動復原最新快照，將數據損失轉為自動復原"
  - "測試驗證：合成撕裂映像（integrity_check 失敗、rebuild 零行）6/6 通過"
tags: [durability, database, atomic-writes, backup-recovery, agentdb]
topics: []
importance: 4
novelty: 2
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.25.2 — AgentDB atomic flushes + backup auto-restore (#2584)

Ruflo 3.25.2 修復了 AgentDB（sql.js 資料庫）在併發全映像刷新時導致磁碟映像損壞的問題。核心改進包括原子寫入機制（temp → fsync → rename），透過 writeFileAtomic 和 writeFileRestricted 防止中途中斷或併發寫入造成半寫入狀態。備份自動恢復功能則在本地重建無法修復時，自動從 .swarm/backups/ 目錄恢復最新的 integrity_check=ok 快照，將資料全損轉為自動復原。新增合成撕裂映像測試驗證修復效果（6/6 通過），採取主動防禦、即故即閉的設計哲學。

### 重點
- 原子寫入模式（temp → fsync → rename）防止電源中斷或 OOM 造成的半寫入損壞
- 備份自動恢復：sqlite3 .recover 無法救援時自動復原最新快照，將數據損失轉為自動復原
- 測試驗證：合成撕裂映像（integrity_check 失敗、rebuild 零行）6/6 通過

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.25.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

ruflo 3.25.2 — AgentDB durability: atomic flushes + backup auto-restore 
 Fixes #2584 — AgentDB (sql.js) database disk image is malformed under torn/concurrent full-image flushes. 
 
 Atomic DB writes. Every full-image flush now goes temp → fsync → rename (new writeFileAtomic , and writeFileRestricted routed through it), plus the decay-path flush and metrics-db.mjs . A kill/OOM mid-write or a concurrent writer can no longer leave a half-written, malformed image. 
 Backup auto-restore. On a malformed open, when the in-place rebuild can't salvage the image (the reported case where sqlite3 .recover recovered 0 rows), recovery now restores the newest integrity_check=ok snapshot from .swarm/backups/ and parks the corrupt original — turning total loss into automatic recovery. (Rotating periodic backups already existed.) 
 Test: a synthesized torn image (integrity_check fails, rebuild salvages nothing) that must recover via backup-restore — 6/6 pass. 
 
 Additive · fail-closed · zero-regression. npx ruflo@latest . 
 🤖 Generated with RuFlo

</details>