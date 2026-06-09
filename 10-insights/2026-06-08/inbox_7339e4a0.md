---
id: inbox_7339e4a0
date: 2026-06-08
source_ref: "[[00-inbox/2026-06-08/1800-rtk-releases-dev-0-43-0-rc-271-bd26]]"
title: "dev-0.43.0-rc.271"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.271
source: rtk-releases
published_at: 2026-06-08T11:47:52+00:00
fetched_at: 2026-06-08T18:09:47.566344+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK 專案於 2026 年 6 月 8 日發布 dev-0.43.0-rc.271 候選版本。本版本主要變更來自 PR #1956，由開發者 vdufloth 提交。核心改進為以 Rust module 替換原有的 TOML filter，使配置處理更加高效。同時新增了 test phase 支持，進一步完善構建流程。此次為 breaking change，升級時可能需要調整配置。"
key_points:
  - "Rust module 替換 TOML filter，改進配置處理方式"
  - "新增 test phase 支持，完善構建流程"
  - "dev-0.43.0-rc.271 候選版本發布"
tags: [rust, maven, build-tools, version-release]
topics: []
importance: 2
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.43.0-rc.271

RTK 專案於 2026 年 6 月 8 日發布 dev-0.43.0-rc.271 候選版本。本版本主要變更來自 PR #1956，由開發者 vdufloth 提交。核心改進為以 Rust module 替換原有的 TOML filter，使配置處理更加高效。同時新增了 test phase 支持，進一步完善構建流程。此次為 breaking change，升級時可能需要調整配置。

### 重點
- Rust module 替換 TOML filter，改進配置處理方式
- 新增 test phase 支持，完善構建流程
- dev-0.43.0-rc.271 候選版本發布

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.271)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Merge pull request #1956 from vdufloth/feat/mvn-rust-module 

 feat(mvn)!: Rust module replacing TOML filter, adds test phase support

</details>