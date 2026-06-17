---
id: inbox_5f9dc7d2
date: 2026-06-17
source_ref: "[[00-inbox/2026-06-17/2200-superpowers-releases-v6-0-2-0cfb]]"
title: "v6.0.2"
url: https://github.com/obra/superpowers/releases/tag/v6.0.2
source: superpowers-releases
published_at: 2026-06-17T05:43:37+00:00
fetched_at: 2026-06-17T22:04:18.133670+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "superpowers v6.0.2 發布，解決外掛程式安裝相容性問題。移除了曾破壞使用者外掛程式安裝的 evals 子模組。eval 工具套件現已獨立遷移至單獨的存放庫，與發佈的外掛程式完全分離，改善了模組化設計。"
key_points:
  - "移除 evals 子模組，修復外掛程式安裝問題"
  - "eval 工具套件遷移至獨立存放庫"
  - "提升模組化與安裝相容性"
tags: [superpowers, bugfix, plugin-compatibility]
topics: []
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v6.0.2

superpowers v6.0.2 發布，解決外掛程式安裝相容性問題。移除了曾破壞使用者外掛程式安裝的 evals 子模組。eval 工具套件現已獨立遷移至單獨的存放庫，與發佈的外掛程式完全分離，改善了模組化設計。

### 重點
- 移除 evals 子模組，修復外掛程式安裝問題
- eval 工具套件遷移至獨立存放庫
- 提升模組化與安裝相容性

**原文：** [superpowers-releases](https://github.com/obra/superpowers/releases/tag/v6.0.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Install Fixes 
 
 We no longer ship the evals submodule. It broke plugin installs for some users, so the eval harness now lives in its own repo, separate from the published plugin. ( #1778 , #1774 )

</details>