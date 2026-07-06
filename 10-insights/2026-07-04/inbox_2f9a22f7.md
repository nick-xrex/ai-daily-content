---
id: inbox_2f9a22f7
date: 2026-07-04
source_ref: "[[00-inbox/2026-07-04/2200-simon-willison-building-a-world-map-with-only-500-bytes-487c]]"
title: "Building a World Map with only 500 bytes"
url: https://simonwillison.net/2026/Jul/4/building-a-world-map-with-only-500-bytes/#atom-everything
source: simon-willison
published_at: 2026-07-04T23:09:02+00:00
fetched_at: 2026-07-05T22:07:12.666346+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Iwo Kadziela 在 Codex 協助下，利用 deflate 壓縮和 JavaScript 的 DecompressionStream API 產生可信的 ASCII 世界地圖，僅需 445 字節資料。技巧包括用 fetch() 搭配 data: URIs 和 pipeThrough() 管道解壓縮，解壓後直接內嵌為 <pre> 標籤渲染。該方法展示了壓縮技術在微型互動內容中的應用潛力。"
key_points:
  - "445 字節的 base64 編碼 deflate-raw 壓縮資料 + 14 行 JavaScript 足以產生完整 ASCII 世界地圖"
  - "fetch() 支援 data: URIs 搭配 DecompressionStream('deflate-raw') 實現瀏覽器端解壓"
  - "無需載入外部地圖庫，實現極簡產物與即時生成"
tags: [ascii-art, compression, javascript, data-urls, deflate]
topics: []
importance: 2
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Building a World Map with only 500 bytes

Iwo Kadziela 在 Codex 協助下，利用 deflate 壓縮和 JavaScript 的 DecompressionStream API 產生可信的 ASCII 世界地圖，僅需 445 字節資料。技巧包括用 fetch() 搭配 data: URIs 和 pipeThrough() 管道解壓縮，解壓後直接內嵌為 <pre> 標籤渲染。該方法展示了壓縮技術在微型互動內容中的應用潛力。

### 重點
- 445 字節的 base64 編碼 deflate-raw 壓縮資料 + 14 行 JavaScript 足以產生完整 ASCII 世界地圖
- fetch() 支援 data: URIs 搭配 DecompressionStream('deflate-raw') 實現瀏覽器端解壓
- 無需載入外部地圖庫，實現極簡產物與即時生成

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/4/building-a-world-map-with-only-500-bytes/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Building a World Map with only 500 bytes 
Iwo Kadziela (assisted by Codex) figured out a way to generate a credible ASCII world map using 445 bytes of data: 
 
 The key trick is to use deflate compression, which is then wired together using this neat snippet of JavaScript. I didn't know you could use fetch() with data: URIs like this: 
 fetch('data:;base64,1ZpLsgIxCEXnrM...==').then(
 r =&gt; r.body.pipeThrough(new DecompressionStream('deflate-raw'))
).then(
 s =&gt; new Response(s).text()
).then(
 t =&gt; b.innerHTML = '&lt;pre style=font-size:.65vw&gt;' + t
)
 

 Via Hacker News 

 Tags: ascii-art , data-urls , javascript

</details>