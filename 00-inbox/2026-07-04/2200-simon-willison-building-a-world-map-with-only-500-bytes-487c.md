---
id: inbox_2f9a22f7
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Jul/4/building-a-world-map-with-only-500-bytes/#atom-everything"
author: ""
published_at: 2026-07-04T23:09:02+00:00
fetched_at: 2026-07-05T22:00:22.976866+00:00
content_hash: "487c4611618fa9cd5f8e6352c146d84960e316b0c35b666ebb1590494e04044a"
lang: en
caption_quality: None
raw: true
topics: []
---

# Building a World Map with only 500 bytes

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