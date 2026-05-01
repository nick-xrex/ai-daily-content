---
id: inbox_faaef963
date: 2026-04-30
source_ref: "[[00-inbox/2026-04-30/1257-infoq-main-nestjs-v12-roadmap-full-esm-migration-st-354a]]"
title: "NestJS v12 Roadmap: Full ESM Migration, Standard Schema Validation and Modernised Toolchain"
url: https://www.infoq.com/news/2026/04/nestjs-12-roadmap-esm/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-04-30T16:00:00+00:00
fetched_at: 2026-05-01T13:07:00.955164+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "NestJS 發佈了其 v12.0.0 版本的路線圖，計劃於 2026 年 Q3 初期發布。該版本涵蓋三個主要升級方向。首先，框架計劃完全遷移從 CommonJS 至 ES Module（ESM），統一模組系統。其次，route decorators 將原生支持 Standard Schema 驗證規範，簡化請求數據驗證的配置。第三，NestJS 將全面更新開發工具鏈：用 Vitest（更快的單元測試框架）取代 Jest，用 oxlint（基於 Rust 的快速 linter）取代 ESLint，用 Rspack（Webpack 的高性能 Rust 實現）取代 Webpack 進行打包。這次全棧現代化旨在提升開發效率和框架性能。"
key_points:
  - "完整的 CommonJS to ESM 遷移，統一模組系統標準（計劃 Q3 2026 初期完成）"
  - "Route decorators 原生支持 Standard Schema 驗證，簡化數據驗證配置邏輯"
  - "工具鏈全面更新：Jest→Vitest、ESLint→oxlint（Rust 實現）、Webpack→Rspack（性能提升）"
tags: [nestjs, esm-migration, typescript, bundling, testing-tools]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## NestJS v12 Roadmap: Full ESM Migration, Standard Schema Validation and Modernised Toolchain

NestJS 發佈了其 v12.0.0 版本的路線圖，計劃於 2026 年 Q3 初期發布。該版本涵蓋三個主要升級方向。首先，框架計劃完全遷移從 CommonJS 至 ES Module（ESM），統一模組系統。其次，route decorators 將原生支持 Standard Schema 驗證規範，簡化請求數據驗證的配置。第三，NestJS 將全面更新開發工具鏈：用 Vitest（更快的單元測試框架）取代 Jest，用 oxlint（基於 Rust 的快速 linter）取代 ESLint，用 Rspack（Webpack 的高性能 Rust 實現）取代 Webpack 進行打包。這次全棧現代化旨在提升開發效率和框架性能。

### 重點
- 完整的 CommonJS to ESM 遷移，統一模組系統標準（計劃 Q3 2026 初期完成）
- Route decorators 原生支持 Standard Schema 驗證，簡化數據驗證配置邏輯
- 工具鏈全面更新：Jest→Vitest、ESLint→oxlint（Rust 實現）、Webpack→Rspack（性能提升）

**原文：** [infoq-main](https://www.infoq.com/news/2026/04/nestjs-12-roadmap-esm/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<img src="https://res.infoq.com/news/2026/04/nestjs-12-roadmap-esm/en/headerimage/generatedHeaderImage-1777478248947.jpg" /><p>NestJS has announced a draft pull request for its upcoming v12.0.0 release, scheduled for early Q3 2026. Key changes include a transition from CommonJS to ESM, native Standard Schema support in route decorators, and shifts in testing and linting tools. Vitest will replace Jest, and oxlint will replace ESLint, while Rspack will replace Webpack for bundling.</p> <i>By Daniel Curtis</i>

</details>