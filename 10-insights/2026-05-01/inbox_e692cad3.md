---
id: inbox_e692cad3
date: 2026-05-01
source_ref: "[[00-inbox/2026-05-01/0131-simon-willison-inaturalist-sightings-9d91]]"
title: "iNaturalist Sightings"
url: https://simonwillison.net/2026/May/1/inat-sightings/#atom-everything
source: simon-willison
published_at: 2026-05-01T19:35:41+00:00
fetched_at: 2026-05-03T01:35:30.445635+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 在露營時完全用手機和 Claude Code for web 開發了 iNaturalist Sightings 工具。架構包括三層：Python CLI（inaturalist-clumper）將觀察按時間（2 小時）和地理位置（5km）聚類；Git scraping 自動化定期執行工具並將結果提交到 GitHub clumps.json；靜態 HTML 前端直接通過 CORS fetch GitHub JSON，無後端依賴。前端支持縮略圖懶加載和點擊彈出模態框查看大圖，顯示物種公名。整個工具實現跨帳戶觀察的統一檢視，完全無伺服器架構。"
key_points:
  - "聚類邏輯：2 小時和 5km 範圍內的觀察視為同一事件，減少冗餘"
  - "Git scraping 自動化：定期執行 Python CLI 並提交結果到 GitHub，無需常駐服務"
  - "靜態 + JavaScript 前端：直接 CORS fetch 遠端 JSON，無後端伺服器，完全無伺服器架構"
tags: [claude-code, git-scraping, serverless-architecture, api-integration, static-frontend]
topics: [foundation_models.claude]
importance: 4
novelty: 3
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## iNaturalist Sightings

Simon Willison 在露營時完全用手機和 Claude Code for web 開發了 iNaturalist Sightings 工具。架構包括三層：Python CLI（inaturalist-clumper）將觀察按時間（2 小時）和地理位置（5km）聚類；Git scraping 自動化定期執行工具並將結果提交到 GitHub clumps.json；靜態 HTML 前端直接通過 CORS fetch GitHub JSON，無後端依賴。前端支持縮略圖懶加載和點擊彈出模態框查看大圖，顯示物種公名。整個工具實現跨帳戶觀察的統一檢視，完全無伺服器架構。

### 重點
- 聚類邏輯：2 小時和 5km 範圍內的觀察視為同一事件，減少冗餘
- Git scraping 自動化：定期執行 Python CLI 並提交結果到 GitHub，無需常駐服務
- 靜態 + JavaScript 前端：直接 CORS fetch 遠端 JSON，無後端伺服器，完全無伺服器架構

**原文：** [simon-willison](https://simonwillison.net/2026/May/1/inat-sightings/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<p><strong>Tool:</strong> <a href="https://tools.simonwillison.net/inat-sightings">iNaturalist Sightings</a></p>
        <p>I wanted to see my <a href="https://www.inaturalist.org">iNaturalist</a> observations - across two separate accounts - grouped by when they occurred. I'm camping this weekend so I built this entirely on my phone using Claude Code for web.</p>
<p>I started by building an <a href="https://github.com/simonw/inaturalist-clumper">inaturalist-clumper</a> Python CLI for fetching and "clumping" observations - by default clumps use observations within 2 hours and 5km of each other.</p>
<p>Then I setup <a href="https://github.com/simonw/inaturalist-clumps">simonw/inaturalist-clumps</a> as a <a href="https://simonwillison.net/series/git-scraping/">Git scraping</a> repository to run that tool and record the result to <a href="https://github.com/simonw/inaturalist-clumps/blob/main/clumps.json">clumps.json</a>.</p>
<p>That JSON file is hosted on GitHub, which means it can be fetched by JavaScript using CORS.</p>
<p>Finally I ran this prompt against my <a href="https://github.com/simonw/tools">simonw/tools</a> repo:</p>
<blockquote>
<p><code>Build inat-sightings.html - an app that does a fetch() against https://raw.githubusercontent.com/simonw/inaturalist-clumps/refs/heads/main/clumps.json and then displays all of the observations on one page using the https://static.inaturalist.org/photos/538073008/small.jpg small.jpg URLs for the thumbnails - with loading=lazy - but when a thumbnail is clicked showing the large.jpg in an HTML modal. Both small and large should include the common species names if available</code></p>
</blockquote>
    
    
        <p>Tags: <a href="https://simonwillison.net/tags/tools">tools</a>, <a href="https://simonwillison.net/tags/claude-code">claude-code</a>, <a href="https://simonwillison.net/tags/inaturalist">inaturalist</a>, <a href="https://simonwillison.net/tags/generative-ai">generative-ai</a>, <a href="https://simonwillison.net/tags/ai">ai</a>, <a href="https://simonwillison.net/tags/llms">llms</a></p>

</details>