---
id: inbox_bd7cb4d2
date: 2026-08-01
source_ref: "[[00-inbox/.../inbox_bd7cb4d2]]"
title: "v0.44.2"
url: https://github.com/rtk-ai/rtk/releases/tag/v0.44.2
source: rtk-releases
published_at: 2026-08-01T16:53:01+00:00
fetched_at: 2026-08-02T03:39:09.750830+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK v0.44.2 發布，主要聚焦安全性改進。三大修復：(1) 將歷史數據庫、tee 日誌、審計日誌設為 owner-only 訪問權限；(2) 強化已存在的數據目錄權限；(3) 修正 tee 日誌路徑包含空格時的引號恢復提示。這些修復直接提升文件系統安全隔離，防止未授權訪問。"
key_points:
  - "歷史數據庫、tee 日誌、審計日誌改為 owner-only 權限"
  - "強化已存在數據目錄的權限設置"
  - "修正帶空格路徑的引號恢復機制"
tags: [rtk, security, bug-fix, access-control]
topics: []
importance: 3
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v0.44.2

RTK v0.44.2 發布，主要聚焦安全性改進。三大修復：(1) 將歷史數據庫、tee 日誌、審計日誌設為 owner-only 訪問權限；(2) 強化已存在的數據目錄權限；(3) 修正 tee 日誌路徑包含空格時的引號恢復提示。這些修復直接提升文件系統安全隔離，防止未授權訪問。

### 重點
- 歷史數據庫、tee 日誌、審計日誌改為 owner-only 權限
- 強化已存在數據目錄的權限設置
- 修正帶空格路徑的引號恢復機制

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/v0.44.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v0.44.2

0.44.2 (2026-08-01) 
 Bug Fixes 
 
 security: store history db, tee logs and audit log owner-only ( 57b7900 ) 
 security: tighten data dirs that already exist ( 18925c2 ) 
 tee: quote recovery hint paths with spaces ( 8a24ce2 )

</details>