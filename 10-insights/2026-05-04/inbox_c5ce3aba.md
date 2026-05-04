---
id: inbox_c5ce3aba
date: 2026-05-04
source_ref: "[[00-inbox/.../inbox_c5ce3aba]]"
title: "Claude Design built this skeumorphic keyboard simulator website in one session - whatever you type and enter is visible to the public"
url: https://www.reddit.com/r/ClaudeAI/comments/1t3crw7/claude_design_built_this_skeumorphic_keyboard/
source: reddit-claudeai
published_at: 2026-05-04T09:34:56+00:00
fetched_at: 2026-05-04T14:33:05.577099+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude 在單次 session 內完成擬物化鍵盤模擬器網站，展示 Figma 集成與前端開發能力。Claude 自動安裝 Figma 社區解析器（fig kiwi）並遍歷 98 個設計節點以提取漸層與模糊效果，手動移植所有 SVG 層至 CSS 實現精確視覺，並通過隱藏 `<input>` 元素保留原生 OS 快捷鍵（如 Cmd+ArrowLeft）。背景資源由 CORS proxy 自 Unsplash 快取為 WebP 優化加載。該案例展示 AI 在設計細節處理、第三方工具集成與用戶體驗最佳實踐的能力。"
key_points:
  - "Claude 自動安裝第三方解析器（fig kiwi）並遍歷 98 設計節點，提取漸層模糊效果後進行 CSS 移植"
  - "使用隱藏 `<input>` 元素替代自定義 div，以保留 Cmd+ArrowLeft、Cmd+Backspace 等 OS 快捷鍵功能"
  - "背景通過 CORS proxy 快取為 WebP 格式，減少加載時間改善性能"
tags: [claude, figma-integration, frontend-development, css, ui-design]
topics: [foundation_models.claude]
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Claude Design built this skeumorphic keyboard simulator website in one session - whatever you type and enter is visible to the public

Claude 在單次 session 內完成擬物化鍵盤模擬器網站，展示 Figma 集成與前端開發能力。Claude 自動安裝 Figma 社區解析器（fig kiwi）並遍歷 98 個設計節點以提取漸層與模糊效果，手動移植所有 SVG 層至 CSS 實現精確視覺，並通過隱藏 `<input>` 元素保留原生 OS 快捷鍵（如 Cmd+ArrowLeft）。背景資源由 CORS proxy 自 Unsplash 快取為 WebP 優化加載。該案例展示 AI 在設計細節處理、第三方工具集成與用戶體驗最佳實踐的能力。

### 重點
- Claude 自動安裝第三方解析器（fig kiwi）並遍歷 98 設計節點，提取漸層模糊效果後進行 CSS 移植
- 使用隱藏 `<input>` 元素替代自定義 div，以保留 Cmd+ArrowLeft、Cmd+Backspace 等 OS 快捷鍵功能
- 背景通過 CORS proxy 快取為 WebP 格式，減少加載時間改善性能

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t3crw7/claude_design_built_this_skeumorphic_keyboard/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Claude Design built this skeumorphic keyboard simulator website in one session - whatever you type and enter is visible to the public

<table> <tr><td> <a href="https://www.reddit.com/r/ClaudeAI/comments/1t3crw7/claude_design_built_this_skeumorphic_keyboard/"> <img alt="Claude Design built this skeumorphic keyboard simulator website in one session - whatever you type and enter is visible to the public" src="https://preview.redd.it/juj74ld803zg1.png?width=640&amp;crop=smart&amp;auto=webp&amp;s=857372a2baddecd9634ebf2b8fa6414a3edc2e1f" title="Claude Design built this skeumorphic keyboard simulator website in one session - whatever you type and enter is visible to the public" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>It's a skeuomorphic typing app. What you press on your real keyboard lights up on the rendered one, and pressing enter broadcasts your line into a public transcript everyone can see.</p> <p>Started with a one line prompt: &quot;keyboard recorder with a calculator tape history scrolling above, skeuomorphic. Claude shipped v1 in one pass, but generic.&quot;</p> <p>Next I uploaded a Figma file of the keys I actually wanted. Claude installed fig kiwi (community parser for Figma's binary format), walked all 98 nodes, pulled exact gradients and blurs. CSS recreations kept coming out &quot;ringed&quot; and too sharp. The fix was to port all SVG layers from Figma one by one.</p> <p>For typing logic, the first version used a custom div as input, so Cmd+ArrowLeft and Cmd+Backspace did nothing. The fix was to use a hidden `&lt;input&gt;` underneath the orange display, mirroring its value into the visible text and letting the OS handle every shortcut natively.</p> <p>Backgrounds are real Unsplash photos (marble, walnut, barnwood, slate) fetched through a CORS proxy and served back as cached WebP.</p> <p>Live here: <a href="http://asdf.app.teenyapp.com">asdf.app.teenyapp.com</a></p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/invocation02"> /u/invocation02 </a> <br /> <span><a href="https://i.redd.it/juj74ld803zg1.png">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t3crw7/claude_design_built_this_skeumorphic_keyboard/">[comments]</a></span> </td></tr></table>

</details>