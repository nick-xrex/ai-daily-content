---
id: inbox_06334cae
date: 2026-07-28
source_ref: "[[00-inbox/.../inbox_06334cae]]"
title: "dev-0.44.2-rc.344"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.44.2-rc.344
source: rtk-releases
published_at: 2026-07-28T17:36:54+00:00
fetched_at: 2026-07-29T03:36:50.948254+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK dev-0.44.2-rc.344 釋出，修復 tee 命令恢復提示路徑中的 escaped space 處理。恢復路徑現加以引號確保空格不被誤解。"
key_points:
  - "Tee 恢復提示路徑加引號，避免含空格的恢復路徑被分割解析"
tags: [rtk, rc-release, tee-command]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.44.2-rc.344

RTK dev-0.44.2-rc.344 釋出，修復 tee 命令恢復提示路徑中的 escaped space 處理。恢復路徑現加以引號確保空格不被誤解。

### 重點
- Tee 恢復提示路徑加引號，避免含空格的恢復路徑被分割解析

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.44.2-rc.344)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# dev-0.44.2-rc.344

Merge pull request #2325 from fengjikui/fix/escaped-space-tee-path 

 fix(tee): quote recovery hint paths with spaces

</details>