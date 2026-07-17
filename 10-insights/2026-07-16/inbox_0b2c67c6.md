---
id: inbox_0b2c67c6
date: 2026-07-16
source_ref: "[[00-inbox/2026-07-16/0012-infoq-main-presentation-the-rust-high-performance-t-f05f]]"
title: "Presentation: The Rust High Performance Talk You Did Not Expect"
url: https://www.infoq.com/presentations/rust-tps-service/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-07-16T10:20:00+00:00
fetched_at: 2026-07-17T00:19:20.911262+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruth Linehan 介紹了從 Kotlin 遷移高性能緩存服務到 Rust 的案例，這次遷移出人意料地打破了團隊對交付速度和工程開銷的內部預設。她重點討論了 Rust borrow checker 的人體工程學改進、編譯時安全驗證如何縮短開發者反饋迴圈、以及如何運用 Criterion 和 flamegraphs 等高級分析工具來優化併發代碼路徑。該案例展示 Rust 在高性能系統中的實際優勢超越了傳統認知。"
key_points:
  - "Kotlin 到 Rust 遷移打破了對交付速度與工程開銷的內部預設，提升高性能服務開發效率"
  - "編譯時安全驗證縮短開發反饋迴圈，Rust 的 borrow checker 人體工程學改善開發體驗"
  - "使用 Criterion 與 flamegraphs 工具優化併發代碼路徑，量化性能收益"
tags: [rust-migration, performance-optimization, concurrent-programming, kotlin-to-rust, compile-time-safety]
topics: []
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Presentation: The Rust High Performance Talk You Did Not Expect

Ruth Linehan 介紹了從 Kotlin 遷移高性能緩存服務到 Rust 的案例，這次遷移出人意料地打破了團隊對交付速度和工程開銷的內部預設。她重點討論了 Rust borrow checker 的人體工程學改進、編譯時安全驗證如何縮短開發者反饋迴圈、以及如何運用 Criterion 和 flamegraphs 等高級分析工具來優化併發代碼路徑。該案例展示 Rust 在高性能系統中的實際優勢超越了傳統認知。

### 重點
- Kotlin 到 Rust 遷移打破了對交付速度與工程開銷的內部預設，提升高性能服務開發效率
- 編譯時安全驗證縮短開發反饋迴圈，Rust 的 borrow checker 人體工程學改善開發體驗
- 使用 Criterion 與 flamegraphs 工具優化併發代碼路徑，量化性能收益

**原文：** [infoq-main](https://www.infoq.com/presentations/rust-tps-service/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Ruth Linehan explains how migrating high-performance caching services from Kotlin to Rust shattered internal preconceptions around delivery velocity and engineering overhead. She discusses the ergonomics of the Rust borrow checker, shares how compile-time safety shortens the developer feedback loop, and profiles how tools like Criterion and flamegraphs optimize concurrent code paths. By Ruth Linehan

</details>