---
id: inbox_f880b442
date: 2026-04-22
source_ref: "[[00-inbox/2026-04-22/0156-medium-tag-ai-35-claude-code-commands-tricks-and-workf-73c5]]"
title: "35 Claude Code Commands, Tricks, and Workflows That Actually Matter"
url: https://medium.com/@okyerevansjohn/35-claude-code-commands-tricks-and-workflows-that-actually-matter-e52c5f377e46?source=rss------artificial_intelligence-5
source: medium-tag-ai
published_at: 2026-04-22T01:51:35+00:00
fetched_at: 2026-04-22T02:01:32.120172+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "文章整理了使用 Claude Code 的 35 個實戰技巧，分為五大類別：必要指令（Plan Mode、/compact、/clear、/init、/cost、/memory 等）、生產力技巧（參考檔案、截圖除錯、測試優先、增量開發、git checkpoint）、架構技巧（依賴評估、安全掃描、效能分析、重構規劃）、工作流自動化（git hooks、CI/CD、環境設定）和除錯恢復（再現問題、依賴衝突、循環實作脫逃）。核心原則強調「建設前先規劃」及「增量開發搭配測試」，使用 Plan Mode 進行架構設計、/compact 壓縮上下文、git checkpoint 保存檢查點便於回滾。這份指南涵蓋從基礎指令到進階工作流自動化的完整路徑。"
key_points:
  - "五大技巧類別：Essential Commands（Plan Mode、/compact、/clear、模型切換）、Productivity（test-first、incremental build、git checkpoint）、Architecture（依賴評估、安全掃描）、Automation、Debug & Recovery"
  - "Plan Mode 用於架構規劃，/compact 壓縮長會話 context，/clear 分離 context，git checkpoint 便於快速回滾"
  - "核心工作流：建設前規劃 → 增量開發搭配測試 → 每步驟檢查點 → diff 審核 → 文檔化"
tags: [claude-code, workflows, productivity, testing, planning]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## 35 Claude Code Commands, Tricks, and Workflows That Actually Matter

文章整理了使用 Claude Code 的 35 個實戰技巧，分為五大類別：必要指令（Plan Mode、/compact、/clear、/init、/cost、/memory 等）、生產力技巧（參考檔案、截圖除錯、測試優先、增量開發、git checkpoint）、架構技巧（依賴評估、安全掃描、效能分析、重構規劃）、工作流自動化（git hooks、CI/CD、環境設定）和除錯恢復（再現問題、依賴衝突、循環實作脫逃）。核心原則強調「建設前先規劃」及「增量開發搭配測試」，使用 Plan Mode 進行架構設計、/compact 壓縮上下文、git checkpoint 保存檢查點便於回滾。這份指南涵蓋從基礎指令到進階工作流自動化的完整路徑。

### 重點
- 五大技巧類別：Essential Commands（Plan Mode、/compact、/clear、模型切換）、Productivity（test-first、incremental build、git checkpoint）、Architecture（依賴評估、安全掃描）、Automation、Debug & Recovery
- Plan Mode 用於架構規劃，/compact 壓縮長會話 context，/clear 分離 context，git checkpoint 便於快速回滾
- 核心工作流：建設前規劃 → 增量開發搭配測試 → 每步驟檢查點 → diff 審核 → 文檔化

**原文：** [medium-tag-ai](https://medium.com/@okyerevansjohn/35-claude-code-commands-tricks-and-workflows-that-actually-matter-e52c5f377e46?source=rss------artificial_intelligence-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<div class="medium-feed-item"><p class="medium-feed-image"><a href="https://medium.com/@okyerevansjohn/35-claude-code-commands-tricks-and-workflows-that-actually-matter-e52c5f377e46?source=rss------artificial_intelligence-5"><img src="https://cdn-images-1.medium.com/max/890/1*g0nJq9bANuH_lIZsWdFOsw.jpeg" width="890" /></a></p><p class="medium-feed-snippet">I&#x2019;ve been building with Claude Code daily &#x2014; automating real client workflows, shipping AI systems, debugging production code at odd hours&#x2026;</p><p class="medium-feed-link"><a href="https://medium.com/@okyerevansjohn/35-claude-code-commands-tricks-and-workflows-that-actually-matter-e52c5f377e46?source=rss------artificial_intelligence-5">Continue reading on Medium »</a></p></div>

</details>