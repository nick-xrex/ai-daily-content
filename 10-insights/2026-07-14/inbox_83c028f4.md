---
id: inbox_83c028f4
date: 2026-07-14
source_ref: "[[00-inbox/2026-07-14/2200-simon-willison-lobste-rs-is-now-running-on-sqlite-4b32]]"
title: "lobste.rs is now running on SQLite"
url: https://simonwillison.net/2026/Jul/14/lobsters-sqlite/#atom-everything
source: simon-willison
published_at: 2026-07-14T19:44:11+00:00
fetched_at: 2026-07-14T22:11:41.436510+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Lobsters 社群網站於本週末完成了從 MariaDB 遷移至 SQLite 的計畫，經過 8 年籌劃、三次主要 PR 迭代。新架構將整個服務運行在單一 VPS 上，主資料庫檔案 3.8GB，另有 1.1GB 快取、218MB 隊列及 555MB 速率限制資料庫。效能指標全面提升：CPU 和記憶體使用量均大幅下降，VPS 成本減半。遷移 PR 涉及 30 commits、188 個檔案、淨增加 735 行代碼，團隊已確認架構穩定且為永久選擇。"
key_points:
  - "單一 VPS 架構運行完整應用，VPS 成本減少 50%，替代原先的多伺服器 MariaDB 部署"
  - "主資料庫 3.8GB + 快取 1.1GB + 隊列 218MB + 限流 555MB，CPU 與記憶體使用率同時下降"
  - "遷移涉及 30 commits、188 檔案、淨增 735 行代碼，耗時 8 年籌劃評估（2018 年起）"
tags: [sqlite, infrastructure, database, migrations, production]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## lobste.rs is now running on SQLite

Lobsters 社群網站於本週末完成了從 MariaDB 遷移至 SQLite 的計畫，經過 8 年籌劃、三次主要 PR 迭代。新架構將整個服務運行在單一 VPS 上，主資料庫檔案 3.8GB，另有 1.1GB 快取、218MB 隊列及 555MB 速率限制資料庫。效能指標全面提升：CPU 和記憶體使用量均大幅下降，VPS 成本減半。遷移 PR 涉及 30 commits、188 個檔案、淨增加 735 行代碼，團隊已確認架構穩定且為永久選擇。

### 重點
- 單一 VPS 架構運行完整應用，VPS 成本減少 50%，替代原先的多伺服器 MariaDB 部署
- 主資料庫 3.8GB + 快取 1.1GB + 隊列 218MB + 限流 555MB，CPU 與記憶體使用率同時下降
- 遷移涉及 30 commits、188 檔案、淨增 735 行代碼，耗時 8 年籌劃評估（2018 年起）

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/14/lobsters-sqlite/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

lobste.rs is now running on SQLite 
Community site Lobsters has been planning a migration away from MariaDB since August 2018 - originally targeting PostgreSQL, but last year they decided to investigate SQLite instead. 
 This weekend they completed the migration, and now consider it stable enough that it looks like this is the permanent architecture for the site going forward: 
 
 SQLite seems to have passed with flying colors: cpu usage is down, memory usage is down, site seems to be snappier at least for me, 1/2 the vps cost once mariadb vps is taken down 
 
 The Lobsters Rails application now runs on a single VPS, with a primary content SQLite database file that's around 3.8GB. There's also a 1.1GB cache database, a 218MB queue database, and a still growing 555MB rack_attack database used by the Rack::Attack middleware for blocking and throttling abusive requests. 
 There are plenty more details in both the linked thread and this SQLite migration PR by Thomas Dziedzic, which added 735 lines and removed 593 lines across 30 commits and 188 files. That PR built on top of previous PRs #1705 , #1871 , and #1924 . 
 This is a really useful case study, and a great reminder that you can get a whole lot done with a single server and SQLite in 2026.

 Tags: migrations , ops , rails , sqlite , lobsters

</details>