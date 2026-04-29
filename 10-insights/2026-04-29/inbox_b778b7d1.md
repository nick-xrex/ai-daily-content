---
id: inbox_b778b7d1
date: 2026-04-29
source_ref: "[[00-inbox/2026-04-29/0658-reddit-claudeai-how-to-make-a-product-promo-video-with-c-b00c]]"
title: "How to make a Product Promo Video with Claude Design (Prompts inside)"
url: https://www.reddit.com/r/ClaudeAI/comments/1sypn6t/how_to_make_a_product_promo_video_with_claude/
source: reddit-claudeai
published_at: 2026-04-29T05:32:53+00:00
fetched_at: 2026-04-29T07:30:41.358724+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Reddit 用戶分享了用 Claude Design 製作產品宣傳影片的工程化流程。核心策略：場景優先思考（像導演列場景單，而非設計師思考），第一提示輸入包含 7 個連續場景、UI 細節（URL 字符串、按鈕標籤、進度文本）和品牌參考 URL，第二提示做迭代修正（快速過渡、修正特定場景、控制時長 <40 秒）。作者強調兩次提示即足夠，避免一次性追求完美。文中提供了可套用的通用模板，涵蓋問題陳述、痛點呈現、產品核心行動、工作狀態、結果呈現、結果去向、結論動畫等 7 幕。影片後由外部工具 (claudevideoexport.com) 轉換為 MP4，音軌另行添加。"
key_points:
  - "場景優先法：將影片分解為 7 個清晰場景（文字動畫→問題呈現→產品介紹→核心操作→進度狀態→結果呈現→結論），每場景含 UI 細節（URL、按鈕名、進度數字）"
  - "兩輪迭代足夠：第一提示生成可用草案，第二提示針對性修正（如修正上傳視覺、加快轉換、控制 <40 秒），避免過度預期完美"
  - "通用模板提供：5–7 個可配置的場景框架，支持自訂產品 URL、問題陳述、產品名、UI 風格、轉換速度"
tags: [claude-design-video, prompt-engineering, iterative-refinement, scene-based-thinking]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## How to make a Product Promo Video with Claude Design (Prompts inside)

Reddit 用戶分享了用 Claude Design 製作產品宣傳影片的工程化流程。核心策略：場景優先思考（像導演列場景單，而非設計師思考），第一提示輸入包含 7 個連續場景、UI 細節（URL 字符串、按鈕標籤、進度文本）和品牌參考 URL，第二提示做迭代修正（快速過渡、修正特定場景、控制時長 <40 秒）。作者強調兩次提示即足夠，避免一次性追求完美。文中提供了可套用的通用模板，涵蓋問題陳述、痛點呈現、產品核心行動、工作狀態、結果呈現、結果去向、結論動畫等 7 幕。影片後由外部工具 (claudevideoexport.com) 轉換為 MP4，音軌另行添加。

