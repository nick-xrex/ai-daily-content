---
id: inbox_8dbcbdc1
date: 2026-07-28
source_ref: "[[00-inbox/.../inbox_8dbcbdc1]]"
title: "v0.44.1"
url: https://github.com/rtk-ai/rtk/releases/tag/v0.44.1
source: rtk-releases
published_at: 2026-07-28T13:59:05+00:00
fetched_at: 2026-07-29T03:36:50.943214+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK v0.44.1 發布，包含三項 bug 修復。Hook 層級修復 Windows 上 Copilot CLI shell tool 檢測（#3178），確保工具在 Windows 環境中正確識別。Search 命令最小化輸出，只在明確請求時才顯示 nb line 參數，減少預設雜訊。CI/CD 層級更新 git app token，確保下一版本發佈流程順暢。"
key_points:
  - "Windows Copilot CLI shell tool 檢測修復（#3178），確保 hook 在 Windows 環境中正確識別工具"
  - "Search 命令輸出最小化：僅在使用者請求時才顯示 nb line，減少預設輸出雜訊"
  - "CI/CD 層級 git app token 更新，確保下一版本發佈流程順暢"
tags: [rtk, windows, copilot-cli, ci-cd]
topics: []
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v0.44.1

RTK v0.44.1 發布，包含三項 bug 修復。Hook 層級修復 Windows 上 Copilot CLI shell tool 檢測（#3178），確保工具在 Windows 環境中正確識別。Search 命令最小化輸出，只在明確請求時才顯示 nb line 參數，減少預設雜訊。CI/CD 層級更新 git app token，確保下一版本發佈流程順暢。

### 重點
- Windows Copilot CLI shell tool 檢測修復（#3178），確保 hook 在 Windows 環境中正確識別工具
- Search 命令輸出最小化：僅在使用者請求時才顯示 nb line，減少預設輸出雜訊
- CI/CD 層級 git app token 更新，確保下一版本發佈流程順暢

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/v0.44.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v0.44.1

0.44.1 (2026-07-28) 
 Bug Fixes 
 
 cicd: git app token for next release ( cdfb14c ) 
 hook: detect Copilot CLI shell tool on Windows ( 10ca886 ), closes #3178 
 search: display nb line only if requested ( a8b9eb3 )

</details>