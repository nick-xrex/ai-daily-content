---
id: inbox_5d102c7e
date: 2026-07-23
source_ref: "[[00-inbox/2026-07-23/0148-rtk-releases-dev-0-44-0-rc-327-3009]]"
title: "dev-0.44.0-rc.327"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.44.0-rc.327
source: rtk-releases
published_at: 2026-07-23T11:23:24+00:00
fetched_at: 2026-07-24T02:00:47.941175+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK 發佈開發版 dev-0.44.0-rc.327。此版本的核心改進是修復了 benchmark 測試套件中 curl 和 wget 命令的確定性問題（PR #3170）。在進行效能評估時，外部工具的非確定性回應可能導致測試結果不一致，影響基準測試的可比較性。此修復通過使用預定義的確定性回應確保每次 benchmark 運行都能產生一致的結果。這對於追蹤版本之間的效能變化、驗證最佳化效果至關重要。穩定的 benchmark 環境是評估系統改進的基礎。"
key_points:
  - "修復 benchmark 中 curl/wget 回應的確定性問題（PR #3170）"
  - "確保評估結果的可重複性，避免外部工具的非確定性行為影響測試結論"
tags: [rtk-releases, benchmark, bug-fix]
topics: []
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.44.0-rc.327

RTK 發佈開發版 dev-0.44.0-rc.327。此版本的核心改進是修復了 benchmark 測試套件中 curl 和 wget 命令的確定性問題（PR #3170）。在進行效能評估時，外部工具的非確定性回應可能導致測試結果不一致，影響基準測試的可比較性。此修復通過使用預定義的確定性回應確保每次 benchmark 運行都能產生一致的結果。這對於追蹤版本之間的效能變化、驗證最佳化效果至關重要。穩定的 benchmark 環境是評估系統改進的基礎。

### 重點
- 修復 benchmark 中 curl/wget 回應的確定性問題（PR #3170）
- 確保評估結果的可重複性，避免外部工具的非確定性行為影響測試結論

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.44.0-rc.327)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Merge pull request #3170 from TaKO8Ki/fix/deterministic-network-bench... 

 ...marks 

 fix(benchmark): use deterministic curl and wget responses

</details>