---
id: inbox_d04084ba
date: 2026-07-08
source_ref: "[[00-inbox/.../inbox_d04084ba]]"
title: "What a harness is and how to build one with Claude Agent SDK"
url: https://www.lennysnewsletter.com/p/what-a-harness-is-and-how-to-build
source: substack-lennys-newsletter
published_at: 2026-07-08T12:03:35+00:00
fetched_at: 2026-07-10T01:06:52.328652+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Lenny's Newsletter 介紹了如何使用 Anthropic Claude Agent SDK 構建自訂 harness，來自動化軟體開發中的重複性任務。作者實現了一個具體案例：用 harness 自動化 Sentry 錯誤平台的 bug 分類流程，完全避免了每次都編寫「親愛的 Agent，請修復這個」式樣提示詞的繁瑣工作。Harness 是一種 Claude Agent 架構模式，允許開發者定義可復用的自動化工作流，而不是每次都從零開始編寫提示。這個模式特別適合企業環境中的規模化自動化需求，能顯著減少人工干預和提示工程的成本。文章提供了實際的構建步驟和代碼示例，讀者可直接應用於自己的自動化場景。"
key_points:
  - "Claude Agent SDK harness 自動化了 Sentry bug 分類流程，消除了重複性的『親愛的 Agent，請修復』提示詞工程工作"
  - "Harness 是可復用的 Claude Agent 架構模式，相比每次臨時編寫提示詞，顯著降低自動化成本和人工干預"
  - "案例包含實際構建步驟和代碼示例，可直接應用於其他企業自動化場景（Sentry、issue triage、log analysis）"
tags: [claude-agent-sdk, automation, sentry, bug-triage, harness-pattern]
topics: [foundation_models.claude, agents.mcp]
importance: 4
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## What a harness is and how to build one with Claude Agent SDK

Lenny's Newsletter 介紹了如何使用 Anthropic Claude Agent SDK 構建自訂 harness，來自動化軟體開發中的重複性任務。作者實現了一個具體案例：用 harness 自動化 Sentry 錯誤平台的 bug 分類流程，完全避免了每次都編寫「親愛的 Agent，請修復這個」式樣提示詞的繁瑣工作。Harness 是一種 Claude Agent 架構模式，允許開發者定義可復用的自動化工作流，而不是每次都從零開始編寫提示。這個模式特別適合企業環境中的規模化自動化需求，能顯著減少人工干預和提示工程的成本。文章提供了實際的構建步驟和代碼示例，讀者可直接應用於自己的自動化場景。

### 重點
- Claude Agent SDK harness 自動化了 Sentry bug 分類流程，消除了重複性的『親愛的 Agent，請修復』提示詞工程工作
- Harness 是可復用的 Claude Agent 架構模式，相比每次臨時編寫提示詞，顯著降低自動化成本和人工干預
- 案例包含實際構建步驟和代碼示例，可直接應用於其他企業自動化場景（Sentry、issue triage、log analysis）

**原文：** [substack-lennys-newsletter](https://www.lennysnewsletter.com/p/what-a-harness-is-and-how-to-build)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# What a harness is and how to build one with Claude Agent SDK

Listen now | &#127897;&#65039; I built a custom Claude Agent SDK harness to automate Sentry bug triage, saved the "dear agent, please fix this" prompt forever, and show you exactly how to build your own

</details>