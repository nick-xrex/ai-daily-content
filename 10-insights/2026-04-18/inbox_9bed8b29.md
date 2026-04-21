---
id: inbox_9bed8b29
date: 2026-04-18
source_ref: "[[00-inbox/.../inbox_9bed8b29]]"
title: "Adding a new content type to my blog-to-newsletter tool"
url: https://simonwillison.net/guides/agentic-engineering-patterns/adding-a-new-content-type/#atom-everything
source: (resumed)
published_at: 2026-04-18T03:15:36+00:00
fetched_at: 2026-04-21T02:36:17.457693+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 分享 agentic engineering 最佳實踐，展示用三行簡短提示讓 Claude Code 完成複雜任務的方法。案例：更新 blog-to-newsletter.html 工具以支援新內容類型「beats」（帶描述的外部內容連結）。關鍵做法包括：(1) 指示 agent 複製參考程式碼到 /tmp；(2) 準確指定目標檔案；(3) 參考現成實現（blog 的 Atom feed 邏輯）；(4) 提供驗證機制（python -m http.server + browser automation）；(5) 指示比較實時結果與預期。結果 PR 268 正確地新增 UNION SQL 子句，過濾草稿與無註解的 beats，展示高效 prompt engineering 可顯著減少 agent 誤解。"
key_points:
  - "參考程式碼克隆比逐行說明更高效，讓 agent 從實例推斷邏輯而非翻譯文字說明"
  - "提供具體驗證機制（本地伺服器 + browser automation），使 agent 能自我驗證而非盲目執行"
  - "引用現成功能模型而非重新說明，減少提示複雜度與歧義"
tags: [agentic-engineering, claude-code, prompt-engineering, automation, best-practices]
topics: [agents.mcp]
importance: 3
novelty: 3
deep_dive_candidate: false
deep_dive_approved: false
---

## Adding a new content type to my blog-to-newsletter tool

Simon Willison 分享 agentic engineering 最佳實踐，展示用三行簡短提示讓 Claude Code 完成複雜任務的方法。案例：更新 blog-to-newsletter.html 工具以支援新內容類型「beats」（帶描述的外部內容連結）。關鍵做法包括：(1) 指示 agent 複製參考程式碼到 /tmp；(2) 準確指定目標檔案；(3) 參考現成實現（blog 的 Atom feed 邏輯）；(4) 提供驗證機制（python -m http.server + browser automation）；(5) 指示比較實時結果與預期。結果 PR 268 正確地新增 UNION SQL 子句，過濾草稿與無註解的 beats，展示高效 prompt engineering 可顯著減少 agent 誤解。

### 重點
- 參考程式碼克隆比逐行說明更高效，讓 agent 從實例推斷邏輯而非翻譯文字說明
- 提供具體驗證機制（本地伺服器 + browser automation），使 agent 能自我驗證而非盲目執行
- 引用現成功能模型而非重新說明，減少提示複雜度與歧義

**原文：** [(resumed)](https://simonwillison.net/guides/agentic-engineering-patterns/adding-a-new-content-type/#atom-everything)