### 重點
- 場景優先法：將影片分解為 7 個清晰場景（文字動畫→問題呈現→產品介紹→核心操作→進度狀態→結果呈現→結論），每場景含 UI 細節（URL、按鈕名、進度數字）
- 兩輪迭代足夠：第一提示生成可用草案，第二提示針對性修正（如修正上傳視覺、加快轉換、控制 <40 秒），避免過度預期完美
- 通用模板提供：5–7 個可配置的場景框架，支持自訂產品 URL、問題陳述、產品名、UI 風格、轉換速度

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1sypn6t/how_to_make_a_product_promo_video_with_claude/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/ClaudeAI/comments/1sypn6t/how_to_make_a_product_promo_video_with_claude/"> <img alt="How to make a Product Promo Video with Claude Design (Prompts inside)" src="https://external-preview.redd.it/bzB6cDd2MWplMnlnMcXOxLNy6AW8a1VFbPgc_xEI8C-mRPVUkZLv29xirsYR.png?width=640&amp;crop=smart&amp;auto=webp&amp;s=f3ff44c971f1c90e1334821616bbe414e7df5581" title="How to make a Product Promo Video with Claude Design (Prompts inside)" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>I just made this product promo video completely with Claude code. Explaining the process here with the prompts. I also have a generic prompt at the bottom that you might want to use. </p> <h1>Step 1: Describe your video in scenes</h1> <p>Don’t think in “design.” Think in scenes — like a director giving a shot list to a crew.</p> <p>This is the first prompt I used:</p> <pre><code>Make a slick product intro video for my product https://claudevideoexport.com - Scene 1: Text animation — &quot;How to get MP4 from Claude Design Animation&quot; - Scene 2: Show a small browser window with &quot;Claude Design&quot; open. Pan to the top right with &quot;Present&quot; link and &quot;Share&quot; button. Show a mouse clicking &quot;Present&quot; → dropdown appears → mouse clicks &quot;New Tab&quot;. New tab opens and the URL is copied. URL reads: &quot;https://2d0b2821-9f01-40b1-b0a6-2f4db6601a33.claudeusercontent.com/v1/design/projects/2d0b2...&quot; - Scene 3: Switch to claudevideoexport.com showing a form. URL is pasted into the form and &quot;Export&quot; is clicked. - Scene 4: Fast-moving progress bar going from 0% to 100%. Text reads &quot;Rendering Video (0/2000 frames)&quot; — counter increments to 2000/2000. - Scene 5: A file icon labeled &quot;video.mp4&quot; pops up and downloads. - Scene 6: video.mp4 gets uploaded to YouTube, then Instagram, then Facebook. - Scene 7: Text animation — &quot;Make Claude Design Animations → Get MP4 using ClaudeVideoExport.com&quot; Use the look and feel of https://claudevideoexport.com. UI components should look like they belong to that site. </code></pre> <p><strong>What makes this prompt work:</strong> It’s sequential. Each scene has a clear action. The UI details — the URL string, the button labels, the progress text — give Claude enough to build something that looks real rather than generic. And anchoring to a real website URL lets Claude pull design references.</p> <h1>Step 2: Refine with a follow-up pass</h1> <p>First output was close but not quite right. The platform upload scenes looked static, and the overall pace was slow. One more prompt:</p> <pre><code>- The file upload to YouTube, Instagram &amp; Facebook should look like the file being dragged and dropped onto those sites in a browser. Show a basic drag-and-drop UI element for each site matching their brand colors. Get the correct icons for each platform from the web. - Make overall scene transitions faster and slicker. Keep the whole thing under 40 seconds. </code></pre> <p>That’s it. Two prompts total. The second one fixed exactly what needed fixing.</p> <p><strong>The lesson:</strong> Don’t try to get everything right in one massive prompt. Get a working draft, watch it, note what’s off, fix those specific things. Claude Design responds well to targeted correction.</p> <h1>The generic prompt you can steal for any product</h1> <pre><code>Make a 30–45 second product intro video for [YOUR PRODUCT URL]. Scenes: - Scene 1: Text animation — &quot;[One-line problem statement]&quot; - Scene 2: Show the old/painful way of doing this. Use a browser window. Keep it simple and recognizable. - Scene 3: Introduce [PRODUCT NAME]. Show the core action (the thing the user actually does — paste URL, upload file, click button, etc.) - Scene 4: Show the product working. Progress indicator, loading state, or live output — whatever fits. - Scene 5: Show the result. File icon, dashboard, confirmation screen — make it feel satisfying. - Scene 6: Show where the result goes. Social platforms, email, Slack, client — wherever the output lands. - Scene 7: Text animation — &quot;[Core value proposition in one line]&quot; Use the look and feel of [YOUR PRODUCT URL] for all UI components. Colors, fonts, and style should match the site. Keep transitions smooth and fast-paced throughout. </code></pre> <p>Then follow up with one refinement prompt targeting anything that’s off.</p> <p>To export the animation into MP4, you can use my tool - <a href="http://claudevideoexport.com">claudevideoexport.com</a><br /> Audio was added to the video outside of any of these tools. </p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/gnurpreet_"> /u/gnurpreet_ </a> <br /> <span><a href="https://v.redd.it/6a2jyk1je2yg1">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1sypn6t/how_to_make_a_product_promo_video_with_claude/">[comments]</a></span> </td></tr></table>

</details>