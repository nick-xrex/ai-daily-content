---
id: inbox_aac9db51
date: 2026-07-03
source_ref: "[[00-inbox/2026-07-03/0115-rtk-releases-dev-0-44-0-rc-308-d00d]]"
title: "dev-0.44.0-rc.308"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.44.0-rc.308
source: rtk-releases
published_at: 2026-07-03T14:57:46+00:00
fetched_at: 2026-07-04T01:22:28.301767+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK dev-0.44.0-rc.308 候選版本上線，新增 TOML filters 在 hook 中的整合功能，支持透過 TOML 配置進行條件過濾；同時改進 tee tail 提示信息的可用性。此為 RC 階段的漸進式功能引入。"
key_points:
  - "TOML filters 整合至 hook，支持配置驅動的過濾條件"
  - "改進 tee tail 提示，提升用戶體驗"
tags: [toml, hook, filtering]
topics: []
importance: 1
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.44.0-rc.308

RTK dev-0.44.0-rc.308 候選版本上線，新增 TOML filters 在 hook 中的整合功能，支持透過 TOML 配置進行條件過濾；同時改進 tee tail 提示信息的可用性。此為 RC 階段的漸進式功能引入。

### 重點
- TOML filters 整合至 hook，支持配置驅動的過濾條件
- 改進 tee tail 提示，提升用戶體驗

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.44.0-rc.308)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Merge pull request #2748 from rtk-ai/feat/toml-filters-in-hook 

 feat(hook): wire TOML filters + better tee tail hint

</details>