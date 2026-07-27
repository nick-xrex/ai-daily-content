---
id: inbox_bfeab01a
date: 2026-07-26
source_ref: "[[00-inbox/2026-07-26/0123-rtk-releases-dev-0-44-0-rc-332-d434]]"
title: "dev-0.44.0-rc.332"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.44.0-rc.332
source: rtk-releases
published_at: 2026-07-26T10:27:16+00:00
fetched_at: 2026-07-27T01:32:32.984226+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK dev-0.44.0-rc.332 修復了權限檢查邏輯中的空白字符逃逸問題。當使用者在權限配置中插入多餘空白時，系統原本無法識別這些空白並套用拒絕規則，允許不應通過的請求。本次修復確保空白字符無法繞過權限驗證。這是針對 Copilot CLI 等工具整合前的穩定性工作。"
key_points:
  - "修復權限驗證邏輯中的空白字符逃逸漏洞，確保拒絕規則在任何輸入格式下都能正確執行"
  - "防止使用者透過在配置中插入空白字符來規避安全政策"
  - "屬 rc.332 預發布版本，針對權限模組的細緻穩定工作"
tags: [rtk, permissions, security-fix, whitespace-handling]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.44.0-rc.332

RTK dev-0.44.0-rc.332 修復了權限檢查邏輯中的空白字符逃逸問題。當使用者在權限配置中插入多餘空白時，系統原本無法識別這些空白並套用拒絕規則，允許不應通過的請求。本次修復確保空白字符無法繞過權限驗證。這是針對 Copilot CLI 等工具整合前的穩定性工作。

### 重點
- 修復權限驗證邏輯中的空白字符逃逸漏洞，確保拒絕規則在任何輸入格式下都能正確執行
- 防止使用者透過在配置中插入空白字符來規避安全政策
- 屬 rc.332 預發布版本，針對權限模組的細緻穩定工作

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.44.0-rc.332)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Merge pull request #3211 from rtk-ai/fix/permission-whitespace-normal... 

 ...ization 

 fix(permissions): stop extra whitespace from evading deny rules

</details>