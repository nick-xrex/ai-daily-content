---
id: inbox_0d80298e
date: 2026-05-23
source_ref: "[[00-inbox/2026-05-23/0348-medium-tag-claude-the-claude-skills-directory-that-saved-m-125e]]"
title: "The .claude/skills/ Directory That Saved Me 75% of My Tokens"
url: https://medium.com/@darshshah1816/the-claude-skills-directory-that-saved-me-75-of-my-tokens-e73d8730e64d?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-05-23T20:00:51+00:00
fetched_at: 2026-05-24T03:56:15.187040+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Skills（存在於 `.claude/skills/` 的 markdown 文件）通過編碼用戶偏好和工作流實現 token 優化。示例 skills：`/caveman`（壓縮通信模式，節省 ~75% tokens）、`/grill-me`（詳細提問模式，實現前解決決策分支）、`/diagnose`（結構化 debugging）。Skills 使用 YAML frontmatter + instruction 結構，分兩層級作用域：個人 (`~/.claude/skills/`) 跨專案使用，項目特定 (`.claude/skills/`) 與團隊共享。根本問題：Claude Code 每次重啟無記憶，導致過度解釋浪費 token；Skills 編碼這些模式後，經驗使用者可立即迭代、降低 token 消耗。"
key_points:
  - "三個核心 skills 範例：`/caveman`（節省 ~75% tokens）、`/grill-me`（決策前深入探索）、`/diagnose`（結構化 debugging）"
  - "Skills 本質：preference codification，避免每次重啟後重新解釋；個人層級 (`~/.claude/skills/`) vs 項目層級 (`.claude/skills/`)"
  - "實踐框架：『preferences as reusable code』；特別對經驗使用者有效，減少基礎解釋開銷、加快迭代速度"
tags: [claude-skills, token-optimization, workflow-automation, productivity, preference-encoding]
topics: [foundation_models.claude]
importance: 4
novelty: 3
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## The .claude/skills/ Directory That Saved Me 75% of My Tokens

Claude Skills（存在於 `.claude/skills/` 的 markdown 文件）通過編碼用戶偏好和工作流實現 token 優化。示例 skills：`/caveman`（壓縮通信模式，節省 ~75% tokens）、`/grill-me`（詳細提問模式，實現前解決決策分支）、`/diagnose`（結構化 debugging）。Skills 使用 YAML frontmatter + instruction 結構，分兩層級作用域：個人 (`~/.claude/skills/`) 跨專案使用，項目特定 (`.claude/skills/`) 與團隊共享。根本問題：Claude Code 每次重啟無記憶，導致過度解釋浪費 token；Skills 編碼這些模式後，經驗使用者可立即迭代、降低 token 消耗。

### 重點
- 三個核心 skills 範例：`/caveman`（節省 ~75% tokens）、`/grill-me`（決策前深入探索）、`/diagnose`（結構化 debugging）
- Skills 本質：preference codification，避免每次重啟後重新解釋；個人層級 (`~/.claude/skills/`) vs 項目層級 (`.claude/skills/`)
- 實踐框架：『preferences as reusable code』；特別對經驗使用者有效，減少基礎解釋開銷、加快迭代速度

**原文：** [medium-tag-claude](https://medium.com/@darshshah1816/the-claude-skills-directory-that-saved-me-75-of-my-tokens-e73d8730e64d?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I was in a Claude Code session last week, debugging a gnarly type error. Claude gave me a four-paragraph explanation of what a TypeScript&#x2026; Continue reading on Medium »

</details>