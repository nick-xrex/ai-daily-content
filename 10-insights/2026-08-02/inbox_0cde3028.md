---
id: inbox_0cde3028
date: 2026-08-02
source_ref: "[[00-inbox/.../inbox_0cde3028]]"
title: "dev-0.44.3-rc.349"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.44.3-rc.349
source: rtk-releases
published_at: 2026-08-02T18:02:11+00:00
fetched_at: 2026-08-03T00:24:16.719322+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK dev-0.44.3-rc.349 發布，修正 Copilot hooks 防止其在未設定的命令上無聲地決定權限。此修正確保系統不會自動核准危險操作，須經明確授權，提升權限控制的安全性和透明度。"
key_points:
  - "RTK RC 版本修正：防止 Copilot 在未設定命令上無聲決定權限"
  - "確保危險操作需要明確授權決定"
  - "提升權限控制機制的安全性和可追蹤性"
tags: [rtk, copilot, permissions, security, authorization]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.44.3-rc.349

RTK dev-0.44.3-rc.349 發布，修正 Copilot hooks 防止其在未設定的命令上無聲地決定權限。此修正確保系統不會自動核准危險操作，須經明確授權，提升權限控制的安全性和透明度。

### 重點
- RTK RC 版本修正：防止 Copilot 在未設定命令上無聲決定權限
- 確保危險操作需要明確授權決定
- 提升權限控制機制的安全性和可追蹤性

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.44.3-rc.349)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# dev-0.44.3-rc.349

Merge pull request #3212 from rtk-ai/fix/copilot-parity-omit-permissi... 

 ...on-decision 

 fix(hooks): stop Copilot from silently deciding permission on unconfigured commands

</details>