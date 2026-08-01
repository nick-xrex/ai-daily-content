---
id: inbox_7c6610ac
date: 2026-08-01
source_ref: "[[00-inbox/2026-08-01/0615-medium-tag-claude-anyone-with-the-link-can-view-what-the-c-835b]]"
title: "“Anyone With the Link Can View”: What the Claude Search Leak Taught Us About Building Aisty"
url: https://medium.com/@joehoward0110/anyone-with-the-link-can-view-what-the-claude-search-leak-taught-us-about-building-aisty-7c96f520eb7a?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-08-01T04:46:17+00:00
fetched_at: 2026-08-01T06:23:26.413539+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "分析了 Claude Search 发生的一起权限泄漏事件——仅因为 URL 被共享，任何人就能访问敏感数据，本不应该这样。看似不起眼的警告标签最终成为重大安全事故。作者从中提取教训，讨论在构建 AI 应用（如 Aisty）时应如何避免类似权限控制缺陷，强调安全设计中看似微小的 UI 元素也可能导致灾难级后果。"
key_points:
  - "Claude Search 权限泄漏：仅通过链接分享即可绕过访问控制"
  - "设计缺陷：不起眼的警告标签无法有效阻止非授权访问"
  - "教训：AI 应用需要默认拒绝（deny-by-default）的权限架构"
tags: [claude-security, access-control, privacy-leak, ui-security]
topics: [foundation_models.claude]
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## “Anyone With the Link Can View”: What the Claude Search Leak Taught Us About Building Aisty

分析了 Claude Search 发生的一起权限泄漏事件——仅因为 URL 被共享，任何人就能访问敏感数据，本不应该这样。看似不起眼的警告标签最终成为重大安全事故。作者从中提取教训，讨论在构建 AI 应用（如 Aisty）时应如何避免类似权限控制缺陷，强调安全设计中看似微小的 UI 元素也可能导致灾难级后果。

### 重點
- Claude Search 权限泄漏：仅通过链接分享即可绕过访问控制
- 设计缺陷：不起眼的警告标签无法有效阻止非授权访问
- 教训：AI 应用需要默认拒绝（deny-by-default）的权限架构

**原文：** [medium-tag-claude](https://medium.com/@joehoward0110/anyone-with-the-link-can-view-what-the-claude-search-leak-taught-us-about-building-aisty-7c96f520eb7a?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

A quiet warning label just became the story of the wee, and it&#x2019;s worth sitting with. Continue reading on Medium »

</details>