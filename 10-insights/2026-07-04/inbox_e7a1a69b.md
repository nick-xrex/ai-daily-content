---
id: inbox_e7a1a69b
date: 2026-07-04
source_ref: "[[00-inbox/2026-07-04/2200-ruflo-releases-v3-21-1-memory-search-recall-init-self-l-11d4]]"
title: "v3.21.1 — memory search recall + init self-learning fixes"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.21.1
source: ruflo-releases
published_at: 2026-07-04T15:06:45+00:00
fetched_at: 2026-07-04T22:05:43.759741+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RuFlo v3.21.1 修復兩個回歸問題，恢復記憶搜尋和自學習初始化功能。#2558：記憶搜尋故障根因為 Phase-2 BM25 融合無聲移除覆蓋率下限（IDF 坍縮導致查詢詞所在文件評分低於閾值）且 WAL 寫入未檢查點；修復包含覆蓋率重校、友善回召融合、儲存時 wal_checkpoint 及精準向量計數，169/169 記憶測試全過。#2545：npx ruflo init 自學習失效根因為 @claude-flow/memory 落在 npx 快取而非專案 node_modules；修復透過 .claude-flow/memory-package.json 側車檔案追蹤已解析路徑，hook 優先讀取並在缺失時大聲失敗，doctor --fix 可自動修復。"
key_points:
  - "修復 #2558：BM25 覆蓋率下限、WAL checkpoint、融合策略，使搜尋真正回召已儲存項目"
  - "修復 #2545：optionalDependency 解析問題，引入 .claude-flow/memory-package.json 側車檔案，失敗明確化"
  - "完全向後相容，169/169 記憶測試套件通過"
tags: [bug-fix, memory-search, wal-checkpoint, dependency-resolution]
topics: []
importance: 2
novelty: 1
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.21.1 — memory search recall + init self-learning fixes

RuFlo v3.21.1 修復兩個回歸問題，恢復記憶搜尋和自學習初始化功能。#2558：記憶搜尋故障根因為 Phase-2 BM25 融合無聲移除覆蓋率下限（IDF 坍縮導致查詢詞所在文件評分低於閾值）且 WAL 寫入未檢查點；修復包含覆蓋率重校、友善回召融合、儲存時 wal_checkpoint 及精準向量計數，169/169 記憶測試全過。#2545：npx ruflo init 自學習失效根因為 @claude-flow/memory 落在 npx 快取而非專案 node_modules；修復透過 .claude-flow/memory-package.json 側車檔案追蹤已解析路徑，hook 優先讀取並在缺失時大聲失敗，doctor --fix 可自動修復。

### 重點
- 修復 #2558：BM25 覆蓋率下限、WAL checkpoint、融合策略，使搜尋真正回召已儲存項目
- 修復 #2545：optionalDependency 解析問題，引入 .claude-flow/memory-package.json 側車檔案，失敗明確化
- 完全向後相容，169/169 記憶測試套件通過

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.21.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Two external-reported regression fixes. 
 Fixed 
 
 #2558 — memory search broken (keyword recall random, HNSW index 0 vectors). Two defects: the Phase-2 BM25 fusion silently dropped the keyword-coverage floor (IDF collapses on small corpora → docs containing the query word scored below threshold), and WAL-mode writes were never checkpointed so WAL-blind readers saw 0 vectors. Fix: coverage floor + recall-friendly fusion + wal_checkpoint on store + accurate total_vectors . Search now recalls confirmed-stored entries (targeted, not a dump). 169/169 memory suite. 
 #2545 — npx ruflo init left self-learning a silent no-op. @claude-flow/memory (optionalDependency) lands in the npx cache, off the project's node_modules walk-up, so the auto-memory hook never resolved it. Fix: init records the resolved path in a .claude-flow/memory-package.json sidecar; hook reads it first and now fails LOUD when memory is genuinely absent; doctor --fix repairs it. 
 
 PRs: #2567 , #2564

</details>