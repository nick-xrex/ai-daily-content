---
id: inbox_ef4ef4b0
date: 2026-04-20
source_ref: "[[00-inbox/.../inbox_ef4ef4b0]]"
title: "Podcast: Engineering Stable, Secure and Scalable Platforms: A Conversation with Matthew Liste"
url: https://www.infoq.com/podcasts/engineering-stable-secure-scalable-platforms/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-04-20T11:00:00+00:00
fetched_at: 2026-04-22T02:34:34.561376+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Matthew Liste 討論平台工程的核心挑戰：穩定性、安全性與可擴展性。指出資源競爭（resource contention）是導致系統意外崩潰的隱藏主因，而這類故障在規模擴大時尤其難以預測與控制。強調平台服務作為應用開發基礎層的故障會級聯影響整個生態，因此穩定性必須優先於功能豐富度。安全性與可擴展性的平衡需要深思。"
key_points:
  - "資源競爭是平台系統故障的隱藏主因，常因不同應用的未知資源需求而觸發"
  - "平台服務的穩定性直接制約了應用層開發效率，故障成本指數級放大"
  - "規模化時平台架構設計需權衡安全隔離與資源利用率"
tags: [platform-engineering, system-reliability, resource-contention, scalability, cloud-native]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Podcast: Engineering Stable, Secure and Scalable Platforms: A Conversation with Matthew Liste

Matthew Liste 討論平台工程的核心挑戰：穩定性、安全性與可擴展性。指出資源競爭（resource contention）是導致系統意外崩潰的隱藏主因，而這類故障在規模擴大時尤其難以預測與控制。強調平台服務作為應用開發基礎層的故障會級聯影響整個生態，因此穩定性必須優先於功能豐富度。安全性與可擴展性的平衡需要深思。

### 重點
- 資源競爭是平台系統故障的隱藏主因，常因不同應用的未知資源需求而觸發
- 平台服務的穩定性直接制約了應用層開發效率，故障成本指數級放大
- 規模化時平台架構設計需權衡安全隔離與資源利用率

**原文：** [infoq-architecture](https://www.infoq.com/podcasts/engineering-stable-secure-scalable-platforms/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Podcast: Engineering Stable, Secure and Scalable Platforms: A Conversation with Matthew Liste

<img src="https://res.infoq.com/podcasts/engineering-stable-secure-scalable-platforms/en/smallimage/the-infoq-podcast-logo-thumbnail-1775134657783.jpg" /><p>In this podcast, Michael Stiefel spoke to Matthew Liste about building and managing software platforms. Platform services act as the basis for application development, and must always be stable, secure, and scalable. Scaling these systems is particularly difficult because unknown resource contention often causes them to break.</p> <i>By Matthew Liste</i>

</details>