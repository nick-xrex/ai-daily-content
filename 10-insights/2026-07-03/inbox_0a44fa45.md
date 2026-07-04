---
id: inbox_0a44fa45
date: 2026-07-03
source_ref: "[[00-inbox/2026-07-03/0115-simon-willison-open-source-ai-gap-map-5cd3]]"
title: "Open Source AI Gap Map"
url: https://simonwillison.net/2026/Jul/3/open-source-ai-gap-map/#atom-everything
source: simon-willison
published_at: 2026-07-03T22:04:31+00:00
fetched_at: 2026-07-04T01:23:13.276260+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Current AI 非營利組織於今年 2 月成立（已獲 4 億美元資金承諾），發布首版開源 AI 生態地圖（Gap Map v0.1），涵蓋 421 個精深產品：266 個軟體工具、85 個模型、50 個資料集、20 個硬體項目，來自 228 個組織。地圖以 14 個類別跨 3 層堆疊（模型元件、產品/UX、基礎設施）組織，另有 24,400 個未分類的開源産品。所有數據（1,184 個 YAML 檔案）以 MIT 授權開放，可透過 Datasette Lite 探索追蹤的 16,185 個 GitHub 倉庫。"
key_points:
  - "Gap Map v0.1 索引 421 個深度產品（266 工具、85 模型、50 資料集、20 硬體），來自 228 組織"
  - "開源資料集含 1,184 YAML 檔案、完整 schema、研究筆記本，MIT 授權發布在 currentai-org/os-ai-map"
  - "追蹤 16,185 GitHub 倉庫，建立 14 分類跨 3 層堆疊的生態全景"
tags: [open-source-ai, gap-map, ecosystem-index, datasette, ai-infrastructure]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Open Source AI Gap Map

Current AI 非營利組織於今年 2 月成立（已獲 4 億美元資金承諾），發布首版開源 AI 生態地圖（Gap Map v0.1），涵蓋 421 個精深產品：266 個軟體工具、85 個模型、50 個資料集、20 個硬體項目，來自 228 個組織。地圖以 14 個類別跨 3 層堆疊（模型元件、產品/UX、基礎設施）組織，另有 24,400 個未分類的開源産品。所有數據（1,184 個 YAML 檔案）以 MIT 授權開放，可透過 Datasette Lite 探索追蹤的 16,185 個 GitHub 倉庫。

### 重點
- Gap Map v0.1 索引 421 個深度產品（266 工具、85 模型、50 資料集、20 硬體），來自 228 組織
- 開源資料集含 1,184 YAML 檔案、完整 schema、研究筆記本，MIT 授權發布在 currentai-org/os-ai-map
- 追蹤 16,185 GitHub 倉庫，建立 14 分類跨 3 層堆疊的生態全景

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/3/open-source-ai-gap-map/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Open Source AI Gap Map 
 Current AI is "a global partnership building a public option for AI", founded as a non-profit at the AI Action Summit in Paris in February 2025 and backed by serious capital ($400m already committed). 
 They launched their Gap Map a couple of days ago - an attempt at indexing the current state of open source AI: 
 
 The Gap Map v0.1 details 421 products in depth: 266 software tools and libraries, 85 models, 50 datasets, and 20 hardware projects, produced by 228 organizations. These products are organized into 14 categories across 3 layers of the stack (model components, product / UX, and infrastructure). The remaining 24,400 artifacts constitute the uncategorized long tail of the open source AI ecosystem, and will carry no score until they are researched and cited. 
 
 The map itself is interesting to explore, but I'm more excited about the underlying data - released under an MIT license in the currentai-org/os-ai-map GitHub account: 1,184 YAML files plus the notebooks, schemas and other scripts used to help gather them. 
 Since the files are on GitHub you can use Datasette Lite to explore some of them - here are 16,185 GitHub repos the project is tracking as a CSV file loaded into Datasette Lite.

 Tags: open-source , ai , datasette-lite , generative-ai , local-llms , llms

</details>