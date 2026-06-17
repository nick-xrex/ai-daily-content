---
id: inbox_0ae2f9aa
date: 2026-06-17
source_ref: "[[00-inbox/2026-06-17/2200-simon-willison-click-to-play-a-still-that-plays-d0d2]]"
title: "&lt;click-to-play&gt; — a still that plays"
url: https://simonwillison.net/2026/Jun/17/click-to-play-component/#atom-everything
source: simon-willison
published_at: 2026-06-17T03:56:10+00:00
fetched_at: 2026-06-17T22:05:50.490789+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "`<click-to-play>` 是一個漸進式增強的 Web Component，由 Simon Willison 開發。它將 GIF 圖片轉換為靜態預覽圖加點擊播放按鈕的互動形式。用戶只有在點擊按鈕時才會加載 GIF 文件，避免了不必要的大文件自動下載。這個組件適合在網頁上展示 GIF 動畫但希望節省頻寬和初始加載時間的場景。原始標記簡單明淨：包含指向 GIF 的超連結和預覽圖像。作者為了在 Datasette 文章中展示行編輯工具的演示動畫而開發了這個組件。"
key_points:
  - "`<click-to-play>` Web Component 實現懶加載 GIF，用戶點擊時才下載"
  - "HTML 標記：`<a href=\"GIF URL\"><img src=\"預覽圖\"></a>`，自動轉為可互動組件"
  - "應用場景：性能優化、流量節省，減少非必要的大文件初始加載"
tags: [web-component, gif-optimization, progressive-enhancement, javascript, lazy-loading]
topics: []
importance: 1
novelty: 1
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## <click-to-play> — a still that plays

`<click-to-play>` 是一個漸進式增強的 Web Component，由 Simon Willison 開發。它將 GIF 圖片轉換為靜態預覽圖加點擊播放按鈕的互動形式。用戶只有在點擊按鈕時才會加載 GIF 文件，避免了不必要的大文件自動下載。這個組件適合在網頁上展示 GIF 動畫但希望節省頻寬和初始加載時間的場景。原始標記簡單明淨：包含指向 GIF 的超連結和預覽圖像。作者為了在 Datasette 文章中展示行編輯工具的演示動畫而開發了這個組件。

### 重點
- `<click-to-play>` Web Component 實現懶加載 GIF，用戶點擊時才下載
- HTML 標記：`<a href="GIF URL"><img src="預覽圖"></a>`，自動轉為可互動組件
- 應用場景：性能優化、流量節省，減少非必要的大文件初始加載

**原文：** [simon-willison](https://simonwillison.net/2026/Jun/17/click-to-play-component/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Tool: &lt;click-to-play&gt; — a still that plays 
 A progressive enchantment Web Component that turns this markup: 
 &lt;click-to-play&gt;
 &lt;a href="URL to GIF"&gt;
 &lt;img src="URL to first frame" alt="..."&gt;
 &lt;/a&gt;
&lt;/click-to-play&gt;
 
 Into a still frame with a click to play button which loads the GIF on demand. For when you don't want big GIFs to be loaded unless people want to play them. 
 Here's an example that demonstrates the new row editing tools in Datasette - in fact I built this Web Component for that post. 
 
 
 Tags: gif , javascript , progressive-enhancement , web-components

</details>