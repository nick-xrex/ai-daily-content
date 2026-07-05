---
id: inbox_10abdf90
date: 2026-07-04
source_ref: "[[00-inbox/2026-07-04/2200-ruflo-releases-v3-23-0-nightly-vector-db-backup-21ec]]"
title: "v3.23.0 — nightly vector-DB backup"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.23.0
source: ruflo-releases
published_at: 2026-07-04T21:42:33+00:00
fetched_at: 2026-07-04T22:05:43.752653+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RuFlo v3.23.0 新增向量記憶 DB 的每日備份機制，解決長期持久化和故障復原需求。採用 better-sqlite3 的線上備份 API（而非簡單檔案拷貝）確保 WAL 模式下的一致性與無損性，避免無聲資料損壞。備份支援輪轉策略，預設保留 7 份舊版本；亦支援 GCS 離線備份（--gcs gs://...）實現異地冗餘。框架提供 CLI 命令（--db/--dir/--keep/--gcs）與 24 小時自動守護進程，預設啟用但可選退出（-w）。所有變更向後相容，涉及 3-package 訓練。"
key_points:
  - "使用 better-sqlite3 線上備份 API 而非簡單拷貝，避免 WAL 模式下資料損壞"
  - "支援本地輪轉保留策略（預設 7 份）與 GCS 離線備份（--gcs gs://...）"
  - "提供 CLI 工具與 24 小時自動守護進程（預設啟用，-w 可退出）"
tags: [vector-db, backup, sqlite-wal, persistence]
topics: []
importance: 3
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.23.0 — nightly vector-DB backup

RuFlo v3.23.0 新增向量記憶 DB 的每日備份機制，解決長期持久化和故障復原需求。採用 better-sqlite3 的線上備份 API（而非簡單檔案拷貝）確保 WAL 模式下的一致性與無損性，避免無聲資料損壞。備份支援輪轉策略，預設保留 7 份舊版本；亦支援 GCS 離線備份（--gcs gs://...）實現異地冗餘。框架提供 CLI 命令（--db/--dir/--keep/--gcs）與 24 小時自動守護進程，預設啟用但可選退出（-w）。所有變更向後相容，涉及 3-package 訓練。

### 重點
- 使用 better-sqlite3 線上備份 API 而非簡單拷貝，避免 WAL 模式下資料損壞
- 支援本地輪轉保留策略（預設 7 份）與 GCS 離線備份（--gcs gs://...）
- 提供 CLI 工具與 24 小時自動守護進程（預設啟用，-w 可退出）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.23.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Nightly vector-memory DB backup 
 
 WAL-safe snapshots of .swarm/memory.db via better-sqlite3's online .backup() — a naive copy of a WAL-mode DB can corrupt; this is consistent + non-destructive (read-only source). 
 Rotation (keep last N, default 7) + optional GCS offsite ( --gcs gs://... / RUFLO_BACKUP_GCS ). 
 memory backup CLI ( --db/--dir/--keep/--gcs ) + a daemon backup worker (24h, enabled by default, opt-out via -w ). 
 
 All backward-compatible. 3-package train at 3.23.0. 
 🤖 Generated with RuFlo

</details>