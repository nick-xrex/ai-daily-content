---
id: inbox_0c83ead4
date: 2026-04-22
source_ref: "[[00-inbox/2026-04-22/0248-hackernews-github-cli-now-collects-pseudoanonymous-b1c3]]"
title: "GitHub CLI now collects pseudoanonymous telemetry"
url: https://cli.github.com/telemetry
source: hackernews
published_at: 2026-04-22T11:58:58+00:00
fetched_at: 2026-04-24T03:14:44.705054+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitHub CLI 現已預設啟用偽匿名遙測資料蒐集，追蹤使用者命令執行頻率、錯誤發生率、流量模式等，但不收集代碼內容或認證令牌。用戶可透過設定環境變數 GH_NO_TELEMETRY=1 或修改設定檔禁用遙測。該變更反映開源工具商業化後普遍採納數據驅動改進的趨勢。對依賴 GitHub CLI 的開發團隊、企業安全政策制定，和開發環境配置有實踐意義。"
key_points:
  - "GitHub CLI 新增偽匿名遙測，可用環境變數 GH_NO_TELEMETRY=1 關閉"
  - "遙測追蹤命令執行和錯誤頻率，但排除代碼和認證資料"
  - "企業用戶需更新安全基線配置；反映開源工具的商業化數據驅動趨勢"
tags: [github-cli, telemetry, privacy, developer-tools, data-collection]
topics: []
importance: 3
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## GitHub CLI now collects pseudoanonymous telemetry

GitHub CLI 現已預設啟用偽匿名遙測資料蒐集，追蹤使用者命令執行頻率、錯誤發生率、流量模式等，但不收集代碼內容或認證令牌。用戶可透過設定環境變數 GH_NO_TELEMETRY=1 或修改設定檔禁用遙測。該變更反映開源工具商業化後普遍採納數據驅動改進的趨勢。對依賴 GitHub CLI 的開發團隊、企業安全政策制定，和開發環境配置有實踐意義。

### 重點
- GitHub CLI 新增偽匿名遙測，可用環境變數 GH_NO_TELEMETRY=1 關閉
- 遙測追蹤命令執行和錯誤頻率，但排除代碼和認證資料
- 企業用戶需更新安全基線配置；反映開源工具的商業化數據驅動趨勢

**原文：** [hackernews](https://cli.github.com/telemetry)