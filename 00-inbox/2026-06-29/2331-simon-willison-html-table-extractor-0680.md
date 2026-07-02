---
id: inbox_22250345
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Jun/29/html-table-extractor/#atom-everything"
author: ""
published_at: 2026-06-29T23:38:21+00:00
fetched_at: 2026-07-01T23:31:30.817436+00:00
content_hash: "0680c648d7e9b5bdb615fd7408e00a49ce63f103db0e6af71a6c941e489ab171"
lang: en
caption_quality: None
raw: true
topics: []
---

# HTML table extractor

Tool: HTML table extractor 
 Yet another in my growing collection of paste-conversion tools. This one accepts pasted rich text from browsers (with embedded HTML tables) and converts every detected table into HTML, Markdown, CSV, TSV, or JSON. 
 Try it out by selecting everything on the Wikipedia List of cities and towns in the San Francisco Bay Area page and pasting it directly into the tool: 
 
 On a similar note, I recently rebuilt my Rich text to markdown tool to add support for tables and generally improve the UI. 
 Update : It turns out Wikipedia has an open CORS API for retrieving the full rendered HTML content of any page - demo here - so I had Codex add the ability to search Wikipedia for a page and then automatically import and display any tables from that page. 
 
 
 Tags: html , tools , wikipedia , cors