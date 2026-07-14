---
id: inbox_edfed425
date: 2026-07-14
source_ref: "[[00-inbox/2026-07-14/0115-simon-willison-using-uvx-in-github-actions-in-a-cache-f-a07f]]"
title: "Using uvx in GitHub Actions in a cache-friendly way"
url: https://simonwillison.net/2026/Jul/14/uvx-github-actions-cache/#atom-everything
source: simon-willison
published_at: 2026-07-14T00:56:20+00:00
fetched_at: 2026-07-14T01:20:26.374272+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison分享在GitHub Actions中使用uvx的快取最佳化方案。關鍵技巧是設置UV_EXCLUDE_NEWER環境變數為固定日期（如\"2026-07-12\"），使uvx工具解析到該日期前的最新版本。此日期納入GitHub Actions快取key，實現版本綁定。每次workflow運行避免從PyPI下載新版本，顯著提升CI/CD效率。升級工具時僅需調整日期，無需改動workflow邏輯，降低維護複雜度。"
key_points:
  - "UV_EXCLUDE_NEWER環境變數設為固定日期，使版本解析確定性化、避免PyPI重複下載"
  - "將日期納入GitHub Actions快取key實現版本綁定，提升CI可預測性"
  - "升級工具時修改日期即可，無需改動workflow邏輯，簡化CI/CD維護"
tags: [uv, github-actions, caching, ci-cd, python-tooling]
topics: []
importance: 2
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Using uvx in GitHub Actions in a cache-friendly way

Simon Willison分享在GitHub Actions中使用uvx的快取最佳化方案。關鍵技巧是設置UV_EXCLUDE_NEWER環境變數為固定日期（如"2026-07-12"），使uvx工具解析到該日期前的最新版本。此日期納入GitHub Actions快取key，實現版本綁定。每次workflow運行避免從PyPI下載新版本，顯著提升CI/CD效率。升級工具時僅需調整日期，無需改動workflow邏輯，降低維護複雜度。

### 重點
- UV_EXCLUDE_NEWER環境變數設為固定日期，使版本解析確定性化、避免PyPI重複下載
- 將日期納入GitHub Actions快取key實現版本綁定，提升CI可預測性
- 升級工具時修改日期即可，無需改動workflow邏輯，簡化CI/CD維護

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/14/uvx-github-actions-cache/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

TIL: Using uvx in GitHub Actions in a cache-friendly way 
 I finally found a cache-friendly recipe for using uvx tool-name in GitHub Actions workflows that I like. 
 The trick is setting a UV_EXCLUDE_NEWER: "2026-07-12" environment variable at the start of the workflow and then using that as part of the GitHub Actions cache key. This means any uvx tool-name commands will resolve to the most recent version as-of that date, and you can bust the cache and upgrade the tools by bumping the date in the future. 
 My goal here is to use Python tools in GitHub Actions without every run of the workflow hitting PyPI to download a fresh copy of the tool and its dependencies. 
 
 
 Tags: packaging , pypi , python , github-actions , uv

</details>