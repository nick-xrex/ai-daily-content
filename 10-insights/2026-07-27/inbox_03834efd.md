---
id: inbox_03834efd
date: 2026-07-27
source_ref: "[[00-inbox/.../inbox_03834efd]]"
title: "dev-0.44.1-rc.339"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.44.1-rc.339
source: rtk-releases
published_at: 2026-07-27T17:33:17+00:00
fetched_at: 2026-07-28T01:17:34.805846+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK dev-0.44.1-rc.339 進行重構工作，將 Rust 代碼中的 lazy_static 依賴改為 LazyLock。LazyLock 是 Rust 1.80+ 內建的同步初始化機制，移除外部依賴同時保持相同功能，改善編譯體積與時間。"
key_points:
  - "RTK dev-0.44.1-rc.339：lazy_static → std::sync::LazyLock 重構"
  - "移除外部依賴，使用 Rust 標準庫原生同步初始化方案"
  - "典型的依賴現代化與代碼精簡實踐"
tags: [rtk, rust-refactor, dependency-management, lazy-initialization]
topics: []
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.44.1-rc.339

RTK dev-0.44.1-rc.339 進行重構工作，將 Rust 代碼中的 lazy_static 依賴改為 LazyLock。LazyLock 是 Rust 1.80+ 內建的同步初始化機制，移除外部依賴同時保持相同功能，改善編譯體積與時間。

### 重點
- RTK dev-0.44.1-rc.339：lazy_static → std::sync::LazyLock 重構
- 移除外部依賴，使用 Rust 標準庫原生同步初始化方案
- 典型的依賴現代化與代碼精簡實踐

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.44.1-rc.339)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# dev-0.44.1-rc.339

Merge pull request #3244 from TaKO8Ki/refactor/replace-lazy-static 

 refactor: replace `lazy_static` with `LazyLock`

</details>