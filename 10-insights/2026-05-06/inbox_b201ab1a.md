---
id: inbox_b201ab1a
date: 2026-05-06
source_ref: "[[00-inbox/2026-05-06/1001-codex-releases-rusty-v8-v147-4-0-c5f3]]"
title: "rusty-v8-v147.4.0"
url: https://github.com/openai/codex/releases/tag/rusty-v8-v147.4.0
source: codex-releases
published_at: 2026-05-06T02:16:45+00:00
fetched_at: 2026-05-06T10:06:04.964944+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "rusty-v8 v147.4.0 發布，更新內容為 CI 配置調整：使 rusty_v8 staging 環境選用 host llvm tools。此為基礎設施級別的依賴版本更新，與 OpenAI Codex 開發工具鏈的構建流程最佳化相關，用戶層面無直接感知。"
key_points:
  - "rusty-v8（Rust 綁定 V8 JavaScript 引擎）版本更新至 v147.4.0"
  - "CI/構建流程優化：採用 host llvm tools 而非其他工具鏈，可能改進編譯速度或相容性"
  - "基礎設施維護，最終用戶無感知的依賴更新"
tags: [build-tools, ci, infrastructure]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## rusty-v8-v147.4.0

rusty-v8 v147.4.0 發布，更新內容為 CI 配置調整：使 rusty_v8 staging 環境選用 host llvm tools。此為基礎設施級別的依賴版本更新，與 OpenAI Codex 開發工具鏈的構建流程最佳化相關，用戶層面無直接感知。

### 重點
- rusty-v8（Rust 綁定 V8 JavaScript 引擎）版本更新至 v147.4.0
- CI/構建流程優化：採用 host llvm tools 而非其他工具鏈，可能改進編譯速度或相容性
- 基礎設施維護，最終用戶無感知的依賴更新

**原文：** [codex-releases](https://github.com/openai/codex/releases/tag/rusty-v8-v147.4.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<p>ci: make rusty_v8 staging select host llvm tools</p>

<p>Co-authored-by: Codex &lt;noreply@openai.com&gt;</p>

</details>