---
id: inbox_40ca4cd6
date: 2026-06-26
source_ref: "[[00-inbox/.../inbox_40ca4cd6]]"
title: "dev-0.43.0-rc.292"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.292
source: rtk-releases
published_at: 2026-06-26T18:06:53+00:00
fetched_at: 2026-06-29T00:56:10.460608+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK dev-0.43.0-rc.292 重構了搜索功能的引擎執行策略。此前系統在執行搜索指令時，可能隱式地用 ripgrep (rg) 替代使用者指定的 grep 或其他搜索工具。經過此次重構（#2641），系統現在忠實地執行使用者明確選擇的搜索引擎，而不進行工具替代。此改進增強了可預測性和透明性，使搜索行為與使用者期望保持一致，避免了隱式替代導致的行為差異和潛在的意外結果。這對於依賴特定搜索工具行為的高級用戶尤為重要。"
key_points:
  - "搜索引擎執行策略重構：不再隱式用 ripgrep (rg) 替代用戶指定的工具"
  - "確保執行的搜索引擎與用戶選擇完全一致"
  - "提升搜索行為的可預測性和工具透明度"
tags: [rtk, search, refactor, engine-execution]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.43.0-rc.292

RTK dev-0.43.0-rc.292 重構了搜索功能的引擎執行策略。此前系統在執行搜索指令時，可能隱式地用 ripgrep (rg) 替代使用者指定的 grep 或其他搜索工具。經過此次重構（#2641），系統現在忠實地執行使用者明確選擇的搜索引擎，而不進行工具替代。此改進增強了可預測性和透明性，使搜索行為與使用者期望保持一致，避免了隱式替代導致的行為差異和潛在的意外結果。這對於依賴特定搜索工具行為的高級用戶尤為重要。

### 重點
- 搜索引擎執行策略重構：不再隱式用 ripgrep (rg) 替代用戶指定的工具
- 確保執行的搜索引擎與用戶選擇完全一致
- 提升搜索行為的可預測性和工具透明度

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.292)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# dev-0.43.0-rc.292

Merge pull request #2641 from rtk-ai/fix/grep-faithful-engine 

 refacto(search): run the invoked engine instead of substituting rg for grep

</details>