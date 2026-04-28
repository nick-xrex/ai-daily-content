---
id: inbox_a318eac5
date: 2026-04-27
source_ref: "[[00-inbox/2026-04-27/0248-infoq-main-uber-migrates-75-000-test-classes-from-j-af00]]"
title: "Uber Migrates 75,000+ Test Classes from Junit 4 to Junit 5 Using Automated Code Transformation"
url: https://www.infoq.com/news/2026/04/uber-junit4-junit5-migration/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-04-27T14:07:00+00:00
fetched_at: 2026-04-28T02:55:01.929090+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Uber 工程團隊使用 OpenRewrite 和內部編排工具，成功將 75,000+ 個測試類別從 JUnit 4 自動化遷移至 JUnit 5。透過啟用 Bazel 上的 JUnit Platform 雙執行模式，並透過持續整合驗證所有變更，在超大規模單一倉庫環境中完成測試基礎設施的現代化。"
key_points:
  - "75,000+ 測試類遷移規模，創業界大規模案例"
  - "OpenRewrite + 內部編排工具實現全自動化轉換"
  - "Bazel + JUnit Platform 雙執行模式驗證正確性"
tags: [junit-migration, openrewrite, bazel, automated-transformation]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Uber Migrates 75,000+ Test Classes from Junit 4 to Junit 5 Using Automated Code Transformation

Uber 工程團隊使用 OpenRewrite 和內部編排工具，成功將 75,000+ 個測試類別從 JUnit 4 自動化遷移至 JUnit 5。透過啟用 Bazel 上的 JUnit Platform 雙執行模式，並透過持續整合驗證所有變更，在超大規模單一倉庫環境中完成測試基礎設施的現代化。

### 重點
- 75,000+ 測試類遷移規模，創業界大規模案例
- OpenRewrite + 內部編排工具實現全自動化轉換
- Bazel + JUnit Platform 雙執行模式驗證正確性

**原文：** [infoq-main](https://www.infoq.com/news/2026/04/uber-junit4-junit5-migration/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<img src="https://res.infoq.com/news/2026/04/uber-junit4-junit5-migration/en/headerimage/generatedHeaderImage-1776546803798.jpg" /><p>Uber engineers migrated over 75,000 test classes from JUnit 4 to JUnit 5 using automated code transformation with OpenRewrite and internal orchestration. By enabling the JUnit Platform for dual execution with Bazel and validating changes through CI, the team modernized testing infrastructure while maintaining correctness at monorepo scale.</p> <i>By Leela Kumili</i>

</details>