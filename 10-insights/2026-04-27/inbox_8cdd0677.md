---
id: inbox_8cdd0677
date: 2026-04-27
source_ref: "[[00-inbox/2026-04-27/0248-infoq-architecture-uber-migrates-75-000-test-classes-from-j-0eee]]"
title: "Uber Migrates 75,000+ Test Classes from Junit 4 to Junit 5 Using Automated Code Transformation"
url: https://www.infoq.com/news/2026/04/uber-junit4-junit5-migration/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-04-27T14:07:00+00:00
fetched_at: 2026-04-28T02:58:05.608133+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Uber 工程團隊利用 OpenRewrite 與內部編排工具，自動化遷移超過 75,000 個測試類別，從 JUnit 4 升級至 JUnit 5。團隊透過啟用 JUnit Platform 並與 Bazel 配合進行雙執行模式，經由持續整合驗證所有變更，在單一 monorepo 規模下完成現代化同時維持測試正確性。此案例展示大規模技術債清償的可行自動化策略。注：本項目非 AI 相關內容。"
key_points:
  - "規模：遷移 75,000+ 測試類別，使用 OpenRewrite 自動程式碼轉換"
  - "執行策略：JUnit Platform + Bazel 雙執行模式，CI 全程驗證"
  - "關鍵成果：Monorepo 規模下同時保證測試正確性與基礎設施現代化"
tags: [junit5-migration, code-automation, testing-infrastructure, bazel]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Uber Migrates 75,000+ Test Classes from Junit 4 to Junit 5 Using Automated Code Transformation

Uber 工程團隊利用 OpenRewrite 與內部編排工具，自動化遷移超過 75,000 個測試類別，從 JUnit 4 升級至 JUnit 5。團隊透過啟用 JUnit Platform 並與 Bazel 配合進行雙執行模式，經由持續整合驗證所有變更，在單一 monorepo 規模下完成現代化同時維持測試正確性。此案例展示大規模技術債清償的可行自動化策略。注：本項目非 AI 相關內容。

### 重點
- 規模：遷移 75,000+ 測試類別，使用 OpenRewrite 自動程式碼轉換
- 執行策略：JUnit Platform + Bazel 雙執行模式，CI 全程驗證
- 關鍵成果：Monorepo 規模下同時保證測試正確性與基礎設施現代化

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/04/uber-junit4-junit5-migration/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<img src="https://res.infoq.com/news/2026/04/uber-junit4-junit5-migration/en/headerimage/generatedHeaderImage-1776546803798.jpg" /><p>Uber engineers migrated over 75,000 test classes from JUnit 4 to JUnit 5 using automated code transformation with OpenRewrite and internal orchestration. By enabling the JUnit Platform for dual execution with Bazel and validating changes through CI, the team modernized testing infrastructure while maintaining correctness at monorepo scale.</p> <i>By Leela Kumili</i>

</details>