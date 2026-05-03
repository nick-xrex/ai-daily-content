---
id: inbox_127ffe4e
date: 2026-05-02
source_ref: "[[00-inbox/2026-05-02/0132-hackernews-vs-code-inserting-co-authored-by-copilot-4314]]"
title: "VS Code inserting &#39;Co-Authored-by Copilot&#39; into commits regardless of usage"
url: https://github.com/microsoft/vscode/pull/310226
source: hackernews
published_at: 2026-05-02T19:57:26+00:00
fetched_at: 2026-05-03T02:09:22.155602+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "VS Code 在 PR #310226 中將 Git 擴展的 `git.addAICoAuthor` 設定預設值從「off」改為「all」，導致軟體自動在提交訊息中插入 `Co-authored-by: Copilot` 標籤，即使使用者未實際使用 Copilot、甚至啟用了 `disableAIFeatures` 設定仍會插入，以隱性方式推出未告知使用者。社群開發者強烈反彈，認為這是對提交元數據的不當篡改，違反知情同意原則。維護者最終承認迴歸問題，承諾在版本 1.119 修復，指出三大缺陷：應尊重禁用 AI 功能的設定、不應歸屬非 AI 生成代碼、需要更完善測試覆蓋。"
key_points:
  - "VS Code 自動插入 Copilot 歸屬，即使未使用或已禁用 AI 功能，以隱性方式推出"
  - "核心問題：違反知情同意和開源倫理，對提交元數據的不當篡改"
  - "版本 1.119 修復計畫：尊重禁用設定、避免非 AI 代碼歸屬、強化測試覆蓋"
tags: [vs-code, copilot, git, ethics, ai-transparency]
topics: []
importance: 4
novelty: 3
insight_quality: 5
insight_type: data-point
deep_dive_candidate: true
deep_dive_approved: false
---

## VS Code inserting 'Co-Authored-by Copilot' into commits regardless of usage

VS Code 在 PR #310226 中將 Git 擴展的 `git.addAICoAuthor` 設定預設值從「off」改為「all」，導致軟體自動在提交訊息中插入 `Co-authored-by: Copilot` 標籤，即使使用者未實際使用 Copilot、甚至啟用了 `disableAIFeatures` 設定仍會插入，以隱性方式推出未告知使用者。社群開發者強烈反彈，認為這是對提交元數據的不當篡改，違反知情同意原則。維護者最終承認迴歸問題，承諾在版本 1.119 修復，指出三大缺陷：應尊重禁用 AI 功能的設定、不應歸屬非 AI 生成代碼、需要更完善測試覆蓋。

### 重點
- VS Code 自動插入 Copilot 歸屬，即使未使用或已禁用 AI 功能，以隱性方式推出
- 核心問題：違反知情同意和開源倫理，對提交元數據的不當篡改
- 版本 1.119 修復計畫：尊重禁用設定、避免非 AI 代碼歸屬、強化測試覆蓋

**原文：** [hackernews](https://github.com/microsoft/vscode/pull/310226)