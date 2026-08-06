---
id: inbox_63d250bd
date: 2026-08-05
source_ref: "[[00-inbox/.../inbox_63d250bd]]"
title: "Build an AI code review bot in 30 minutes with Vercel Eve"
url: https://www.lennysnewsletter.com/p/build-an-ai-code-review-bot-in-30
source: substack-lennys-newsletter
published_at: 2026-08-05T12:04:01+00:00
fetched_at: 2026-08-06T00:32:48.094689+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者用 Vercel Eve agents 和 Codex 在 30 分鐘內構建了 Merge Mommy ─ 一個自動化 PR 審查機器人。該機器人具備三項核心功能：評估 PR 風險等級、自動批准低風險變更、對高風險變更發送 Slack 通知。此案例展示了如何快速組合現代 AI agent 框架與程式碼模型，實現 code review 流程自動化，並透過分層設計最小化人工審查工作量。

```mermaid
flowchart LR
    A[\"PR 提交\"] --> B[\"Vercel Eve + Codex 評估\"]
    B --> C[\"風險評分\"]
    C --> D{風險等級}
    D -->|低| E[\"自動批准\"]
    D -->|高| F[\"Slack 通知\"]
    E --> G[\"完成\"]
    F --> G
```"
key_points:
  - "Vercel Eve agents + Codex 30 分鐘完成 PR 審查機器人 Merge Mommy 構建"
  - "三層功能：風險評分、自動批准低風險變更、Slack 異常通知"
  - "分層設計分離機械性判斷與人工判斷，最小化 code review 人力投入"
tags: [vercel-eve, codex, pr-review-bot, agent-application, automation]
topics: []
importance: 3
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Build an AI code review bot in 30 minutes with Vercel Eve

作者用 Vercel Eve agents 和 Codex 在 30 分鐘內構建了 Merge Mommy ─ 一個自動化 PR 審查機器人。該機器人具備三項核心功能：評估 PR 風險等級、自動批准低風險變更、對高風險變更發送 Slack 通知。此案例展示了如何快速組合現代 AI agent 框架與程式碼模型，實現 code review 流程自動化，並透過分層設計最小化人工審查工作量。

```mermaid
flowchart LR
    A["PR 提交"] --> B["Vercel Eve + Codex 評估"]
    B --> C["風險評分"]
    C --> D{風險等級}
    D -->|低| E["自動批准"]
    D -->|高| F["Slack 通知"]
    E --> G["完成"]
    F --> G
```

### 重點
- Vercel Eve agents + Codex 30 分鐘完成 PR 審查機器人 Merge Mommy 構建
- 三層功能：風險評分、自動批准低風險變更、Slack 異常通知
- 分層設計分離機械性判斷與人工判斷，最小化 code review 人力投入

**原文：** [substack-lennys-newsletter](https://www.lennysnewsletter.com/p/build-an-ai-code-review-bot-in-30)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Build an AI code review bot in 30 minutes with Vercel Eve

Watch now | &#127897;&#65039; I used Vercel Eve agents and Codex to build Merge Mommy: a PR review bot that scores risk, auto-approves the easy ones, and pings me in Slack for the rest

</details>