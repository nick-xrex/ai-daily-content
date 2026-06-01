---
id: inbox_ea0eb5d7
date: 2026-06-01
source_ref: "[[00-inbox/2026-06-01/2245-rtk-releases-dev-0-43-0-rc-256-e6cd]]"
title: "dev-0.43.0-rc.256"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.256
source: rtk-releases
published_at: 2026-06-01T16:51:24+00:00
fetched_at: 2026-06-01T22:51:13.036906+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK (Rust Token Killer) 版本 dev-0.43.0-rc.256 發布。此版本的主要變更為在 Cargo.toml 中透過 rust-version 欄位正式聲明最小支持 Rust 版本 (MSRV) 為 1.91。MSRV 聲明為 Rust 官方標準做法，允許套件管理器與使用者在安裝前驗證版本相容性。此舉明確 RTK 工具的向下相容性邊界。對於使用較舊 Rust 環境的開發者而言，可提前評估升級或使用替代方案的必要性。"
key_points:
  - "MSRV 1.91 聲明：透過 Cargo.toml 的 rust-version 欄位正式宣告最低支援版本"
tags: [rust, msrv, tooling]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.43.0-rc.256

RTK (Rust Token Killer) 版本 dev-0.43.0-rc.256 發布。此版本的主要變更為在 Cargo.toml 中透過 rust-version 欄位正式聲明最小支持 Rust 版本 (MSRV) 為 1.91。MSRV 聲明為 Rust 官方標準做法，允許套件管理器與使用者在安裝前驗證版本相容性。此舉明確 RTK 工具的向下相容性邊界。對於使用較舊 Rust 環境的開發者而言，可提前評估升級或使用替代方案的必要性。

### 重點
- MSRV 1.91 聲明：透過 Cargo.toml 的 rust-version 欄位正式宣告最低支援版本

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.256)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Merge pull request #2002 from YOMXXX/feat/msrv-1.91 

 chore(cargo): declare MSRV via rust-version = "1.91"

</details>