---
id: inbox_0356e0f1
date: 2026-05-10
source_ref: "[[00-inbox/.../inbox_0356e0f1]]"
title: "I built a Chrome extension for Claude that adds message-level bookmarks"
url: https://www.reddit.com/r/ClaudeAI/comments/1t91inn/i_built_a_chrome_extension_for_claude_that_adds/
source: reddit-claudeai
published_at: 2026-05-10T08:47:04+00:00
fetched_at: 2026-05-11T02:29:32.566686+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Chrome 擴充 Claude Toolbox 為 claude.ai 加入訊息級書籤、全文搜尋、批量匯出功能。解決長對話（200+ 訊息）內容查詢困難。Claude 參與開發：搭建 IndexedDB 同步層與遷移邏輯、編寫訊息 schema 與滾動高亮動畫、調試後台同步競態條件、草擬 10 語言 i18n 字串。免費版支持 2 個對話的書籤 + 全文搜尋 + 後台同步；付費 $5/月或 $49 終身。"
key_points:
  - "訊息級書籤 + 全文搜尋解決長對話內容定位痛點（減少手動翻頁）"
  - "IndexedDB 同步層設計支持跨裝置同步和本地遷移，競態調試教學示例"
  - "梯度商業模式：免費版（2 對話）驗證產品-市場契合度，付費版（$49 終身）覆蓋全部對話"
tags: [chrome-extension, productivity, bookmarks, search, claude-ai]
topics: [foundation_models.claude]
importance: 3
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## I built a Chrome extension for Claude that adds message-level bookmarks

Chrome 擴充 Claude Toolbox 為 claude.ai 加入訊息級書籤、全文搜尋、批量匯出功能。解決長對話（200+ 訊息）內容查詢困難。Claude 參與開發：搭建 IndexedDB 同步層與遷移邏輯、編寫訊息 schema 與滾動高亮動畫、調試後台同步競態條件、草擬 10 語言 i18n 字串。免費版支持 2 個對話的書籤 + 全文搜尋 + 後台同步；付費 $5/月或 $49 終身。

### 重點
- 訊息級書籤 + 全文搜尋解決長對話內容定位痛點（減少手動翻頁）
- IndexedDB 同步層設計支持跨裝置同步和本地遷移，競態調試教學示例
- 梯度商業模式：免費版（2 對話）驗證產品-市場契合度，付費版（$49 終身）覆蓋全部對話

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t91inn/i_built_a_chrome_extension_for_claude_that_adds/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# I built a Chrome extension for Claude that adds message-level bookmarks

I'm one of the people behind Claude Toolbox, a Chrome extension specifically for claude.ai. Wanted to share it here because the bookmark feature came out of an annoyance I kept hitting myself. What it does You can bookmark any individual message inside a Claude conversation. Click to save a reply, give it a label if you want, then later click the bookmark and the page scrolls straight to that message and highlights it for a second. No more hunting through 200 messages for the code snippet Claude gave you last Tuesday. It also does full-text search across all your synced conversations and one-click export as TXT or JSON. How Claude helped me build it &quot;Used Claude Code to scaffold the IndexedDB sync layer and migration logic&quot; &quot;Claude wrote the first pass of the message-bookmark schema and the scroll-to highlight animation&quot; &quot;Debugged a race condition in the background sync with Claude by pasting the worker logs&quot; &quot;Drafted the i18n strings for all 10 locales by giving Claude the EN file and asking for one locale at a time&quot; Free to try The free tier covers full-text search and lets you bookmark messages across 2 conversations, plus background sync. That was the version I shipped first to make sure the workflow was actually useful. Paid is $5/month or $49 one-time lifetime if you want it across every conversation. Screenshot Bookmark any Claude message with one click. Works across all your conversations. Claude Toolbox bookmarks panel with saved messages and scroll-to navigation Link https://chromewebstore.google.com/detail/claude-toolbox/camddjjmcemmmlndbciaodchkodhgibh Happy to answer anything about the build or the design tradeoffs in the comments. &#32; submitted by &#32; /u/Ok_Negotiation_2587 [link] &#32; [comments]

</details>