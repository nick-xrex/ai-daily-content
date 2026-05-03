---
id: inbox_7c638d2d
date: 2026-05-02
source_ref: "[[00-inbox/2026-05-02/0131-simon-willison-sightings-49ff]]"
title: "Sightings"
url: https://simonwillison.net/2026/May/2/sightings/#atom-everything
source: simon-willison
published_at: 2026-05-02T17:26:40+00:00
fetched_at: 2026-05-03T01:35:30.443345+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 購置新的 Canon R6 Mark II 相機，開始拍攝大量野生動物照片並分享到 iNaturalist。為了整合這些照片到個人部落格，他在露營時用手機通過 Claude Code for web 開發了一個新功能。該功能將 iNaturalist 上超過十年的觀察數據（跨兩個帳戶）回溯整合到部落格中。整合後，這些生物觀察可以在部落格首頁、日期存檔頁面和全站搜尋結果中查詢，無縫延伸了既有的內容聯播系統。"
key_points:
  - "在手機上用 Claude Code for web 開發；支援快速迭代和現場開發"
  - "回溯整合 10+ 年 iNaturalist 觀察（跨兩個帳戶）到部落格數據庫"
  - "集成內容可在首頁、日期存檔和全站搜尋查詢，無需單獨頁面"
tags: [claude-code, api-integration, blogging-automation, external-data-syndication]
topics: [foundation_models.claude]
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Sightings

Simon Willison 購置新的 Canon R6 Mark II 相機，開始拍攝大量野生動物照片並分享到 iNaturalist。為了整合這些照片到個人部落格，他在露營時用手機通過 Claude Code for web 開發了一個新功能。該功能將 iNaturalist 上超過十年的觀察數據（跨兩個帳戶）回溯整合到部落格中。整合後，這些生物觀察可以在部落格首頁、日期存檔頁面和全站搜尋結果中查詢，無縫延伸了既有的內容聯播系統。

### 重點
- 在手機上用 Claude Code for web 開發；支援快速迭代和現場開發
- 回溯整合 10+ 年 iNaturalist 觀察（跨兩個帳戶）到部落格數據庫
- 集成內容可在首頁、日期存檔和全站搜尋查詢，無需單獨頁面

**原文：** [simon-willison](https://simonwillison.net/2026/May/2/sightings/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<p><strong><a href="https://simonwillison.net/elsewhere/sighting/">/elsewhere/sightings/</a></strong></p>
I have a new camera (a Canon R6 Mark II) so I'm taking a lot more photos of birds. I share my best wildlife photos on <a href="https://www.inaturalist.org/">iNaturalist</a>, and based on yesterday's <a href="https://simonwillison.net/2026/May/1/inat-sightings/">successful prototype</a>  I decided to add those to my blog.</p>
<p><img alt="Screenshot of a &quot;Sightings&quot; webpage with a search bar and RSS icon, showing &quot;Filters: Sorted by date&quot; and &quot;208 results page 1 / 7 next » last »»&quot;. First entry: SIGHTING 7:51 PM — Acorn Woodpecker, with two photos labeled &quot;Acorn Woodpecker&quot; of black and white woodpeckers with red caps on tree branches, dated 2nd May 2026. Second entry: SIGHTING 10:08 AM – 11:17 AM — Acorn Woodpecker, Western Fence Lizard, Osprey, with three photos labeled &quot;Acorn Woodpecker&quot; (bird on bare branches against blue sky), &quot;Wester...&quot; (lizard on tree bark), and &quot;Osprey&quot; (nest on a utility pole), dated 1st May 2026. Third entry: SIGHTING 11:11 AM — White-crowned Sparrow, with a photo labeled &quot;White-crowned Sparrow&quot; of a sparrow with black and white striped head singing with open beak, dated 30th Apr 2026." class="blogmark-image" src="https://static.simonwillison.net/static/2026/beats-sightings.jpeg" /></p>
<p>I built this feature on my phone using Claude Code for web, as an extension of my <a href="https://simonwillison.net/2026/Feb/20/beats/">beats system</a> for syndicating external content. Here's <a href="https://github.com/simonw/simonwillisonblog/pull/668">the PR</a> and prompt.</p>
<p>As with my other forms of incoming syndicated content sightings show up on the homepage, the date archive pages, and in site search results.</p>
<p>I back-populated over a decade of iNaturalist sightings, which means you that if you <a href="https://simonwillison.net/search/?q=lemur">search for lemur</a> you'll see my lemur photos from Madagascar in 2019!


    <p>Tags: <a href="https://simonwillison.net/tags/blogging">blogging</a>, <a href="https://simonwillison.net/tags/photography">photography</a>, <a href="https://simonwillison.net/tags/wildlife">wildlife</a>, <a href="https://simonwillison.net/tags/ai">ai</a>, <a href="https://simonwillison.net/tags/inaturalist">inaturalist</a>, <a href="https://simonwillison.net/tags/generative-ai">generative-ai</a>, <a href="https://simonwillison.net/tags/llms">llms</a>, <a href="https://simonwillison.net/tags/ai-assisted-programming">ai-assisted-programming</a>, <a href="https://simonwillison.net/tags/claude-code">claude-code</a></p>

</details>