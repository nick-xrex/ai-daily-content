---
id: inbox_ffcbd828
date: 2026-05-21
source_ref: "[[00-inbox/2026-05-21/0917-medium-tag-claude-why-claude-costs-keep-rising-in-agent-wo-849a]]"
title: "Why Claude Costs Keep Rising in Agent Workflows (and How I Stopped the Hidden Token Leaks)"
url: https://medium.com/@aikeyfounder/why-claude-costs-keep-rising-in-agent-workflows-and-how-i-stopped-the-hidden-token-leaks-7358fd521fd7?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-05-21T08:04:02+00:00
fetched_at: 2026-05-21T09:28:21.962697+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude agent workflows 成本暴漲的隱藏源頭：非模型定價本身，而是重複調用（duplicate calls）、context 膨脹（context bloat）、retry 風暴（retry storms）三層耗損。作者分享識別與堵止這些隱漏的優化策略，直接降低 agent 生產成本。"
key_points:
  - "成本爆炸三大元兇：重複調用、上文膨脹、重試風暴"
  - "這些隱藏成本不在模型定價表上，藏在 agent 工作流程的架構缺陷裡"
  - "可通過工作流優化直接堵止，避免浪費 token 和運算資源"
tags: [claude, agent-workflows, cost-optimization, token-efficiency]
topics: [foundation_models.claude]
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Why Claude Costs Keep Rising in Agent Workflows (and How I Stopped the Hidden Token Leaks)

Claude agent workflows 成本暴漲的隱藏源頭：非模型定價本身，而是重複調用（duplicate calls）、context 膨脹（context bloat）、retry 風暴（retry storms）三層耗損。作者分享識別與堵止這些隱漏的優化策略，直接降低 agent 生產成本。

### 重點
- 成本爆炸三大元兇：重複調用、上文膨脹、重試風暴
- 這些隱藏成本不在模型定價表上，藏在 agent 工作流程的架構缺陷裡
- 可通過工作流優化直接堵止，避免浪費 token 和運算資源

**原文：** [medium-tag-claude](https://medium.com/@aikeyfounder/why-claude-costs-keep-rising-in-agent-workflows-and-how-i-stopped-the-hidden-token-leaks-7358fd521fd7?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Most cost spikes aren&#x2019;t caused by model pricing alone &#x2014; they come from duplicate calls, context bloat, and retry storms that quietly burn&#x2026; Continue reading on Medium »

</details>