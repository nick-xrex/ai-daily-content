---
id: inbox_a49cdc73
date: 2026-06-14
source_ref: "[[00-inbox/2026-06-14/2200-rtk-releases-dev-0-43-0-rc-276-5b38]]"
title: "dev-0.43.0-rc.276"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.276
source: rtk-releases
published_at: 2026-06-14T16:30:06+00:00
fetched_at: 2026-06-14T22:04:37.211682+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK dev-0.43.0-rc.276 發布，修復 grep 引數解析穩定性（#2333）。包含：trailing_var_arg 處理、-v invert-match 支持、--version 傳遞、safe rg 調用等改進。此版本詳細變更說明有限，主要涉及命令行工具內部最佳化。"
key_points:
  - "修復 trailing_var_arg 邊界情況"
  - "支援 -v invert-match 倒序匹配"
  - "改進 rg 調用安全性"
tags: [grep, argument-parsing, cli]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.43.0-rc.276

RTK dev-0.43.0-rc.276 發布，修復 grep 引數解析穩定性（#2333）。包含：trailing_var_arg 處理、-v invert-match 支持、--version 傳遞、safe rg 調用等改進。此版本詳細變更說明有限，主要涉及命令行工具內部最佳化。

### 重點
- 修復 trailing_var_arg 邊界情況
- 支援 -v invert-match 倒序匹配
- 改進 rg 調用安全性

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.43.0-rc.276)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Merge pull request #2333 from KuSh/grep_arg_parsing 

 fix(grep): stabilize argument parsing — trailing_var_arg, -v invert-match, --version passthrough, safe rg invocation

</details>