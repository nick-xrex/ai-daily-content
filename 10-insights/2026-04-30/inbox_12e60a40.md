---
id: inbox_12e60a40
date: 2026-04-30
source_ref: "[[00-inbox/2026-04-30/1257-reddit-claudeai-spent-an-evening-making-a-launch-video-w-a7ea]]"
title: "Spent an evening making a launch video with Claude + Blender MCP"
url: https://www.reddit.com/r/ClaudeAI/comments/1t09rrr/spent_an_evening_making_a_launch_video_with/
source: reddit-claudeai
published_at: 2026-04-30T21:34:28+00:00
fetched_at: 2026-05-01T13:37:59.604524+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "獨立開發者用 Claude + Blender MCP 在一晚 90 分鐘內製作了習慣追蹤應用 Spira 的 10 秒視頻（用於 App Store / TikTok）。Claude 先「召集委員會」參考（Lubezki、Hokusai、James Cameron 等）來設計視效方向，自動處理 iPhone 螢幕錄製的裁剪，執行 ~800 行 Python 生成相機軌跡、發射材料、體積霧、粒子交錯。首版過度設計（Fibonacci 爆發），用自然語言「變得溫柔，像宮崎駿夢境」修正到最終版本。"
key_points:
  - "自然語言驅動 3D 資產生成（相機軌跡、材料、粒子、霧效）節省數日時間"
  - "「參考委員會」方法指導視覺方向，使結果高度藝術性而非平凡"
  - "漸進式修訂工作流：初稿 → 概念調整 → 最終輸出，全程對話"
tags: [blender-mcp, 3d-video, ai-creative, natural-language-engineering]
topics: [agents.mcp]
importance: 3
novelty: 3
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Spent an evening making a launch video with Claude + Blender MCP

獨立開發者用 Claude + Blender MCP 在一晚 90 分鐘內製作了習慣追蹤應用 Spira 的 10 秒視頻（用於 App Store / TikTok）。Claude 先「召集委員會」參考（Lubezki、Hokusai、James Cameron 等）來設計視效方向，自動處理 iPhone 螢幕錄製的裁剪，執行 ~800 行 Python 生成相機軌跡、發射材料、體積霧、粒子交錯。首版過度設計（Fibonacci 爆發），用自然語言「變得溫柔，像宮崎駿夢境」修正到最終版本。

### 重點
- 自然語言驅動 3D 資產生成（相機軌跡、材料、粒子、霧效）節省數日時間
- 「參考委員會」方法指導視覺方向，使結果高度藝術性而非平凡
- 漸進式修訂工作流：初稿 → 概念調整 → 最終輸出，全程對話

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t09rrr/spent_an_evening_making_a_launch_video_with/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/ClaudeAI/comments/1t09rrr/spent_an_evening_making_a_launch_video_with/"> <img alt="Spent an evening making a launch video with Claude + Blender MCP" src="https://external-preview.redd.it/a3ZteHBqNnJiZXlnMbEA6yRpXf2URmnxGIanaZ9XjyEwk-VZgj7bNUHdFSKc.png?width=640&amp;crop=smart&amp;auto=webp&amp;s=5fac55adf6645ff52c33d0f6c01255245d46bc1e" title="Spent an evening making a launch video with Claude + Blender MCP" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>Solo dev working on a habit tracker app (Spira — habits become flowers that bloom over time). Needed a 10s vertical video for App Store / TikTok and didn't have a week to spend on it.</p> <p>Hooked up the Blender MCP server, described what I wanted: a phone floating in a Miyazaki-meets-Apple atmosphere, dust motes drifting like in sunlight, the app on screen, slow camera reveal ending on a flower closeup.</p> <p>A few moments worth sharing:</p> <p>- It convened a &quot;committee&quot; of references (Lubezki, Hokusai, James Cameron) before designing the shot. Felt overengineered until I saw the output.</p> <p>- I just sent it the iPhone screen recording — it auto-cropped the iOS REC bar with ffmpeg before mapping it onto the 3D screen.</p> <p>- First pass was too aggressive (Fibonacci petal explosion + glowing roots, looked like a startup logo). Told it &quot;make it gentler, like a Miyazaki dream&quot; — got the version below.</p> <p>Roughly 90 min of back-and-forth, three full renders, ~800 lines of Python written and executed in Blender. Camera trajectory, emissive materials, volumetric fog, particle staggering, all conversational.</p> <p>Final video attached.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Positive_Camel2086"> /u/Positive_Camel2086 </a> <br /> <span><a href="https://v.redd.it/9zw2we6rbeyg1">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t09rrr/spent_an_evening_making_a_launch_video_with/">[comments]</a></span> </td></tr></table>

</details>