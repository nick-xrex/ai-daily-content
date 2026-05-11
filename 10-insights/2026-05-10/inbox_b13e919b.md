---
id: inbox_b13e919b
date: 2026-05-10
source_ref: "[[00-inbox/.../inbox_b13e919b]]"
title: "Built an MCP that gives Claude Code the ability to watch screen recordings of UI bugs"
url: https://www.reddit.com/r/ClaudeAI/comments/1t9frna/built_an_mcp_that_gives_claude_code_the_ability/
source: reddit-claudeai
published_at: 2026-05-10T19:04:30+00:00
fetched_at: 2026-05-11T02:29:32.561417+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者 Ashad 構建了 motif MCP，讓 Claude Code 能觀看 UI bug 的螢幕錄影。motif 使用 Gemini 2.5 Flash 按幀序列處理視頻（而非單幀截圖），能捕捉 200ms 過衝或懸停狀態重置等時間敏感的視覺問題，自動輸出視覺現象、根本原因和修復 diff。設置只需 Gemini API key 和 mcp.json 兩行配置，之後告訴 Claude Code 「watch the recording」即可。此工具大幅減少手動描述視覺 bug 的時間，提高修復效率。"
key_points:
  - "Gemini 2.5 Flash 逐幀處理視頻比單幀截圖更能捕捉時間相關的 UI bug（如動畫過衝、狀態重置時序）"
  - "一行 URL 設置模式（npx motif-mcp），無需環境變數或分步配置，降低使用門檻"
  - "輸出包含視覺現象、根本原因、可直接應用的 diff，閉環完整"
tags: [mcp, claude-code, video-analysis, gemini-2-5-flash, ui-debugging]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Built an MCP that gives Claude Code the ability to watch screen recordings of UI bugs

開發者 Ashad 構建了 motif MCP，讓 Claude Code 能觀看 UI bug 的螢幕錄影。motif 使用 Gemini 2.5 Flash 按幀序列處理視頻（而非單幀截圖），能捕捉 200ms 過衝或懸停狀態重置等時間敏感的視覺問題，自動輸出視覺現象、根本原因和修復 diff。設置只需 Gemini API key 和 mcp.json 兩行配置，之後告訴 Claude Code 「watch the recording」即可。此工具大幅減少手動描述視覺 bug 的時間，提高修復效率。

### 重點
- Gemini 2.5 Flash 逐幀處理視頻比單幀截圖更能捕捉時間相關的 UI bug（如動畫過衝、狀態重置時序）
- 一行 URL 設置模式（npx motif-mcp），無需環境變數或分步配置，降低使用門檻
- 輸出包含視覺現象、根本原因、可直接應用的 diff，閉環完整

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t9frna/built_an_mcp_that_gives_claude_code_the_ability/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Built an MCP that gives Claude Code the ability to watch screen recordings of UI bugs

One thing Claude Code can't do natively is watch a video. For most bugs that's fine, but for anything visual, hover states, animations, scroll behavior, you end up spending more time describing the bug than actually fixing it. I built motif to handle this. You record the bug, point motif at the file, and it returns what's visually happening, the root cause, and a diff. It uses Gemini 2.5 Flash as it processes video as a frame sequence rather than a single screenshot. That distinction matters when the bug is a 200ms overshoot or a hover state that resets at the wrong time. Setup is a Gemini API key and two lines in your mcp.json. After that you just tell Claude Code to watch the recording.That's the whole interface. npx motif-mcp to try it. Repo: https://github.com/Ashad001/motif , still early so feedback is welcome. https://reddit.com/link/1t9frna/video/xd83w09fyc0h1/player &#32; submitted by &#32; /u/ashadis [link] &#32; [comments]

</details>