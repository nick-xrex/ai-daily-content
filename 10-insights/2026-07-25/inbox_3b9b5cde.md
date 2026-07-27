---
id: inbox_3b9b5cde
date: 2026-07-25
source_ref: "[[00-inbox/2026-07-25/0123-rtk-releases-dev-0-44-0-rc-331-e9e4]]"
title: "dev-0.44.0-rc.331"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-0.44.0-rc.331
source: rtk-releases
published_at: 2026-07-25T13:40:21+00:00
fetched_at: 2026-07-27T01:32:33.008420+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK dev-0.44.0-rc.331 修復了 hooks 層的權限決策發射機制。修復使得 permissionDecision 能正確發出 allow 信號，支援 Copilot CLI 的簡化重寫流程。此舉減少了 Copilot 與 RTK 整合的複雜度。"
key_points:
  - "修復 permissionDecision hooks 正確發出 allow 決策，支援簡化 Copilot CLI 重寫"
  - "降低 Copilot 與 RTK 整合的複雜度，加快許可決策流程"
  - "涉及 hooks 層架構，屬核心決策機制改進"
tags: [rtk, hooks, copilot-cli, permission-decision]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-0.44.0-rc.331

RTK dev-0.44.0-rc.331 修復了 hooks 層的權限決策發射機制。修復使得 permissionDecision 能正確發出 allow 信號，支援 Copilot CLI 的簡化重寫流程。此舉減少了 Copilot 與 RTK 整合的複雜度。

### 重點
- 修復 permissionDecision hooks 正確發出 allow 決策，支援簡化 Copilot CLI 重寫
- 降低 Copilot 與 RTK 整合的複雜度，加快許可決策流程
- 涉及 hooks 層架構，屬核心決策機制改進

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-0.44.0-rc.331)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Merge pull request #3149 from guyoron1/fix/copilot-permission-decision 

 fix(hooks): emit permissionDecision allow for simple Copilot CLI rewrites

</details>