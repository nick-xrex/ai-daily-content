---
id: inbox_45d06e3e
date: 2026-05-22
source_ref: "[[00-inbox/2026-05-22/1801-simon-willison-pydantic-monty-investigation-f91f]]"
title: "pydantic-monty investigation"
url: https://simonwillison.net/2026/May/22/monty-investigation/#atom-everything
source: simon-willison
published_at: 2026-05-22T22:41:00+00:00
fetched_at: 2026-05-31T18:09:32.580567+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 使用 Claude Code 調查 Pydantic 最新發布的 Monty（用 Rust 實現的 Python 沙盒子集）。驗證了核心安全機制的有效性，包括 max_duration_secs、max_memory、max_allocations 和 max_recursion_depth 等四項資源限制都按預期正常運作。此調查確認該沙盒環境的約束機制可信，為企業使用 Monty 執行不信任代碼提供了技術保障。"
key_points:
  - "Monty：Pydantic 用 Rust 實現的安全 Python 子集沙盒"
  - "驗證四項核心限制：時間上限（max_duration_secs）、記憶體（max_memory）、分配次數（max_allocations）、遞迴深度（max_recursion_depth）都有效"
  - "Claude Code 可用於代碼安全性審核和約束機制驗證"
tags: [pydantic, monty, sandboxing, rust, security]
topics: []
importance: 2
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## pydantic-monty investigation

Simon Willison 使用 Claude Code 調查 Pydantic 最新發布的 Monty（用 Rust 實現的 Python 沙盒子集）。驗證了核心安全機制的有效性，包括 max_duration_secs、max_memory、max_allocations 和 max_recursion_depth 等四項資源限制都按預期正常運作。此調查確認該沙盒環境的約束機制可信，為企業使用 Monty 執行不信任代碼提供了技術保障。

### 重點
- Monty：Pydantic 用 Rust 實現的安全 Python 子集沙盒
- 驗證四項核心限制：時間上限（max_duration_secs）、記憶體（max_memory）、分配次數（max_allocations）、遞迴深度（max_recursion_depth）都有效
- Claude Code 可用於代碼安全性審核和約束機制驗證

**原文：** [simon-willison](https://simonwillison.net/2026/May/22/monty-investigation/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Research: pydantic-monty investigation 
 It's been a few months since I last poked at Monty , the sandboxed subset of Python implemented in Rust. I had Claude Code look at the most recent release. 
 Importantly the max_duration_secs , max_memory , max_allocations , and max_recursion_depth settings all appear to work as advertised. 
 
 
 Tags: python , sandboxing , pydantic

</details>